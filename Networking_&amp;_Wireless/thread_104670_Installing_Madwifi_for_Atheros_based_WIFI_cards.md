---
title: "Installing Madwifi for Atheros based WIFI cards"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by thezerogroup on 2005-12-16
Installing madwifi is easy. .  . 


```

sudo gedit /etc/apt/sources.list

```

and add the following line to the bottom of the file: 
```

deb ftp://debian.marlow.dk/ sid madwifi
deb-src ftp://debian.marlow.dk/ sid madwifi

```

Now let's update apt
```

sudo apt-get update

```

Now lets install the madwifi packages: 

```

sudo apt-get install madwif*

```

[SIZE="2"]The repositories are maintained courtesy of Martin List-Petersen. . . . [/SIZE]

---

### Post by CaptainMorgan on 2005-12-16
I had everything go smooth with your instructions. Im running Breezy, and I received no errors. Got my hopes up though... rebooted and I still have no signal or access to router or net. Strange though, Wifi-Radar knows it's there but it gets no signal,.. KwifiManager has no signal yet is able to get the correct Access Point. Key is correct, right settings, open wep.. etc. 

I just don't get it.

---

### Post by Lambert on 2005-12-16
Unless I'm missing something this doesn't install the driver. It's just source code that downloads and ends up in /usr/src

There are some steps that need to be added to finish the installation.

Also breezy comes with v .9.6 (which is old) does this need to be uninstalled first? If so how?

---

### Post by CaptainMorgan on 2005-12-16
aye, I found madwifi.org to walk through the steps... so far so good but I get to [B]Makefile.inc:102: Default KERNELPATH not found, using /usr/src/linux
Makefile.inc:109: *** KERNELPATH: /usr/src/linux does not exist.  Stop.
[/B]

Here's my makefile located in /usr/src/madwifi-ng/ :

