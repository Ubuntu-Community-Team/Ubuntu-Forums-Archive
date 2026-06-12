---
title: "Looking to build a Mythbuntu system (for the first time)"
date: 2010-01-12
forum: Mythbuntu
---

### Post by Macka01 on 2010-01-12
Hi everyone,

As the title says, I am looking to build my first Mythbuntu box, however I am not so sure which hardware to select, even after reading a number of threads and a reasonable amount of the MythTV wiki.

Further more, I am quite new to Linux, though I have used a Solaris dumb terminal at uni.

At the moment I am just looking at feasibility of a Mythbuntu system vs a commercial PVR, if it turns out to be appropriate then I plan to build one.

Considerations:

[LIST]
[*]The system will be a dedicated PVR, the only web functionality is likely to be for program guides. It is only intended to record and playback TV, DVDs and media from other networked non Linux machines (most likely using SAMBA, if at all possible).
[*]The system must be as cheap, if not more so then a commercial PVR.
[*]It must be able to record at least 2 HD digital channels at once on a combined front/back end. Optionally, it would be nice to be able to record analogue channels, though they are being phased out by the end of this year.
[*]Must be easy enough for my Mother and siblings to use - from what I've seen so far that shouldn't be a big problem.
[*]Must be relatively easy to set up, I don't want to have to spend hours and hours installing software and reinstalling it just to get the system usable - I don't mind spending a few days tweaking it to get the best experience, I just don't want the initial setup to be too painful.
[*]Whilst I (and other members of the household) have considerable Windows knowledge, my Linux knowledge is somewhat lacking, though I'm sure I can pickup what i need to know with reasonable speed.
[*]I can also program, granted mostly in high-level languages (I consider C, C++ to be relatively low-level), so there may be opportunities for me to work on Myth code in the future.
[/LIST]
Is Mythbuntu likely to be any good for my needs?

**Hardware**
I'm not sure where to start with this, do I go with a 32-bit or 64-bit system?
What Motherboards should I avoid due to compatibility problems?
What size PSU am I likely to need?

I have started looking at Graphics cards, my understanding is a 1GB MSI 9600GT is compatible with linux and MythTV, can do VDPAU and given its price ($95) would be perfect for the proposed system.

Onboard sound should be enough, a long as it has the connector for the GFX card, allowing HDMI to be used.

For the HDD, I was thinking a Samsung SATA 1TB ($95) would be sufficient.

How much RAM am I likely to need?
Is 1 GB or 2GB sufficient?
I can get Kingston DDR2 1GB 800 ($30).


Selecting a capture card seems to be the most complex part, If I can work this out, then selecting the Motherboard should be easier. 

I'm not sure what would be best to go with, all I know is I intend to exclusively capture digital TV (anlague TV will be gone by the end of this year).

My understanding is that because digital TV is already in MPEG format then no additional encoding is necessary and it can be dumped almost directly from the capture card to the HDD, but that doesn't really help me.


So far, that is $200 + Mobo + CPU + capture cards + case + (possible Wireless adapter)
Assuming Mobo+cpu + capture cards <$200 then I'm still within budget.


Is anyone able to give me any advice on selecting the best Capture card/motherboard for what I want?

---

