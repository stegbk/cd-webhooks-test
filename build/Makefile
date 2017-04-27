.PHONY:  clean all install


REPODIR = /opt/cd-webhooks
BUILDDIR = $(REPODIR)/build
SRCDIR = $(REPODIR)/src
TOUCHDIR = $(BUILDDIR)/touch

WEBHOOKS_IMAGE = webhooks-image

ALL_IMAGES = 	$(WEBHOOKS_IMAGE) 

ALL_TOUCHFILES := $(foreach IMG,$(ALL_IMAGES),$(TOUCHDIR)/$(IMG))

all: $(ALL_TOUCHFILES)

clean:
	rm -rf $(TOUCHDIR)
	# Ensure heapster is running
	mkdir $(TOUCHDIR)

$(TOUCHDIR)/$(WEBHOOKS_IMAGE): $(SRCDIR)/docker/Dockerfile-webhooks 
		docker build --file=$(REPODIR)/src/docker/Dockerfile-webhooks \
       --tag=elasticbox/${WEBHOOKS_IMAGE}:latest \
       $(REPODIR)/src && touch $(TOUCHDIR)/$(WEBHOOKS_IMAGE)