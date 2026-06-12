---
title: "Recommendations on digital tuner card"
date: 2008-10-10
forum: Mythbuntu
---

### Post by bglaze1 on 2008-10-10
I had previously settled on all the hardware I was going to use for my MythTV system, but have since had some budget constraints, and am forced to rethink my system.  For one, I am no longer getting a new computer, and I am forced to use an old existing computer, and try to upgrade it to work with Myth.  I just need to settle on a tuner card.  I had recommendations to use the KWorld 115 and the HDHomeRun.  I was all for tinkering and trying to get things working, but with my new budget, I don't want to risk not being able to figure it out, so I would prefer to get something that works out of the box.

I am currently getting my TV from an antenna in my attic.  In the future, when the money isn't so tight and I buy that big HDTV, I will upgrade to cable or satellite.  But for now, I just want a card that can handle over the air ATSC.  If it can handle analog signals that is a bonus.  But I want to be able to get something that will continue to work for me after the U.S. digital swichover in Feb.  

So in reading some similar posts here, one user with somewhat similar requirements for his tuner card was told to get a pcHDTV 5500.  In some further reading, one place made that seem like it was supported right out of the box, and another place made me not so sure that it was supported.  Anyone have info on this card and its performance?

Another card that was really popular and widely supported is the Hauppauge PVR-150.  Is there a digital equivalent that is equally well supprted in MythTV?  

I read the MythTV wiki and it seemed like there were some digital equivalents to the PVR-150, but that none of them were really fully supported in Myth.  Is that true? Or is that wiki slightly out of date? When I was looking to get the KWorld 115, it was being replaced with the KWorld 120, but there is no mention of that card on the MythTV wiki, so that made me think that maybe the wiki is a little out of date (unless the 120 is just so new that it is not supported at all and thus not listed).

Anyways, if anyone has any other recommendations, I would love to hear them.  Thanks in advance for all of your help.

---

### Post by ian dobson on 2008-10-11
Hi,

[www.linuxtv.org](www.linuxtv.org) is a good place to look for what cards are supported in linux.

Regards
Ian Dobson

---

### Post by newlinux on 2008-10-11
The kworld 120 only has experimental support and isn't ready for prime time. the kworld 115 will do what you want, you will have to load a firmware (once) and load a module in /etc/modules (once) and then it works. the procedure has been detailed on this forum many times and takes less than 5 minutes - then the card works like any other digital/analog hybrid card in myth.

The pchdtv 5500 is supported and pretty much has the same capabilities as the kworld 115. It's overpriced in my opinion but should work out of the box. If you go to the web site listed above and go to ATSC devices you'll see a long list.

---

### Post by bglaze1 on 2008-10-11
So I was looking through the list on linuxtv.org at the supported ATSC PCI cards.  There is a column for supported in the kernel, does that mean that it is recognized and works right away?  
For example, the KWorld 115 says it is in 2.6.24, does that mean that I wouldn't have to do those patches to make it work?  I guess I don't know what that means.
Also, is being supported in the kernel the same thing as being supported by MythTV?
Thanks again.

---

### Post by newlinux on 2008-10-11
No, you will still have to load the firmware. It's not really a patch you have to apply, just copying a file into the firmware directory so the card has the firmware.  Saying it is supported in the kernel means it will work without modifications to the kernel in Linux. Myth will work with most cards that work in Linux, as far as I know.

---

### Post by bglaze1 on 2008-10-12
Since I was planning on getting a new computer before my budget tightened up, I didn't pay attention to this, but the KWorld 115 system requirements call for a P4 2.4GHz processor (recommended).  Do you know, will I be ok using my old computer that only is a P4 1.8 GHz?  If not, do you know another card that would work, if so, will I still be able to get decent resolution?  I don't have an HDTV yet, if that helps to define "decent."  Thanks again.

---

### Post by newlinux on 2008-10-12
You can use a kworld 115 witha P4 1.8, but you won't be able to very easily playback any HD broadcasts (this is true of any HD playback from any card with that processor). The problem isn't the tuner card with HD playback (all the cards capture the same input stream, they have nothing to do with what resolution you can playback at), it is the CPU requirements of playback. You might be able to get it to work using XvMC.

