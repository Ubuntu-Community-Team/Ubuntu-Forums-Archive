---
title: "Brasero cannot estimate Video file size correctly"
date: 2008-11-19
forum: Multimedia Software
---

### Post by SteveDee on 2008-11-19
I'm trying to burn video files to a DVD using Brasero.

I select "Video Project" then add a .mpeg file with a 1 hour playing time. As I understand it, this is supposed to create the required files & structure to allow the DVD to play on a tv.

However, the first time I do this Brasero estimates the play time as 9min 37sec. If I remove this file from the project, and then add it once again it estimates the play time as 9hrs 37min.

I've added all GStreamer plugins and even uninstalled/re-installed Brasero.

Can anyone advise?

---

### Post by billd42 on 2008-11-23
I wonder if your issue is related to this bug:  [http://bugzilla.gnome.org/show_bug.cgi?id=561580]("http://bugzilla.gnome.org/show_bug.cgi?id=561580") related to audio files.

---

### Post by zander1013 on 2008-11-23
> **SteveDee said:**
> I'm trying to burn video files to a DVD using Brasero.

I select "Video Project" then add a .mpeg file with a 1 hour playing time. As I understand it, this is supposed to create the required files & structure to allow the DVD to play on a tv.

However, the first time I do this Brasero estimates the play time as 9min 37sec. If I remove this file from the project, and then add it once again it estimates the play time as 9hrs 37min.

I've added all GStreamer plugins and even uninstalled/re-installed Brasero.

Can anyone advise?


i myself have not used Brasero yet, however, i have used GnomeBaker and have noticed that sometime the estimated time to finish is inaccurate.

if Brasero does not run the job to finish then try installing GnomeBaker and using that instead.

also, i have never tried to burn a dvd for playback on tv.

---

### Post by SteveDee on 2008-11-23
Thanks for the input guys.

Firstly, I didn't think GnomeBaker could take a range of video files (like mpeg) & create a "TV playable" DVD. But I'll give this a try if you think it supports this feature.

With Brasero I've found I can add a .vob file to a video project and it always seems to correctly estimate the playing time. I can also preview both the .vob and .mpeg files in Brasero. However, when I click the 1st "Burn" button it takes me to a 2nd screen (Disk Burning Setup) where both the "Burn" and "Properties" buttons are greyed out, so I cannot go any further.
It did occur to me that maybe it won't work with a DVD-RW, but on the setup screen it says "Status: the medium can be recorded". And even selecting "Image File" does not allow me to proceed.


As far as my mpeg files are concerned, there could be a wider problem. Before upgrading from 8.04 to 8.10 I could record video with Me-TV and playback happily with MPlayer. But since the upgrade I've had to switch to SMPlayer in order to see & hear the video in sync ([http://ubuntuforums.org/showthread.php?t=968196](http://ubuntuforums.org/showthread.php?t=968196)).
I guess video encoding is a bit of a mine field at the best of times. Anyway my point is, if there is some kind of codec problem for MPlayer, maybe Brasero is suffering too.

But I think the first step is to solve the greyed out "Burn" button problem...any ideas?

---

### Post by oaxacamatt1 on 2008-11-23
I agree with one of the writers from above I dislike Brasero and use Gnomebaker or even K3B.  Much better functionality.

Hope this helps,
Matt

---

### Post by SteveDee on 2008-11-26
Just to wrap this one up, I was unable to get Brasero to work so its now been deleted.
I'm now running DeVeDe to compile video from my mpeg files (god its slow! but it works), and then burn the iso using Nautilus.
Thanks to those that offered help.

---

