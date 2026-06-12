---
title: "vlc and mplayer won't play flv files, only sound"
date: 2008-08-26
forum: Multimedia Software
---

### Post by owl on 2008-08-26
Hello,

i just downloaded some .flv files. When i try to play them either with mplayer or vlc i get only sound, no video at all.
I am on kubuntu hardy heron.
The same embedded file is played well in firefox.
any solution guys?

---

### Post by owl on 2008-08-26
well it looks like the flv files i had downloaded only had the sound in them indeed! video had not been downloaded.
So it is ok now.

---

### Post by unknown23 on 2009-11-27
vlc is not playing any files

xine crashes when i launch it

real player does not work either

i NEED a simple set of instructions on how to get vlc to play .flv files

i read all the threads over two weeks,and this is just getting to be way too much

i just want to watch a film ..... is that so hard to do in linux?

for fuxsake, this is aggervating!

---

### Post by andrew.46 on 2009-11-27
Hi unknown,

> **unknown23 said:**
> i NEED a simple set of instructions on how to get vlc to play .flv files

Could you play one of these .flv files from the commandline as follows:

```
cvlc -v **[COLOR="Red"]*myfile.flv*[/COLOR]**
```

and then post the command + full terminal output here? This should give a few hints about what is going wrong...

Andrew

---

### Post by wilee-nilee on 2009-11-27
> **unknown23 said:**
> vlc is not playing any files

xine crashes when i launch it

real player does not work either

i NEED a simple set of instructions on how to get vlc to play .flv files

i read all the threads over two weeks,and this is just getting to be way too much

i just want to watch a film ..... is that so hard to do in linux?

for fuxsake, this is aggervating!

Not knowing what distro your running, makes it hard to help you, but the restricted extras and the medibuntu pack should be all you need.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also the post above me may be helpful but if your unable to get it working at this point a CLI is a little bit above what is needed.

xine and gxine are problematic for me and not necessarily needed.

---

### Post by unknown23 on 2009-11-29
i run karmic

did what was suggested above

didnt do anything, and i just wish someone would give me codes torun in the terminal to get this to work

i just want to watch films on my laptop

 lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

---

### Post by unknown23 on 2009-11-29
shadowcast@shadowcast:~$ cvlc -v test.flv
VLC media player 1.0.2 Goldeneye
[0x8a04140] main libvlc warning: could not open plugins cache file /home/shadowcast/.cache/vlc/plugins-04041e.dat for reading
[0x8a2a490] main demux warning: no access_demux module matching "file" could be loaded
[0x8b5cde0] main interface error: no interface module matched "globalhotkeys,none"
[0x8b5cde0] main interface error: no suitable interface module
[0x8a04140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8b5ccf8] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Can't stat test.flv
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x8a28920] dvdnav demux warning: cannot open dvdnav
[0x8a29930] vcdx access warning: Can't get file status for test.flv:
No such file or directory
[0x8a29930] vcdx access warning: could not retrieve file info for `test.flv': No such file or directory
[0x8a29930] vcdx access warning: can't open nrg image file test.flv for reading
[0x8a29930] access_file access error: cannot open file test.flv (No such file or directory)
[0x8a29930] main access error: File reading failed
[0x8a29930] main access error: VLC could not open the file "test.flv".
[0x8a29930] cdda access warning: could not open test.flv
[0x8b59998] main input error: open of `test.flv' failed: no suitable access module
[0x8b59998] main input error: Your input can't be opened
[0x8b59998] main input error: VLC is unable to open the MRL 'test.flv'. Check the log for details

---

### Post by mc4man on 2009-11-29
> "cvlc -v [COLOR="Red"]myfile.flv[/COLOR]

It's meant that you replace the red with the name of an actual flash video that you have  **and path** if not loose in home folder

That's why your getting this, the file either doesn't exist or  it's not loose in home folder

> [0x8b59998] main input error: VLC is unable to open the MRL 'test.flv'

---

### Post by frenchn00b on 2010-01-26
> **mc4man said:**
> It's meant that you replace the red with the name of an actual flash video that you have  **and path** if not loose in home folder

That's why your getting this, the file either doesn't exist or  it's not loose in home folder

vlc -I dummy or cvlc arent the best to play flv

the best is mplayer.

btw check here: [http://ubuntuforums.org/showthread.php?t=1390764](http://ubuntuforums.org/showthread.php?t=1390764)

---

