---
title: "NDISWRAPPER cannot blacklist driver"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by SteveZsuzska on 2009-04-23
Hi,

I hope someone will be able to help with this one as I've run out of ideas.

I'm trying to use a TP-LINK TL-WN321G USB wireless card with Intrepid. I checked that it was compatible with Linux before I bought it and I gather it needs driver rt73. I installed the XP driver from the CD that came with it using the graphical front end for NDISWRAPPER. When I try to use it, it recognises the wireless network and some days it will connect but on other days the Network Manager applet will just spin for a while and then the dialogue box will appear asking for the WEP key (which is already filled in and correct). If I enter ndiswrapper -l I get:
rt73 : driver installed
        device (148F:2573) present (alternate driver: rt73usb)
I gather this means that the native driver might be conflicting with ndiswrapper so i tried to blacklist it by adding 'blacklist rt73usb' to the end of /etc/modprobe.d/blacklist but this changes nothing, even after reboot. My network is ad hoc and uses a 64/128 bit hex key. I can connect to it using a laptop running 7.04 with a Netgear card.

Any ideas why I cannot blacklist this driver?

Thanks,

Steve

---

### Post by chili555 on 2009-04-23
> Any ideas why I cannot blacklist this driver?According to *modinfo rt73usb*, this module depends on several others:```
depends:        rt2x00lib,rt2x00usb,crc-itu-t
```I suspect that when your card is being detected, one of these is loaded, which itself then loads *rt73usb*. I suggest blacklisting all of these to see if the problem goes away. Please post back so the searchers will know what worked...or not.

---

### Post by SteveZsuzska on 2009-04-24
Thanks for the reply. I think you may be correct about the other drivers. lsmod indicated that rt2x00usb, ndiswrapper and ohci_hcd were associated with usb. So I blacklisted rt2x00usb and it no longer appears. 

The connection appears to be a little more reliable but not completely so. rt73usb is not listed at all when I do an lsmod, but I still get the message about the alternate driver from ndiswrapper. If it doesn't appear in the lsmod output, does this mean it's not loaded? Any idea why ndiswrapper still refers to it? Thank you for your patience with a newbie.

Steve

---

### Post by chili555 on 2009-04-24
> So I blacklisted rt2x00usb and it no longer appears. And how about the others I quoted? Does lsmod show that any of them are loaded? I'd blacklist them, too.> If it doesn't appear in the lsmod output, does this mean it's not loaded? Correct. It is not loaded.> Any idea why ndiswrapper still refers to it?Nope.

---

