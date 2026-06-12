---
title: "ndiswrapper - Hard Freeze (Loading Twice?)"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by JustRandomName on 2006-02-11
Hi,

I am trying to find the problem why my computer keeps hard locking when the network is under heavy load. The following is what happens in the /var/log/message right before a crash:

```
Feb 11 04:27:30 localhost gconfd (pbaines-7904): Resolved address "xml:readwrite:/home/pbaines/.gconf" to a writable configuration source at position 0
Feb 11 04:28:15 localhost kernel: [4294807.676000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
Feb 11 04:28:15 localhost kernel: [4294807.769000] ndiswrapper: driver rt73 (Belkin,08/02/2005, 1.00.00.0000) loaded
Feb 11 04:28:17 localhost kernel: [4294809.098000] wlan0: vendor: 'IEEE 802.11g Wireless Card.'
Feb 11 04:28:17 localhost kernel: [4294809.098000] wlan0: ndiswrapper ethernet device 00:11:50:ba:f2:b1 using driver rt73, 050D:705A.F.conf
Feb 11 04:28:17 localhost kernel: [4294809.100000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb 11 04:28:17 localhost kernel: [4294809.100000] usbcore: registered new driver ndiswrapper
Feb 11 04:28:46 localhost kernel: [4294838.574000] ip_tables: (C) 2000-2002 Netfilter core team
```



It seems that ndiswrapper is trying to load itself again. Why would it do this? Anyway to prevent it?
Funny how the ip_tables message is the last? could this be anything to do with it?

I have a Belkin F5D7050 USB card, there seems to be many different chipsets that this card has. Mine is the RT73 (unfortunatly not supported by the RT2x00 Project). There is some native modules here: but they are for older kernels (and none with smp support) 

[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

The kernel I am on at the minute is the default 2.6.12-10-686-smp

The version of ndiswrapper I am using is 1.8 (the utils seem to be 1.7, this is the latest version of that). I have tried all the different combinations of ndiswrappers and the drivers on the belkin website (turns out that ndiswrapper has to be 1.8 (1.9 doesn't work), and the drivers are the ones from my CD).

Thanks for your time.

---

### Post by JustRandomName on 2006-02-16
Just following up incase anyone else has this problem.

So far I have a stable system (for about an hour so far, maybe I am talking too soon but it is a lot better than the 10 minutes per crash than before)

ndiswrapper is not trying to load it self again (just me getting muddled in the logs)

Anyway version 1.10 works ( ndiswrapper 1.7 and lower doesn't, also 1.9 doesn't) and use the CD drivers.

---

### Post by oimon on 2006-03-01
Hello JustRandom,

Did you find the ndiswrapper 1.8 worked OK with the uniprocessor kernel?

I have this problem with my SMP kernel, but booting uniprocessor works OK..

Not sure what version i have (its the breezy repos one), but i will try with the new version too

Dapper is too far away. i will have to compile :S
cheers

---

### Post by JustRandomName on 2006-03-07
I tried it with both kinds of kernels and they both gave the same results.

Compile ndiswrapper from source (1.10 that's one point ten, not one point one) and install the drivers that came with the CD.

If you still have the box that it came in try and look for a small sticker with the version number on (mine is v3000 UK)

---

