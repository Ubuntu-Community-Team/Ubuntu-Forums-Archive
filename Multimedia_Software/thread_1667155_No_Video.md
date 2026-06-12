---
title: "No Video"
date: 2011-01-14
forum: Multimedia Software
---

### Post by PostWax on 2011-01-14
Hi All:

I have seen a lot of post about this problem but I have not be able to solve my issue

No video just sound in mplayer, miro and VLC.  If I change VLC to X11 then it will play videos. I do enjoy miro and mplayer and would like to keep on using them.  My install is fresh as of three days ago.  I was running 10.04 previous for months with no issues with above.  Best I can figure I have a problem with my codex.  Not sure how to correct.  Please help.

Let me know what info you need from me and how to get.  I am still fairly new at linux even though I have been using it off and on for a few years.

Yes I am running 64 bit.

I am willing to upgrade to 10.10 if that will help.:P

Ron

---

### Post by PostWax on 2011-01-15
Bump

---

### Post by BicyclerBoy on 2011-01-15
You changed the playback method from what to X11 ?  XvMC?

My guess is that you have no 2d or 3d video drivers & no video h/w support.

What video hardware?
What driver is load for this ?

VLC comes fully loaded except for libdvdcss & better versions of shared ffmpeg libraries.

---

### Post by PostWax on 2011-01-15
Sorry not sure what VLC was originally set up as but I changed it to X11 video output

My hard ware is Nvidia 9500GT and the drive was set to Version 173.  I am gong to change it the recommended drive and re=start.

Be back soon.

Ron

---

### Post by PostWax on 2011-01-15
Sorry same results with the recommended driver.  

What else can I try?

I used to be able to play video in Mplayer and Miro with no problems.  Now I did have to re-install 10.04 due to a bad hard drive.

Thanks any help

Ron

---

### Post by PostWax on 2011-01-15
Recommended Drive did not help.  Any other ideas?

FYI Mplayer Miro used to work just fine.  I had to re-install everything when my hard drive died.

Thanks for you help.  Any more ideas that I can try?  My best guess is something in my system is corrupt but I do not know where to begin looking.

Thanks 

Ron

---

### Post by PostWax on 2011-01-15
Every thing seems to working now.  All I did was reload w64codecs with synaptic and reset Mplayer back to default.  Even Miro now works.  Not sure what was the cure.  Thanks for you help.

Ron

---

### Post by BicyclerBoy on 2011-01-15
Your h/w will support vdpau decode playback of mpeg-2 & mpeg-4/h264.

This needs to be supported in the media player tho'.

AFAIK That requires building VLC.

Getting recent mplayer from 3rd party ppa has this support.

---

