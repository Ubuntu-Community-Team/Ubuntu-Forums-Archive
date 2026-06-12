---
title: "Dell Mini 10v Mythtv Volume too Low"
date: 2009-09-13
forum: Multimedia Software
---

### Post by FishFoot on 2009-09-13
Hey Guys,

I have a dell 10v that I've installed Ubuntu Netbook Remix 9.04 on.  I also installed mythfrontend to connect to my backend server from my laptop.

After I first installed it I had some trouble with the volume level from Mythfrontend.  Actually I was having trouble with volume all around.  I checked alsamixer and made sure my volume levels were all good but still, things were REALLY quiet.

The soundcard is a ALC272

I finally found a thread which discussed installing a package from the proposed updates which had a patch to make the mic work.  I couldn't find the exact package in the list so I just updated everything.

After a reboot things were a lot better.  I had to reset the volume levels via alsamixer but once I did that and played a youtube video everything was perfect.  The sound was LOUD now.

So I loaded up mythfrontend again and sure enough, volume is still quiet.

I'd be happy to provide any config file output... I'm at a loss as to exactly what to do.  The system is using pulesaudio and when I bring up the volume control for pulseserver there is some interesting info.  If I play the youtube video and I look at the stream in the volume control it looks normal.  The audio display shows at about half the volume.  When I run myth however, the bar is only filled to 1/8th.  This leads me to believe the sound is coming "out" of mythtv quiet and piping into the pulseaudio server quietly.

Help... please.

Fishfoot

---

### Post by FishFoot on 2009-09-14
Bump

---

### Post by ultimatebuster on 2009-09-19
Don't know if this will help you or not, but I think it will :) [http://thekks.net/570](http://thekks.net/570)

---

### Post by FishFoot on 2009-09-19
Thank you for the suggestion.  I had done that already to no avail.  I'm really looking for a way to raise the volume that Mythtv is pumping into the pulseaudio server.

---

