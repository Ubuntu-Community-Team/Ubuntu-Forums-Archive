---
title: "Problem with video players"
date: 2015-02-14
forum: Multimedia Software
---

### Post by pe ter pa n on 2015-02-14
with SMplayer the videos are played in slow motion (the sound is ok and not in slow motion). I have installed it after not be able to use VLC, because the image was always stopping and with so much "green squares" that it was impossible to watch it. With video player also the same issue with the slow motion, when the video works.
   
Ubuntu 14.04 LTS
Memory 2,0 GiB

 Processor Intel® Atom™ CPU N270 @ 1.60GHz × 2

 Graphics Intel® 945GME x86/MMX/SSE2

 OS type 32-bit

 Disk 76,5 GB

---

### Post by QIII on 2015-02-14
Hello!

Do you mean slow motion or low frames per second?

---

### Post by pe ter pa n on 2015-02-14
hi!
I mean slow motion.

---

### Post by ajgreeny on 2015-02-14
Just out of interest, are these videos in HD, which may be too high a bitrate for your system to be able to play?

---

### Post by pe ter pa n on 2015-02-14
the films I've tried to seen are both in mp4 format. I have checked now and the most part of the movies I have seen are in .avi format, But also in mp4

---

### Post by pe ter pa n on 2015-02-14
Graphics:  Card: Intel Mobile 945GSE Express Integrated Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:27ae 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1024x600@60.0hz 
           GLX Renderer: Mesa DRI Intel 945GME x86/MMX/SSE2 GLX Version: 1.4 Mesa 10.1.3 Direct Rendering: Yes


with inxi -Gxx command it appears the intel driver is unloaded. Can this be a problem?

---

### Post by SeijiSensei on 2015-02-14
That Intel graphics card coupled with an Atom processor doesn't have enough "horsepower" to display high-definition video at full speed.  

You could try some alternative video drivers in SMPlayer.  Go to Options > Preferences > General, then click the Video tab at the top.  SMPlayer is probably using the default "xv" driver.  Try the Intel versions or OpenGL and see if things improve.  I'm doubtful that they will though.

---

### Post by pe ter pa n on 2015-02-14
thanks for the help. I've tried to select other default drivers, but with no success. thanks anyway

---

### Post by pe ter pa n on 2015-02-14
As "solution" I converted the file from mp4 to mkv and I can watch it in SMPlayer. Not high quality, but it works.

---

### Post by SeijiSensei on 2015-02-14
You must have done something else to the file along the way, too.  Matroska (MKV) and MP4 are "container" formats.  Simply moving the video stream from the MP4 container to the MKV container shouldn't have changed the video's characteristics at all.  My guess is that you re-encoded the video portion with a less CPU-demanding codec like MPEG4 or XviD before storing it in the Matroska container file.  That's probably why you see a loss of quality, too. I bet the original was in H.264, which is much more compressed.  Since the Intel 9xx series of on-board video adapters has no dedicated circuitry for decompressing H.264, it passes the task on to the CPU.  Atom processors are fine for many tasks, but pretty underpowered for video decompression.

---

### Post by Rob Sayer on 2015-02-16
Yup, you must have reencoded it to something with lower bitrate and/or resolution.  Probably a lower quality preset.  As mentioned the filename extension doesn't mean a thing.

Smplayer is faster than vlc but if it's not fast enough for your hardware try gnome-mplayer, which is a lighter mplayer GUI with less features but more speed.

Or just use mplayer in CLI mode, which is a bit further than I'd actually go myself.  I learned in pre windowing days but I've been avoiding CLI as much as I can for years too.

The main thing I'm really wondering, though, is which DE version of ubuntu the OP has installed.  If it's Unity I suspect a problem with 3D hardware acceleration support in linux.  Try a lighter DE version like Lubuntu or Xubuntu.

---

