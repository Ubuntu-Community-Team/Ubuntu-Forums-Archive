---
title: "[SOLVED] ffmpeg is BROKEN!!!! or is it?"
date: 2008-09-19
forum: Multimedia Software
---

### Post by Cresho on 2008-09-19
Hello all, I just want to know why after I reinstalled my ubuntu (reinstalled because i was bored) my ffmpeg is broken!

Here is the story.  I use ffmpeg and winff (this one is the gui..sort of) to convert mp4 high definition home xacti hd1000 videos so avidemux can cut and paste scene edit.  I need to go from winff to avidemux because avidemux will not properly build vbr timemap without the step and cause audio sync issues.

I just need verification if it is broken at the moment.


and yes the command lines do not work.  and yes I have all version of gstreamer from main repo installed.

winff with ffmpeg and wine work just fine though I WANT NATIVE!

ohh and if you want outputs (even though i just need to know if its broken) ill post my outputs.

---

### Post by kostkon on 2008-09-19
> **Cresho said:**
> Hello all, I just want to know why after I reinstalled my ubuntu (reinstalled because i was bored) my ffmpeg is broken!

Here is the story.  I use ffmpeg and winff (this one is the gui..sort of) to convert mp4 high definition home xacti hd1000 videos so avidemux can cut and paste scene edit.  I need to go from winff to avidemux because avidemux will not properly build vbr timemap without the step and cause audio sync issues.

I just need verification if it is broken at the moment.


and yes the command lines do not work.  and yes I have all version of gstreamer from main repo installed.

winff with ffmpeg and wine work just fine though I WANT NATIVE!

ohh and if you want outputs (even though i just need to know if its broken) ill post my outputs.
Then please post the error messages that you get.

I don't think it's broken.

And it is better to install the version of *FFmpeg* that is offered by the [*Medibuntu* repository]("http://medibuntu.org/") that has the support for restricted formats enabled.

[Add this repository to your software sources list]("https://help.ubuntu.com/community/Medibuntu") and then install *FFmpeg*. Either this or you'll get an update notification (I think) if you have already installed the version that is offered by the *Ubuntu* repos.

---

### Post by Cresho on 2008-09-20
I updated this info.  I tried this on a skeleton system and it works.

Thanks a bunch.

Now I can edit my home videos with winff

---

### Post by Cresho on 2008-09-20
okay!  IT's still broken.  In a fresh install, doing what I did was fine and the method you posted was fine as well.  after installing lives and mplayer, it broke everything!

i tried uninstalling

sudo apt-get remove ffmpeg

or sudo aptitude purge ffmpeg

I tried verious other ways and then tried reinstalling ffmpeg and still I get unknown xvid error.  Rediculous!

---

### Post by Cresho on 2008-09-21
OKAY!  I FOUND OUT WHAT HAPPENED!  :popcorn:

appearantly from what I read, ffmpeg is going in between transitions and the commands have changed slightly.  THis is why I was getting xvid erors.

What I did was replaced a preset.xml which resides in your winff folder with a newer one.  Since I am not running a newer ffmpeg and am using an older one, I was getting the error.  COdec initiation through the command lines are changing.  NOthing wrong with ffmpeg....sort of.

---