```
#
# Copyright (c) 2002-2005 Sam Leffler, Errno Consulting
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer,
#    without modification.
# 2. Redistributions in binary form must reproduce at minimum a disclaimer
#    similar to the "NO WARRANTY" disclaimer below ("Disclaimer") and any
#    redistribution must be conditioned upon including a substantially
#    similar Disclaimer requirement for further binary redistribution.
# 3. Neither the names of the above-listed copyright holders nor the names
#    of any contributors may be used to endorse or promote products derived
#    from this software without specific prior written permission.
#
# Alternatively, this software may be distributed under the terms of the
# GNU General Public License ("GPL") version 2 as published by the Free
# Software Foundation.
#
# NO WARRANTY
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# ``AS IS'' AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF NONINFRINGEMENT, MERCHANTIBILITY
# AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL
# THE COPYRIGHT HOLDERS OR CONTRIBUTORS BE LIABLE FOR SPECIAL, EXEMPLARY,
# OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER
# IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF
# THE POSSIBILITY OF SUCH DAMAGES.
#
# $Id: //depot/sw/linuxsrc/src/802_11/madwifi/madwifi/Makefile $
#

#
# Makefile for the HAL-based Atheros driver.
#
DEPTH=	.

# release tag versioning
-include $(KERNELPATH)/ath_version.mk
export EXTRAVERSION

include Makefile.inc

# NB: the order is important here
DIRS=	${ATH_HAL} ${WLAN} ${ATH_RATE} ${ATH} ${TOOLS}

all: configcheck
	mkdir -p ${SYMBOLSDIR}
	for i in ${DIRS}; do \
		$(MAKE) -C $$i || exit 1; \
	done

install:
	@# check if there are modules left from an old installation
	@# might cause make to abort the build
	sh scripts/find-madwifi-modules.sh $(DESTDIR)/lib/modules/$(KERNELRELEASE)

	for i in ${DIRS}; do \
		$(MAKE) -C $$i install || exit 1; \
	done
ifeq ($(DESTDIR),)
	(export MODULEPATH=${MODULEPATH}; depmod -ae)
endif
	echo "KERNELRELEASE=$(KERNELRELEASE)" > ./install.log
	echo "DESTDIR=$(DESTDIR)" >> ./install.log
	
uninstall:
	sh scripts/remove-old-modules.sh
	sh scripts/remove-old-tools.sh

FILES=	ath_hal COPYRIGHT ath include Makefile Makefile.inc \
	README release.h share net80211 ath_rate
HAL_TAG=ATH_HAL_20030802

release:
	DATE=`date +'%Y%m%d'`; TAG="MADWIFI_$${DATE}"; DIR="madwifi-$${DATE}"; \
	cvs tag -F $${TAG} ${FILES}; \
	rm -rf $${DIR}; mkdir $${DIR}; \
	cvs export -d $${DIR} -r $${TAG} linux; \
	(cd $${DIR}; cvs export -r ${HAL_TAG} hal); \
	tar zcf $${DIR}.tgz --exclude=CVS --exclude=hal/freebsd $${DIR}; \
	rm -rf $${DIR}

clean:
	for i in ${DIRS}; do \
		$(MAKE) -C $$i clean; \
	done
	rm -rf ${SYMBOLSDIR}

info:
	@echo "The following settings will be used for compilation:"
	@echo "TARGET       : $(TARGET)"
	@echo "OS           : $(OS)"
	@echo "BUS          : $(BUS)"
	@if [ ! -z "$(TOOLPATH)" ]; then \
	    @echo "TOOLPATH     : $(TOOLPATH)"; \
	fi	
	@echo "KERNELRELEASE: $(KERNELRELEASE)"
	@echo "KERNELPATH   : $(KERNELPATH)"
	@echo "KERNELCONF   : $(KERNELCONF)"
	@echo "MODULEPATH   : $(MODULEPATH)"
	@echo "KMODSUF      : $(KMODSUF)"
	@if [ ! -z "$(DESTDIR)" ]; then \
	    echo "DESTDIR      : $(DESTDIR)"; \
	    echo "SYSTEMMAP    : $(SYSTEMMAP)"; \
	fi

sanitycheck:
	@echo -n "Checking requirements... "
	
	@# check if kernel configuration file is available
	@if [ ! -f $(KERNELCONF) ]; then \
	    echo "FAILED"; \
	    echo "'$(KERNELCONF)' not found."; \
	    echo "You need to configure your kernel."; \
	    exit 1; \
	fi
	
	@# check if specified rate control is available
	@if [ ! -d $(ATH_RATE) ]; then \
	    echo "FAILED"; \
	    echo "Selected rate control $(ATH_RATE) not available."; \
	    exit 1; \
	fi
	
	@# see if uudecode is available
	@if [ -z "$(UUDECODE)" ]; then \
	    echo "FAILED"; \
	    echo "The 'uudecode' tool was not found on your system. Please make sure"; \
	    echo "it is installed in your PATH, then try again."; \
	    exit 1; \
	fi
	
	@echo "ok."

# new targets should be inserted ABOVE this line in order to avoid
# problems with the included kernel configuration file below.
include $(KERNELCONF)

configcheck: sanitycheck
	@echo -n "Checking kernel configuration... "
	
	@# check version of kernel and wireless.h
	@echo $(KERNELRELEASE) | grep -q -i '^[2-9]\.[4-9]\.' || { \
	    echo "FAILED"; \
	    echo "Only kernel versions 2.4.x and above are supported."; \
	    echo "You have $(KERNELRELEASE)."; \
	    exit 1; \
	}
	
	@# check kernel configuration
	@if [ -z "$(CONFIG_SYSCTL)" ]; then \
	    echo "FAILED"; \
	    echo "Please enable sysctl support."; \
	    exit 1; \
	fi
	@if [ -z "$(CONFIG_NET_RADIO)" ]; then \
	    echo "FAILED"; \
	    echo "Please enable wireless extensions."; \
	    exit 1; \
	fi
	@if [ -z "$(CONFIG_CRYPTO)" ]; then \
	    echo "FAILED"; \
	    echo "Please enable crypto API."; \
	    exit 1; \
	fi
	
	@echo "ok."

``` 

IF it's any help. I checked with Syn, the sources are installed.. repo's checked. Most instructions so far appear to have made positive results since I installed Breezy a couple hours ago. This makefile kernelpath is the first.. any suggestions?

thank you

---

### Post by Lambert on 2005-12-16
I don't think that's the correct path. When I downloaded the file it ended up as

madwifi.tar.gz

then when I unzipped it created a file /modules/madwifi  that's where my make file ended.

/usr/src/modules/madwifi$ ls
ath      ath_rate  hal      Makefile      net80211   symbols
ath_hal  debian    include  Makefile.inc  release.h

There are things that need to be cleared up here though. I'm not that knowledgeable with compiling plus this involves the restricted-modules as madwifi is included in that packages. So something needs to happen with that package. Like I said, not that knowledgeable here but I believe to get the latest version to work  you have to 

