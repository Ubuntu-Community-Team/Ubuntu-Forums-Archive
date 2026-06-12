---
title: "LinkSys WPC54GX4....so close, yet so far....??"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by mbobak on 2006-06-04
Hi,

Help!

I'm running a fresh (just installed today) copy of 6.06 Dapper Drake, on an older Sony VIAO (PCG-FX270).  I just got a new LinkSys WPC54GX4, only to discover it's not supported natively.  So, I installed ndiswrapper, checked the ndiswrapper wiki, and discovered that they didn't list it as working either.  So, I went to LinkSys, got the latest driver, and tried using that.  Surprisingly, it seemed to work.

I did:
ndiswrapper -i tmimo3p.inf
ndiswrapper -d 17cb:0002 tmimo3p
depmod -a
modprobe ndiswrapper

All the above worked successfully.

I can do 'iwconfig' and I can see 'wlan0'.  So, I'm thinking I'm home free.

I do:
iwlist wlan0 scan

and I see my AP.

I do:
iwconfig wlan0 mode managed
iwconfig wlan0 essid linksys

Ok, so far so good.  Now 'iwconfig wlan0' shows it's associated w/ my AP.

Now, I use the network connection dialog to set my IP, netmask, router and DNS servers.  (No DHCP here.)  I've quadruple checked it, and everything looks ok.

when I try to ping my gateway, I get "Destination host unreachable", and I'm at a loss to explain why......


Help!!

AdvThanksance,

-Mark

---

### Post by nzruss on 2006-06-04
I'm having similar problems. 

Clue here:

[http://www.ubuntuforums.org/showthread.php?t=186538&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=186538&highlight=wpc54g)

---

### Post by mbobak on 2006-06-04
Hmmm...thanks for the pointer, but it didn't work for me.....

Note that I have the WPC54GX4.  This is the card w/ the SRX400 support for longer range and higher throughput.  So, the driver is different than yours (I assume).

The fwcutter didn't work, it complained that "input file is wrong or not supported by fwcutter".

Oh well....and the struggle continues.....


-Mark

---

### Post by nzruss on 2006-06-06
how about this...?

[http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101](http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101)

---

### Post by mbobak on 2006-06-08
Thanks, but that link is for a WPC54G v3.  That's an 802.11g card w/ a Broadcom chipset.

My card is (was) a WPC54GX4.  Note that's 'X4', and is a reference to SRX-400, aka MIMO, and NOT a version number.  This card has an Airgo Networks chipset.

I gave up on it and picked up a D-Link DWL-G650M, and it works like a charm w/ ndiswrapper.

-Mark

---

### Post by justinmiller87 on 2008-03-05
If it's a MIMO based card, you might be able to get it to work with the instructions in my signature for the Airgo chip.

---

