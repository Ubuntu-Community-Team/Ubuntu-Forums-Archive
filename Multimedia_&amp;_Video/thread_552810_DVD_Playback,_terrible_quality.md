---
title: "DVD Playback, terrible quality"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by emar82 on 2007-09-17
I was hoping someone could help me with this problem.

No matter what I try using to play a DVD movie, the application either crashes or the video output looks choppy and the color is messed up. Here is a screenshot->  [http://209.129.8.8/~erick/vlc.png](http://209.129.8.8/~erick/vlc.png)

I have libdvdcss2 installed, my nvidia drivers installed and I have tried using Ogle, Kaffeine, VLC and Totem. All players either produce that output or crash. Here is some terminal information when running VLC.

erick@progek:~$ vlc
VLC media player 0.8.6 Janus
[00000298] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found


I am assuming that last line might have something to do with it and I've googled it but could not find a solution. I also have my DMA enabled. Here is that output.

erick@progek:~$ sudo hdparm /dev/hda

/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


Again, that last line has me worried.

Lastly, I am running Ubuntu Feisty Fawn with all the latest updates. My machine is an HP Pavilion dv6000, X2 Turion with Nvidia (drivers installed). Any ideas as to what could cause this playback?

---

### Post by emar82 on 2007-09-17
Bump

---

### Post by stoodleysnow on 2007-09-17
You could try reinstalling the dvd codecs.
Add/Remove Apps, select 'All available apps' and search for dvd.
hopefully this should at least improve it a bit.:)

---

### Post by emar82 on 2007-09-18
Thanks but that didn't seem to work. VLC just looks terrible and now totem plays it up until the part where the movies begin but then complains about libdvdcss not being installed but it is.

---

### Post by emar82 on 2007-09-18
I downloaded an old version of libdvdcss and I noticed that I was able to see the DVD menus this time. I then downgraded with  sudo /usr/share/doc/libdvdread3/install-css.sh and VLC plays it fine. Totem however wont, nor will Kaffeine but I can at least watch DVDs now. Interesting enough, my girlfriends Desktop which has my exact setup plays DVDs fine without downgrading and I tried to downgrade last night with no success so I'm not exactly sure what did the trick.

I can confirm though that my update manager wants to update libdvdcss2, if I install that update my DVD playback will be broken again

---

