---
title: "Problems with NDISWrapper and Broadcom Chipset"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by n.b.r. on 2006-03-08
Hi all, I'm having trouble with ndiswrapper, which I have never used before. I am running Breezy on an HP pavilion ze4900, lcpci reports my wireless nic as ```
0000:02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```
I followed the instructions at [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683), using the win32 broadcom drivers that came on the HP restore cd - I went through the process twice, trying both bcmwl5.inf and bcmwl5a.inf. The interface wlan0 now shows up in the network config gui, when I enable it and set it as the default gateway, it doesn't connect to my network. The command ```
#iwlist wlan0 scan
``` returns ```
wlan0        no scan results
```. The output of iwconfig wlan0 is ```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
the output of ifconfig wlan0 is
```
wlan0     Link encap:Ethernet  HWaddr 00:90:4B:9D:44:A6
          inet6 addr: fe80::290:4bff:fe9d:44a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e0200000-e0201fff
```
I added ndiswrapper to /etc/modules because the ndiswrapper module was not loading at boot time by default. Also, when the machine boots, it hangs for a while when it tries to bring up the network interfaces - long enough for the frame buffer to go away and revert to a plain old console while it finishes booting.

I also threw another wireless card in the pcmcia slot (an old netgear with a prism chipset) and it worked instantly, so I'm pretty sure the problem is with ndiswrapper.

Any help would be most appreciated!
Thanks

Nick

---

### Post by mdmarmer on 2006-03-08
The .inf file is not enough for the Broadcom cards

Copy the .sys and .cat files from Windows as well

Also, the newest versions of ndiswrapper have problems with Broadcom

If the first answer doesn't work, make sure you have removed any drivers that were there before (ndiswrapper -e xxxxx.inf) and make sure you have not upgraded ndiswrapper

Mike

---

### Post by eltaito on 2006-03-08
Broadcom cards are a nightmare.  I have a emachines M5310 (save your emachines suck jokes...i know i know :) )....anyway it has a built in broadcom wireless card.  I had the EXACT same problems you do.....my problem actually turned out to be the fact that, with my particular card, there is no way to actually tell if it is ON..and in fact, most of the time it wouldn't turn on no matter what method I used (booting into Windows to turn it on and then back into Linux just isn't an option...its rediculous).....older versions of ndiswrapper worked better for me, but everytime I upgraded the kernel I had to go through the entire process again.  My recommendation is to just use the PCMCIA card you have and save yourself a head-ache......i eventually got tired of the broadcom/ndiswrapper problems and purchased a Netgear 511T for $30 which worked out of the box in Breezy.  From now on I am definately boycotting Broadcom based products (and ATI products but thats another issue all together)

---

### Post by n.b.r. on 2006-03-08
Thanks for the replies.
I had copied the .sys files the first time but not the .cat. I went through the same procedure, only this time with the .cat files also on my desktop - still no luck. I'm having the same problem. I am using the ndiswrapper 1.1-4ubuntu2 from the Breezy repositories. Do I need to use an older ndiswrapper - and if so, does that mean I will have to compile it, or is there a way of pulling an older .deb from the repositories?

eltaito, unfortunately I need the pcmcia card for something else, I would like to get the wireless going on this thing without investing any more $... if it comes down to it I will buy another cheap card, but I'd rather learn how to get it working, and besides, learning linux is fun;)

---

### Post by sal on 2006-03-08
yes i have an emachines m6810 with head aches from broadcom and ati.
tell me do the ati drivers mess with your resulution? when i install them on my machine i can only get 1024x768 from a screen thats default 1200x800 with the xorg drivers.

---

### Post by n.b.r. on 2006-03-08
Success!

Very strange... all I did was reboot again, and now it's working.

Thank you very much for the help.

---

### Post by eltaito on 2006-03-10
sal...when I try to install new ati drivers with my emachines 5310 they do mess with my resolution big time...but I usually don't worry about that...the default drivers that come with Unbuntu work fine for every day use.....my resolution is at 1280x800 by default and thats fine...i don't use the machine for anything graphic intensive (the damn thing over heats anyways when the ATI card is working full out...i don't know what kind of drop out engineers designed this thing)

n.b.r.....careful with that "its just working now thing".....i've done that a ton of times where I just gave up on ndiswrapper...reboot and its magically working...but then it just stops sometimes and when you update to a new kernel...well your nightmare begins anew......but I do agree, learning linux is fun.  Even though I shelled out some cash for a pmcia card, i still like to play with ndiswrapper to figure out whats going on.  I have no real problems with Linux (yet) except for the stupid broadcom chipset.  But anyway, I hope it keeps on working for you....having wireless internet and a great OS like unbuntu is a great feeling.....I love this distro

---

### Post by n.b.r. on 2006-03-11
Well, I've rebooted dozens of times since then - so far it's still good - I even upgraded from the 386 to the 686 kernel, and no problems.

Ubuntu has treated me very well so far. It recently replaced Slackware as the main OS on my desktop, and it's proven to be a great laptop distro as well (this broadcom thing has been my only issue).

Thanks!

---

