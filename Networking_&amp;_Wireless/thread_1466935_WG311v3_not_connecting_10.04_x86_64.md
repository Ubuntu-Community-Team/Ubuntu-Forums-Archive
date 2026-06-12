---
title: "WG311v3 not connecting 10.04 x86_64"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by jerome1232 on 2010-04-30
I made the switch to 10.04 today, fresh install from the alt cd.

I'm using ndiswrapper, I Guess I'm using version 1.55, with utils vesrion 1.9

```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-21-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-21-generic SMP mod_unload modversions 

```

In 9.10 I've used the driver from [this]("http://ubuntuforums.org/showthread.php?t=320111") thread, specifically [this]("http://ubuntuforums.org/showpost.php?p=4026062&postcount=14") post, it worked with wep and wpa-psk.

I just installed ndiswrapper and am using the above driver, I can see networks but can't connect to my network open, wep or wpa.

Any one have any ideas or know of another driver that works?

---

### Post by nokbar on 2010-04-30
hmmmm I can't even see any wireless networks.
I am also using the latest ndiswrapper packages.

---

### Post by partner007 on 2010-04-30
Bump. Same issue.

---

### Post by CytotoxicTcell on 2010-05-01
Did this work in 32bit? I remember having this device in 2007. I tryed 64bit and it did not work so i was forced to use 32bit.

---

### Post by jerome1232 on 2010-05-01
As an update with some finagaling, trying different drivers

 I finally got it working with the original driver I mentioned in my op. I always have to reboot after installing the driver to get the changes to take affect.

I also seem to get inconsistent results, If I boot up one time I might not see networks, reboot can see networks but can't connect, reboot it's fine, reboot again can no longer connect... etc...

---

### Post by nate_nightroad on 2010-05-07
> **jerome1232 said:**
> As an update with some finagaling, trying different drivers

 I finally got it working with the original driver I mentioned in my op. I always have to reboot after installing the driver to get the changes to take affect.

I also seem to get inconsistent results, If I boot up one time I might not see networks, reboot can see networks but can't connect, reboot it's fine, reboot again can no longer connect... etc...

same here...however the good news is the netgear finally release windows 7 64bit driver

maybe someone can look into it and get the inf file to work with ndiswrapper

---

### Post by stiiky on 2010-05-08
I've got a similar issue. Except I can't get past ndiswrapper inserting the driver into the shell. I've followed the steps from the ubuntu documentation guide as well as the posts at the top of this thread. After installing drivers, iwconfig reports no wireless extensions at eth0 and lo.

Any tips? cheers

---

### Post by jerome1232 on 2010-05-08
Under 32 bit inserting the module works fine, under 64 bit, I have to put 'ndiswrapper' in /etc/modules and restart, and cross my fingers that it works.

I did try netgears newest win7 driver but it seems to be 32 bit and I couldn't find anything about a 64 bit driver like one of the posts mentioned? Does anyone have more info about that.

I actually just gave it up and bought a F5D9050v3. It's a usb adapter by belkin, works out of the box no headaches. But I do still have the netgear lying around unreturned as of yet so if there's some better success with getting it to work (I'm not switching to 32 bit for wifi) more info is great.

---

### Post by stiiky on 2010-05-08
Thanks for the reply. That would make sense then, as I tried to install it under win7 pro (x64) too and the driver wasn't working (thought windows reported it was an error with the bios). I'll try hiding ndiswrapper elsewhere, otherwise going to have to bite the bullet and actually pay for something for once.
Cheers

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be  helping for other Netgear adapters. Or  You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :smile:

---

### Post by jerome1232 on 2010-06-01
Okay so after much trial and tribulation I think I got it working, I have to leave so I haven't been able to determine if this driver is stable or not yet.

I found this driver [here]("http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64") to work with wpa, it does seem to not connect to wpa2 and crash all usb activity (at least my usb mouse and keyboard stop working while everything else works fine)

However connecting to my network with wpa works fine, albiet the signal is weak compared to the Belkin adapter I'm also using.

Hopefully this helps some of you out.

---

### Post by flash63 on 2010-06-01
Hello,
try this driver for 64bit

[http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522](http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522)

---

