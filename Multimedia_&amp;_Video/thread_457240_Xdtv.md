---
title: "Xdtv"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by Cresho on 2007-05-28
I am currently trying out television viewing and recording on my ubuntu system.  I have a bt878 tv tuner from avermedia.  I use a gametheater xp for sound card.  Everything works but one thing.

xdtv was installed using this repository.

deb [ftp://ftp.las.ic.unicamp.br/pub/debian-marillat](ftp://ftp.las.ic.unicamp.br/pub/debian-marillat) unstable main

help files are here. [http://sourceforge.net/project/showfiles.php?group_id=67268](http://sourceforge.net/project/showfiles.php?group_id=67268)

I launch the program from a terminal with "xdtv"  and has tons of short cuts and explenation are through the help files.   i installed lame as well for audio recording.  I can record video like with no problems at all but I have an audio issue.  I am running aux as my primary audio device to listen to audio and I know I need to use line in but don't feel like running a wire to the front port of the gametheater xp box.  How can I tell xawtv to use aux instead of line-in for use with audio and recording?

any suggestions?

---

### Post by ramadhian on 2007-07-07
Try add this one repository at  the end of file "/etc/apt/sources.list"

deb [http://nicolas.estre.free.fr/ubuntu](http://nicolas.estre.free.fr/ubuntu) edgy main

then do:

sudo apt-get install libxdtv-i18n-en xdtv libxdtv-theme-aqua-en libxdtv-theme-carbone-en xaw3dg xfig libzvbi0


Its work here on my Ubuntu 7.04

---

### Post by L_V on 2008-02-20
Did somebody succeed to install xdtv in Gutsy or Hardy ?

---

### Post by stoppage on 2008-02-21
I installed XdTV on Ubuntu "Feisty" using repository.........."deb [http://nicolas.estre.free.fr/ubuntu](http://nicolas.estre.free.fr/ubuntu) edgy main." The fullscreen display is distorted (stretched horizontally) and this despite trying many different resolutions. Can anybody decipher some of this from the terminal?....

tony@youhits:~$ xdtv 



This is xdtv 2.4.0 running on Linux/i686 (2.6.20-16-generic).

scandir: No such file or directory

filename = /home/tony/.xdtv/xdtvrc

X Error of failed request:  XF86DGANoDirectVideoMode

  Major opcode of failed request:  136 (XFree86-DGA)

  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)

  Serial number of failed request:  13

  Current serial number in output stream:  13

xdtv_v4l-conf had some trouble, trying to continue anyway

Warning: Missing charsets in String to FontSet conversion

wmhooks: netwm detected

wmhooks: netwm state above supported

wmhooks: netwm fullscreen supported

wmhooks: nothing found...

DGA: server=2.0, include=2.0

VidMode: server=2.2, include=2.2

  available video mode(s): ...............
Selected XvImage adaptor with yuyv support: NV05 Video Blitter on port 126 (grabdisplay)

No XvVideo port available.

WARNING: video memory base unknown, may be caused by a problem

  with xdtv_v4l-conf or a non-availability of DGA

  and frame buffer devices: CLASSICAL OVERLAY IS DISABLED !

*** GRABBER DEVICE TYPE = v4l2

Warning: Cannot convert string "-xxl-ledfixed-medium-r-semicondensed--39-120-75-75-c-180-*-*" to type FontStruct

Warning: Missing charsets in String to FontSet conversion

MMX, SSE, AMD MMX extensions, SSE2, 3DNOW, have been detected.

Method sse

*** AUDIO DEVICE TYPE = alsa

*** MIXER DEVICE TYPE = alsa




Any help here appreciated

---

### Post by L_V on 2008-02-24
I also tried xdtv from Mandriva which has been updated: [_xdtv-2.4.1cvs6-1mdv2008.0.i586.rpm_](http://sourceforge.net/project/showfiles.php?group_id=67268)

and the one from [_Marillat_](http://xawdecode.sourceforge.net/htmlpageFR/indexFR.shtml)

The main problem in Gutsy is to solve the dependancy issues, and to solve this bug:

```
Warning: Cannot convert string "-xxl-ledfixed-medium-r-semicondensed--39-120-75-75-c-180-*-*" to type FontStruct

Warning: Missing charsets in String to FontSet conversion
```
I've spent 4 days on that one without any solution.
Impossible to adjust the OSD size.

The cause is these bugs:
[https://launchpad.net/ubuntu/+source/xfig/+bug/2066](https://launchpad.net/ubuntu/+source/xfig/+bug/2066)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/63408](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/63408)
[https://bugs.launchpad.net/ubuntu/+source/xfontsel/+bug/35330](https://bugs.launchpad.net/ubuntu/+source/xfontsel/+bug/35330)

It seems the problem have something to do with locales, and font paths which are no longer in xorg.conf.

It should be easier if ubuntu makes its own xdtv package.

---

