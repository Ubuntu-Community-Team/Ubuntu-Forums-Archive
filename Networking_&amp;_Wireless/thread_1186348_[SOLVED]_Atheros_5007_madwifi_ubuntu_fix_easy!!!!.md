---
title: "[SOLVED] Atheros 5007 madwifi ubuntu fix easy!!!!"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by xenosaga456 on 2009-06-13
Download link at bottom of page

Atheros 5007 or 5007a to work with the following commands in ubuntu

MAKE SURE U EXTRACT THIS TO THE DESKTOP!!!!!!! !!CRITICAL!!


1. First go to System> Administration-> Hardware Drivers "and disable by un-ticking the following option"

Atheros Hardware Access Layer (Hal)
support for Atheros 802.11 wireless LAN cards

Then reboot your system




2. After reboot do thease commands in Terminal



cd Desktop/Atheros\ 5007\ fix/madwifi-hal-0.10.5.6

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot




3. Finally go to System> Administration-> Hardware Drivers "and re-enable by ticking the following option"

Atheros Hardware Access Layer (Hal)
support for Atheros 802.11 wireless LAN cards


at this point make sure everything conserning Atheros is Enabled and then reboot one more time and it should work



(Also with the torrent i have a nother text in the tar.gz that tells you how to get the activity LED to work on ur WLAN switch if u have one)


Download here: [http://thepiratebay.org/torrent/4941604](http://thepiratebay.org/torrent/4941604)

---

### Post by kbrowne1 on 2010-01-31
I couldn't find the document you mentioned on the torrent site. Please update the address, or just give us the file name so we can search the site for it.

---

### Post by pdc on 2010-01-31
If you google on 

> madwifi hal

the first link that comes up is

[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

you will find a series of tar.gz files

you will need to "unpack" the one you download with the command

> tar -zxvf <filename>

but when you use the terminal you need to be "inside" the place that you downloaded your file to

---

