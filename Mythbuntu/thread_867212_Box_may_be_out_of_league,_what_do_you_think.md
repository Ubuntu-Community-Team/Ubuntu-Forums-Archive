---
title: "Box may be out of league, what do you think???"
date: 2008-07-22
forum: Mythbuntu
---

### Post by baphomet420 on 2008-07-22
Alright...
I have an old box, that I am wanting to make a half way functional mythbuntu box out of...

I do not have cable or satillitte service, so I do not need to have a tv turner and all that...

Its basically going to be my media center...  Just playing video and music files (would also like to be able to stream HULU.com content)...

My specs are crappy for this box...  Its an old (e-machine)... lol...
Its got 1gig celeron processor (this is going to be my downfall)
256mb or ram (have another stick on order for 512)  max allowed by chipset
ATI Radeon 9200 video card w/ 128mb ddr (PCI Slot)  (this is a brand new card, i tried to get nvidia, but they are pretty much non existent anymore for a std. PCI slot)

I already know that I will have to do the ATI non free drivers to get tv-out working...

The problem that I am having is this, I used this box for over a year with (freespire 1.0)..  It played video content great!!!  Full screen did not lag what so ever...  and that was with the integrated intel 810 graphics...

I have tried out dozens of distros on it since...  They all lag on video playback (only get maybe a frame every other second)...  This is with the intel embed graphics or the new radeon card..  CPU is running at 100% (must be the culprit)...

Is there a way around this???  I mean it worked great in the past..  Not now..  I do still get great video playback in puppy linux (the distro im trying to stay away from for this)..  everything else has been crappy...

is it possible that I wore the processor out after 7 years of use???  or is 1 gig just not going to be enough for what I want to do???  
they do have a pentium 3 avalible that is compatible with my chipset..  its the same specs except it was twice the cache...  im afraid i would end up with the same result from it though...

any ideas???  (beside getting a new board and processor, im broke yall) hehehehe....

also, if i get this working to my satifaction (im simple, doesn't take much to satisfy me) i think it would be cool as **** to have a nes and snes emulator in the menu...  

so that all I really want to do with the box...  play back video and mp3s (on local hard drive and soon to come off of wireless network (once i get it set up)), and play nes and snes emulators..  and also stream online content (i see that option already there :) )...

am i going to be able to pull this off with this box???

---

### Post by andrewc6l on 2008-07-22
I have no problem on an old 1GHz box doing FC4 + Myth 0.17 + patches. Later releases have more trouble (and in fact I am still working on getting Mythbuntu 8.04 running HD capably on a 3 GHz box). You might want to consider an older OS and MythTV release if you want acceptable performance on some of the higher CPU items.

1 GHz won't let you do HD, but it will serve SD admirably, and MP3 is easy. Not sure what the emulators need.

---

### Post by nickrout on 2008-07-23
That box will adequately:

[LIST=1]
[*]record encoded material, ie either hardware encoded by a pvr 150/250/350/500 or from a digital source like dvb-s|t or atsc, assuming standard definition
[*]play back standard definition video or recordings
[/LIST]

However you will run into trouble if:
[LIST=1]
[*]you are expecting it to play back HD material
[*]you try to transcode or commflag at the same time as anything else
[*]push it too hard
[/LIST]

I use an i810 chipset on my mythbox, but it is driven by a 2.4GHz celeron processor.

---

### Post by newlinux on 2008-07-23
I echo what the others have said.  I have used snes emulators on my 1.6Ghz Celeron M and it struggles a bit with most games I play (can't do them full screen at all), so I think you may have a problem with the snes emulator at least...

---