1. remove restricted-modules (of cousre if you do this you will have to compile and install any module that you need from that package. here is a list of what's in it.)

- madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

2. install build-essentials make and linux-headers from the repositories

3. then to install madwifi it should be this command

sudo make && sudo make install

somebody needs to clear this up as I don't believe first post is complete. more is needed.

Also there is a version of madwifi included in breezy. It's dated but most atheros cards work out of box with no trouble, did you try to get wireless going before installing this version?

---

### Post by CaptainMorgan on 2005-12-16
[QUOTE=Lambert]I don't think that's the correct path. When I downloaded the file it ended up as

madwifi.tar.gz

then when I unzipped it created a file /modules/madwifi  that's where my make file ended.

/usr/src/modules/madwifi$ ls
ath      ath_rate  hal      Makefile      net80211   symbols
ath_hal  debian    include  Makefile.inc  release.h

There are things that need to be cleared up here though. I'm not that knowledgeable with compiling plus this involves the restricted-modules as madwifi is included in that packages. So something needs to happen with that package. Like I said, not that knowledgeable here but I believe to get the latest version to work  you have to 

1. remove restricted-modules (of cousre if you do this you will have to compile and install any module that you need from that package. here is a list of what's in it.)

- madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

2. install build-essentials make and linux-headers from the repositories

3. then to install madwifi it should be this command

sudo make && sudo make install

somebody needs to clear this up as I don't believe first post is complete. more is needed.

Also there is a version of madwifi included in breezy. It's dated but most atheros cards work out of box with no trouble, did you try to get wireless going before installing this version?[/QUOTE]


got it unpacked and like you said it ended up in modules... my Kernepath is still off though...


I definately tried it before do anything... it was first thing i went to after installation.  Still the first thing Im on. If I can get wifi working I can leave the uncomfortable position of being close to the router and go find a comfortable seat later to customize it. :D

---

### Post by Lambert on 2005-12-16
Well let's see a little more about your wireless device.

Run this command

sudo lshw -businfo

look through the output for your wireless device and notice what class it is. Mine looks like this.

Bus info     Device    Class          Description
pci@03:00.0  ath0      network        AR5212 802.11abg NIC

my class is network

then run 

sudo lshw -C <class>

so for me it's

sudo lshw -C network

post that output here.

Also is it a card or internal device? What make model is it?

---

### Post by CaptainMorgan on 2005-12-16
[B]pci@04:02.0   ath0        network        AR5212 802.11abg NIC
[/B]

right on the money... 


after the class run: sudo lshw -C network here is the output for ath0:

```
network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@04:02.0
       logical name: ath0
       version: 01
       serial: <nu:m:b:e:r>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11a
       resources: iomemory:a8400000-a840ffff irq:21

```

---

### Post by Lambert on 2005-12-16
see this line

configuration: broadcast=yes driver=ath_pci .......

this means you have a driver loaded for the device so there's nothing to install.

now we just need to configure your network.

now run and post these commands

iwconfig

sudo ifconfig ath0 up (no output on this one, just needed for next command)

sudo iwlist ath0 scan

post the out put here.

what's your network settings

Is your router on a or g protocol?

open signal: wep: wpa?

if using wep open or restricted? ascii or hexadecimal key?

---

### Post by jdgiotta on 2005-12-16
Does anyone know if MadWifi would help run my Netgear HA501?

It's one of those 802.11a cards that probably lasted a few weeks before 802.11b.

---

### Post by Lambert on 2005-12-16
Linux in general shows mixed results it looks like so all you can do is try.

Do the same as my above post. bootup, plug in the card then run the lshw commands to see if you get the same configuration: line to see if it loads the driver for the device. If so then just try to configure it.

post back results but you may want to start a new thread if you have problems.

---

### Post by stanh on 2007-02-01
Well I've been trying to install wifi on an hp/compaq 4010 for a week.  It has a mini-pci with a Atheros 5212 chipset.

I followed the instructions on the first page and everthing checks, until I run the command 

sudo iwlist ath0

Then I get "ath0 failed to read scan data :device temporarily unavailable.

Network Settings shows this device is enabled, however the blue wireless led on the front panel is not on leading me to believe the card isn't active, at least transmitting....

Any help would be appreciated

---

### Post by stanh on 2007-02-01
Finally...after 1 week.  Problem solved.  I'm connected.  Don't have WEP working yet but I finally have wireless working.

Here's what I found buried on the MADWIFI site.  Seems on some mini-pci cards, pin 13 can cause the radio to be stuck off. Put some tape over the pin and Bingo, it works. This link has some pictures of the pin location.  My card looked a little different, didn't have all the foils shown but I figured it out.

This may not work for your card but it it worth looking into.

[http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt](http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt)

I'm sending this reply.....wireless!!

---

