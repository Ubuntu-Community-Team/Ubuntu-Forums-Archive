---
title: "Otus ar9170 wireless driver"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by azteech on 2009-05-03
Does anyone know if the Otus ar9170 wireless driver has been incorporated into 9.04? If not, is it made available in the repositories?

Reason for asking: have a Netgear WN111v2 wirless adapter. I am not able to make it work in 8.04.

Have tried the recommended method ( [http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520) ) found here on the forum. Unfortunately every time I attempt to use ndiswrapper, I am told I am using an incorrect windows driver, though I know it is not.

lsusb shows that the adapter is being recognized by linux. so, I know it is not the adapter that is at fault.

Hope there is an answer some where that I am over looking. Any assistance on this issue would be appreciated.

---

### Post by Euphorion on 2009-07-03
Hallo

This advice may be coming a little late, but I have just only seen your post. If you have upgraded to intrepid or jaunty, does not matter for this link is applicable. The drivers are not included in Jaunty or in the repositories, will be included the .30 Kernel. The link refers to the German Ubuntu Community and is an How To in order to install the native ar9170 drivers. I have a D-Link DWA-160 using the same chip and have managed to get it to work with jaunty using this how to.

[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

The text is in German, but the commands are in English and you should be able to follow them alright. One thing in jaunty when the make install command is issued, the script will after doing its job hang with following text which will repeat itself over and over.

```
Running athenable ath5k...
Disabling ath_pci ...mv: Aufruf von stat für "volatile/ath_pci.ko" nicht möglich: No such file or directory
FATAL: Could not rename /lib/modules/2.6.28-11-generic/modules.alias.bin.temp into /lib/modules/2.6.28-11-generic/modules.alias.bin: No such file or directory
```Just terminate the script with CTRL + c  or q this does not affect the working of the ar9170 driver it will be loaded and will work, this occurs owing the fact that Jaunty no longer supports the old madwifi drivers.

Hope it works for you as it did for me. Should you need some help with the odd German word I can help you there.

---

