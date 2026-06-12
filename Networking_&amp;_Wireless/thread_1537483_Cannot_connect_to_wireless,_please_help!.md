---
title: "Cannot connect to wireless, please help!"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by sightpirate on 2010-07-23
Hi, I'm wicked new to Linux, so pardon me if I haven't a clue.
 
I'm using Ubuntu Netbook Edition 10.04, on an Asus EeePC 904HA.
 
Yesterday, I was connecting to my wireless network, which has WPA2 security, just fine. Then, I disconnected randomly (I'm used to random disconnects, as I'm a great distance away from my router.)
 
Usually, I just reconnect. I tried and tried, and I still can't. I've restarted my computer, gotten right next to the router, turned networking off and back on, and so on. Still, no luck.
 
You know, when you're conecting to a wireless network, there's the icon with the two grey circles that turn green and the blue swirl? They both turn green, like usual, and then they just go back to the two computers with the red "X". You know what I'm talking about.
 
All other computers on my network work fine, so it's just my Asus.
 
Please help?

---

### Post by JackNocturne on 2010-07-23
Ok start of with some simple **trouble-shooting, **type the following in **terminal**(Command Line)

```
ifconfig eth1
```   print the output here

---

### Post by sightpirate on 2010-07-23
```
eth1: error fetching interface information: Device not found
```
 
Something tells me that's bad...

---

### Post by thieved on 2010-07-23
> **sightpirate said:**
> ```
eth1: error fetching interface information: Device not found
```
 
Something tells me that's bad...

I got the same, running 10.04 though.

---

### Post by petrus250 on 2010-07-23
Yep, I had the same problem, asus with 10.04. As far as I know, unless you want to write a script to do it (please do) there is no fix. I simply reverted to 9.10, sorry.

---

### Post by sightpirate on 2010-07-23
> **petrus250 said:**
> Yep, I had the same problem, asus with 10.04. As far as I know, unless you want to write a script to do it (please do) there is no fix. I simply reverted to 9.10, sorry.
 
Really? I thought I was the only one. :D
 
I guess I'll do that, but it isn't the first time I've had to switch OS's. I used to have Windows, but my disk got unmountable, so I installed UNR 10.04.

---

### Post by thieved on 2010-07-23
> **sightpirate said:**
> Really? I thought I was the only one. :D
 
I guess I'll do that, but it isn't the first time I've had to switch OS's. I used to have Windows, but my disk got unmountable, so I installed UNR 10.04.

I'm just running a custom box, been updating without a disk since 9.04.

---

### Post by petrus250 on 2010-07-23
Well I found that lucid was faster and aesthetically more pleasing but I would rather have wireless

---

### Post by petrus250 on 2010-07-23
Oh, on I forgot, asus, for some reason use a ra0 interface so rather than using 
[FONT=monospace]ifconfig eth1 you are going to need to run 'ifconfig ra0[/FONT]' (for future reference:D)

---

