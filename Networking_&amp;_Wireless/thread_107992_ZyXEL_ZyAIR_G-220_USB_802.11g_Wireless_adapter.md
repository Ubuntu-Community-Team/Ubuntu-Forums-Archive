---
title: "ZyXEL ZyAIR G-220 USB 802.11g Wireless adapter"
date: 2005-12-24
forum: Networking &amp; Wireless
---

### Post by blixel on 2005-12-24
I just bought the ZyXEL ZyAIR G-220 USB 802.11g Wireless adapter.  Before
opening the box, I searched around google for about an hour to see if this
USB adapter worked with Linux.  I found some encouraging links so I decided
to open the box and give it a shot on my 12" Apple iBook which has a fresh
install of Ubuntu 5.10

I opened a terminal and typed "sudo tail -f /var/log/messages", and then I
plugged in the USB adapter.  The light on the USB adapter came on, and I saw
some activity in the log.

```
Dec 24 16:56:08 localhost kernel: [ 1837.403412] usb 4-1: new high speed USB device using ehci_hcd and address 6
Dec 24 16:56:09 localhost kernel: [ 1838.078196] zd1211 - version 5000
Dec 24 16:56:09 localhost kernel: [ 1838.093174] Release Ver = 3043
Dec 24 16:56:09 localhost kernel: [ 1838.093197] EEPORM Ver = 4330
Dec 24 16:56:09 localhost kernel: [ 1838.113580] zd1211: probe of 4-1:1.0 failed with error -5
Dec 24 16:56:09 localhost kernel: [ 1838.113595] usbcore: registered new driver zd1211
Dec 24 16:56:09 localhost usb.agent[5819]:      zd1211: loaded successfully
```

So the USB adapter appears to have a Linux module, and it appears to load automatically upon insertion.  That's a good thing, I think.  But ...

```
david@archangel:~$ dmesg  | grep zd
[   56.857261] zd1211 - version 5000
[   56.881085] zd1211: usb_control_msg 1 fail: FFFFFFB9
[   56.881089] zd1211_Download_IncludeFile failed
[   56.881097] zd1211: probe of 4-1:1.0 failed with error -5
[   56.881108] usbcore: registered new driver zd1211
```

I notice in the dmesg output that "Download_IncludeFile failed" ... not sure what that means, but obviouslly something isn't right.

```
david@archangel:~$ lsmod | head
Module                  Size  Used by
zd1211                242376  0
rfcomm                 45852  0
l2cap                  28356  5 rfcomm
bluetooth              60712  4 rfcomm,l2cap
cpufreq_userspace       5356  1
cpufreq_stats           6468  0
cpufreq_powersave       1888  0
cpufreq_ondemand        7580  0
cpufreq_conservative     8868  0
```

I can see that the module is indeed loaded ... but from there, I don't know what to do.  When I type "ifconfig -a", there are no new network adapters for me to setup.  And when I go to the System -> Administration -> Networking UI tool, there are no additional network adapters there either.  (Not surprising of course since they don't appear with "ifconfig -a".)

Based on the message in the log, it appears as though something is failing, but I'm not sure what.  I've tried unplugging the adapter, removing the module, and plugging it back in.  That of course (and unfortunately) didn't "magically" solve the problem.

Any ideas?  Anyone?

---

### Post by djgenesis on 2005-12-24
Have you tried reistalling the drivers? Do you know if the hardware has windows drivers? Give ndiswrapper a shot. 
Just an idea. Hope it helps
Genxx

---

### Post by blixel on 2005-12-24
[QUOTE=djgenesis]Have you tried reistalling the drivers? Do you know if the hardware has windows drivers? Give ndiswrapper a shot. 
Just an idea. Hope it helps
Genxx[/QUOTE]

I tried unloading and reloading the module, if that's what you mean?

Do I have to download firmware or something like that?

---

### Post by JonnyRo on 2006-07-31
Try contacting these folks.

[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

There is an asterisk next to the driver support entry for your card.  Maybe you can help them out with some testing, and in turn they could help you get your stuff working.

---

### Post by az on 2006-07-31
> **JonnyRo said:**
> Try contacting these folks.

[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

There is an asterisk next to the driver support entry for your card.  Maybe you can help them out with some testing, and in turn they could help you get your stuff working.

Yeah.  Use the latest version (83) of the driver.  It's a dynamic project and a lot of changes are in the latest version.  The next version (the rewritten one) is now part of the official kernel tree (2.6.18).

Install linux-headers-386 (or whatever your architecture) and build-essential.  Dowload the newest version of the driver and unpack it.  Make and make install it.  I'm not sure if that will overwite the zd1211 driver that ships with ubuntu or not.  But try finding the zd1211.ko module you just built and loding it

insmod zd1211.ko

and then insert your device.  If everything works, make sure that driver is loaded instead of the old one.  

You will have to keep recompiling the new driver every time you update your kernel. 

But it's a great device with fully-GLPed drivers and redistributabel firmware.

---

### Post by Bl@de on 2006-09-10
Hi everybody! I also own a ZyAIR g-220 usb dongle and I've just installed the latest kubuntu. I installed the latest zydas driver (83) but I can't get it working... ](*,) 

The dongle is recognized by the driver and I am able to activate it with

[INDENT]ifcofig wlan0 up[/INDENT]

and then set the essid of my AP with

[INDENT]iwconfig wlan0 essid MY_ESSYD[/INDENT]

I use no dhcp and I set the IP with

[INDENT]ifconfig wlan0 xxx.xxx.xxx.xxx[/INDENT]

But it does not stick to the AP!!!
I disabled every kind of protection on the AP... so no wep/wpa nor mac address filtering.
To be sure to load the latest module I compiled I used 

insmod path/zd1211.ko

Even if I try with the graphical manager shipped with kubuntu, no way: it sees the AP and even other ones (so scanning works), with the correct channel, but it does not stick to it:confused: 

Am I missing something or doing something wrong? Any clue?
Thank you,
Bl@de

---

### Post by blixel on 2006-09-10
My ZyXEL ZyAIR G-220 works with Ubuntu 6.06 LTS on my G4 12" iBook without doing anything.

However, it only works if I plug the dongle directly into the USB port on the iBook.  If I use the extension cable, it doesn't work.

---

### Post by Bl@de on 2006-09-10
> **blixel said:**
> My ZyXEL ZyAIR G-220 works with Ubuntu 6.06 LTS on my G4 12" iBook without doing anything.

However, it only works if I plug the dongle directly into the USB port on the iBook.  If I use the extension cable, it doesn't work.

Uhm... My one is connected through the ext cable... I'll give a try without it (it seems so strange however).
What driver do you use? the zydas one or are yu using ndiswrapper?

---

### Post by Bl@de on 2006-09-10
Hi again.
I tried removing the ext cable but it does not change :-k 
I've been able to make it working using ndiswrapper and winxp drivers... Now it connetcs and I'm able to surf the internet, but i seems not so responsive...

Maybe I'll try with a new release of zydas in the future.

However does anybody use successfully the g220 with zd1211 drivers and not trough ndiswrapper?

---

### Post by krzysz00 on 2007-07-15
> **JonnyRo said:**
> Try contacting these folks.

[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

There is an asterisk next to the driver support entry for your card.  Maybe you can help them out with some testing, and in turn they could help you get your stuff working.

that site doesn't exist anymore

---

### Post by Poiema on 2007-09-17
This site now forwards you here:
[http://zd1211.wiki.sourceforge.net/](http://zd1211.wiki.sourceforge.net/)

---

