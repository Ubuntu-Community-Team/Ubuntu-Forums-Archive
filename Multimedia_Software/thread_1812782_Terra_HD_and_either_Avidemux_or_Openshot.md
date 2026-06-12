---
title: "Terra HD and either Avidemux or Openshot"
date: 2011-07-26
forum: Multimedia Software
---

### Post by DavidVS on 2011-07-26
I eventually [did]("http://ubuntuforums.org/showthread.php?t=1784990") [buy]("http://ubuntuforums.org/showthread.php?t=1790416") a Terra HD from Zareason that I love, but I cannot get it to do my video editing of Flip Mino home videos.  I know the machine is capable.  It plays bigger AVI files without any problem.  For sound it uses the Realtek chipset.

Samples of the .avi Flip Mino videos are [*here*]("http://blip.tv/davidvs/rss").  A nice short one for experimenting with is 2.3 MB, [*here*]("http://blip.tv/file/get/Davidvs-20101226AtPettingZooSheep136.avi").

According to Avidemux, the Flip Mino videos have the following video properties...
[INDENT]  Codec 4CC: XVID
  Image Size: 640 x 480
  Aspect Ratio: 1:1 (1:1)
  Frame Rate: 30.000 fps
[/INDENT]and the following audio properties...
[INDENT]  Codec: MSADPCM
  Channels: Mono
  Bitrate: 22179 Bps / 177 kbps
  Variable Bitrate: No
  Frequency: 44100 Hz
[/INDENT]
My goal is simply to trim the beginning and end to get the best segment in each home movie.

**Avidemux** worked great on my old machine as long as I changed the output audio format to MP3(LAME).  But Avidemux is not working and wants to know all sorts of things about devices of which I am ignorant.  The default settings must be wrong since the audio playback is choppy and usually the video saves to a one-frame broken file.

I also tried **Openshot** and it has no device preference issues.  However, I am ignorant of how to make it save the videos properly.  It wants to "export" the video using all sorts of options, none of which are simply "use the setting for the only track".  Based on the 640x480 size I tried some Square NTSC tests but the exported file was always much too big -- usually larger than the untrimmed original!

Also, Openshot appears to lack a keyboard shortcut or button for "move the beginning or end of the clip back or forwards one frame".  Is it really expecting me to use the mouse to position the clip's borders precisely?

I have no vested interest in which software is used.  Nor do I care about the resulting file format as long as it is neither wastefully large nor senselessly abandoning quality.  I just want to share my home movies with friends and family.

Thanks for any help!

---

### Post by gordintoronto on 2011-07-26
Generally, for a video editing program to produce its final output, the process is called "rendering." Perhaps you could find some tutorials on Youtube or Vimeo, on using Openshot.

My preference is Cinelerra, but you really need to spend a couple of hours on "Cinelerra for Grandma" and Youtube tutorials before you attempt to use it.

---

### Post by DavidVS on 2011-07-27
I'm not sure why Openshot uses the term "export" instead of "render".

I doubt those tutorials will tell me which file formats are closest to non-HD Flip video, with no loss of quality or only a slight loss of quality.

---

