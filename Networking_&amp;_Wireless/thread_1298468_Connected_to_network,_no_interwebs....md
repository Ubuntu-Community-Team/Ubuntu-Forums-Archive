---
title: "Connected to network, no interwebs..."
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by keelay42 on 2009-10-22
First, I'm new to the site, so hey. I've dabbled in nix based stuff a little with the Air force, but other than that, not at all. I'm basically a n00b that is kinda familiar with terms, that's all.
     My problem is that I am connected to my wireless network, but I have no internet. It was working yesterday. I have changed nothing. It's an older eMachines laptop that I drug out of my closet yesterday, installed Jaunty, and everything was good. I had an internet connection, surfed a while last night. I wake up today to play, and have no internet (I'm on my other m$ based laptop now). I'm connecting through an external USB wireless adapter (linksys). I have a decent connection, and have google'd the hell out of this all day. No other fix I have found has done it for me. 

result of ifconfig:

wlan1 has packets going, no errors, no drops etc.

(i have an internal network card, wlan0, but is not associated)

result of iwconfig:

wlan0 shows, but access point is not assosiated, Tx power is 0dBm, everything is 0 since its not even running

wlan1
IEEE 802.11bg
mode: managed  Frequency: 2.437 GHz  Access point: 00:1c:10:9b:00:80
bitrate = 1 mb/s    Tx-power=11dbm
retry min limit:7  RTS thr: off    Fragment thr=2352 B
Power management off
Link quality=43/100  Signal level: -74 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

What am I missing here? Why am I only transmitting 1mb/s? 
When I ping anything, I get responses( icmp_seq=3 ttl=48 time=38.2ms), but it says 31 packets transmitted, 3 recieved. 90% packet loss, time 102389ms. 
Why am I dropping so many packets?
I know my wireless adapter is fine, I can put it in the computer I am using now, and connect through it. In fact, I'm connected via the adapter now. 

WHAT AM I MISSING??

---

### Post by earthpigg on 2009-10-23
hi,

lets verify it is not a hardware problem.

pop in a liveCD and boot from that. how is your connection now?

---

### Post by keelay42 on 2009-10-23
Well.....
No, from the Live cd it still doesn't work. That figures that out. On to the next option..
  
   My internal card (Rioworks BCM4401 100Base-T), will not do anything. How would I go about doing something with that?

---

