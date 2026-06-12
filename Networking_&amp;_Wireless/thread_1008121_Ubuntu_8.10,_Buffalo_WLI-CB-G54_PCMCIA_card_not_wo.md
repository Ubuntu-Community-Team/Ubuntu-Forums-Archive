---
title: "Ubuntu 8.10, Buffalo WLI-CB-G54 PCMCIA card not working, ndiswrapper installed"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by marty pain on 2008-12-11
Hi all. I have been searching this for a few days now, and I still completely stuck.

Ubuntu 8.10
Buffalo WLI-CB-G54 PCMCIA Card

I found this post with the same problem
[http://ubuntuforums.org/showthread.php?t=29160&highlight=WLI2-PCI-G54](http://ubuntuforums.org/showthread.php?t=29160&highlight=WLI2-PCI-G54)

However, I have installed NDISGTK from the Ubuntu CD, added the driver using the GUI from the original CD came with the card. The driver is present in the installed hardware list, and it notes the hardware is present. No lights are on the card (power or connection).

I went through the post above. $ sudo ifup wlan0 reported ignoring unknown interface as stated in the post. I added the "iface wlan0 inet dhcp" to the interfaces file in /etc/network and re-booted the machine. Still no luck. I checked the RadioState in all the config files in the location mentioned (etc/ndiswrapper/bcmwl5) and all were set to 0. However, the diver name on my machine is different to the one in the post. The .inf file has a different name (I'm not at the machine right now so can't check the name) but the .sys is named bcmwl5.

So still no luck and I can't find any more information. The only differences between my system and the above post is the name of the driver within ndiswrapper, and on my system I don't have a /etc/modules file. Is this due to the version of Ubuntu or should I create this file and move ndiswrapper there?

Any help with this would be very appreciated. Would love to get this system to a usable state so I can finally start using Linux on a regular basis.

Thanks!

---

### Post by marty pain on 2008-12-11
Does nobody have any ideas on this? Should I just buy a different card?

---

### Post by Ayuthia on 2008-12-11
Can you post the results of:
```
uname -a
lspci -nn
lsusb
lshw -C network
dmesg|grep ndiswrapper
```
It sounds like you have installed ndiswrapper correctly, but it might be that the module was not able to load properly.

---

### Post by marty pain on 2008-12-11
Thanks, I can post the results up later today. At work for the moment so will have to wait until I get home.

Thanks for this!

---

### Post by medic563 on 2009-05-16
Anyone get this card working?  What is the trick?

---

