---
title: "Movie Player crashes with AVI files"
date: 2011-03-20
forum: Multimedia Software
---

### Post by skinks on 2011-03-20
With Ubuntu 10.10, the Movie Player crashes every time I try and play an AVI video file.  I did not have this problem with my last version of Ubuntu (9.04).  I don't know what to do.:sad:

---

### Post by skinks on 2011-03-20
I loaded Banshee, hoping that would work in playing my video (AVI) files.  As with Moveplayer, Banshee crashes immediately when I try and play an AVI file.  I tried to play both old and new AVI files and I get the same problem.

---

### Post by BicyclerBoy on 2011-03-20
When you say movie player do you mean the default ubuntu totem player ?

AFAIK this uses gstreamer.
You may need to add the good bad & ugly gstreamer plugins packages (multiverse) etc..

Try to launch this program from the command line (terminal) to then see the errors.

AVI is just a container (& not a very good one).. they can contain almost anything.

Run 
ffmpeg -i
or 
mediainfo
AVIDeMux
on your files to find out the contents..

---

### Post by skinks on 2011-03-22
Yes, the player is Totem Movie Player 2.32.0.  I checked all Gstreamer plugins fromUbuntu Software Center.  All were installed except one.  I installed, but still have the same problem.  Totem crashes as soon as video starts to play.  

I installed and ran ffmpeg.  When I checked an AVI file, videos were mjpeg files with audio being pcm_s16le.  Below is output from ffmpeg.    



Input #0, avi, from 'MVI_2134.AVI':
  Metadata:
    ISFT            : CanonMVI03
  Duration: 00:00:05.73, start: 0.000000, bitrate: 6540 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s

---

### Post by Mark Phelps on 2011-03-23
Try using MPlayer. After I started using that, I quit using the Totem play altogether.  I believe that MPlayer provides its own codecs.

---

### Post by no2498 on 2011-03-23
try installing smplayer
i know its the front end for totem but it works much better

---

### Post by skinks on 2011-03-23
I installed both Gnome MPlayer and SMPlayer.  They worked but in Preference for each I had to change the video output from xv to gl.  It didn't work with xv.  I don't know why.

Strangely for both programs the progress bar at the bottom of video worked for the first videos I played.  Thereafter the bar shows only 0:00 and there is no way to move around inside the video.  But, it is good to be viewing my videos again.  Thanks all for the help!

---

### Post by bogdarnet on 2011-03-24
Is mediainfo available from Synaptic?  I can't find it.

Ah, I see, I misread the sourceforge page... never mind.

---

