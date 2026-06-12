---
title: "Hardy 64 bits wont play WMV"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Kaisersoze on 2008-04-26
Hi group, 

I have switched from hardy 32 to 64 bits (fresh install) Everything is fine except the WMV codecs.

For some reason I am not able to play any WMV files. I have installed Mplayer and Splayer.

Followed the instructions on:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=codecs](http://ubuntuforums.org/showthread.php?t=766683&highlight=codecs)

and 

[http://ubuntuforums.org/showthread.php?t=755939#post4721444](http://ubuntuforums.org/showthread.php?t=755939#post4721444)

Divx, mp3 etc.. all play ok. WMV doesnt play!

If I type sudo apt-get install w64codecs the system reports everything is already installed.

I would appreciate any suggestion on how to solve this problem. Kind regards, 
KaiserSoze

---

### Post by Archmage on 2008-04-26
Some WMV-files are locked and need an additional key (that you can buy).

Mplayer can't play this.

---

### Post by Kaisersoze on 2008-04-26
> **Archmage said:**
> Some WMV-files are locked and need an additional key (that you can buy).

Mplayer can't play this.


I know.. but the thing is that used to play these files with no problems on hardy 32 and gutsy 7.10...:confused:

---

### Post by cor2y on 2008-04-26
try launching mplayer or gmplayer from the terminal and play the file and post the error message here.

---

### Post by Major_Kong on 2008-04-26
> **Kaisersoze said:**
> I know.. but the thing is that used to play these files with no problems on hardy 32 and gutsy 7.10...:confused:

The 64-bit package is not the same as the 32-bit package. (there are missing codecs)

---

### Post by Kaisersoze on 2008-04-26
> **Major_Kong said:**
> The 64-bit package is not the same as the 32-bit package. (there are missing codecs)

OK. But.. is there anyway to play WMV files on 64 version?  Thanks and regards, 
K

---

### Post by cor2y on 2008-04-26
As far as i know ,maybe the 64bit users can say, w64codecs is exactly the same as w32codecs package just optimized for 64bit usage.
Kaisersoze you said you installed w64codecs right?

---

### Post by Kaisersoze on 2008-04-26
> **cor2y said:**
> As far as i know ,maybe the 64bit users can say, w64codecs is exactly the same as w32codecs package just optimized for 64bit usage.
Kaisersoze you said you installed w64codecs right?

Yep.. everything is installed and OK.

$ sudo apt-get install w64codecs
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w64codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxx@xxxx:~$ 


Thank you

---

### Post by cor2y on 2008-04-26
You will have to post the message you get via the terminal with mplayer
For wmv playback with totem-gstreamer or totem-xine the w64codecs are not needed.
Just every plugin for gstreamer 
gstreamer ugly, gstreamer ffmpeg, gstreamer bad, gstreamer fluendo
On the xine side you will need libxine1 libxine1-gnome libxine1-plugins libxine1-misc-plugins and libxine1-ffmpeg.

---

### Post by Kaisersoze on 2008-04-26
> **cor2y said:**
> You will have to post the message you get via the terminal with mplayer
For wmv playback with totem-gstreamer or totem-xine the w64codecs are not needed.
Just every plugin for gstreamer 
gstreamer ugly, gstreamer ffmpeg, gstreamer bad, gstreamer fluendo
On the xine side you will need libxine1 libxine1-gnome libxine1-plugins libxine1-misc-plugins and libxine1-ffmpeg.

I have verified and all libs are installed.

Mplayer output is:

Playing ccent13.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  800x600  24bpp  1000.000 fps   33.8 kbps ( 4.1 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Requested video codec family [wmsdmod] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x3253534D.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Requested audio codec family [wma9spdmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wma9spdshow] (afm=dshow) not available.
Enable it at compilation.
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video

---

### Post by cor2y on 2008-04-26
Well there you have it.
The w64codecs pack is not there or at least installed where mplayer expects it to be.
Time to go on a codec hunt /usr/lib/codecs is where the w64codecs should be installed and where mplayer should look for them, if yours ended up in /usr/local/lib/codecs then you will either have to create a symlink or move the codecs folder to /usr/lib/
You could try taking the codec package from the medibuntu repo directly.
[http://packages.medibuntu.org/pool/non-free/w/w64codecs/](http://packages.medibuntu.org/pool/non-free/w/w64codecs/)

---

### Post by velo.br on 2008-05-21
> **cor2y said:**
> As far as i know ,maybe the 64bit users can say, w64codecs is exactly the same as w32codecs package just optimized for 64bit usage.
Kaisersoze you said you installed w64codecs right?

Looking at mediabuntu repositories:
[http://packages.medibuntu.org/pool/non-free/w/w64codecs/](http://packages.medibuntu.org/pool/non-free/w/w64codecs/)
[http://packages.medibuntu.org/pool/non-free/w/w32codecs/](http://packages.medibuntu.org/pool/non-free/w/w32codecs/)

W64 has only 220Kb
W32 has 13.6Mb

They can't have same content.

Is there any other source to w64codecs file?


VELo

---

### Post by cor2y on 2008-05-21
I don't know about a deb package but there is the source of the w32/w64 codecs, the mplayer site itself
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
Its not in deb form but i believe it just requires extracting to where mplayer will look for the codecs (in the newer version of mplayer its /usr/lib/codecs) but even at the mplayer site they are only a few kb in size and not as large as the 32bit version.

---

### Post by velo.br on 2008-05-21
And how I install that file?

Is there any parameter to apt-get?


VELO

---

### Post by cor2y on 2008-05-21
it requires extracting to the directory where mplayer will look for it.
Unlike the deb file that requires installing.
However i have not seen anyone complain that the deb version of the w64codec pack does not work so try that one first before using the .tgz file.

---

### Post by Tyriel on 2008-05-22
I am also having this problem and trying to figure out how to fix it.

---

### Post by mc4man on 2008-05-22
> I am also having this problem and trying to figure out how to fix it.
here is a very recent thread about the same, the short of it is that playback of wmv is possible but atm your not going to get far with either the w64codecs or the mplayer binaries.
[http://ubuntuforums.org/showthread.php?t=800572](http://ubuntuforums.org/showthread.php?t=800572)

---

