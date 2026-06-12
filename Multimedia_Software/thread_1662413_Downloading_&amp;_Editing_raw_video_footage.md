---
title: "Downloading &amp; Editing raw video footage"
date: 2011-01-08
forum: Multimedia Software
---

### Post by unueco on 2011-01-08
BACKGROUND:
  I frequent a website features live video streams. Afterwards, they also uploads the videos for playing online. When videos are played Flash files accumulate in /tmp which I save and edit.

RECENT PROBLEM:
1) When I play the videos online, they never "start". I just get that typical circling arrow that general indicates the file is downloading to a buffer before playing....but even after 5 minutes...it never starts. While this is happening, a file is accumulating in /tmp.

2) As a test, I tried editing the temp file that appears in /tmp using OpenShot. The file is very large (on the order of 800Mb). But in the editor, only a few seconds of video appear. The rest is a blank white screen. I examined the file in a hex editor and it all "looks" the same (I can't read the Hex of course...but nothing obvious appears...like lots of 00 bytes).

Curious if anyone has any ideas or suggestions.

---

### Post by BicyclerBoy on 2011-01-08
I would imagine that streamed webinar/webcast video is a transport stream container.

OpenShot may not be the best app for this..

VLC & mplayer are stream players that can handle broken/missing/damaged/incomplete files..

Do you have flash plugin installer installed ?
How old is your firefox ?

Recent flash video can be mpeg-4/10 H264AVC  this is CPU intensive if full screen HD.

Use mediainfo or ffprobe to determine the file container streams & encoding used.

---

### Post by unueco on 2011-01-08
Thank you for your comprehensive and helpful response.

> **BicyclerBoy said:**
> 
VLC & mplayer are stream players that can handle broken/missing/damaged/incomplete files..



I do have VLC installed. It is my default video player.

> **BicyclerBoy said:**
> 
Do you have flash plugin installer installed ?


Installed where? In VLC? Firefox?



> **BicyclerBoy said:**
> 
How old is your firefox ?


Firefox version 3.5.8  Ubuntu 9.10




> **BicyclerBoy said:**
> 
Use mediainfo or ffprobe to determine the file container streams & encoding used.

Thank you. I'll need to MAN those to understand more how the work.

Thanks again for the helpful information!

---

### Post by BicyclerBoy on 2011-01-08
Ubuntu firefox & flash is/was a bad combination in 9.10 if memory serves..

You could try changing your synaptic settings/repositories/ update settings to include proposed backports..
This might let you install later firefox & flash addon/plugin.

The flash plugin is in firefox. Check firefox menu:tools/add-ons/plugins.
The firefox flash plug-in can be installed via synaptic..BUT this only installs the adobe installer.

Try your video in VLC & then open the menu tools/media information.

What version is your VLC then ?

---

### Post by unueco on 2011-01-08
Looking a bit further into the situation, I notice that stream files I have previously downloaded (by saving out of the /tmp directory) that work properly are listed as FLASH video. However those which I downloaded by cannot successfully play or edit are listed as QUICKTIME video. 

Also, I did try playing the unsuccessful ones in VLC. Sure enough, they play for a few seconds up to a point...then fail. 

Finally....neither mediainfo nor ffprobe seem to be pre-installed in ubuntu and don't seem to be part of the canonical system (not in the software repository)...

---

### Post by BicyclerBoy on 2011-01-09
What version is the VLC ?
Have played some old quicktime (Utube type clips) in VLC on netbook but never come across any real video.. 

ffprobe is part of ffmpeg package

mediainfo is probably in medibuntu.
You should add medibuntu ubuntu-restricted-extras

Would suggest you add a 3rd party ppa to get a later VLC if possible..

---

### Post by unueco on 2011-01-09
> **BicyclerBoy said:**
> What version is the VLC ?

1.0.2

> **BicyclerBoy said:**
> Try your video in VLC & then open the menu tools/media information.

Please see attached screen capture.....

---

### Post by BicyclerBoy on 2011-01-09
That VLC version is old ..

The video codec appears to imply this video to be VC1.
I do not if this correct..

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
The comments about Repositories..
> Make sure you have an universe repository activated.   Search for vlc and install it. You should install vlc-plugin-pulse  and mozilla-plugin-vlc as well.
 If you are interested in streaming or transcoding, you should additionnally install libavcodec-extra-52 from a multiverse repository.



Maybe the libavcodec-extra-52 may fix this.

---

