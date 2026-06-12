---
title: "Belkin f5d8010"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by pottzie on 2010-12-10
I'm trying to get a Balkin f5d8010 working in Ubuntu 10.10, 64 bit. Most of what I see from searching the web is from 2008 or earlier. Anyone know if the newer kernel(s) include support for this, or can I get the drivers somewhere?
 For what it's worth, lspci shows:
```

02:09.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
03:00.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 01)


```

 I came across this.
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=show&redirect=F5D8010](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=show&redirect=F5D8010)
 If it's still current, I'll try it, unless anyone knows of something better.

---

### Post by pottzie on 2010-12-10
Just as an update, I followed the guide, it had several errors (for me, anyway), and fizzled out at about step 7 or 8. I installed ndiswrapper from the Package Manager, but when I tried to install the .inf file, it said it wouldn't work. when i tried it again, ndiswrapper said it was already installed. And it doesn't work, no idea how to check what (or how many!) drivers I've got onboard right now.
 I'm posting using the Belkin usb that I've had for a while, but it's slower than dial up. It works, though.

---

### Post by pottzie on 2010-12-10
Filling in a little more info:
```

pottzie@pottzie-desktop:~$ ndiswrapper -l
autorun : invalid driver!
pottzie@pottzie-desktop:~$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.35-23-generic/updates/dkms/ndiswrapper.ko): Operation not permitted


```

---

### Post by pottzie on 2010-12-11
Digging a little deeper, I followed an updated version of the link I referred to earlier.
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

 kludging around with it, and what I had done earlier, I made it through with somewhat better results. Instruction #9,"gksudo network-admin" didn't work, no matter what i tried, but other than that, it looked OK. No network upon rebooting, so I fell back to trying to use the .inf file from the cd that came with the Belkin. Still got the same errors, and no network or driver installed, ndiswrapper showed "error" when I tried the . inf file. 
 Decided to "dmesg tail," and saw that "kernel is 64 bit, but Windows driver is 32 bit." Yes, i'm running Ubuntu 10.10, 64 bit. The driver did say that it was for Windows XP, but I thought that 32 bit software worked in/on 64 bit systems. Guess that's the problem.

---

