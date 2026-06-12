---
title: "Netgear WG311v2 mixup"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by aeolist on 2006-06-23
So I'm running 6.06 after Windows 2000 nuked itself last week. I haven't used Linux in a very long time and am therefore pretty rusty. I picked Ubuntu from some recommendations and I have to say I'm extremely impressed with it.

I have a few small problems though. I was having trouble getting my Netgear WG311v2 working so I used this guide to try and fix it: [https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111)

I followed it exactly and now my wireless adapter is no longer listed in my networking configuration menu. I just found this now and feel pretty stupid: [http://ubuntuforums.org/showthread.php?t=198598](http://ubuntuforums.org/showthread.php?t=198598)

So now I'm wondering how to get everything back to normal so I can get this thing working.

I'm also contemplating buying a Linksys WMP54G and ridding myself of this piece of Netgear crap that has been nothing but trouble since I bought it. If I install this will Ubuntu automatically detect and set it up?

Thanks, and please be gentle.

---

### Post by aeolist on 2006-06-23
Someone please help.

---

### Post by noname101 on 2006-06-24
If your using ndiswrapper, then you need to blacklist acx_pci or acx. Though you can get the card to work without ndiswrapper, very easily just add options acx firmware_ver=1.2.1.34 to /etc/modprobe.d/options. 
```
sudo gedit /etc/modprobe.d/options
```
add at the bottom:
options acx firmware_ver=1.2.1.34
If that firmware version doesn't work try 1.2.0.30.
From [this]("http://ubuntuforums.org/showthread.php?t=198598") thread.

---

### Post by aeolist on 2006-06-24
I never did anything with ndiswrapper

---

### Post by forsaken163 on 2006-06-25
I need some help too. Did the exact same thing as person above: followed instructions found here: [https://help.ubuntu.com/community/WifiDocs/Driver/acx111?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/acx111?highlight=%28WifiDocs%2FDriver%29)

and now my wireless card doesn't show up anymore. Everything up until the last part, adding acx.ko works fine, but when I run this: sudo insmod acx.ko i get the error: insmod: can't read 'acx.ko': No such file or directory
so, I really need some help.
Thanks in advance.

---

### Post by aeolist on 2006-06-27
So, I've looked into ndiswrapper and I think I can get this working if I can get the system to recognize the Netgear adaptor like it did when I first installed Ubuntu. I don't know what precisely that "fix" did to my modules, but I'd really appreciate some help getting it fixed.

I've gotten the OS set up just the way I like it and I'd *really* rather not reinstall from scratch.

---

### Post by forsaken163 on 2006-06-28
Try this: ```
 lsmod | grep acx 
``` and tell me what you get. If you get nothing, I believe you need to copy the two files that this walkthrough had you move: [https://help.ubuntu.com/community/WifiDocs/Driver/acx111?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/acx111?highlight=%28WifiDocs%2FDriver%29) back to their original locations, and then run ```
 
sudo insmod acx.ko 
sudo depmod -a
```

Make sure to also have this in /etc/modprobe.d/options (sudo and gedit)
```
# Ensure a working version of the acx111 firmware is used.
options acx firmware_ver=1.2.1.34
```

Also run ```
sudo iwconfig wlan0 essid YOURSSID 
``` and then reboot. Hopefully, your wireless will connect autmatically on next load.

I personally just reinstalled everything and just added the firmware code to /etc/modprobe.d/options and everything has been working decently enough for me.

I don't know anything about ndiswrapper; i haven't tried using it. It would take someone like 30 days constant to crack your WEP key...just use that. Let me know if the above works for you!

---

### Post by bigken on 2006-06-28
[quote=noname101]If your using ndiswrapper, then you need to blacklist acx_pci or acx. Though you can get the card to work without ndiswrapper, very easily just add options acx firmware_ver=1.2.1.34 to /etc/modprobe.d/options. 
```
sudo gedit /etc/modprobe.d/options
``` add at the bottom:
options acx firmware_ver=1.2.1.34
If that firmware version doesn't work try 1.2.0.30.
From [this]("http://ubuntuforums.org/showthread.php?t=198598") thread.[/quote]

This worked a treat for me no probs :D

---

