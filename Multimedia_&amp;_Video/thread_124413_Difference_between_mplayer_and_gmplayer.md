---
title: "Difference between mplayer and gmplayer?"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by swong1 on 2006-02-01
Hi, I installed mplayer, but I also get gmplayer. Are they the same? mplayer can play my .wmv files, but gmplayer can't. It just loads and freezes. Correct me if I'm wrong, I think gmplayer is the GUI front end. Issuing the command mplayer, does not bring up the GUI, but typing gmplayer does. gmplayer still needs mplayer to actually play the files. So, it appears there is some miscommunication between the two. Has anybody encountered the same problem? What is the solution?

The problem only started after I upgraded to Breezy.

---

### Post by bored2k on 2006-02-01
Try loading gmplayer _then_ loading the files from the GUI. And you are correct, gmplayer requires mplayer because it's just a frontend for mplayer, which is _not_ a GUI application.

---

### Post by swong1 on 2006-02-01
[QUOTE=bored2k]Try loading gmplayer _then_ loading the files from the GUI. And you are correct, gmplayer requires mplayer because it's just a frontend for mplayer, which is _not_ a GUI application.[/QUOTE]

I did as you suggested. gmplayer only shows a black screen, and no sound either. All the buttons are unresponsive. It does show the correct movie title however.

---

### Post by swong1 on 2006-02-03
bum. 

Anyone?

---

### Post by mpvano on 2006-02-03
Is it possible you have more than one copy of mplayer/gmplayer installed?

How are you "starting" them. If you type the command name into a terminal window then your bash "PATH" variable determines where it looks for them. If you are using a nautilus function to load them, or clicking on a nautilus icon, then the path variable may or may not be used depending on the "properties" for the file type or the icon you clicked on.

Examine all of the above. You can tell what terminal commands will load by typing "which mplayer" and "which gmplayer" commands.

If you have more than one installed, you need to sort that out first before you troubleshoot getting one of them working.

Mario

---

### Post by macbuff on 2006-02-03
gmplayer is just a symbolic link to mplayer when mplayer has been compiled with the '-GUI' option.

John

---

### Post by swong1 on 2006-02-03
Thanks for your responses, mpvano and macbuff.

```

which mplayer
which gmplayer

```

produces the output:

/usr/bin/mplayer
/usr/bin/gmplayer

As macbuff and bored2k wrote, gmplayer is just the GUI frontend for mplayer.

---

### Post by swong1 on 2006-02-06
I get the following error message by typing gmplayer. The part in bold type is interesting. I have mplayer, but gmplayer is not detecting it. Could anyone help me troubleshoot? Thanks!

```

MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.



vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
[B]mplayer: could not connect to socket
mplayer: No such file or directory[/B]
Failed to open LIRC support.
You will not be able to use your remote control.

Exiting... (Quit)

```

---

### Post by afhp on 2006-02-07
Another thing that I've noticed is that gmplayer is quite picky about its configuration (-vo and -ao) as well as the current display settings (spec. color depth).

---

### Post by swong1 on 2006-02-07
[QUOTE=afhp]Another thing that I've noticed is that gmplayer is quite picky about its configuration (-vo and -ao) as well as the current display settings (spec. color depth).[/QUOTE]
 Thanks afhp. I tried -ao and -vo, but still get the same error message.

With both flags together, I get an extra error message:

```

==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.26% (ratio: 3995->176400)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Error opening/initializing the selected video_out (-vo) device.

```

---

