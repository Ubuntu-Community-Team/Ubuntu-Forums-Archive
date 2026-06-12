---
title: "what did i do to my wireless drivers?!?"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by carolinealicia on 2009-04-02
here is info about my wireless card: 
 Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
the chipset WAS ipw2200BG

I was trying to install madwifi following these directions, but towards the last few steps I got nothing but errors.

This is what I see now

02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
        Subsystem: Intel Corporation Device 2701
        Flags: medium devsel, IRQ 11
        Memory at e0214000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: <access denied>
        Kernel modules: ipw2200

So yah i can't use wireless anymore (currently has a mega long ethernet cord stretching from router downstairs to my bedroom upstairs.


I really need some help.. Is there anyway to roll drivers back? I've been a ubuntu/linux user for 2 months now. I should have followed my gut instinct and realized i was too newbie to pull this off but it seemed simple enough. 

I've tried downloading the old drivers (ipw2200-1.2.2) but more errors. 

[carol@kazokuKEIKAKU:~/ipw2200-1.2.2$ sudo make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.27-11-generic/include'.

-e You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1
]

ughh.....

---

### Post by chili555 on 2009-04-02
Please open a terminal and do:```
iwconfig
```Please post the result. Does your interface seem active, but just won't connect?

I have a machine with an ipw2200 card in it that worked fine until the latest update. I got it working again by *_removing_* *linux-backports-modules-intrepid-generic.* Some here have gotten theirs rolling by *installing* backports. Go figure!> Is there anyway to roll drivers back?If you have not gotten past 'make' you have done no harm at all.

---

### Post by carolinealicia on 2009-04-02
ohh a reply *excited*

'no wireless extensions' for everything (lo, eth0, pan0). lo is loopback right? Before i ruined my wireless i was on eth1. the lan cable is using auto eth0 right now.

---

### Post by chili555 on 2009-04-02
Please run:```
sudo modprobe ipw2200
```Any errors? Then rerun:```
iwconfig
```Did *eth1* show up?

---

### Post by carolinealicia on 2009-04-02
> **chili555 said:**
> Please run:```
sudo modprobe ipw2200
```Any errors? Then rerun:```
iwconfig
```Did *eth1* show up?

You fixed and I learned some new commands:D awesome. Thank you ever so much :KS

---

