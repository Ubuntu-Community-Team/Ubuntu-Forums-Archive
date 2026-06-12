---
title: "xawtv no video with PVR-250, help!!"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by mocha on 2007-06-16
I'm trying to get xawtv to work with a WinTV PVR-250.  I know the card is working because I can use mplayer to see the video, so the drivers are installed ok.

This is what I get when I try to run it.

```
mocha@mocha-c2d:~$ xawtv -nodga
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
xinerama 0: 1280x1024+0+0
xinerama 1: 1024x768+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

```

And then I just see a small black screen.  Please help!  Thanks.

---

### Post by wolfen69 on 2007-06-16
this is a response of mine from another thread:

btw, if you get a hauppauge card(pvr150,250,350,and 500 will do fine) a quick way to get tv going is download vlc player, then get ivtv drivers from synaptic. open vlc/ file/open capture device/ OK. to change channels,open terminal: ivtv-tune -c25 (25 is channel number)

there are other ways to get tv going, but this method works, so i go with it.

---

### Post by mocha on 2007-06-17
I understand you, but how do you use VLC to take advantage of the MPEG2 encoder on the PVR cards?  I want to use an all in one package if possible.  Something like MythTV but not as bulky.  Is it possible?

---

