---
title: "Atheros 5007 fix"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by xenosaga456 on 2009-06-08
Download link at bottom of page

Atheros 5007 or 5007a to work with the following commands in ubuntu

MAKE SURE U EXTRACT THIS TO THE DESKTOP!!!!!!!    !!CRITICAL!!


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

[B]
Download here: [http://thepiratebay.org/torrent/4941604](http://thepiratebay.org/torrent/4941604)[/B]

---

