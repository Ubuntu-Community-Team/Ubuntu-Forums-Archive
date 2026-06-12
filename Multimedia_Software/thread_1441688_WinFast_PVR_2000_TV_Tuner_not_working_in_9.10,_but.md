---
title: "WinFast PVR 2000 TV Tuner not working in 9.10, but is recognised"
date: 2010-03-29
forum: Multimedia Software
---

### Post by mastablasta on 2010-03-29
Ubuntu version: Karmic Koala (ubuntu 9.10)
 
I've been fiddling arround quite some time with this card. So far i established the following:
 
1. Card is supported by drivers already available in kernel (v4l, v4l(2)).
2. Card is recognised by Skype as well as by gstreamer. However gstreamer gives me mostly greeen screen when i test it. no propper picture. both found it on video1 (video0 is webcam).
3. I know it is supposed to work well in Linux ([http://www.linux.com/archive/forums/topic/336](http://www.linux.com/archive/forums/topic/336)) - instructions are for fedora here.
4. there are quite a few tutorial for this card online (even ubuntu), however they are for older version and most of them consist of getting new drivers installed (which are already included with Karmic).
 
So far i tried:
TV Time - blank screen - it is trying to get video from video0 device, which is webcam. i can not set it to use video1 instead as when i click in the menu to change input nothing happens.
 
VLC player - i select use device and set it to V4l or PVR. in both cases the programme itself switches to video0 and turns on my webcam. Nothing else happens. I also installed iv-tv including all necessary libraries and dependancies - as suggested as solution to similar model of card. Didn't change anyhting. 
 
MeTV - is only for DVB devices, so it doesn't work anyway, because this tuner is not DVB device...
 
MplayerTV - tries to get input form video0 despite setting it to video1
 
Can anyone help me with this? it's basically the only thing that is not working yet (most other things i already solved-sort of). I am also interested why the programmes keep switching automaticly to video0 for input when i clearly state to them to use video1?!

If this can not be solved can anyone suggest another cheap TV tunner that "just works" in Ubuntu (including remote control)?! I have a big monitor and i think i could use it as TV instead of getting a new TV....

---

### Post by mastablasta on 2010-04-20
3 weeks, not a single reply?!?!?!
 
I am bumping this and i would like to ask any moderator that in case they think i can get support for this elsewhere to please move the thread there.

---

### Post by Elfy on 2010-04-20
moved to multimedia

---

