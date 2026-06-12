---
title: "Linksys WUSB600N not recognized"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by Gemu on 2010-09-03
I think lightning may have killed it. It was working fine. Now I cant get it recognised no matter what I do. It also quit working in Win XP where I never had a problem with it because it had its own connection software. Any ideas???

dmesg yields this-

 RTUSB disconnect successfully
[  312.876034] usb 2-1: new full speed USB device using uhci_hcd and address 7
[  312.996021] usb 2-1: device descriptor read/64, error -71
[  313.220031] usb 2-1: device descriptor read/64, error -71
[  313.436038] usb 2-1: new full speed USB device using uhci_hcd and address 8
[  313.556025] usb 2-1: device descriptor read/64, error -71
[  313.780031] usb 2-1: device descriptor read/64, error -71
[  313.996032] usb 2-1: new full speed USB device using uhci_hcd and address 9
[  314.404022] usb 2-1: device not accepting address 9, error -71
[  314.516021] usb 2-1: new full speed USB device using uhci_hcd and address 10
[  314.924029] usb 2-1: device not accepting address 10, error -71
[  314.924046] hub 2-0:1.0: unable to enumerate USB device on port 1
[  343.664017] pan0: no IPv6 routers present
[  809.024049] usb 1-1: new high speed USB device using ehci_hcd and address 10
[  809.182271] usb 1-1: configuration #1 chosen from 1 choice
[  809.182837] 
[  809.182839] 
[  809.182840] === pAd = ffffc20020b41000, size = 598568 ===
[  809.182841] 
[  809.182845] <-- RTMPAllocAdapterBlock, Status=0
guest3@guest3-desktop:~$

---

### Post by MaindotC on 2010-09-03
Hi, Gemu.  Please try following the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know where you are having difficulty.  In the future, [this thread](http://ubuntuforums.org/showthread.php?p=6183681) will tell you how to post a wireless card issue and the typical information necessary for others to assist you.  Also, check [this wiki](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) to see if your wireless card is supported.  I believe I helped someone with a post the other day and it was a similar card.

I really want your wireless card to work, but I need you to follow those steps first.  It sounds to me like you may not have the proper driver installed or configured properly.  You may even want to try ndiswrapper if the native driver doesn't work.  However, if you think lightening killed it then it could very well be a hardware issue and you could get a new, supported, wireless card for $25.

---

### Post by Gemu on 2010-09-04
Thanks for the reply. It must be a problem with the usb adapter. I tryed reinstalling the thing and nm-tool, lshw -C network yields nothing, as well as iwconfig.

It didn't work to start with in Ubuntu 10.04 until I recompiled the software in the new kernel. It had worked in 9.04 out of the box. Now it doesn't work with 9.04. No command can find the device. On windows XP the device is recognized for a second and keeps getting bumped off.

Its almost like the USB device has its communicating addresses changed inside. It could be fryed I guess.


 Can you recommend a USB wireless card. I like USB with an extension cord because of its versatility. That one was great but they are pricey.

---

### Post by bkratz on 2010-09-04
You might look here

[http://wize.com/wireless-adapters/t117480-ubuntu](http://wize.com/wireless-adapters/t117480-ubuntu)

---

### Post by MaindotC on 2010-09-04
> **Gemu said:**
> I tryed reinstalling the thing and nm-tool, lshw -C network yields nothing, as well as iwconfig.

Definitely sounds like a hardware problem :(  lshw should list it but just for kicks you can also try lsusb.
> 
 Can you recommend a USB wireless card. I like USB with an extension cord because of its versatility. That one was great but they are pricey.

Here is a list of [Supported Wireless Cards](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) that have been tested for Ubuntu.  Here is a list of [supported wireless cards tested on Linux in general](http://linuxwireless.org/en/users/Devices).

---

