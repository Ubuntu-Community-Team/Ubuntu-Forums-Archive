---
title: "realtek rt8188cus or?"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by ubunt72 on 2013-08-18
[http://wikidevi.com/wiki/Edimax_EW-7811Un](http://wikidevi.com/wiki/Edimax_EW-7811Un)

 RTL8188CUS  
 But, I cannot find this adapter for cheaper than$15.
 

 [https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)
 

 [http://ubuntuforums.org/showthread.php?t=2092934&page=7](http://ubuntuforums.org/showthread.php?t=2092934&page=7)
 

 [http://ubuntuforums.org/showthread.php?t=2139058](http://ubuntuforums.org/showthread.php?t=2139058)
 

 The Edup EP-N8508GS USB is $8 and has the rtl8188cus chipset, also.   

 

 Or, alternatively, the TP-Link TL-WN725N nano wifi adapter which is similar but has a different realtek chipset/driver.    
 [http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2](http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2)
 

 Most will probably be version 2 by now so using the 8188eu driver.    
 

 [http://packages.ubuntu.com/raring/all/linux-firmware/filelist](http://packages.ubuntu.com/raring/all/linux-firmware/filelist)
 The firmware looks like it's missing in the list?
 

 So, the how-to in the other threads apply?
 

 The EDUP EP-N8531 has the ralink RT5370 chipset but the ralink drivers for this sounds like it is a routine, too, and the adapters having this chipset seem to not have as good a signal as the realtek ones?

I'm leaning towards the Edup EP-N8508GS but I'd like some feedback particularly from those who have these nano dongles that have the rt8188cus chipset.   Is the most recent way to install it straight forward?   Please recommend (something)! :)

---

### Post by kurt18947 on 2013-08-19
If you want plug 'n' play and are running 12.10 or later, I'd recommend the RT5370.  I have one of each, Edimax EW-7811Un & an Ebay no-name RT5370.  The Edimax won't work without a Realtek driver and Realtek hasn't been real good about keeping that driver updated.  The driver on RealTek's site works with 12.04 & 12.10 but not 13.04 or 13.10.    I'm using a modified driver found here on 13.04: 
[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)
It works well in 13.04 but I'm not sure about 13.10.  The upside to the Edimax is signal strength and speed are very good for such a small form factor.

The RT5370 performance seems to depend on the router or wireless access point.  Some are pretty strong, others are pretty weak.  Bear in mind my 5370 is a generic adapter and I doubt there was much effort expended on antenna optimization.  I haven't tried the RT5370 on 12.04 so don't know if it works out of the box there or not.

---

### Post by ubunt72 on 2013-08-19
Thanks for your reply, Kurt!
RT5370 firmware appears to be included in the firmware-ralink package if you check the Debian wiki.   So, in theory, using a flavour of Debian, you need to install the 'firmware-ralink' package and then the ralink RT5370 devices should work after that.    But, I cannot find it listed in any Ubuntu package. 

 In Ubuntu, it appears, the firmware packages are all within the linux-firmware package.   
 I only see it up to rt3290.bin, though.

 [https://help.ubuntu.com/community/WifiDocs/Device/Ralink_RT5370](https://help.ubuntu.com/community/WifiDocs/Device/Ralink_RT5370)
 [http://askubuntu.com/questions/310572/edup-ep-n8531-wireless-usb-nano-adapter-driver-install](http://askubuntu.com/questions/310572/edup-ep-n8531-wireless-usb-nano-adapter-driver-install)

This is an old driver:
2011_0407_RT3070_RT3370_RT5370 _RT5372_Linux_STA_V2.5.0.2_DPO.bz2

 Ralink has merged with a company known as Mediatek and they have as the latest driver:
2.5.0.3 for RT5370.
 But, the download is not there.   You have to email mediatek?!?    Ridiculous?
 
 [http://wikidevi.com/wiki/Ralink_RT5370_Reference_Design](http://wikidevi.com/wiki/Ralink_RT5370_Reference_Design)
 
I found a file online:   Ralink_RT3070_LinuxSTA_V2.5.0.3.zip
I think mediatek might email this file?
Either way, this is an extremely aburd process to get the most recent/correct driver?   I'm guessing these companies are not keeping up to date with kernel changes and at times, you have to compile the driver with the kernel or something?   This ambiguity doesn't make me want to order a ralink device and the realtek ones aren't much better.

Edit:  I bet you have to make sure this is installed/completed, too??????:
                        You have to install Linux headers corresponding to your kernel release, to get the build directory mentioned:

 apt-get install linux-headers-[version]
 You can get the kernel release by typing:
 uname -r

Probably the package, 'build-essential' too?

---

### Post by chili555 on 2013-08-19
Here ya go:```
$ modinfo [COLOR="#FF0000"]rt2800usb [/COLOR]
filename:       /lib/modules/3.8.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL 
[COLOR="#FF0000"]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E11543F7E315F8F145D43CA
<snip>
alias:          usb:v148Fp[COLOR="#FF0000"]5370[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
<snip>

```I believe that's what you are looking for.

---

### Post by ubunt72 on 2013-08-19
Yes, that looks interesting.   Is that your output?  However, it looks like it's using an older driver version, perhaps?  Ver. 2.3.0?   I guess the main thing is that it is working.   How are your connections and speeds?   Was it plug-n-play using the linux firmware package or? 

I discovered that either chipset (the realtek and ralink) is available at sites like ebay with these nano usb adapters for about $8 (for either realtek or ralink).   So, if it's not the best result, at least it won't cost much but time and under ten bucks.

---

### Post by chili555 on 2013-08-19
> Is that your output? Yes, but it's the same for anyone running Ubuntu 13.04.>  How are your connections and speeds? Was it plug-n-play using the linux firmware package or? I don't have the device. My point was to demonstrate that the driver exists in 13.04 by default and the world isn't nearly as primative as this:> this is an extremely aburd process to get the most recent/correct driver? I'm guessing these companies are not keeping up to date with kernel changes and at times, you have to compile the driver with the kernel or something? That is, the driver for these common devices exists in a default install of Ubuntu and, for that matter, the firmware. It ought to work out of the box.

---

### Post by kurt18947 on 2013-08-20
I did have a infrequently used notebook with running 12.04 so I plugged the RT5370 based device in. The command 'uname-a' indicated that kernel 3.2 was in use, not 3.5 from 12.04.2.  The device worked without any magic spells or incantations, just a couple minutes in 'network connections' to remove several old obsolete connections and define a current wifi connection.

---

