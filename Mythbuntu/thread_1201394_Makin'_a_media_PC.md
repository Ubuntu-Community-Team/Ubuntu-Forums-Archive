---
title: "Makin' a media PC"
date: 2009-07-01
forum: Mythbuntu
---

### Post by Cowzor on 2009-07-01
I posted this over at [http://ubuntuforums.org/showthread.php?t=1200949]("http://ubuntuforums.org/showthread.php?t=1200949") but didn't realise at the time this forum was here as well, Appolagies.

So I picked up a good pc today, only the power supply is busted.

I was thinking of uses for it and thought it would be pretty neat to turn it into a media center, and I was thinking Mythbuntu would be the way to go.

So I've got a few questions I was hoping some people around here had some experience with and could answer for me.

First of all, I want to be able to play HD content on there, so an onboard graphics chip just isn't going to cut it. Are there any reccomendations on low end pci express video cards capable of playing HD content (I'm assuming HD is properly supported, ofcourse)?

Second, what's the media remote support like on Mythbuntu?

Many thanks in advance for your help.

---

### Post by ahood on 2009-07-01
> **Cowzor said:**
> I posted this over at [http://ubuntuforums.org/showthread.php?t=1200949]("http://ubuntuforums.org/showthread.php?t=1200949") but didn't realise at the time this forum was here as well, Appolagies.

So I picked up a good pc today, only the power supply is busted.

I was thinking of uses for it and thought it would be pretty neat to turn it into a media center, and I was thinking Mythbuntu would be the way to go.

So I've got a few questions I was hoping some people around here had some experience with and could answer for me.

First of all, I want to be able to play HD content on there, so an onboard graphics chip just isn't going to cut it. Are there any reccomendations on low end pci express video cards capable of playing HD content (I'm assuming HD is properly supported, ofcourse)?

Second, what's the media remote support like on Mythbuntu?

Many thanks in advance for your help.