The CPU requirements of HD playback are pretty much the same whether you are using an HD display or not - your processor still has to be able to decode HD stream.

---

### Post by bglaze1 on 2008-10-19
Thanks again, newlinux.
When you say I can't handle playback of HD broadcasts, are you referring to just playing back anything that I capture digitally over the air?  Or specifically capturing HD channels, and playing them back in HD?  

Are channels (for example your local ABC, NBC, CBS, and FOX affiliates) typically broadcast digitally in both HD and SD?

Because if they are, then you could just select the appropriate channels to record at the resolution you prefer.  If this were the case, that would eliminate most of the processing that needs to occur, since capturing doesn't take much of a toll on the processor, and, if it were already converted to the appropriate resolution, I would just need to output the stream without any decoding to the TV.  And I would assume that my computer would be able to handle recording SD channels and playing them back in SD without much problem. Is that correct?

I just want to capture SD video and play it back to an old tube TV in SD.  I have a NVIDIA GeForce FX5200 AGP card with 256MB DDR and 2GB RAM in my system, would that graphics card and RAM help with the decoding at all?

Also, XvMC seems like it would be helpful.  Do you know is that just a simple configuration thing in MythTV, or is it a much more complex process than say a simple GUI configuration? It looks like there are a few drivers that I would need to get and install, but I don't know much more beyond that.

When you say, "the CPU requirements of HD playback are pretty much the same whether you are using an HD display or not," are you saying that there is just no way I can display SD video streams from the KWorld 115 (or any other digital capture card) because it is too taxing on the CPU to decode those MPEG-2 streams to an SD resolution?

If so, that goes against what I was thinking above, does this just mean that if I want to get digital over the air SD video, I need to have a higher powered processor?

---

### Post by newlinux on 2008-10-19
> **bglaze1 said:**
> Thanks again, newlinux.
When you say I can't handle playback of HD broadcasts, are you referring to just playing back anything that I capture digitally over the air?  Or specifically capturing HD channels, and playing them back in HD?  

I am talking specifically HD channels, you should be able to playback digital SD channels no problem 

> 
Are channels (for example your local ABC, NBC, CBS, and FOX affiliates) typically broadcast digitally in both HD and SD?

Where I live the local networks OTA broadcasts are HD, and most of their subchannels are in SD.
> 
Because if they are, then you could just select the appropriate channels to record at the resolution you prefer.  If this were the case, that would eliminate most of the processing that needs to occur, since capturing doesn't take much of a toll on the processor, and, if it were already converted to the appropriate resolution, I would just need to output the stream without any decoding to the TV.  And I would assume that my computer would be able to handle recording SD channels and playing them back in SD without much problem. Is that correct?


Well you could capture and decode the SD versions of the channels just fine, assuming they exist. They would require decoding (all playback of TV captures will require decoding) just SD is much easier to decode than HD.
> 
I just want to capture SD video and play it back to an old tube TV in SD.  I have a NVIDIA GeForce FX5200 AGP card with 256MB DDR and 2GB RAM in my system, would that graphics card and RAM help with the decoding at all?

 In Linux, most of the decoding is done by the CPU (limitation of the video card drivers in Linux). That card is plenty sufficient. not much RAM or Video RAM is needed for decoding TV signals. Gaming needs them more.
> 
Also, XvMC seems like it would be helpful.  Do you know is that just a simple configuration thing in MythTV, or is it a much more complex process than say a simple GUI configuration? It looks like there are a few drivers that I would need to get and install, but I don't know much more beyond that.

[http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC) should help. I haven't used XvMC in a couple of years so I don't know how much has changed...

> 
When you say, "the CPU requirements of HD playback are pretty much the same whether you are using an HD display or not," are you saying that there is just no way I can display SD video streams from the KWorld 115 (or any other digital capture card) because it is too taxing on the CPU to decode those MPEG-2 streams to an SD resolution?


Yes, there is no way you would be able to playback HD mpeg-2 streams if your CPU isn't powerful enough without offloading more of the processing to your video card. In linux, currently the only way to do this is XvMC, but I don't know if that will be enough. I think a P4 1.8Ghz is too little. The resolution that you play something back at is only part of the equation. Before you can scale playback to your monitor resolution the signal must be decoded. HD signals require much more decoding than SD signals - and this is true whether or not you are displaying them in an SD or HD signal.
> 
If so, that goes against what I was thinking above, does this just mean that if I want to get digital over the air SD video, I need to have a higher powered processor?

