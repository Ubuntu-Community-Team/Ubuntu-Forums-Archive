---
title: "enabling wireless"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by nikonfrz on 2009-03-31
so i have this kinda piece of machine called and emachine m6811! the only way to turn the wireless card on in windows is by using th Fn key and F2(wireless). i don't have a button and i don't know how to manually turn it on in ubuntu. i'm trying to get wireless set up and working but i can't find out how to turn the damn thing on lol. any help would be much appreciated :)

---

### Post by nikonfrz on 2009-04-01
ok so i have read for about 3 hours trying to figure this wireless business out. i have a hot key to turn my wireless on. so far i found a program to assign hot keys but i can't get my wireless card to turn on. it's wlan0 and i used ifconfig wlan0 up and it says "SIOCSIFFLAGS: No file found"
i have searched to figure that out too i end up going in circles and i'm at a wall with this. if there is anything anyone can do to help me out it would be much appreciated.

---

### Post by nikonfrz on 2009-04-02
root@vpkeebs1-laptop:/home/vpkeebs1# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Magzee on 2009-04-02
Hi I am having similar probs trying to get my dell inspiron 8600 working. I have loaded a fresh install of Ubuntu Studio on a second partition.  I have a working wireless connection on the windows partition but nothing for Ubuntu. I have made some headway though so I thought I would share.  

I edited:     /etc/network/interfaces  
It should give you:   
auto lo 
iface lo inet loopback

and.. auto eth0
iface eth0 inet dhcp  *(dhcp was something different)*
(and then ip address gateway subnet etc.)

Now I'm only guessing here, eth0 would be referring to the wired network adapter. Basically this above is saying a wired connection with ip auto assigned by dhcp. I tried (a lot of things) and have set up eth1 configured for my wireless connection.  Believe it or not I used the ubuntu help pages re networking.  So at 4am today I called it a night and decided I needed to download a driver for Broadcom to work on Ubuntu.  Its funny that setting up XP on this dell with a wireless connection a few years back was no easy task either...  

Can't find a driver and the Broadcom driver that downloaded yesterday as part of the updates (got very excited) doesn't work.  

Tonight I have just read this:


"STEP 1: CLEAN YOUR SYSTEM

IMPORTANT NOTE ABOUT CLEANING YOUR SYSTEM:

One of the most common reasons why many people can't get their wireless working is because their system is in a state of chaos. If you have made ANY previous attempts to get your wireless working -- either using fwcutter, ndiswrapper, or the bcm43xx drivers -- this how-to will most likely not work UNTIL you reverse your previous changes. In many cases, it is much easier to simply reinstall ubuntu and come straight to this how-to."

..as part of a "how to" install a certain broadcom adapter in a different dell model.  So its given me pause to stop and investigate further before I make too much of a mess.  I will let you know if I find anything else.

Cheers
Magz

---

