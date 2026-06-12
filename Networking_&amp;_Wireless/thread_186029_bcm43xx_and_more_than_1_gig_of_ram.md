---
title: "bcm43xx and more than 1 gig of ram"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by djsamsel on 2006-06-01
a week ago i was finally able to get the broadcom 4306 wireless card working on my gateway notebook. i think i remember that the driver does not work if there is 1 or more gigs of ram installed on the system. however, right now i can't find that statement anywhere in the wiki. so i installed a gig chip in the system (total is 1.25 gigs). the blue wireless light still comes on, but i'm not connecting to the wireless router anymore. does anyone know if there is a work around? 

if i do "sudo iwconfig eth0" i get

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

doing "sudo iwconfig eth0 ap any" has no impact. any suggestions or guides that i've missed would be most appreciated.

---

### Post by elmagique on 2007-07-05
i've got exactly 1 gig of ram and it works perfectly, however my high speed card (125 Mbit/s) can't go faster than 11 Mbit/s.
bcm43xx is confusing

but try it with just the one gig, maybe it will work

---

