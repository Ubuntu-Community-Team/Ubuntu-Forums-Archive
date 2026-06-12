---
title: "HD video card shopping"
date: 2009-12-27
forum: Multimedia Software
---

### Post by le_vainqueur on 2009-12-27
I am going to buy a video card to hook up my desktop to my Samsung 1080p HDTV.  I've tried to find articles/posts about what to look for, but haven't been successful.  

My computer has a Core 2 Duo processor, I think it's 2.3 GHz, maybe 2.1.  I'll have to check.  Is that enough for HD video?

My second concern is the PC power supply.  What sort of requirements will there be?

I have 4 GB RAM, so no concerns there. 

The final concern is a card that works well with Ubuntu (obviously Nvidia is a good choice), and one that will allow for 1080p video.  I would eventually like to buy a BlueRay drive for the computer as well.  I don't know if this will effect the choice of video card or not.

What other things should I take into consideration?  If there are any articles/guides/threads on this, I would greatly appreciate any links.

---

### Post by mörgæs on 2009-12-28
Have you seen the hardware compatibility list at 
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) ?

---

### Post by cascade9 on 2009-12-28
> **le_vainqueur said:**
> My computer has a Core 2 Duo processor, I think it's 2.3 GHz, maybe 2.1.  I'll have to check.  Is that enough for HD video?

Thats enough for software decoding. 

> **le_vainqueur said:**
> My second concern is the PC power supply.  What sort of requirements will there be?

Depends. For software playback, you will use more CPU power to decode the video. Unless you are already having issues with your power supply at high CPU loads, then you should be fine. 

With a hardware decoder like nVidia cards that support VDPAU (Video Decode and Presentation API for Unix) CPU use will be far lower. if your not a gamer, and want a nVidia card that supports VDPAU, a bottom of the line nVidia 8400 GS will do HD with no problem. Not expensive, and low power requirements. Id spend a few dollars more and get a GT 210/GT 220 as its got a better feature set See here for more info-

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

---

### Post by gradinaruvasile on 2009-12-28
+1 to cascade9's post

Edit:
I recommend 2.3 GHz or higher in case of software decoding. Also check the wiki to select a card with VDPAU set AT LEAST 2. 
Set 3 would be ideal. Bear in mind that more powerful card does not mean automatically higher VDPAU capabilities. 

Check the list closely, pay attention to the core names - those are the keys to VDPAU feature sets, not the generic card names.
And the only way i got VDPAU working is the mplayer command line version from the Nvidia VDPAU PPA :

mplayer -vo vdpau -vc ffh264vdpau moviename

-vo AND -vc switches are mandatory.

---

### Post by autora on 2009-12-28
you will need at least a gforce 8600 +

---

### Post by gradinaruvasile on 2009-12-28
8400 is enough for movies... I have a Nvidia 8200 integrated (ASUS M3N78-VM mobo) with Athlon 3200+ and it flies with 1080p (15-20% CPU).

---

### Post by le_vainqueur on 2009-12-28
Thanks for the advice everyone.  This will definitely help significantly.

> **gradinaruvasile said:**
> +1 to cascade9's post
And the only way i got VDPAU working is the mplayer command line version from the Nvidia VDPAU PPA :

mplayer -vo vdpau -vc ffh264vdpau moviename

-vo AND -vc switches are mandatory.

Was this because the video card was not very compatable with Ubuntu?

---

### Post by gradinaruvasile on 2009-12-28
3 cards, VERY compatible with Ubuntu. 
Nvidia 8200 IGP, Quadro NVS 135M/140M.
 The thing is that there are 2 players currently that have VDPAU support, and only if you download them from the nvidia vdpau ppa: 
mplayer and xine. 
Using the graphical interface for both programs there is an option to use the vdpau output. 

BUT vdpau can be used in 2 modes: 
1. software decoding + vdpau device rendering - means the decoding is done by the CPU, in case of 1080p movies this means that one CPU is fully used (no multithreading yet) and you have to have a very good processor to have smooth playback. Having VDPAU compatible card in this case means no performance gains.
2. hardware decoding + vdpau device rendering - the decoding is made integrally by the video card, this lowers the CPU usage to about 10% with 1080p movies - this is where the VDPAU is really used to its potential. And higher the cards supported VDPAU set (1,2,3), more codecs are supported, meaning more movies work with VDPAU decoding.

Using the graphical interface, only the software decoding was activated, at least for me. The only way i could initialize hardware vdpau was in the command line mplayer's options.

And bear in mind not all movies will work with VDPAU, only if they are made with the VDPAU supported codecs.

---

### Post by le_vainqueur on 2009-12-30
Thanks for the explanation.  That makes some sense now.

---

### Post by le_vainqueur on 2009-12-31
I found this article on building a media PC with Ubuntu. 

[http://linuxlookup.com/guide_to_building_an_open_source_htpc_media_center_on_ubuntu](http://linuxlookup.com/guide_to_building_an_open_source_htpc_media_center_on_ubuntu)

One interesting item to me was that they suggested getting a motherboard with HD capabilities.  How would this compare to purchasing a video card and adding it to my current desktop?  Would the quality be the same/better/worse?  Has anyone used a setup like this in the past?

---

