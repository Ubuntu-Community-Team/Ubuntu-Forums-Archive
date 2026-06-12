---
title: "Need help burning video dvds"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by SeattleUser on 2007-06-24
I'm running Edgy.  I used Kino to capture video from the Firewire port and the used DeVeDe to create an iso image from the raw DV file.  I then inserted a blank dvd and when asked told it to burn a dvd.  I selected the iso file that I created and it proceeded to burn the dvd.  When I play the dvd on my PC everything is fine.  When I play it on a standalone dvd reader the video has pixelization when the camera moved and the sound is out of sync with the video.  What did I do wrong?  Is there a more reliable way to do this.  I want to edit some family videos and burn several copies.

Thanks

---

### Post by Ardrias on 2007-06-25
Personally, for me, the nautilus burning rarely works, and especially not for dvd-videos. Instead I do this:

Turn off the automatic mounting of drives and removables.
Open a terminal and type following:
growisofs -Z /dev/dvd=/path/to/image/file/here.iso -dvd-video

The above hasnt failed me so far, but again I guess results may be different for you.

---

### Post by leibowitz on 2007-06-25
Your problem is related to codecs. You can read the DVD from your computer because you have all codecs installed. The dvd reader can only read DVD-format files.
 
> **SeattleUser said:**
> used DeVeDe to create an iso image from the raw DV file

I suppose you need to convert the files to mpeg. Kino can probably do the job. I can't test right now, but if you need an alternative I know you can use avidemux2. It has a pre-format for DVD output.

---

