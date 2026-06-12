---
title: "New to Mythbuntu, help configuring motherboard CD-IN audio (ALSA)"
date: 2013-01-21
forum: Mythbuntu
---

### Post by T504 on 2013-01-21
I'm trying to configure a pc I have as a mythbuntu backend which will be used by another pc running XBMC to display live tv. For testing purposes only I am running a mythfrontend temporarily on the backend machine.

 I've got an older analog TV tuner card called Winfast tv2000 xp Expert. I can receive picture from it fine although I have to manually input the channels but I not getting any sound when I view  a channel with the frontend. Here is some information relevant to my problem.

> I can hear sound from youtube videos and whatnot from chromium. I think my audio out is fine.
> I am using mythtv-setup to configure the backend. 
> My tuner card is recognized by mythtv-setup as a V4l card
> My tuner card outputs sound through a small wire which must be connected to the CD-in plug on my motherboard.
> On windows I can get the sound from the CD-IN to work so that connection is good. 
> A couple of places in the mythtv wiki say that getting the sound from the CD-IN should be possible but none say how.
> My computer is a mostly stock dell dimension 4600 with a decent graphics card and no sound card.
> In linux I do not know if the motherboard CD-in has to be configured/needs a driver. I do not know how to check if it is even receiving sound. (I'm kindof a linux newb)
> I have tried entering a few things into the mythtv-setup>capture cards>v4l device>audio device field, to no avail. 

What I have tried so far:
> ALSA:dsnoop:CARD=ICH5,DEV=0 (also tried DEV=1,2,3,4,5)
> ALSA:default
> ALSA:capture:CARD=ICH5,DEV=0 (also tried DEV=1,2,3,4,5)

So basically, what do I need to put in that field to get my sound to come from the right place?

Thanks in advance,

T504

---

