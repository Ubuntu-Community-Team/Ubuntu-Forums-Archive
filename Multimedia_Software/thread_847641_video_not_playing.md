---
title: "video not playing"
date: 2008-07-02
forum: Multimedia Software
---

### Post by profeta81 on 2008-07-02
Sorry for asking such a silly question... and sorry for the lack of diagnostic information I'm including in the post but I've no idea where to start...

I have a Toshiba satellite A100-206. I had Ubuntu gutsy installed for a couple of months and almost everything worked out of the box (video and audio needed some fixing). two weeks ago' I decided to try and upgrade to hardy, and since then video playback won't work. when totem start after double clicking on an .avi file a dialog pops up saying:

"The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector."

don't know what the other application could be. maybe something to do with compiz? In the "advanced desktop settings" the video plug in seems is checked...

cheers in advance for reply
lorenzo

---

### Post by bijeeshvs on 2008-07-02
if u dont mind i would suggest a clean hardy installation rather than upgrading.........
sorry i was not able to help this time...................

---

### Post by AliTabuger7 on 2008-07-03
I probably won't be too helpful either, but i'll throw in what i know off the top of my head.

You could try running without compiz by running "metacity --replace"
A command line output on totem might be a little more helpful.
If i were you I would look in this "multimedia systems selector" it talks about.

Out of curiosity, what kind of graphics card does it have? Brand is more important than model number or speed in this and most bug cases.

---

### Post by profeta81 on 2008-07-03
for ***bijeeshvs***:

well... I've got loads of stuff - roughly 15GB - in my home directory which is in the same big root partition as all the rest of the system a part of /boot (that's because of some stupid choices I made when installing my first linux distribution) and a reinstallation would mean too much work, so, that'd be the very last option, especially giving that it's only a problem with the multimedia...

for ***AliTabuger7***:

**graphics card**: ATI Technologies Inc M56P [Radeon Mobility X1600]

**Totem output** when run from command line:

user@host:directory$ totem Back\ to\ the\ Future\ I.avi
** Message: Error: Could not initialise Xv output
xvimagesink.c(1333): gst_xvimagesink_get_xv_support (): /video-sink/bin0/xvimagesink0:
No port available

the dialougue with the error message appears as well as described above... I also tryed with **mplayer**:

user@host:directory$ mplayer Back\ to\ the\ Future\ I.avi 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Back to the Future I.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
[aviheader] Audio stream found, -aid 2
VIDEO:  [XVID]  640x336  12bpp  23.976 fps  1182.5 kbps (144.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2439/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video

A:  45.0 (44.9) of 6964.4 ( 1:56:04.4)  1.1% 
Exiting... (Quit)

Mplayer actually start the playback of the film, but only the audio since it doesn't find the appropriate video output. Finally, as mplayer suggester, I tried **xvinfo**:

user@host:directory$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

hope this si all a bit more helpful

cheers
Lorenzo

---

### Post by AliTabuger7 on 2008-07-03
No adapter present means that it does not think you have a video card. This probably has to do with your xorg.conf (/etc/X11/xorg.conf).

You can revert it to what it was when you first installed ubuntu by running "sudo dpkg-reconfigure xserver-xorg" and then restarting.

This will probably disable your proprietary/restricted ati drivers, and may stop the really fancy compiz effects. You can re-enable the driver later.

---

