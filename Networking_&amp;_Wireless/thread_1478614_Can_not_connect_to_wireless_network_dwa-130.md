---
title: "Can not connect to wireless network dwa-130"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by perro68 on 2010-05-09
I have installed the driver for my usb network adapter
It sees my adapter fine
I see my two routers .....i have both a dsl routher and a router conntected to my cable modem ...it says signal strength of 90

I see my neighbors network as well  

but when i try to connect to either of my routhers

it will not let me

i use WEB ... 128 bit ...it asks for the passpharse

it says it is activating....

and the after a few minutes the same window back up again

i know my pass phrase is correct


when i reboot in windows ...everything works fine ...no problem

but in 10.04 i can not connect to any network

what am i doing wrong

I re entered my pass phrase a 100 times

each time .....the window comes back ...asking for the pass phrase!!!!!!

---

### Post by bkratz on 2010-05-10
> **perro68 said:**
> I have installed the driver for my usb network adapter
It sees my adapter fine
I see my two routers .....i have both a dsl routher and a router conntected to my cable modem ...it says signal strength of 90

I see my neighbors network as well  

but when i try to connect to either of my routhers

it will not let me

i use WEB ... 128 bit ...it asks for the passpharse

it says it is activating....

and the after a few minutes the same window back up again

i know my pass phrase is correct


when i reboot in windows ...everything works fine ...no problem

but in 10.04 i can not connect to any network

what am i doing wrong

I re entered my pass phrase a 100 times

each time .....the window comes back ...asking for the pass phrase!!!!!!

Probably not what you wanted to hear, but I have had a DWA-130 working for about 1-1/2 years and have never gotten it to work with WEP--during all those attempts I found out that WEP is barely better than nothing (easily cracked), and to my surprise when I tried WPA2 with psk it worked very well. If you need any help, just PM me.

---

### Post by perro68 on 2010-05-10
I am now having a problem using my old linksys pccard
 
the lynksys card seem to work find under jaunty ....but when i upgraded to  10.04
 
i can no longer connect to any network
 
although i do see them ..... 
 
i will change both routers to WPA2 when i get home and see how that works

---

### Post by bkratz on 2010-05-10
> **perro68 said:**
> I am now having a problem using my old linksys pccard
 
the lynksys card seem to work find under jaunty ....but when i upgraded to  10.04
 
i can no longer connect to any network
 
although i do see them ..... 
 
i will change both routers to WPA2 when i get home and see how that works

Sorry, but forgot to tell you I also had to change the router to be aes only--not tkip/aes.

---

### Post by coldfinger on 2010-05-28
Which hardware rev, and which driver package are you guys running?

---