### Post by andrewc6l on 2010-01-13
I'm not sure you'll be able to fit all that into $200. Here are some ideas based on what I built:

 - two pcHDTV 5500 cards for digital/analog recording. I've heard good stuff about the HDHomeRun too, but never used it. (I'm in USA doing over-the-air recording - if you're not, your needs might be different).

 - at least a hyperthreading (HT) motherboard - a dual core might be better - to avoid jitter when you're watching TV while recording 2 inputs. (Recording the stream isn't too hard for digital, but playback / calculating commercial skip taxes the CPU.) Pick a "common" one - the more people who have it, the better the support, typically.

 - an NVIDIA video card - it works with the pcHDTVs which can offload some of their work. (I don't know about MSI support on Linux.)

 - a good cooling system. I burnt out two video cards before I got smart and put a fan in the right place.

 - a big hard drive (1T or so). HD streams are about 7G/h.

 - I think I've got 1G of RAM - Myth never seems to use much at all.

MythBuntu 9.04 was easy for me. I haven't upgraded to 9.10 yet; hopefully it will be as smooth. My GF had no problem using MythBuntu once she figured out where a few things were in the menu system.

---

### Post by cascade9 on 2010-01-13
> **Macka01 said:**
> What Motherboards should I avoid due to compatibility problems?
What size PSU am I likely to need?

I have started looking at Graphics cards, my understanding is a 1GB MSI 9600GT is compatible with linux and MythTV, can do VDPAU and given its price ($95) would be perfect for the proposed system.

Onboard sound should be enough, a long as it has the connector for the GFX card, allowing HDMI to be used.

You shouldnt have any major problems with motherboards. 

PSU size- 350-400watts, should do it, go no bigger than 550watts (it would just be a major waste)

A 9600GT 1GB is overkill. Besides, VDPAU has 3 difference 'feature sets'-

> 
Feature Set A
Complete acceleration for [H.264]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC")Partial acceleration for [MPEG-1]("http://en.wikipedia.org/wiki/MPEG-1#Part_2:_Video"), [MPEG-2]("http://en.wikipedia.org/wiki/MPEG-2"), [VC-1]("http://en.wikipedia.org/wiki/VC-1")/[WMV9]("http://en.wikipedia.org/wiki/WMV#Windows_Media_Video")

Feature Set B
Complete acceleration for MPEG-1, MPEG-2, VC-1/WMV9 and H.264.All feature set B hardware cannot decode H.264 for the following widths: 769-784, 849-864, 929-944, 1009-1024, 1793-1808, 1873-1888, 1953-1968, 2033-2048 pixels.

Feature Set C
Complete acceleration for MPEG-1, MPEG-2, [MPEG-4 Part 2 (a.k.a MPEG-4 ASP)]("http://en.wikipedia.org/wiki/MPEG-4_Part_2"), VC-1/WMV9 and H.264.[Global motion compensation]("http://en.wikipedia.org/wiki/Global_motion_compensation") and Data Partitioning are not supported for MPEG-4 Part 2.
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

9600GT is feature set 'A'. An 8400GS is more than you need for a mythTV box, and its feature set 'B'. Probably the best choice would be a GT210/220, for feature set 'C'. Its cheaper than the 9600GT as well, nice bonus. 

I have no idea on how/if you can connect sound cards to video card HDMI. I check this, a lot, before you get anything (stupid HDMI). 

> **Macka01 said:**
> 
For the HDD, I was thinking a Samsung SATA 1TB ($95) would be sufficient.

How much RAM am I likely to need?
Is 1 GB or 2GB sufficient?
I can get Kingston DDR2 1GB 800 ($30).

1TB would be enough. Of course, bigger is always a good thing when your reccording..space gets eaten, fast. 

1GB would be enough...but again, more is better. Almost all motherboards now use dual channel RAM,and if you get DDR2 then its very hard to find 512MB sticks (I can get them but 2x512MB is $50 AU, 2GB is $60. Go 2GB. 

> **Macka01 said:**
> Selecting a capture card seems to be the most complex part, If I can work this out, then selecting the Motherboard should be easier. 

I'm not sure what would be best to go with, all I know is I intend to exclusively capture digital TV (anlague TV will be gone by the end of this year).

My understanding is that because digital TV is already in MPEG format then no additional encoding is necessary and it can be dumped almost directly from the capture card to the HDD, but that doesn't really help me.


So far, that is $200 + Mobo + CPU + capture cards + case + (possible Wireless adapter)
Assuming Mobo+cpu + capture cards <$200 then I'm still within budget.

Is anyone able to give me any advice on selecting the best Capture card/motherboard for what I want?

Hmm..you could poke the mythTV wiki and check- 
[http://www.mythtv.org/wiki/Video_capture_card](http://www.mythtv.org/wiki/Video_capture_card)

IIRC, when I costed one for a friend a few months ago, it was about $90-100 for a decent capture card ($AU). He ended up importing one from the US for $70. That would make your budget....tight. 

Your looking at 
$65-70 CPU 
$60-90 motherboard
??? capture card. 

If that still works, then I'll bother posting exact hardware prices. It might be more do-able from $$$ left over from changing video card (a GT210 is $65, I cant find a 8400GS with HDMI at my Qld supplies. I havent checked the S.A. suppliers now)

---

### Post by hrobinson on 2010-01-13
Hi Macka01,

Have you checked out this link:[U]  [http://www.mythtv.org/wiki/Hardware_Requirements](http://www.mythtv.org/wiki/Hardware_Requirements)
[/U] 
This will tell you in general what you might need.

Have you ever built a home brew system yourself?  200.00 is quite a small budget for a new PVR system.  Just the tuner card alone such as a Hauppauge - Dual PCI Express TV Tuner/Recorder Model: 2250 is around $149.00 alone.  Come to think of it I don't know if MythTV supports this card very well yet.

Remember that you are not going to be able to do this on a severe budget, unless you can get a lot of your components for free or very cheap.

I too would recommend a Dual Core processor with at least 1 gig of ram, an Nvidia video card (Stay away from ATI at all costs). The video card does not have to be powerful.  The one I bought was a GEForce 6200 AGP (who uses AGP these days) for 49.00.  You should not be spending more than 60 on the video card, it would be a waste of money and you would never use its full potential.

Since you have a Hi Def TV you can connect the PVR directly to the TV using the VGA cable.  For me, I have to have a TV out for my old Standard Def TV.

Do this project not because you want to save money, do it because you enjoy the challenge of doing it yourself.  Not because you want to save money.  I believe that the cable company can put a HD PVR in your house for around 150 per year (about 12 bucks or so a month).  From expierence let me tell you its crappy.  The hardware is limited and the interface is very slow.  With Time Warners DVR I had to reboot it at least once a week to prevent it from filling up by itsself, and I can go on and on.  Plus you can do nothing in the terms of upgrading it or adding functionality.  For example, and i am speaking from Time Warner's perspective, you can not stream the contents of the DVR to other TV's in the house like you can with MythTV.

I have seen home built PVRs built for the cost of a new computer (not much more) or around 700 bucks.  Processor not memory is key in an HD system, get the best processor you can afford and build the system around that.  Remember you have to compensate for cooling, its not going to be a silent system.  For High Def, I would suggest a two hard drives.  One for the os (say the smallest you can buy 100gig or 150gig) and a 2TB drive to store your recordings.  You can easily add another 2TB drive if this one runs out.  and it will give you about 285 hours of programming.  with a Commerical DVR you are lucky to get 30 hours ... and its not upgradeable.

If you are looking for a quiet system, build Myttv as a split front end and back end.  Place the back end with the cable box or antenna pickup in a closet and build a silent front end for next to the TV.  This way you can add more front ends for each of the TV's in your house and the front ends can be cheaply built for around 300 per front end.

First step I would look at the link above to get an idea on what hardware you will need.  You have an Idea in your mind what you expect out of your PVR.  In other words what do you want MytTV to do for you, look at that and start to form a plan maybe on paper what you think you will need, not even putting a budget to it at this stage.  At least you will have an idea what hardware you will need to buy vs what hard ware you can recycle for the project.

Good Luck!
and Welcome!

Sincerely,

Harold Robinson

---

### Post by shazbut on 2010-01-13
Have you found the OCAU MythTV wiki yet?  It's a good Australian-specific resource, particularly for TV tuner brands that are commonly sold in shops like MSY etc.  Looks like it hasn't been updated in a while, but some of the cards listed are probably still available.

[See here]("http://www.overclockers.com.au/wiki/MythTV")

---

### Post by Macka01 on 2010-01-13
> **andrewc6l said:**
> I'm not sure you'll be able to fit all that into $200. Here are some ideas based on what I built:

 - two pcHDTV 5500 cards for digital/analog recording. I've heard good stuff about the HDHomeRun too, but never used it. (I'm in USA doing over-the-air recording - if you're not, your needs might be different).


My budget is around the $500 mark, I'm wanting to compete with the Topfield High Definition Set Top Box with PVR and 320GB HDD ([http://www.dse.com.au/cgi-bin/dse.storefront/4b4e64f1022118fe273fc0a87e010676/Product/View/GH5704](http://www.dse.com.au/cgi-bin/dse.storefront/4b4e64f1022118fe273fc0a87e010676/Product/View/GH5704))


I'm mainly wanting digital free to air recording (including HD), if I can also do free to air analogue that would be useful as I can tune in to my (half dead) VCR and run analogue streams through that as an AV to RF converter.

I have looked at the specs for that (and many other cards) on the MythTV wiki, but I find it very confusing, though I think I have sorted one thing out now. Am I correct in thinking I must get a DVB-T capable card? - Note: I am not needing to capture cable or satellite, both of which are too expensive and not really common place in Australia.


> **andrewc6l said:**
> 
 - at least a hyperthreading (HT) motherboard - a dual core might be better - to avoid jitter when you're watching TV while recording 2 inputs. (Recording the stream isn't too hard for digital, but playback / calculating commercial skip taxes the CPU.) Pick a "common" one - the more people who have it, the better the support, typically.

 - an NVIDIA video card - it works with the pcHDTVs which can offload some of their work. (I don't know about MSI support on Linux.)

 - a good cooling system. I burnt out two video cards before I got smart and put a fan in the right place.

 - a big hard drive (1T or so). HD streams are about 7G/h.

 - I think I've got 1G of RAM - Myth never seems to use much at all.

MythBuntu 9.04 was easy for me. I haven't upgraded to 9.10 yet; hopefully it will be as smooth. My GF had no problem using MythBuntu once she figured out where a few things were in the menu system.

I was planning on using a dual core, since they have come down in price and I'm building from scratch. I also want to underclock the CPU to help with heating and power consumption.

I'll keep the NVIDIA tip in mind.

I'll also keep the cooling in mind, I was thinking if I do build this I might use a micro controller and some temperature sensors to monitor things and control the fans, hopefully I can only run the fans when needed, instead of all of the time.

I discovered I can get a 2GB DDR2 stick for $54, which will probably be what I go with.




> **cascade9 said:**
> You shouldnt have any major problems with motherboards. 

PSU size- 350-400watts, should do it, go no bigger than 550watts (it would just be a major waste)



Thanks, that's very useful.


> **cascade9 said:**
> 
A 9600GT 1GB is overkill. Besides, VDPAU has 3 difference 'feature sets'-


[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

9600GT is feature set 'A'. An 8400GS is more than you need for a mythTV box, and its feature set 'B'. Probably the best choice would be a GT210/220, for feature set 'C'. Its cheaper than the 9600GT as well, nice bonus. 

I have no idea on how/if you can connect sound cards to video card HDMI. I check this, a lot, before you get anything (stupid HDMI). 



Does the brand matter?
My local supplier (MSY) is selling the following:

[B]512M GT210
[/B]Inno3D $47
Gainward $47
MSI $47
Gigabyte $54
Asus $56

**512M GT220** Inno3D $66

**1G GT220 **
Inno3D $75
Gainward $75
MSI $75
Gigabyte $88
ASUS $95


> **cascade9 said:**
> 
Hmm..you could poke the mythTV wiki and check- 
[http://www.mythtv.org/wiki/Video_capture_card](http://www.mythtv.org/wiki/Video_capture_card)

IIRC, when I costed one for a friend a few months ago, it was about $90-100 for a decent capture card ($AU). He ended up importing one from the US for $70. That would make your budget....tight. 

Your looking at 
$65-70 CPU 
$60-90 motherboard
??? capture card. 

If that still works, then I'll bother posting exact hardware prices. It might be more do-able from $$$ left over from changing video card (a GT210 is $65, I cant find a 8400GS with HDMI at my Qld supplies. I havent checked the S.A. suppliers now)

I've been reading through the MythTV wiki, though I have been a little confused as to what will and won't work in Australia, as I mentioned above, I mainly want to capture SD/HD digital and if possible analogue (via RF connection or S-Video)

What was the capture card that your friend purchased for $70?


If I go with the following:
512M GT210 ($47)
1TB Samsung ($95)
2G 800 Kingston ($54)
2X whatever TV tuner your friend bought (assuming it is appropriate for my needs) ($140)

Total: $336

I think that is still quite workable.



> **hrobinson said:**
> Hi Macka01,

Have you checked out this link:[U]  [http://www.mythtv.org/wiki/Hardware_Requirements](http://www.mythtv.org/wiki/Hardware_Requirements)
[/U] 
This will tell you in general what you might need.


I have indeed looked at it, my understanding is with the correct choice of capture and display cards, I can offload most of the processing from the CPU, meaning I don't need an overly beefy system, however I still need to keep in mind things like comm flagging


> **hrobinson said:**
> Have you ever built a home brew system yourself? 200.00 is quite a small budget for a new PVR system. Just the tuner card alone such as a Hauppauge - Dual PCI Express TV Tuner/Recorder Model: 2250 is around $149.00 alone. Come to think of it I don't know if MythTV supports this card very well yet.

Remember that you are not going to be able to do this on a severe budget, unless you can get a lot of your components for free or very cheap.[QUOTE]

I have never built a homebrew system myself, though I have certainly made changes to systems over the years, HDD replacements, adding network cards, replacing blown PSUs, adding RAM and cleaning.

My budget is more then $200, it's about $500, though it isn't exactly fixed, my father will be paying for the equipment, however I need to be able to compete with the Topfield unit mentioned above. I think he will be willing to pay up to $700, if it is better, however I'm setting my baseline for $500 and seeing where it goes from there. 


[QUOTE=hrobinson;8660230]I too would recommend a Dual Core processor with at least 1 gig of ram, an Nvidia video card (Stay away from ATI at all costs). The video card does not have to be powerful. The one I bought was a GEForce 6200 AGP (who uses AGP these days) for 49.00. You should not be spending more than 60 on the video card, it would be a waste of money and you would never use its full potential.


Trust me, I know enough people who have [had] problems with ATI, I wouldn't touch their stuff.


 > **hrobinson said:**
> 
Since you have a Hi Def TV you can connect the PVR directly to the TV using the VGA cable. For me, I have to have a TV out for my old Standard Def TV.


I would prefer HDMI, purely because the TV we have has 4 HDMI ports and I want to keep the VGA port free.


> **hrobinson said:**
> 
Do this project not because you want to save money, do it because you enjoy the challenge of doing it yourself. Not because you want to save money. I believe that the cable company can put a HD PVR in your house for around 150 per year (about 12 bucks or so a month). From expierence let me tell you its crappy. The hardware is limited and the interface is very slow. With Time Warners DVR I had to reboot it at least once a week to prevent it from filling up by itsself, and I can go on and on. Plus you can do nothing in the terms of upgrading it or adding functionality. For example, and i am speaking from Time Warner's perspective, you can not stream the contents of the DVR to other TV's in the house like you can with MythTV.


I do enjoy the challenge of the project, if I didn't I wouldn't even bother trying to work out which hardware I need. If it was my own money (and I had a job) I wouldn't be too worried about the cost.

We don't have cable to worry about, most Australians don't feel the need for it/can't afford it.

One of the main reasons for undertaking this project is because I'm not happy with what the commercial units provide, I feel they lack functionality,  using MythTV I get most of the functionality I want plus I can at least attempt to add my own, which is hard but not completely impossible with a commercial unit.


> **hrobinson said:**
> I have seen home built PVRs built for the cost of a new computer (not much more) or around 700 bucks. Processor not memory is key in an HD system, get the best processor you can afford and build the system around that. Remember you have to compensate for cooling, its not going to be a silent system. For High Def, I would suggest a two hard drives. One for the os (say the smallest you can buy 100gig or 150gig) and a 2TB drive to store your recordings. You can easily add another 2TB drive if this one runs out. and it will give you about 285 hours of programming. with a Commerical DVR you are lucky to get 30 hours ... and its not upgradeable.


I'll keep the advice on the processor in mind, though, I thought you could get away with a midrange if the video card had VDPAU.

I'm not planning on a silent system, I know that is very hard and not really possible with a hybrid setup, I'm happy with quiet to medium level noise as we have our TV up quite loud (3/6 people in our family suffer from hearing problems).

As for the HDD capacity, I don't know that we will store stuff for a long time, so we should get away with 1TB; it can always be upgraded later on if the need arises.


> **hrobinson said:**
> If you are looking for a quiet system, build Myttv as a split front end and back end. Place the back end with the cable box or antenna pickup in a closet and build a silent front end for next to the TV. This way you can add more front ends for each of the TV's in your house and the front ends can be cheaply built for around 300 per front end.

First step I would look at the link above to get an idea on what hardware you will need. You have an Idea in your mind what you expect out of your PVR. In other words what do you want MytTV to do for you, look at that and start to form a plan maybe on paper what you think you will need, not even putting a budget to it at this stage. At least you will have an idea what hardware you will need to buy vs what hard ware you can recycle for the project.

Good Luck!
and Welcome!

Sincerely,

Harold Robinson

At this stage, a hybrid front/back end system should be enough and there is always the choice to split the two in the future, depending on how well the initial system performs and whether or not we need to split it up.



> **shazbut said:**
> Have you found the OCAU MythTV wiki yet? It's a good Australian-specific resource, particularly for TV tuner brands that are commonly sold in shops like MSY etc. Looks like it hasn't been updated in a while, but some of the cards listed are probably still available.

[See here]("http://www.overclockers.com.au/wiki/MythTV")

I hadn't discovered it, thank you for the link, I'll start reading it right away.



Thank you very much to everyone for all of your advice so far.

Regards,

Andrew

---

### Post by Eldis on 2010-01-14
I find it very hard to believe a mythtv backend+frontend setup could be made cheaper than a commericially available product I doubt that is even the goal. Rather it's all the other bonuses that come with mythtv that are the reason for prefering mythtv to let's say some topfield box.

A mythtv setup can be made to be quite wife friendly but it takes time and patience from both the builder and the wife. If something goes fubar on my setup I easily spend 10h fixing it spread over a few days. The initial build for an experience user from building a pc to working solution is about 3h. For a newbie it could be 30-100h. It took me months to get my first build working but I was also a linux newbie then and to some extent still am.

I really love my mythtv setup despite the occasional troubles but it will eat up a lot of your spare time if you don't like fiddling with it I doubt you will be happy with it. I enjoy solving the problems with my setup and learning in the process.

My current 2 frontend + 1 backend setup is easily worth 1000$ (hdds and tuners eat up half of it) or more even if bought today and it's already on average ~2 year old components some new some 5 years old. But it does include everything I need. Next to my tv there is just 1 device. In the bedrooms the frontend is mounted behind the lcd's.

Good luck with whatever you decide.

---

### Post by cascade9 on 2010-01-14
> **Macka01 said:**
> I was planning on using a dual core, since they have come down in price and I'm building from scratch. I also want to underclock the CPU to help with heating and power consumption.

I'll also keep the cooling in mind, I was thinking if I do build this I might use a micro controller and some temperature sensors to monitor things and control the fans, hopefully I can only run the fans when needed, instead of all of the time.

I'm not planning on a silent system, I know that is very hard and not really possible with a hybrid setup, I'm happy with quiet to medium level noise as we have our TV up quite loud (3/6 people in our family suffer from hearing problems).

Fanless is pretty hard to do, and not really worth it for TV use IMO. Even fanless systems tend to not be totally silent, hdd noises etc are not that bad on a normal system, but with no fans, suddenly they sound a lot louder. But you should be able to get a very quiet system with underclocking. Getting a fanless video card might help, but they normally cost more than a standard card. 

> **Macka01 said:**
> I discovered I can get a 2GB DDR2 stick for $54, which will probably be what I go with.

I'd really go dual-channel myself. Its worth it for those few dollars more, the extra bandwidth will help, even more so on an underclocked system. Its only $6 more to get 2x1GB DDR2 (MSY prices). For DDR3 its $50 (1x2GB) vs $68 (2x1GB) but I would go dual there as well. 

> **Macka01 said:**
> 
Does the brand matter?
My local supplier (MSY) is selling the following:

[B]512M GT210
[/B]Inno3D $47
Gainward $47
MSI $47
Gigabyte $54
Asus $56

**512M GT220** Inno3D $66

**1G GT220 **
Inno3D $75
Gainward $75
MSI $75
Gigabyte $88
ASUS $95


 I'll keep the advice on the processor in mind, though, I thought you could get away with a midrange if the video card had VDPAU.

I have indeed looked at it, my understanding is with the correct choice of capture and display cards, I can offload most of the processing from the CPU, meaning I don't need an overly beefy system, however I still need to keep in mind things like comm flagging

I would prefer HDMI, purely because the TV we have has 4 HDMI ports and I want to keep the VGA port free.

Trust me, I know enough people who have [had] problems with ATI, I wouldn't touch their stuff.

You can get away with almost anything that supports VDPAU. Theres plenty of people with Atom 1.6Ghz (less power per Mhz than an athlon dualcore) and 8400GS cards. 
 
A GT210 would be fine. Brands...well, you'll always get people who like xxxx btrand, and otehr people who refused to buy zzzz brand. They all work though. 

I'd check what cards have HDMI, if you choose to use HDMI. IMO, its more of a pain than VGA/DVI. IIRC, HDMI was released in part for 'secure HD' (or whatever its called). Made so that that is is harder (meant o be impossible) to intercept HD signals, for 'anti-priacy'. 

I wouldnt get an ATI video card (the ATI version of VDPAU is windows only) but the chipsets are fine. I've been running nVidia on ATI chipset for ages now, 0 problems. 

> **Macka01 said:**
> What was the capture card that your friend purchased for $70?

I cant recall, but I've emailed him asking. It might take a few days to a week for hi to get back to me, hes a busy guy. 

I think that it actually will record 2 channels at once, but I'm waiting to find out. 

> **Macka01 said:**
> 
If I go with the following:
512M GT210 ($47)
1TB Samsung ($95)
2G 800 Kingston ($54)
2X whatever TV tuner your friend bought (assuming it is appropriate for my needs) ($140)

Total: $336

I think that is still quite workable.

I have never built a homebrew system myself, though I have certainly made changes to systems over the years, HDD replacements, adding network cards, replacing blown PSUs, adding RAM and cleaning.

I do enjoy the challenge of the project, if I didn't I wouldn't even bother trying to work out which hardware I need. If it was my own money (and I had a job) I wouldn't be too worried about the cost.

That looks fine to me, like I said, I would get 2x1GB, but its your choice. I'll chuck this in as well-

MSI 740GTM-P25 (AM2+, DDR2)- $47

> **Macka01 said:**
> We don't have cable to worry about, most Australians don't feel the need for it/can't afford it.

I'm always suprised at the number of people here who have cable, even if they dont use it much...maybe south australians are smarter LOL. 

> **Macka01 said:**
> 
One of the main reasons for undertaking this project is because I'm not happy with what the commercial units provide, I feel they lack functionality, using MythTV I get most of the functionality I want plus I can at least attempt to add my own, which is hard but not completely impossible with a commercial unit. 

Yeah, after checking the prices on the site you linked, you should be able to beat the commercial units on all areas (apart from maybe ease of use, and the potential for software issues. 

Good luck ;)

---

### Post by 365nice on 2010-01-14
Have you checked out the blog post by Asa - its about a year old, however I followed it 4 months ago with similar components and am very happy with the results. see: [http://www.winstanleys.org/tech/mythtv/](http://www.winstanleys.org/tech/mythtv/)

It will run without VDPAU and is very quiet - however I just got it to run with VDPAU with the latest stable fixes and am pleased with that as well.

Tim

---

### Post by SiHa on 2010-01-14
Just a thought, but nobody seems to have mentioned integrated graphics.
Just before Christmas I put together a new HD-capable frontend based around [[COLOR="Blue"]_this_[/COLOR]](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=3140) motherboard.
This has an Nvidia 8200 IGP. It doesn't need it, but if you get a nice big (quiet) downwards blowing fan (I use a Scythe Shuriken) it cools the graphics chipset as well.

One of the advantages of this IMHO is that IGP's generally use quite a bit less power than separate cards.

With a dual-Core Athlon II (65W nom) it pulls 55W total decoding HD with VDPAU. 

Oh, and HDMI-out (inc audio) worked OOB for Mythbuntu 9.10. Had to tweak a bit for audio outside of Myth, but nothing major.

---

### Post by laffinet on 2010-01-14
MSY carry the Asus USB MYC-U3100 for $58, which according to overclockers is well supported in myth

I would also recommend looking into motherboards with integrated nvidia graphics. If you can't find anything there, get a separate graphics card, 512M 9400 and up should be enough, which will set you back approx. $50.

---

### Post by Macka01 on 2010-01-15
> **Eldis said:**
> I find it very hard to believe a mythtv backend+frontend setup could be made cheaper than a commericially available product I doubt that is even the goal. Rather it's all the other bonuses that come with mythtv that are the reason for prefering mythtv to let's say some topfield box.


even if it ends up costing the same amount or a little more then most commercially available units, the features may very well out weigh the cost.

I am starting to believe it is possible to make it cheaper, though I may have to use a used capture card.


> **Eldis said:**
> A mythtv setup can be made to be quite wife friendly but it takes time and patience from both the builder and the wife. If something goes fubar on my setup I easily spend 10h fixing it spread over a few days. The initial build for an experience user from building a pc to working solution is about 3h. For a newbie it could be 30-100h. It took me months to get my first build working but I was also a linux newbie then and to some extent still am.


Luckily (perhaps not) I don't have a wife to worry about :P, just my mother and siblings, I think they should be able to cope though; my father doesn't stand a chance with our VCR, nor did he with the last one which we had for maybe 10 years, so there is no winning with him.

Do you update your system at all?

I plan to set it up, tweak it until it's the way I want and then not upgrade anything system-wise, to avoid problems.


> **Eldis said:**
> I really love my mythtv setup despite the occasional troubles but it will eat up a lot of your spare time if you don't like fiddling with it I doubt you will be happy with it. I enjoy solving the problems with my setup and learning in the process.

My current 2 frontend + 1 backend setup is easily worth 1000$ (hdds and tuners eat up half of it) or more even if bought today and it's already on average ~2 year old components some new some 5 years old. But it does include everything I need. Next to my tv there is just 1 device. In the bedrooms the frontend is mounted behind the lcd's.

Good luck with whatever you decide.

I do enjoy troubleshooting problems, but I do hope to be able to settle with a setup and be able to leave it alone (at least until the next MythTV stable update 0.23+ )


Thanks. At this stage I really do want to go ahead with the Myth setup, the idea has me quite excited!




> **cascade9 said:**
> Fanless is pretty hard to do, and not really worth it for TV use IMO. Even fanless systems tend to not be totally silent, hdd noises etc are not that bad on a normal system, but with no fans, suddenly they sound a lot louder. But you should be able to get a very quiet system with underclocking. Getting a fanless video card might help, but they normally cost more than a standard card.


If I find it a problem I could always add soundproofing and adjust fan speeds, but I doubt I'll have any issues with noise anyway.


> **cascade9 said:**
> I'd really go dual-channel myself. Its worth it for those few dollars more, the extra bandwidth will help, even more so on an underclocked system. Its only $6 more to get 2x1GB DDR2 (MSY prices). For DDR3 its $50 (1x2GB) vs $68 (2x1GB) but I would go dual there as well.


Ok, if I go ahead with this I'll definitely follow this advice.


> **cascade9 said:**
> You can get away with almost anything that supports VDPAU. Theres plenty of people with Atom 1.6Ghz (less power per Mhz than an athlon dualcore) and 8400GS cards.

A GT210 would be fine. Brands...well, you'll always get people who like xxxx btrand, and otehr people who refused to buy zzzz brand. They all work though.

I'd check what cards have HDMI, if you choose to use HDMI. IMO, its more of a pain than VGA/DVI. IIRC, HDMI was released in part for 'secure HD' (or whatever its called). Made so that that is is harder (meant o be impossible) to intercept HD signals, for 'anti-priacy'.

I wouldnt get an ATI video card (the ATI version of VDPAU is windows only) but the chipsets are fine. I've been running nVidia on ATI chipset for ages now, 0 problems.


The reason I don't like ATI isn't the hardware, it is the buggy drivers they release for Windows.

How come HDMI is a pain?
It has always looked an easier option with only one cable for audio and HD video


> **cascade9 said:**
> I cant recall, but I've emailed him asking. It might take a few days to a week for hi to get back to me, hes a busy guy.

I think that it actually will record 2 channels at once, but I'm waiting to find out.


I'm currently looking at a Hauppauge Nova-T 500 PCI Dual HD TV Tuner Card, it can do 2 channels and is apparently compatible with Aussie standards, though I'm still interested in what your friend is using, it may be better.


> **cascade9 said:**
> That looks fine to me, like I said, I would get 2x1GB, but its your choice. I'll chuck this in as well-

MSI 740GTM-P25 (AM2+, DDR2)- $47



I'm always suprised at the number of people here who have cable, even if they dont use it much...maybe south australians are smarter LOL.


Are they selling that at MSY or somewhere else?

I think most people with a cable connection in SA use it primarily for internet, I only know of a very small handful of people who actually use it for TV.


> **cascade9 said:**
> Yeah, after checking the prices on the site you linked, you should be able to beat the commercial units on all areas (apart from maybe ease of use, and the potential for software issues.

Good luck 

LOL, so I'm not the only one who thinks it's over priced :D

Thanks.



> **365nice said:**
> Have you checked out the blog post by Asa - its about a year old, however I followed it 4 months ago with similar components and am very happy with the results. see: [http://www.winstanleys.org/tech/mythtv/](http://www.winstanleys.org/tech/mythtv/)

It will run without VDPAU and is very quiet - however I just got it to run with VDPAU with the latest stable fixes and am pleased with that as well.

Tim

I have now. That's a very good find you made.



> **SiHa said:**
> Just a thought, but nobody seems to have mentioned integrated graphics.
Just before Christmas I put together a new HD-capable frontend based around [[COLOR=Blue]_this_[/COLOR]]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=3140") motherboard.
This has an Nvidia 8200 IGP. It doesn't need it, but if you get a nice big (quiet) downwards blowing fan (I use a Scythe Shuriken) it cools the graphics chipset as well.

One of the advantages of this IMHO is that IGP's generally use quite a bit less power than separate cards.

With a dual-Core Athlon II (65W nom) it pulls 55W total decoding HD with VDPAU. 

Oh, and HDMI-out (inc audio) worked OOB for Mythbuntu 9.10. Had to tweak a bit for audio outside of Myth, but nothing major.

*Drools* I think that MoBo is perfect, I'm just not sure if it is the same as this one that MSY is selling: G-B-M85M-US2H  ($75)

I googled that board and nothing, so I am assuming it was a typo on their part; not likely to be much point even asking them, they don't answer the phone, or emails and if you ask in store they sort of ignore you or tell you what you want to hear, even if it isn't correct.

Not too worried if it doesn't work outside Myth, specially if it is easily fixed.



> **laffinet said:**
> MSY carry the Asus USB MYC-U3100 for $58, which according to overclockers is well supported in myth

I would also recommend looking into motherboards with integrated nvidia graphics. If you can't find anything there, get a separate graphics card, 512M 9400 and up should be enough, which will set you back approx. $50.

I'm sure I read somewhere in the Myth wiki that USB capture cards aren't so fantastic, do you have any experience with them?


Yes, I think I might go the way of integrated graphics. Do you know anything about the motherboard I mentioned above (G-B-M85M-US2H)?



So far, if I go with:
Samsung SATA 1TB ($95)
2X 1G 800 Kingston ($60)
G-B-M85M-US2H [assuming it is the correct board] ($75)
Hauppauge Nova-T 500 [seems like the best option so far] (~$70) - I am tracking one on ebay, but I'm likely to miss it anyway, otherwise I wouldn't post this.

Total: $300

That leaves the CPU and the case + optional remote + DVD burner. I may make it <$500 yet :P

---

### Post by cascade9 on 2010-01-15
> **Eldis said:**
> The initial build for an experience user from building a pc to working solution is about 3h. For a newbie it could be 30-100h. It took me months to get my first build working but I was also a linux newbie then and to some extent still am.

This really depends. The 1st time it took me about 4-5hrs (cheap AT case, that says how long ago it was). I think all that childhood lego experience paid off on my 1st build. 

If I 'oohhh' and 'aaahhh' over parts, have a case I havent used before, do a really neat job on cabling and have a non-modular power supply it takes me about 2hrs. Flatout, with a nice workbench setup I have done it in under 30 minutes (and packed the boxes up in that time LOL) 

But I've assembled computers for a living, so I'm hardly typical.  

> **Macka01 said:**
> The reason I don't like ATI isn't the hardware, it is the buggy drivers they release for Windows.

Thankfully, ATI chipset motherboards dont need driver installs under linux. Makes life easier. I had no issues with the ATI chipset under windows for that matter...but I've had real problems here and there with ATI video cards under both windows and linux. 

> **Macka01 said:**
> 
How come HDMI is a pain?
It has always looked an easier option with only one cable for audio and HD video


I've had nasty problems with HDMI, mainly with windows but also with linux. Mostly from audio. Other people haven't (like SiHa).

Last time I checked the cables were more expensive than a GVA/DVI cable and 3.5mm jacks to RCA connections and I've always got spare VGA/DVI cables. I've just rather avoid HDMI myself, but I can see why it would look attractive. 

If SiHa had no issues with HDMI under myth then it looks better IMO. 

> **Macka01 said:**
> 
Are they selling that at MSY or somewhere else?


Yep, that was from MSY. 

> **Macka01 said:**
> *Drools* I think that MoBo is perfect, I'm just not sure if it is the same as this one that MSY is selling: G-B-M85M-US2H  ($75)

I googled that board and nothing, so I am assuming it was a typo on their part; not likely to be much point even asking them, they don't answer the phone, or emails and if you ask in store they sort of ignore you or tell you what you want to hear, even if it isn't correct.

Not too worried if it doesn't work outside Myth, specially if it is easily fixed.


I'm really sorry to say, but there are 4 (!!) versions of that motherboard. Main difference is ver1.0 uses an geforce 8100 chipset/graphics, ver1.1 (and above) have geforce 8200. 

I the 8100 should do myth though, it does do VDPAU. 

MSY is _exactly_ the same here. They never seem to answer the phone, or emails, etc. I have got them to answer 1 time.....then they told me part 'a' was in stock when they were selling part 'b' (A WD-GP 1TB drive, to be exact, and I wanted the 32MB cache version, they said they had it, but it was the 16MB version. I think they were suprised when I read the drive label and said 'sorry, not interested' and walked out)

Still waiting for my friend to get back to me. From what his wife said this evening, hes a bit busy at work,and might not tell me anything till tuesday, his 1 day off a week. Sorry. I will post what hes got when he does though.

---

### Post by Macka01 on 2010-01-16
> **cascade9 said:**
> This really depends. The 1st time it took me about 4-5hrs (cheap AT case, that says how long ago it was). I think all that childhood lego experience paid off on my 1st build. 

If I 'oohhh' and 'aaahhh' over parts, have a case I havent used before, do a really neat job on cabling and have a non-modular power supply it takes me about 2hrs. Flatout, with a nice workbench setup I have done it in under 30 minutes (and packed the boxes up in that time LOL) 

But I've assembled computers for a living, so I'm hardly typical.  


I'm not overly worried about assembly time, I am likely to move slowly and carefully, ensuring cabling is neat to maximise airflow and make it easier for future cleaning. I'd expect 2 - 3 hours tops.

I'm sure both Meccano and lego skills would be useful, 'specially if there are any fiddly screws and nuts for securing the mobo.


> **cascade9 said:**
> Thankfully, ATI chipset motherboards dont need driver installs under linux. Makes life easier. I had no issues with the ATI chipset under windows for that matter...but I've had real problems here and there with ATI video cards under both windows and linux. 



I've had nasty problems with HDMI, mainly with windows but also with linux. Mostly from audio. Other people haven't (like SiHa).

Last time I checked the cables were more expensive than a GVA/DVI cable and 3.5mm jacks to RCA connections and I've always got spare VGA/DVI cables. I've just rather avoid HDMI myself, but I can see why it would look attractive. 

If SiHa had no issues with HDMI under myth then it looks better IMO. 



Yep, that was from MSY. 



I'm really sorry to say, but there are 4 (!!) versions of that motherboard. Main difference is ver1.0 uses an geforce 8100 chipset/graphics, ver1.1 (and above) have geforce 8200. 

I the 8100 should do myth though, it does do VDPAU.



4 version? I assume they are GA, GB, GC, GD ?

If you are correct that the GB has a GeForce 8200 chipset, that should be compatible, the Myth wiki certainly suggests so.

Is there anything I need to be aware of with this particular (GB M85M-US2H) motherboard? I haven't been able to find any issues on google.


> **cascade9 said:**
> MSY is _exactly_ the same here. They never seem to answer the phone, or emails, etc. I have got them to answer 1 time.....then they told me part 'a' was in stock when they were selling part 'b' (A WD-GP 1TB drive, to be exact, and I wanted the 32MB cache version, they said they had it, but it was the 16MB version. I think they were suprised when I read the drive label and said 'sorry, not interested' and walked out)


I think the reason they are like that is it's cheaper to not give any support. It seems to me that with most things, if the price is good the service is not so, if the price is steep the service is usually very good, similar to Internode and TPG. Internode is a bit pricey, but customer service is supposed to be good, TPG on the other hand has very cheap service but I find their customer support to be lousy - if you can't diagnose it yourself TPG tends to be a bad choice.

I bet the guy got a big shock; most people tend to fold with them, me included (though the issue wasn't big); they told me they had one type of RAM and supplied another, though they did assure me it was compatible and they were right.

> **cascade9 said:**
> Still waiting for my friend to get back to me. From what his wife said this evening, hes a bit busy at work,and might not tell me anything till tuesday, his 1 day off a week. Sorry. I will post what hes got when he does though.

No problem, I know what it's like to be busy, though possibly not as busy as he is - I am still a student after all. :P



Would someone mind checking my parts list below? In particular, I want to know if the CPU is compatible with the mobo, as far as I can tell, it is; also, did I miss anything?.

What        Part                Where                Price        Qty    Tot

MOBO        GA-M85M-US2H            MSY                $75        1    $75
CPU        AM3 x2 Athlon 240        MSY                $66        1    $66
RAM        1G 800 Kingston            MSY                $30        2    $60
HDD        Samsung SATA 1TB        MSY                $95        1    $95
Tuner        Hauppauge Nova-T 500        EBAY                ~$70        1    $70
DVD-WR        SATA Aopen            MSY                $33        1    $33
Case
Remote    (may come with tuner)        

Total:                                                    $399 + case


Any recommendations for Cases? not too worried how it looks, I was even considering making one with wood and drilling ventilation holes. As nice as a wooden one may look (it would fit in with the cabinet), I don't really want to go to the effort of building it, techstudies was never really my thing.

---

### Post by cascade9 on 2010-01-16
> **Macka01 said:**
> I'm not overly worried about assembly time, I am likely to move slowly and carefully, ensuring cabling is neat to maximise airflow and make it easier for future cleaning. I'd expect 2 - 3 hours tops.

I'm sure both Meccano and lego skills would be useful, 'specially if there are any fiddly screws and nuts for securing the mobo.

There some smallish patrs, the most fiddly bit is getting the screws into the standoffs. (standoffs = the 'spacers' that raise the motherboard off the motherboard tray in the case).    

IT used to be a lot harder when cases had plastic standoffs (like my old AT case did). Those things were super-fiddly. 

> **Macka01 said:**
> 
4 version? I assume they are GA, GB, GC, GD ?

If you are correct that the GB has a GeForce 8200 chipset, that should be compatible, the Myth wiki certainly suggests so.

Is there anything I need to be aware of with this particular (GB M85M-US2H) motherboard? I haven't been able to find any issues on google.

Nope, they atre all called  GA-M85M-US2H. The revision number appears on the end, e.g. GA-M85M-US2H (rev 1.0).
If you look at the gigabyte site, you can see links to the other revisions (under the main name at top, next to where it says "other version:")- 

[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3081#anchor_os](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3081#anchor_os)

MSY has labeled the GA-M85M-US2H as 'GB-M85M-US2H' because of 'GigaByte'. Its just so people know the brand, not the offical numbering.  

> **Macka01 said:**
> 
I think the reason they are like that is it's cheaper to not give any support. It seems to me that with most things, if the price is good the service is not so, if the price is steep the service is usually very good, similar to Internode and TPG. Internode is a bit pricey, but customer service is supposed to be good, TPG on the other hand has very cheap service but I find their customer support to be lousy - if you can't diagnose it yourself TPG tends to be a bad choice.

I bet the guy got a big shock; most people tend to fold with them, me included (though the issue wasn't big); they told me they had one type of RAM and supplied another, though they did assure me it was compatible and they were right. 

From what I've heard, MSY is cheaper than most because of the amount of stock they buy. I've spoken to small computer stores that pay more for parts from the importer than MSY charges retail! They also tend to get a lot of the 'old stock' and discontinued items (like 'rev 1.0' motherboards when rev 1.1/1.2/1.3 versions come out) for as cheap as possible and sell it

Similar priced stores here, like umart (where I go) and gamedude (yes lame name, and they have a shocking attitude) actually have people that answer phones, and will tell you what they actually have in stock and not get it wrong. (umart in particular is very good for that, they have 'in stock/out of stock/special order' next to ever part listed, with real time updates. Also, a much larger range of stock than MSY)

Yeah, the guy was a bit shocked. Im not sure about the S.A. store, but the MSY shops here are in odd places, and I think that when most people have got there they say to themselves 'I cant be bothered to drive all the way over town to get a very similar thing from xxx store'. If  they even know the difference between the parts.  

> **Macka01 said:**
> 
Would someone mind checking my parts list below? In particular, I want to know if the CPU is compatible with the mobo, as far as I can tell, it is; also, did I miss anything?.

What        Part                Where                Price        Qty    Tot

MOBO        GA-M85M-US2H            MSY                $75        1    $75
CPU        AM3 x2 Athlon 240        MSY                $66        1    $66
RAM        1G 800 Kingston            MSY                $30        2    $60
HDD        Samsung SATA 1TB        MSY                $95        1    $95
Tuner        Hauppauge Nova-T 500        EBAY                ~$70        1    $70
DVD-WR        SATA Aopen            MSY                $33        1    $33
Case
Remote    (may come with tuner)        

Total:                                                    $399 + case


Any recommendations for Cases? not too worried how it looks, I was even considering making one with wood and drilling ventilation holes. As nice as a wooden one may look (it would fit in with the cabinet), I don't really want to go to the effort of building it, techstudies was never really my thing.

Parts list looks fine to me. CPU is totally compatible. A pity that MSY doesnt sell DDR2-1066 (supported by that motherboard/CPU combo) but that is part of how they make their money....

Well, apart from the Tuner that I relly havent checked out. Ohhh, and I havent used a Aopen DVD-RW drive, all my DVD-RWs are pioneer, asus ('rebranded' poineer) and sony. But it should work fine. 

As for case...what do you want in a case? Are you fine with a tower, or do you want a desktop (flat) case? Since that gigabyte motherboard is microATX, you could get a microATX case if you want something a little smaller. 

Pity you dotn live here, I've got a Silverstone LCV-20BM (multimedia sytle case, with remote) that I'm thinking I should sell before my next move. *sighs* and I've got a ton of parts I need to get rid of while I think about it :(

---

### Post by Macka01 on 2010-01-16
> **cascade9 said:**
> There some smallish patrs, the most fiddly bit is getting the screws into the standoffs. (standoffs = the 'spacers' that raise the motherboard off the motherboard tray in the case).    

IT used to be a lot harder when cases had plastic standoffs (like my old AT case did). Those things were super-fiddly. 


What do they make them out of these days? I've seen some old computers (1990 and older) with metal standoffs and my PC with plastic standoffs (2001).


> **cascade9 said:**
> Nope, they atre all called  GA-M85M-US2H. The revision number appears on the end, e.g. GA-M85M-US2H (rev 1.0).
If you look at the gigabyte site, you can see links to the other revisions (under the main name at top, next to where it says "other version:")- 

[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3081#anchor_os](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3081#anchor_os)

MSY has labeled the GA-M85M-US2H as 'GB-M85M-US2H' because of 'GigaByte'. Its just so people know the brand, not the offical numbering.



That makes sense, but I think they'd do better to use a different format for their pricelist and just include the brand and the true model name.


> **cascade9 said:**
> From what I've heard, MSY is cheaper than most because of the amount of stock they buy. I've spoken to small computer stores that pay more for parts from the importer than MSY charges retail! They also tend to get a lot of the 'old stock' and discontinued items (like 'rev 1.0' motherboards when rev 1.1/1.2/1.3 versions come out) for as cheap as possible and sell it

Similar priced stores here, like umart (where I go) and gamedude (yes lame name, and they have a shocking attitude) actually have people that answer phones, and will tell you what they actually have in stock and not get it wrong. (umart in particular is very good for that, they have 'in stock/out of stock/special order' next to ever part listed, with real time updates. Also, a much larger range of stock than MSY)

Yeah, the guy was a bit shocked. Im not sure about the S.A. store, but the MSY shops here are in odd places, and I think that when most people have got there they say to themselves 'I cant be bothered to drive all the way over town to get a very similar thing from xxx store'. If  they even know the difference between the parts.  


The amount of/location they purchase from would be the main factor, but I do think their customer service is reflected by their price.

Shame MSY don't have a similar system, I know for a fact Dick Smith Electronics have the system, they just don't make the data publicly available; the number of hours we could have saved if DSE did make it available...


MSY stores over here aren't too poorly placed, there is one near-ish to me, 20 mins by bicycle, 5 mins or so by car. The other one is near China town in the city (a good location since all of their SA employees are Chinese), ~15 mins drive from home. Adelaide is small to say the least, so it would be hard for them to put them in odd spots.


> **cascade9 said:**
> Parts list looks fine to me. CPU is totally compatible. A pity that MSY doesnt sell DDR2-1066 (supported by that motherboard/CPU combo) but that is part of how they make their money....

Well, apart from the Tuner that I relly havent checked out. Ohhh, and I havent used a Aopen DVD-RW drive, all my DVD-RWs are pioneer, asus ('rebranded' poineer) and sony. But it should work fine.


Excellent, I thought it may end up that MSY sold the mobo and not the corresponding CPU(s).

Yeah, I noticed that they didn't have the faster RAM

As for the DVD drive, I plan to just get a cheap one, I'm not expecting it will get a lot of use. Pioneer is only $5 more, so I may go for that (assuming I do go ahead with this build, I really hope to, final say isn't up to me though).


> **cascade9 said:**
> As for case...what do you want in a case? Are you fine with a tower, or do you want a desktop (flat) case? Since that gigabyte motherboard is microATX, you could get a microATX case if you want something a little smaller. 

Pity you dotn live here, I've got a Silverstone LCV-20BM (multimedia sytle case, with remote) that I'm thinking I should sell before my next move. *sighs* and I've got a ton of parts I need to get rid of while I think about it :(

I'll put up with a tower if I have to, but a desktop/horizontal tower is preferable.

A friend recommended I get:
Case      Coolermaster RC334        MSY                $75
PSU        Vantec ION 460            MSY                $52

However that is a tower and it doesn't appear to be too easy to mount the DVD drive along the case. I have seen towers used as desktops with optical drives mounted along the case rather then across, but I'm not sure how to do it.

If postage wasn't expensive, I would ask how much you want to sell it for.


I have attached an image with our cabinet dimensions. I am wanting to remove the VCR and replace it with a Mythbox (or other PVR), put the Wii up with the DVD player (if I use a Mythbox, hopefully there will be no need for the DVD player).



As a side note, I did think about using the Wii as a frontend and using a Myth backend, but the Wii is only capable of SD video (using Homebrew and a ported version of MPlayer).


take a quick look at these prices: [http://www.harveynorman.com.au/page/search?q=PVR](http://www.harveynorman.com.au/page/search?q=PVR) I nearly died.

---

### Post by cascade9 on 2010-01-16
> **Macka01 said:**
> What do they make them out of these days? I've seen some old computers (1990 and older) with metal standoffs and my PC with plastic standoffs (2001).


Brass. That is what 99% of non-plastic standoffs I've ever seen have been made out of (seen the odd 'is it pot metal or some sort of crappy steel', mainly in compaqs) 

> **Macka01 said:**
> That makes sense, but I think they'd do better to use a different format for their pricelist and just include the brand and the true model name.

They would IMO as well. 


> **Macka01 said:**
> The amount of/location they purchase from would be the main factor, but I do think their customer service is reflected by their price.

Shame MSY don't have a similar system, I know for a fact Dick Smith Electronics have the system, they just don't make the data publicly available; the number of hours we could have saved if DSE did make it available...

Probably, yeah. But to get really good customer service, you pay for it. Places like MSY/Umart/gamedude will make you fill out 'RMA' (return to maunfacturer) forms if something goes wrong, other places will just take the part from you and give you a replacement. 

> **Macka01 said:**
> 
MSY stores over here aren't too poorly placed, there is one near-ish to me, 20 mins by bicycle, 5 mins or so by car. The other one is near China town in the city (a good location since all of their SA employees are Chinese), ~15 mins drive from home. Adelaide is small to say the least, so it would be hard for them to put them in odd spots.


Dont temp me even more to move to adelaide. I'm already temped badly, if it wasnt for family I would probably have moved there years ago....

> **Macka01 said:**
> 
Yeah, I noticed that they didn't have the faster RAM

As for the DVD drive, I plan to just get a cheap one, I'm not expecting it will get a lot of use. Pioneer is only $5 more, so I may go for that (assuming I do go ahead with this build, I really hope to, final say isn't up to me though).


Its a pity, but it wont matter that much. I'd just live with DDR2 800 unless you can find some local shop that gets close to MSY prices. Or imprt from the US, the RAM prices there can be shockingly good at times. 


> **Macka01 said:**
> I'll put up with a tower if I have to, but a desktop/horizontal tower is preferable.

A friend recommended I get:
Case      Coolermaster RC334        MSY                $75
PSU        Vantec ION 460            MSY                $52

I wouldnt bother buying a power supply with coolermaster cases that come with a PSU. The coolermasters PSUs are the best of the 'budget' ones IMO. 

BTW- just to make thing easier- get the RC-360- 

[http://www.coolermaster.com/product.php?product_id=6056](http://www.coolermaster.com/product.php?product_id=6056)

Yes, that does convert from tower to desktop config. Good case, nice and cheap, decent power supply, its what your after. 

> **Macka01 said:**
> However that is a tower and it doesn't appear to be too easy to mount the DVD drive along the case. I have seen towers used as desktops with optical drives mounted along the case rather then across, but I'm not sure how to do it.

If postage wasn't expensive, I would ask how much you want to sell it for.


Most of the cases that I've sen that have some way to 'twist' the optical drives have been corporate boxxen. It was very common on compaqs for a while. 

BTW, you dont need to do this. Almost all optical drives work in 'up and down' and as well the standard 'side to side' layout. 

[QUOTE=Macka01;8673674
I have attached an image with our cabinet dimensions. I am wanting to remove the VCR and replace it with a Mythbox (or other PVR), put the Wii up with the DVD player (if I use a Mythbox, hopefully there will be no need for the DVD player).[/QUOTE]

LOL, the RC-360 will slide into your current VCR slot perfectly. 152.4mm space, and the case is 148mm. :biggrin: Couldnt have made a better fit if it was custom made for that case.

---

### Post by Macka01 on 2010-01-16
> **cascade9 said:**
> Dont temp me even more to move to adelaide. I'm already temped badly, if it wasnt for family I would probably have moved there years ago....

Its a pity, but it wont matter that much. I'd just live with DDR2 800 unless you can find some local shop that gets close to MSY prices. Or imprt from the US, the RAM prices there can be shockingly good at times. 


Most people from other states find Adelaide boring, too small and not much to do. Personally, I quite like it here, unfortunately when I finish my degree I will probably have to move to Sydney to get work.


> **cascade9 said:**
> I wouldnt bother buying a power supply with coolermaster cases that come with a PSU. The coolermasters PSUs are the best of the 'budget' ones IMO. 

BTW- just to make thing easier- get the RC-360- 

[http://www.coolermaster.com/product.php?product_id=6056](http://www.coolermaster.com/product.php?product_id=6056)

Yes, that does convert from tower to desktop config. Good case, nice and cheap, decent power supply, its what your after. 

Most of the cases that I've sen that have some way to 'twist' the optical drives have been corporate boxxen. It was very common on compaqs for a while. 


I was told to watch out for them as they tend to die sooner rather then later, but I may  as well go with the one it comes with, until it actually does die.

The RC-360 is much better, being in desktop form. I like the fact it can oporate in either tower or desktop and it looks a lot like a media PC case/a real AV appliance.

The issue was mostly the panels don't seem to be designed for having it rearranged, even though I could probably mount the drive with a different orientation.

> **cascade9 said:**
> BTW, you dont need to do this. Almost all optical drives work in 'up and down' and as well the standard 'side to side' layout.

I'm aware of that, however it is too awkward to be using it on its side for most members of the family.


> **cascade9 said:**
> LOL, the RC-360 will slide into your current VCR slot perfectly. 152.4mm space, and the case is 148mm. :biggrin: Couldnt have made a better fit if it was custom made for that case.

That case is absolutely perfect, there may even be left over room on the bottom shelf with that in place.



Thank you for all of your help, I am hoping to buy the components tomorrow and perhaps even begin assembly.

---

### Post by Macka01 on 2010-01-18
I am pleased to report that as far as I can tell, I have successfully built most of the system, I am just needing a molex-sata connector and I am waiting for the tuner card I bough on ebay.

The mobo ended up costing $70 ($5 discount as it was missing the back plate), the HDD was $6 more, as it was a Seagate. I decided to start with 1GB RAM, and upgrade later if necessary.

Total cost of all parts (inc tuner and Arctic Silver) $456.67

Computer can boot to BIOS config and asks for a boot disk, so I think I can safely assume everything is connected properly. Idling on the BIOS screen the temperature of the CPU is 37°C

I was pleasantly surprised by the MSY salespersons attitude, the first store I went to didn't have the motherboard, but he was happy to try and find an equivalent and was rather helpful. I had to phone the other MSY stores (they don't share stock information, nor can you return parts bought at one store to another store), Adelaide store, as usual took forever to pickup, but the other stores answered with in a few seconds and were much more pleasant than usual.

Now it's just a matter of installing the TV tuner card, getting the DVD drive working and installing Mythbuntu. Can't wait!

---

### Post by cascade9 on 2010-01-19
> **Macka01 said:**
> Most people from other states find Adelaide boring, too small and not much to do. Personally, I quite like it here, unfortunately when I finish my degree I will probably have to move to Sydney to get work.

Gah! Sydney is a hole. Melbourne and Brisneyland are nicer, but who knows how much work there is compared to sydney.  

> **Macka01 said:**
> 
I was told to watch out for them as they tend to die sooner rather then later, but I may  as well go with the one it comes with, until it actually does die.

The RC-360 is much better, being in desktop form. I like the fact it can oporate in either tower or desktop and it looks a lot like a media PC case/a real AV appliance.

I've built a few machines with standard 420 watt coolermaster PSUs, and so far I've been pretty impressed. Not a single failure so far, and one of them has been up for almost 3 years non-stop now. 


> **Macka01 said:**
> 
The issue was mostly the panels don't seem to be designed for having it rearranged, even though I could probably mount the drive with a different orientation.


If the case hasnt been made to allow the drive bays to be 'swung' from side to side over to up and dwn (case in 'tower' mode) then its a right pain to try this. 'Lots of hardware hacking, bleeding, swearing and sweating' type pain. 

> **Macka01 said:**
> 
I'm aware of that, however it is too awkward to be using it on its side for most members of the family.


Fair enough. I had problems training my mum to use a optical drive with it 'pointing the wrong way' (in the end I just built a new case for her)


> **Macka01 said:**
> 
That case is absolutely perfect, there may even be left over room on the bottom shelf with that in place.

Thank you for all of your help, I am hoping to buy the components tomorrow and perhaps even begin assembly.
:mrgreen:

Good luck with building....and cheap advice, if you find you're getting mad at something, go outside and yell at trees/traffic/busses, etc. Sometimes the 1st build can get really fustrating, and its better to avoid playing with delicate computer parts when your mad. At least I know I shouldnt. ;)

---

### Post by mythbuntu101 on 2010-01-19
I just got my system going and flew by the setup after install of Mythbuntu. Does anybody know how to edit the graphic card settings, after install. I have an nVidia card but the settings were set to default. I want to change to use the nVidia drivers.

---

### Post by mythbuntu101 on 2010-01-20
I did a fresh install could not reset the graphic drivers for nVidia use.

---

### Post by Macka01 on 2010-01-20
> **mythbuntu101 said:**
> I just got my system going and flew by the setup after install of Mythbuntu. Does anybody know how to edit the graphic card settings, after install. I have an nVidia card but the settings were set to default. I want to change to use the nVidia drivers.
> **mythbuntu101 said:**
> I did a fresh install could not reset the graphic drivers for nVidia use.


I wish I could help, but as of yet, I know very little about the Linux OS

---

### Post by cascade9 on 2010-01-21
> **mythbuntu101 said:**
> I did a fresh install could not reset the graphic drivers for nVidia use.

You tried "System-> Administration-> Hardware Drivers" and then ticking the 'enable restricted drivers' box?

---

### Post by mythbuntu101 on 2010-01-21
Should I do that? What will it do for me?

---

### Post by williammanda on 2010-01-21
> **mythbuntu101 said:**
> Should I do that? What will it do for me?

When you do that select the most current driver first and then enable. What this does is install the Nvidia driver, it sounds like right now you are using Ubuntus driver.

---

### Post by mythbuntu101 on 2010-01-21
I'm using an nVidia driver but it's application does not offer an option to scale the desktop to an 1080p HDTV. Driver application says nVidia Server. I'll get more details on this post after I leave work.

---

### Post by mythbuntu101 on 2010-01-21
dont have the following path in mythbuntu 9.10

"System-> Administration-> Hardware Drivers" and then ticking the 'enable restricted drivers' box

i do see Applications->System->nvidia x server settings

the above still does not have an option for me to scale my desktop to my hdtv (1080p)

also Applications->System->Hardware drivers shows accelerated graphics driver 185 but there is still no way for me to scale my desktop to hdtv

---

### Post by cascade9 on 2010-01-22
> **mythbuntu101 said:**
> dont have the following path in mythbuntu 9.10

"System-> Administration-> Hardware Drivers" and then ticking the 'enable restricted drivers' box

i do see Applications->System->nvidia x server settings

the above still does not have an option for me to scale my desktop to my hdtv (1080p)

also Applications->System->Hardware drivers shows accelerated graphics driver 185 but there is still no way for me to scale my desktop to hdtv

Have you tried to set the resolution to 1920x1080 when its hooked up to the TV? I cant recall now if the nvidia settings block resolutions that your current monitor cant output. (I think it does, so if your current monitors max resolution is 1600x1200 that is the highest resolution you can set)  

I'd check.....but I'm using a very nice 17'' monitor that goes to 1920x1440 so almost every resolution is open for me.

---

### Post by mythbuntu101 on 2010-01-22
yes, in 'nvidia x server settings' my hdtv (model LG LH30 37") is recognized and resolution set to 1920x1080 . The desktop is really overscaling on the TV though. My output cable is dvi (out) to hdmi (in) . My motherboard has an integratred nvidia 8300 (Asus M4N78 Pro). Maybe the dvi (currently using) output also hdmi output (not tried) are an issue. Asus PDF Manual page # 28 ( 1-18 ) has a solution but I do not see the nvidia screens or application within Mythbuntu 9.10 as suggested in the Asus Manual ( [http://www.logikbase.com/E4387_M4N78%20PRO.pdf]("http://www.logikbase.com/E4387_M4N78%20PRO.pdf") )

---

### Post by Macka01 on 2010-01-25
I received the TV tuner card on Friday and finally purchased a molex-sata power adapter. I previously couldn't install Mythbuntu as my DVD drive had no power and I was getting black screening with the USB loader (tried several different recommended fixes, none worked)

MSY sold out of HDMI cables earlier today, so I missed out again, however I successfully installed Mythbuntu and started setting up MythTV. I even managed to get the TV tuner working, though only one of it 2 tuners (I need an aerial splitter or I'll solder an internal bridge on the card).

EPG is out though, approximately the time is approximately +10:30 from what it should be. I think it may be due to my mobo not using local time and Ubuntu is adding on a further 10:30. I haven't been able to find a solution so far, do you know how to fix this (without changing the BIOS time)? - if not, I'll reinstall.

I have also started documenting my setup: [http://www.andrewcraigmackenzie.com/Blog/2010/01/home-made-pvrdvr-part1/](http://www.andrewcraigmackenzie.com/Blog/2010/01/home-made-pvrdvr-part1/)

---

### Post by novellahub on 2010-01-25
> **Macka01 said:**
> I received the TV tuner card on Friday and finally purchased a molex-sata power adapter. I previously couldn't install Mythbuntu as my DVD drive had no power and I was getting black screening with the USB loader (tried several different recommended fixes, none worked)

MSY sold out of HDMI cables earlier today, so I missed out again, however I successfully installed Mythbuntu and started setting up MythTV. I even managed to get the TV tuner working, though only one of it 2 tuners (I need an aerial splitter or I'll solder an internal bridge on the card).

EPG is out though, approximately the time is approximately +10:30 from what it should be. I think it may be due to my mobo not using local time and Ubuntu is adding on a further 10:30. I haven't been able to find a solution so far, do you know how to fix this (without changing the BIOS time)? - if not, I'll reinstall.

I have also started documenting my setup: [http://www.andrewcraigmackenzie.com/Blog/2010/01/home-made-pvrdvr-part1/](http://www.andrewcraigmackenzie.com/Blog/2010/01/home-made-pvrdvr-part1/)

In your BIOS, set your time to GST time.  I do this with all of my machines.  Then have Ubuntu manage the time zone to your appropriate one.

---

### Post by Macka01 on 2010-01-26
> **novellahub said:**
> In your BIOS, set your time to GST time.  I do this with all of my machines.  Then have Ubuntu manage the time zone to your appropriate one.

Thanks, all fixed.

Now I just need to work out how to keep the program guide from crashing the front end (it won't display, when watching live TV) and how to get the DVD functionality working.

---

