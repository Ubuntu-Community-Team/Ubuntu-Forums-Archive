---
title: "ndiswrapper stops"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by aaronhahn777 on 2009-03-04
I've only been using ubuntu since christmas and I am having some difficulties with "sudo modprobe ndiswrapper"

I installed a d-link usb wireless device (took me forever), but now I find that the wireless often cuts out after using it for some time.

I've been reading other similar posts ( [http://ubuntuforums.org/showthread.php?p=1809544#post1809544](http://ubuntuforums.org/showthread.php?p=1809544#post1809544) ), but I cannot solve this one on my own.  I don't want to do a fresh install and I had a feeling the following file contents might help.  

Any tips would help.  Thanks in advance.

Here is my /etc/network/interfaces:
# The loopback network interface
auto lo
iface lo inet loopback

Modules file:
# modules loading at boot
loop
lp
fuse
ndiswrapper

My blacklist file:
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m)
blacklist snd_aw
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp

---

### Post by kevdog on 2009-03-04
Can you be more specific on what problems you are having with sudo modprobe ndiswrapper?

Thanks.

---

### Post by aaronhahn777 on 2009-03-04
My network manager will disconnect me from wireless after a few minutes of browsing.  Sometimes I have 15 minutes, other times I only have a few seconds.  After this, I am unable to start up the wireless again. 

It's rather intermittent...  sometimes the wireless works when I reboot., other times it doesn't.  I tried removing "ndiswrapper" from "modules list" and manually running it from the terminal when I need it.  But still, I run the command "sudo modprobe ndiswrapper" and it might or might not work.  Furthermore, it will quit working after a few minutes.

I've read several posts and I think it has something to do with ndiswrapper.  Should I use a different version?  Perhaps something in my blacklist is causing another module to run (or not in my blacklist)?

Any help? (i'm a beginner in linux)

---

### Post by aaronhahn777 on 2009-03-18
just bought a "retail plus+ IEE 802.11B/G V1.0" and it worked flawlessly out of the box...  

after wasting 40 hours with d-link and ndiswrapper... and almost going back to xp...  dang that's nice (also cheapest one in the store... $24)


Simply:
>installed 8.10
>inserted usb stick
>enjoyed surfing

---

### Post by aaronhahn777 on 2009-03-18
second thought... sometimes it disconnects after surfing for some time.

---

