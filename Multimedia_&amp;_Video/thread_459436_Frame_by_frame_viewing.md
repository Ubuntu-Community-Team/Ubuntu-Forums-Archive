---
title: "Frame by frame viewing"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by AvixK7 on 2007-05-30
I was wondering if anyone knew of a media player that allows you to scroll through a video one frame at a time. Kind of like Quicktime. Xine allows you to view videos at slow motion but not frame per frame. And VLC, while great at playing nearly every possible video format isn't great for frame by frame either.

---

### Post by QwUo173Hy on 2007-05-30
mplayer has this functionality. Press the . button to go into frame mode, and press the same button to step frame by frame.

---

### Post by AvixK7 on 2007-06-13
the problem is that Mplayer doesn't ever work properly unless it's being used in firefox. I ALWAYS get some kind of error when trying to use mplayer. 

> fatal error
Error opening/initializing the selected video_out (_vo) device

any idea why this happens? I installed mplayer through synaptic as usual...

Thanks the help so far :)

---

### Post by QwUo173Hy on 2007-06-14
I've had a similar error in the  past. I corrected it by running gmplayer (mplayer with a gui frontend).

Right click on the player window and choose 'preferences'. Go into the video tab and choose a different driver  . In my attachment, you can see that the 'xv' driver works for me. You need to restart mplayer (not Ubuntu) for the changes to take effect and you may need to try a few to get it right for your system.

---

### Post by AvixK7 on 2007-06-15
Thanks I'll give that a try.

Dan

---

### Post by jrchan on 2007-07-22
Thank you **jarlath** I have the same error (Error opening/initializing the selected video_out (-vo) device ) when trying to open AVI files in MPlayer (installed normaly with apt-get install mplayer). In my case changing video driver preferences in MPlayer to use X11- X11 (XImage/Shm) works fine for me.

JRChan

---

### Post by QwUo173Hy on 2007-07-23
You're very welcome jrchan. Glad you got it going ;)

---

### Post by rylleman on 2008-04-17
To get back to the original question which I think hasn't been answered yet, are there any media players that can do forward *and* backward frame stepping? (mplayer can only go forward...)

---

### Post by aeiah on 2008-04-17
whilst not actually a media player, avidemux will do this.

---

### Post by rylleman on 2008-04-17
Thank you.
It a bit awkward but now at least I have a tool to work with.

---

### Post by Adrastos on 2008-05-28
easyubuntu is a script that automates installation of some items. Use at your own risk. See [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) 
I installed it and it worked for my case.

---

