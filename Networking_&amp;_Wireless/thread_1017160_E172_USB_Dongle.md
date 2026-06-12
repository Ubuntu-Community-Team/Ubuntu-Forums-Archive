---
title: "E172 USB Dongle"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by mynydd on 2008-12-20
Hi, i'am running 8.10. My E172 usb dongle connects fine. BUT, the image quality is sub standard. I know this is an option to improve speed but how do I make it display the full quality image?
*Thanks in advance:P*

---

### Post by pytheas22 on 2008-12-20
I'm not sure what you mean by image quality and how it would be affected by the speed of your Internet connection.  If you could please provide a bit more specific information on what you're trying to do, I will try to help.

---

### Post by mynydd on 2008-12-20
Hi, I used to run the stick on vista.The embedded program had an option to view the internet sub standard i.e. it all looked slightly pixelated. Because the stick wasn't downloading the full images its speed would be faster. On 8.10 that is what it is like, and I wish to have the full quality back. I hope this makes more sense.

---

### Post by pytheas22 on 2008-12-20
Thanks for the clarification; I understand better now.  I guess this is like the old tricks that they used to have for speeding up dial-up connections, although I don't know why you'd need it on a wireless connection, which should always be pretty high-speed.

In any case, this seems like a strange kind of setting, and it must be embedded into the device itself, since it persists under Ubuntu.  I think that the easiest way for you to revert to full-quality images would be to plug the device into a Vista machine and use the utility there to set the device to download full images.

There might be a way to reset it from Ubuntu, but it would probably be a lot more complicated than just doing it under Vista.  Are you able to do that?

---

### Post by mynydd on 2008-12-20
Yep, I can do that, good idea.
It is 03:00 here (Wales)so I shall give it a go tomorrow and let you know. Thanks.

---

### Post by mynydd on 2008-12-21
O.K. I have done it. But it has not worked.:(
It is called optimisation. The embedded program called 'VMC lite' does not have the setting. It is only available in the downloaded full blown version of VMC.
If it helps, I can get the whole page to refresh at full 'opimisation' with ctrl + f5.

---

### Post by pytheas22 on 2008-12-21
> The embedded program called 'VMC lite' does not have the setting. It is only available in the downloaded full blown version of VMC.

Can you download the full version of VMC and use it to change the setting?  Thsi is probably the easiest, and possibly only, way to solve the problem.

Also, if you could post the output of this command (while the dongle is plugged in), we can google for the PCI ID of your card and see if it turns anything up:
```

lsusb
```

---

### Post by mynydd on 2008-12-21
I did use the full version, but I guess because that version is on the laptop and not in the usb the command does not hold on the usb?

mynydd@mynydd-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mynydd@mynydd-laptop:~$

---

### Post by pytheas22 on 2008-12-22
I googled for a while but unfortunately can't find anything about how to resolve the image-quality problem from within Ubuntu (for that matter I can't find anyone who mentions having this problem on Ubuntu to begin with).  With the settings changed through Windows, do you still see compressed images there?

Also, just to be positive that this isn't a Firefox-specific issue, could you try installing a different web browser to see if the image quality is low there as well?  For example, you could try Konqueror:
```

sudo apt-get install konqueror
```

After it installs you can find it under the Applications>Internet menu.

---

### Post by mynydd on 2008-12-22
Hi again, I tried Konqueor and songbird both are the same.
I also had a look on the vodafone forum and saw this.
[IMG]http://i472.photobucket.com/albums/rr89/TWM_mynydd/Optimisation700p.png[/IMG]
Oooopppsss don't think you will be able to read that picture. It says.............


Administrator
Group Icon

Group: Administrators
Posts: 925
Joined: 4-August 08
Member No.: 7,443
Handset(s): E220 Mobile Broadband on Mac OSX 10.5.4



	
Hey all

If you download and replace your current VMC version with VMC version 9.2.5 (scroll down, 80 meg download), you'll have an option from the dashboard itself to turn the Optimisation off. I do understand it can cause frustration, depending on what you need or want internet access for.

Uninstall the original, reboot, install the version 9.2.5, reboot, load up and there will be an option either in 'tools' or 'options' (forgive my foggy memory on the placement of it!) for 'Optimisation'. You can there set it to on or off, and any connections running 'through' the VMC 9.2.5 will display images at full quality.

The optimisation is determined at network-level, based on whether your VMC sends the command to disable it or leaves it as it is.

Let me know how you get on smile.gif


Daz

eForum Team 
This issue is not a great hardship for me. So do not waste too much of your time researching it.

---

### Post by pytheas22 on 2008-12-22
Do you know what that poster is referring to with 'tools' and 'options'?  How would you access those settings under Windows?

The thing that I don't understand is where exactly the image-compression setting is stored.  At first, I was thinking that it must be embedded into the device somehow, like in its firmware, in which case changing the setting under Windows should cause it to remain that way under any operating system.

But since changing the setting in Vista doesn't seem to do anything under Ubuntu, I'm wondering now if it's the driver that decides whether images should be compressed.  If that's the case, there may or may not be an option to change it under Ubuntu.  If the driver is not well developed, it may be impossible to change.

Also, what is the output of:
```

lshw -C Network
```

You could also try posting in that forum that you have in your screenshot; maybe someone there has used this device under Linux.

---

### Post by mynydd on 2008-12-23
mynydd@mynydd-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:ce:05:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:12:f8:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 46:36:58:5c:6b:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


I put this question on here because I had read, ubuntu and vodafone had got together to work on mobile broadband. I thought it would have been a straight forward answer. Thanks for your help, but please do not spend too much of your time on it:)

---

### Post by pytheas22 on 2008-12-23
I think Canonical did work with Vodafone to help integrate it into Ubuntu.  I'm not sure why they make it so difficult to change this image-compression setting.  But I'm still not even sure which module is driving the card, so if this doesn't bother you too much, I'm willing to let it go.  Sorry we didn't find a real answer...

---

### Post by mynydd on 2008-12-24
This problem is minor; and I do not wish to tie you up on it when others need your help more.
I am really enjoying the Ubuntu experience. I think it is brilliant to find so many people helping each other for no reward. So, I am off to do my bit and track some 'bugs'. Thank you very much for your time.:P

---

