---
title: "Problems with playing and compressing avi files created by Matlab"
date: 2010-02-23
forum: Multimedia Software
---

### Post by UeB on 2010-02-23
Hallo,

I am using Ubuntu 9.10. With Matlab I created an uncompressed avi film using the functions avifile() getframe() addframe(). It is basically a series of plots of tracks in a particle detector.

I can play this avi file with Totem but the colours are not right they are to dark. VLC (1.0.2) only shows a black frame for the hole time of the video (but in the right size though...). And when opened with avidemux the colours are too bright (green becomes turquoise, blue becomes violet and so on) AND the film is played up side down (vertical flip) but this seems to be a known bug: [https://bugs.launchpad.net/avidemux/+bug/451656](https://bugs.launchpad.net/avidemux/+bug/451656)


Because my Boss who what's to see this video uses Windoes I looked up on the MS web page what code ships by default with every version of windows (media player). Of these avidemux supports mjpeg, so I used avidemux to compress the video with this codec.

The compressed avi file looks the same in Totem as the uncompressed (colours too dark) and the same in avidemux (colours to bright).
VLC also cannot play the the compressed, too. (well there is no error but all it shows is a black frame for over 2 min as with the uncompressed file)

Next I tried Windows media player 11 on windows vista on the same machine. There the uncompressed video workes AND has the right colours. But the (MJPEG) compressed files looks the same as in Totem (colours too dark). While VLC (1.0.5) on Vista shows only the first frame of the movie for the hole playing time.

Interestingly the Matlab example file for creating avi movies produces a wobbeling sin survace, that works in VLC.

Does anybody know what is happening here? And how I can get a compressed video file, has the right colours on both Linux and Windows?

By the way Totem calles the codec of the uncompressed video "palettized 24 RGB" and VLC is calling it RV24. While the compressed version is called mjpeg (Totem) and MJPG (VLC).

thanks in advance

---

### Post by UeB on 2010-02-24
To add some more confusion: my colleague using Windows XP can play the mjpeg compressed film with windows media player in the correct colours...

---

### Post by UeB on 2010-02-25
I played a bit around with the film parameters. Now I use a higer resoltion higher frame rate much more frames.

Totem still uses to dark colours
VLC on Linux now works but it looks the same wrong way as in Totem
Avidemux uses also wrong colours but different then Totem ( as described in my fist post)
The mjpeg compressed version looks the same in all of theses 3 player as the uncompressed version looks in them.

In windows vista:
WMP 11: uncompressed version plays with correct colours; compressed version looks the same as in Totem
VLC: uncompressed version plays with correct colours; compressed version looks the same as in Avidemux


I have still now idea what is going on here...

---

### Post by jetak on 2011-04-15
I am having the same problem. I created an .avi movie using Matlab 2010s videoWriter in Windows 7 Ultimate using the default settings except for the frame rate (fr = 2/s). The movie plays fine using InfranViews built in player and the HP crapware player shipped with the PC. Windows Media player works and actually does a pretty good job. VLC on Windows and Mac does not work. If you figure out a fix please post, and vice versa. 

Good Matlabbing.

---

### Post by UeB on 2011-05-08
> **jetak said:**
> If you figure out a fix please post, and vice versa. 


No I did not, sadly I just accepted the wrong colours.

Also I did not have to make another video since a year now.

---

