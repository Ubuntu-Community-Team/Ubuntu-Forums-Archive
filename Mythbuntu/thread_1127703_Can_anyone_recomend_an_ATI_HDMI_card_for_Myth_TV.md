---
title: "Can anyone recomend an ATI HDMI card for Myth TV?"
date: 2009-04-16
forum: Mythbuntu
---

### Post by gdbutcher on 2009-04-16
Can anyone recommend a Myth TV Compatible ATI 3D graphics card with HDMI?

The reason I'm after a ATI card is that I've spent 4 days trying to get my Nvidia 8500 GT to a) not overscan and b) get HDMI sound without the slightest bit of success. I decided enough is enough. 

I unplugged the 8500 plugged the HDMI lead straight into onboard ATI 1200 express rebooted, installed proprietry driver, rebooted and it worked!! Full 1080i with no overscan, and sorted the sound within 15 mins! :D

but on the downside MYTH Tv's display is garbage and I can't play 3D games.
   
Thats why I'm thinking of buying a new ATI Card any suggestions would be more than welcome?

---

### Post by nickrout on 2009-04-16
> **gdbutcher said:**
> Can anyone recommend a Myth TV Compatible ATI 3D graphics card with HDMI?

The reason I'm after a ATI card is that I've spent 4 days trying to get my Nvidia 8500 GT to a) not overscan and b) get HDMI sound without the slightest bit of success. I decided enough is enough. 

I unplugged the 8500 plugged the HDMI lead straight into onboard ATI 1200 express rebooted, installed proprietry driver, rebooted and it worked!! Full 1080i with no overscan, and sorted the sound within 15 mins! :D

but on the downside MYTH Tv's display is garbage and I can't play 3D games.
   
Thats why I'm thinking of buying a new ATI Card any suggestions would be more than welcome?

I don't think any sane person would recommend an ati card for mythtv.

Did you try setting your TV to deal with the overscan? Often the solution is in the TV not in the computer!

---

### Post by AKADAP on 2009-04-17
I have not tried NVidia, but I can not yet recommend ATI.

Though a lot of the bugs I had with it have been fixed with the latest proprietary driver (garbage when changing channels between channels running at different resolutions, or when the resolution of the channel I was watching changed, and crashing) some have not (syncing video to the vertical blank (causes tearing) no hardware de-interlace & poor software de-interlace (feathering)). 

The open source driver did not work at all when I attempted to install Ubuntu 8.10 64 the first time. (I had to install in safe mode). Also, I don't believe that the open source drive works yet with the 2560x1600 native resolution of my monitor.

---

### Post by tobiz on 2009-04-17
gdbutcher, 
Nvidia cards are in general better for Linux than ATI. Nvidia does provide drivers and support for use with Linux (but on the basis of  no guarantee they work). My M/B has onboard GF8200 chip and everything works including 5.1 audio over HDMI from HD TV.  Getting audio to work require(s/d) a re-build of the alsa sound system, see Nvidia Linux forums for details. I'm using the 177 driver from Nvidia, up to you whether you want to go with closed or open source.

---

### Post by jyavenard on 2009-04-18
> **gdbutcher said:**
> Can anyone recommend a Myth TV Compatible ATI 3D graphics card with HDMI?

The reason I'm after a ATI card is that I've spent 4 days trying to get my Nvidia 8500 GT to a) not overscan and b) get HDMI sound without the slightest bit of success. I decided enough is enough. 


If you're having trouble to get a nvidia card to work properly, I can only imagine how it's going to be worse with ATI crap.
Their drivers are terrible ; and that's when they work.

Also with a 8500GT, getting sound over HDMI has nothing to do with the nvidia drivers or card.
It uses a SPDIF passthrough cable ; so you need to get digital sound working with your motherboard. Usually it's just a matter of entering the right ALSA device in mythtv and checking the DD and DTS passthrough option.

For overscan, the issue is usually with the TV rather than the drivers or the video card.

---

### Post by gdbutcher on 2009-04-18
Thanks for all your suggestions everyone. The problem is with my Sanyo TV by default it displays in "full mode" according to the instructions. I couldn't manually correct it, it doesn't even let me change the aspect ratio in HDMI mode!? 

I bought a NVIDIA GTS250 because some people had reported overscan being solved with a direct HDMI - HDMI connection, it was great card but it didn't solve the problem either. 

Took it back and bought a Radeon HD4850 and it works! using Ubuntu 9.04 Jaunty and the catalyst 9.4 drivers. Myth TV installed very easily, had a slight problem with double image, changed the interlace options and that corrected it. I'm watching family guy on it right now! :D

Its only been a couple of hours but so far so good, maybe ATI are starting to get there act together!!

---

### Post by GuiGuy on 2009-04-18
> **gdbutcher said:**
> 
The reason I'm after a ATI card is that I've spent 4 days trying to get my Nvidia 8500 GT to a) not overscan and b) get HDMI sound without the slightest bit of success. I decided enough is enough. 


I now the feeling :( - I've spent the last two days trying to find linux software to make video slidewshows. Windows is starting to look good again... Ooops, OT, he's ranting again... ;)


Regarding overscan, I came up against that and then realised my LG LCD TV had a setting called "Just Scan". It seems to adjust it nicely and if there is any distortion it isn't apparent. 

Sorry if that doesn't help...

---

