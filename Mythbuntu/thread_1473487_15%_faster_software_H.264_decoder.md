---
title: "15% faster software H.264 decoder"
date: 2010-05-05
forum: Mythbuntu
---

### Post by kingmoffa on 2010-05-05
Hi there, 

Im thinking of upgrading my systems to 0.23 when it comes out. Mainly because my systems cannot play HDTV at the moment so am wondering if this update to 0.23 will help:

15% faster software H.264 decoder

Can anyone confirm this figure? Or give some real world examples of software HDTV playback?

---

### Post by williammanda on 2010-05-05
> **kingmoffa said:**
> Hi there, 

Im thinking of upgrading my systems to 0.23 when it comes out. Mainly because my systems cannot play HDTV at the moment so am wondering if this update to 0.23 will help:

15% faster software H.264 decoder

Can anyone confirm this figure? Or give some real world examples of software HDTV playback?

First thing to consider is the equipment. I can give you the results from my system monitor but my equipment maybe a variable in the equation. What equipment do you have and what benchmark are you using?

---

### Post by cascade9 on 2010-05-05
If your systems can only *just* not play HD, then it might help. 

I doubt that a 15% improvement will get you from 'cannot play' into 'plays well' though.

---

### Post by LowSky on 2010-05-05
> **kingmoffa said:**
> Hi there, 

Im thinking of upgrading my systems to 0.23 when it comes out. Mainly because my systems cannot play HDTV at the moment so am wondering if this update to 0.23 will help:


What are your system's specs?

15% might sound great but 15% of zero is still zero.

---

### Post by tgm4883 on 2010-05-05
Probably won't help. In the US anyway, HDTV is transmitted in mpeg2.

---

### Post by kingmoffa on 2010-05-06
Hi, 

thanks for the replies. 

Im trying to play UK freesat HDTV - BBCHD and ITV 1 HD. 

BBCHD very nearly plays ok - a small stutter every couple of mins or so.  According to wikipedia its:

"The UK broadcasts are typically at a resolution of 1440x1080i and encoded in MPEG-4 H.264/AVC"

ITV1 HD stutters every 30 seconds or so. 

My hardware isn't the best. 2GHZ Pentium Celeron Dual Core.

---

### Post by ian dobson on 2010-05-06
> **kingmoffa said:**
> Hi, 

thanks for the replies. 

Im trying to play UK freesat HDTV - BBCHD and ITV 1 HD. 

BBCHD very nearly plays ok - a small stutter every couple of mins or so.  According to wikipedia its:

"The UK broadcasts are typically at a resolution of 1440x1080i and encoded in MPEG-4 H.264/AVC"

ITV1 HD stutters every 30 seconds or so. 

My hardware isn't the best. 2GHZ Pentium Celeron Dual Core.


And whats your graphic card? I'm running a very underclocked e5200 (800MHz) with a nvidia 9600gt graphic card/VDPAU and can play anything I throw at it, BBC HD (I just love Doctor who).

Regards
Ian Dobson

---

### Post by kingmoffa on 2010-05-06
Graphics card is an onboard nvidia 7100 

I know if I buy a new card VDPAU will help a lot. But that costs money and PCI(E) slots that I dont have spare.

---

### Post by kingmoffa on 2010-05-20
Right I took the plunge and upgraded mythtv to 0.23 using the mythbuntu daily builds repo. 

All went really well :)

Unfortunately although the 15% faster software H.264 decoder did help - it wasnt enough to let my system decode HDTV well enough to watch. 

So now Im after some hardware advice. 

Can anyone please recommend 

a) Nvidia VDPAU graphics cards that is fanless and small and cheap. 

I did try a passive cooled Geforce 9500GT but the heatsink was so big that I had to remove tuners. Dont want to do that. 

OR
b) cheap CPU upgrade - I would love to go quad core but at £120 its a bit to expensive. (cheapest I could find). Will myth software decoding even use all 4 cores?


OR 

c) Motherboard - socket 775  mini atx VDPAU motherboard. hdmi a bonus. 

THanks in advance.

---

### Post by cascade9 on 2010-05-20
> **kingmoffa said:**
> a) Nvidia VDPAU graphics cards that is fanless and small and cheap. 

I did try a passive cooled Geforce 9500GT but the heatsink was so big that I had to remove tuners. Dont want to do that. 

OR
b) cheap CPU upgrade - I would love to go quad core but at £120 its a bit to expensive. (cheapest I could find). Will myth software decoding even use all 4 cores?

OR 

c) Motherboard - socket 775  mini atx VDPAU motherboard. hdmi a bonus. 

THanks in advance.

a- I am guessing that the passive cooled 9500GT was a double-slot cooler. There are single-slot passive video cards- I've got a gigabyte 8600GT fanless that is single slot. 

IMO, for your use, you want a card that supports VDPAU feature set 'c', and I think a GT220 would be your best bet. There are single-slot fanless GT220s, sparkle and ECS makes them...but I have no idea about avaibility in the UK. 

2- I'm sure that mythTV will use quad-core for decoding at soem stage (if it doesnt already). 

3- A LGA 775 9300 chipset motherboard would do the job....but it would be more expensive than importing a fanless GT220. Or getting a a normal GT220 and swapping off the fanned cooler and bolting on a fanless cooler.

---

### Post by kingmoffa on 2010-06-03
I've ordered a Gainward GeForce G210 512MB - Its got a passive cooler and I really hope it only takes up 1 slot  (according to what little spec I found on their website it does)

As its a geforce 210 it should do feature spec C ;)

I currently run 0.23 using the daily builds mythbuntu repos so am fairly the myth part of my system is ok. 


Im now wondering about nvidia drivers in mythbuntu 9.10 - currently installed is the 185 series. 
There is a 190 series and an older 173 series aptitude tells me. 
  
Should I use this (190) , stick with the 185 series or use another repository/software for nvidia stuff (eg JYA / or official nvidia software )?

Thanks in advance.

---

### Post by ian dobson on 2010-06-03
Hi,

On my frontend I went over to the 195 drivers, took abit of screwing about to get them working (linux-headers package not installed) but I can't see any real difference to the older 185 ones.

Regards
Ian Dobson

---

### Post by kingmoffa on 2010-06-04
Hi , 
Got my card through - so glad it fits in the single slot. I went with the 190 drivers. Was pretty easy to install

```
aptitude install nvidia-glx-190 nvidia-190-kernel-source nvidia-190-modaliases
```

Aptitude automatically removed the older drivers. 


Changed my myth frontend to use the VDPAU normal playback profile. 

Everything works well so far - recorded the FA Cup final a while back so I had something to see what the football looked like. 

May try and play around a bit with the playback profile - tempted to try out the filters for vdpau - e.g. vdpauhqscaling

Now time to sit back and wait for the World Cup :popcorn:

---