A decent CPU is recommended for HD content, see [[COLOR="Blue"]**Mythbuntu Requirements**[/COLOR]](http://www.mythbuntu.org/requirements)

---

### Post by Cowzor on 2009-07-01
It has a (according to the label on the CPU box) Celeron 440 @ 2 GHz. I do remember seeing something about it being a dualcore somewhere during POST or in the BIOS before the power supply died but I'm not too sure now that I'm reading that the 440 doesn't have a dual core model.

I understood, though, that the video card takes a big chunck off the cpu for HD processing and I assumed this CPU and a recent yet low-end video card would do the trick. Is that a wrong assumption?

---

### Post by utar on 2009-07-01
> **Cowzor said:**
> It has a (according to the label on the CPU box) Celeron 440 @ 2 GHz. I do remember seeing something about it being a dualcore somewhere during POST or in the BIOS before the power supply died but I'm not too sure now that I'm reading that the 440 doesn't have a dual core model.

I understood, though, that the video card takes a big chunck off the cpu for HD processing and I assumed this CPU and a recent yet low-end video card would do the trick. Is that a wrong assumption?

Nvidia cards support accelerated video decoding of all types of codec, but no other cards do this under Linux.  Some other cards do support accelerated mpeg2 decoding, however in practice this doesn't matter since most CPUs can easily decoding mpeg2 in real time.  I personally use a fanless Nvidia card (I think it's a 8500 but can't quite remember) which works well.



Utar

---

### Post by Monsieur Gonzalez on 2009-07-01
Onboard graphics might be good enough, you should check your hardware against the list you'll find [here]("http://www.mythtv.org/wiki/VDPAU#Supported_Cards"), and learn about [VDPAU]("http://www.mythtv.org/wiki/VDPAU#General"). I'm running my media center on a single core Celeron, and it just works great as long as VDPAU is used for HD content.

---

### Post by LowSky on 2009-07-01
VDPAU only works on newer equiptment, I just looked at the specs...

Buy a cheap video card, preferably Nvidia, a cheap decent one is under $50USD (model 9400) I reccomend you spend some decent cash and get a fanless model to save on noise.

you will neeed at least 2Ghz single core processor for HD video, My HTPC is has 2.2GHz and with only onboard graphics it was stuttering and locking up.. A good video card will take the load off the processor and it will run smoothly.

as for remotes, you can buy a Windows MC remote and it will work, mine does.

if you buy a tv tuner card, make sure it does onboard encoding/decoding otherwise the processor will have to do the work,

---

### Post by Cowzor on 2009-07-03
Thanks for all the great replies guys, this was exactly what I was looking for and I'll be going with a 9400 something.

Now all I need to do is figure out how to connect a new power supply (I'm sure getting a replacement for the old one with its 240 watts wouldn't have been enough to power an additional hard drive and video card) to the non standard power socket on the motherboard...

---

### Post by ian dobson on 2009-07-04
Hi,

I'm running the VDPAU backports on my frontend. Hardware C2D underclocked to 1.2GHz and a Nvida 9400 graphic card. CPU load is about 10-15% when playing HD (1080i).

So a 2GHz Celeron shoud be enough. Maybe you can't do commflagging at the same time.

Regards
Ian Dobson

---

### Post by izizzle on 2009-07-04
And for software, there is always [XBMC]("http://xbmc.org/").

---

### Post by Cowzor on 2009-07-04
What would the difference be between installing Mythbuntu and regular Ubuntu and throwing XBMC on top of that?

---

### Post by crez79 on 2009-07-04
[Mythbuntu]("http://www.mythbuntu.org/") is Ubuntu with [mythtv]("http://www.mythtv.org/") integrated into it in a more standardized, preconfigured way. [XBMC]("http://xbmc.org/") can be made to work with myth, but is not a replacement if you want to record tv. You can install mythbuntu and add the ubuntu desktop to it or install ubuntu and add mythbuntu to it, or you can just install mythbuntu if you don't plan on using it for anything else but media. Additionally, you don't have to install mythbuntu, but instead you can install ubuntu and add mythtv to it. In my opinion, for beginers, it would be easiest to get to a working system if you went with mythbuntu instead of straight mythtv. Configuration is a lot more user friendly until you get the hang if linux, if you don't already understand the basics of linux. 

To make things even more complicated, mythtv can be added to many other distributions, not just ubuntu. As long as you stay with the same major version of mythtv, they are all compatible. For simplicity sake, it probably would be easier to stick with a single distro, but certainly isn't required.

XBMC can be configured to work with mythtv as a frontend, but you will still need a myth backend to do the actual recordings and such.

As far as hardware, to me, a VDPAU capable video card is a must. [Appling the backports]("http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html") is easy and was very straightforward for me. There are many options that aren't very pricey and is a good bang for the buck. Nvidia is absolutly required for me to even consider it. The couple non-nvidia cards I have tried didn't work well and was a battle just to get the to the point of working poorly instead of not at all. That was the last time I bought any hardware without a google search.

---

### Post by Cowzor on 2009-07-05
Thanks for the great reply, crez79.

Basically I want to use the same PC as both a front and back end, and besides movies and music I also want to run things like a snes emulator and maybe watch the occasional youtube movie on my tv. And I do have a reasonable knowledge of getting things done in Ubuntu, so I'm guessing, for me, it would probably be best to just install ubuntu and install MythTV onto that?

---

### Post by Cowzor on 2009-07-07
Well first I installed Ubuntu 9.04 and all was fine. I installed mythtv and found it pretty dissapointing, for my needs anyway. So then I installed XBMC and I am very happy with it. Thanks to all the great replies in this thread.

---

### Post by crez79 on 2009-07-07
I am glad you got it working. If you like XBMC, you may want to check out [boxee.]("http://www.boxee.tv/homepage/") It is based on xbmc and has some pretty awesome features.[URL="http://www.boxee.tv/homepage/"]
[/URL]

---