If the channels you want to play back are captured in HD, then yes I think you need a more powerful CPU, unless it works fine with XvMC.

---

### Post by bglaze1 on 2008-10-20
newlinux, thanks again.
I went to antennaweb.org and tried to see if my local channels are in HD or just digital SD.  Not much luck there, it seemed the channels just said the regular station named followed by a "-DT."  I would assume that they are in HD, but then I would have expexted the ending to say it was "-HD" instead of "-DT." Any idea how I could verify that the local stations are transmitting an SD channel?

If I can find that out somehow, then I will know that I can proceed with this older computer and that it will be able to handle the SD capture and display (well, I guess I know that it can handle the SD video already, the question is just whether or not there are SD streams in my area).

So am I safe to assume that the high CPU requirement on those video capture cards is only required if you want HD playback, and if I am just capturing SD, then my minimum requirements would be much lower, since I won't need as much CPU power, and I wouldn't have a problem using my P4 1.8GHz system?

Thanks again.

---

### Post by newlinux on 2008-10-20
Most times they will say DT even if they are HD. I know in my area they don't transmit the major local in SD and HD digitally OTA, only HD, so I'd put money on it that your major locals (Fox, CW, NBC, ABC, CBS) are in HD only OTA. There's no reason for them to simulcast an SD version since TV's and digital converters that aren't HD have hardware to easily decode HD signals. You can try:

[http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels)

and see if they have info on your area. This site will tell you the resolution of OTA and unencrypted QAM channels in your area.

I would pretty much ignore the card specs - they are usually written for windows anyway, and things are different in Linux. A P4 1.8 should be plenty for any mpeg-2 SD decoding. A PIII 700Mhz can decode SD. HD is an order of magnitude more CPU intensive (but still not much for today's processors - my old P4 2.6 could decode HD when I didn't have much else running without XvMC - and a P4 2.6 is slow by today's standards). 

Also, for antenna strength ratings, I found tvfool.com to be more accurate in my area than antennaweb.

---

### Post by bglaze1 on 2008-10-23
So, I am not sure if this will look OK when it posts, but I couldn't figure out how to get it to line up.  I went to the site you recommended (silicondust) for the channel listings, and I grabbed a few of the listings in my area.  So here are a few of them:

Type Channel Program Call Sign     Resolution Aspect 
8vsb 28      3       Station A DT  640x480i   4:3 
8vsb 28      4       Station A DT  1280x720p  16:9 
8vsb 34      1       Station B DT  1920x1080i 16:9 
8vsb 38      3       Station C DT  1920x1080i 16:9
8vsb 38      4       Station C DT3 544x480i   16:9
8vsb 44      3       Station D DT3 704x480i   4:3

Does this mean that I would be able to receive and display Station A on Ch 28 Program 3 no problem, but I wouldn't be able to handle Station B on Ch 34 Program 1 because it is only in HD? 

Also, would I be able to receive the different resolutions like 704x480i?  I assume anything 480 should be no problem.  What about Station A on Ch 28 Program 4 with a resolution of 1280x720p?  Could I recieve that? Or would that really be taxing out my processor?

Just by chance has anyone seen any good deals on tuner cards lately?  The best I have seen the KWorld 115 was for $63.  And the HDHomerun was $160.

---

### Post by newlinux on 2008-10-23
Yep, your processor should have no problems decoding 28.3, 44.3 or 38.4. Again, you may be able to decode the other ones with XvMC, but it is highly doubtful without it (they are all HD resolutions). I'd give XvMC a try. I know others close that CPU power that have gotten HD to work with XvMC. I think after enabling the nvidia restricted driver all you have to:

```

gksudo gedit /etc/X11/XvMCConfig

```
put:

```

libXvMCNVIDIA_dynamic.so.1

```
in that file, and then choose a playback profile in mythfrontend that uses XvMC. When you get there we can help you get it setup.

I haven't bought a tuner card in a couple years, so I can't help you much there, but finding one cheaper than the kworld will probably be difficult. Of course the HDHomerun is a dual tuner so really it is like buying two tuners and doesn't take up a slot in your computer.

---

