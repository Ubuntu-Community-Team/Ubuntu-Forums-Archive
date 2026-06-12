---
title: "NO sound in media/vlc/m player"
date: 2010-04-12
forum: Multimedia Software
---

### Post by crashus on 2010-04-12
My problem is that i have no sound in any video player. The video works perfectly, but with absolutely no sound. I've tried switching output to ALSA, OCC and still no success. My audio files are playing perfect with any music player. In sound setting I'm using Analog stereo duplex, I have the option of choosing HDMI, but than I have no sound whatsoever. 
I encountered this problem once before and I remember the problem was with 2 different codecs i've installed, however now I can't remember anymore.

Does anyone have a clue how to solve this?
thanks

---

### Post by crashus on 2010-04-13
ok i've updated the sistem and now I can play every file extension except avi. I still can't get audio with that.

---

### Post by crashus on 2010-04-14
cmon nobody has a clue?

---

### Post by crashus on 2010-04-14
ok so I've updated the alsa driver to 1.0.22.1, and after I lost the sound in mozilla- flash video didn't play any sound. I solved that problem by removing pulseaudio-
now I still can't hear sound in avi files and I lost my sound configuration panel..

so anyone?

---

### Post by lidex on 2010-04-14
Kinda 'throwing out the baby with the bathwater'. I would suggest re-installing pulse, then go here and follow 'Part A'
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
Now go here and follow the relevant sections:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by crashus on 2010-04-14
hey thanks for the help!

as for the Pulse audio guide, I've followed it to the letter, however I still cannot open the Pulse audio volume control application- I get the Connection failed: Connection refused error. Then using the solution provided by the guide i get the following and the same error:

```
$ pulseaudio & pavucontrol[1] 9201
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:9202): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
```

---

### Post by lidex on 2010-04-14
Open synaptic and search 'esd' - minus the quotes. See how it compares to my screen below.

---

### Post by lidex on 2010-04-14
What is the output of this command:
```
aplay -l
``` 
<lower-case L>

---

### Post by crashus on 2010-04-14
The output to aplay -l 

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



as for the search in synaptic- i do not quite get it what you meant by that- I have the highlighted file in your pic, if you mean that..

---

### Post by lidex on 2010-04-14
You should probably have most of those packages installed is what I meant, except for the obvious you don't use.

---

### Post by crashus on 2010-04-14
ok so I've installed everything on the list that was missing(3), and after restart i can now acces Pulseaudio volume control and other.. I've checked the other site you've suggested and followed theirs instructions to restore sound in flash. basically uninstalled and reinstalled flash, but this still doesn't solve it and my original problem is still there- 
that is I cant hear sound playing .avi files

---

### Post by Yellow Pasque on 2010-04-14
Flash uses ALSA directly. To route it through Pulseaudio, see: [http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

As for the video, it would be helpful to start your video player from the terminal and post relevant output. .avi is a container format and can have different audio codecs.

---

### Post by crashus on 2010-04-14
So routing flash through Pulse audio worked and I got the flash sound back.


but the avi sound still evades me..
running avi in terminal comes out with 
```
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
frame skip 8
frame skip 8

```

---

### Post by lidex on 2010-04-14
In MPlayer, right-click and select preferences. On the audio tab make sure pulse is selected. Close/re-open. Anything?

---

### Post by crashus on 2010-04-14
pulse was selected by default, but i do not use mplayer because i get an error playing any file.
Error opening/initializing the selected video_out(-vo) device.

I changed the video to openGL, ikt now plays, but still without sound

---

### Post by lidex on 2010-04-15
xv probably a better choice. 
> SOUND

Common sound issues with GNOME MPlayer/MPlayer can be solved by enabling the software mixer in both their preferences. In GNOME MPlayer, navigate to "Edit > Preferences > Advanced", and tick the "Software Volume Control" box. As for MPlayer users, right-click on the video window and navigate to "Preferences > Audio", then tick the "Enable Software Mixer" box. If you launched a video before carrying out these steps, open the video again with the new sound setting in place, or restart GNOME MPlayer/MPlayer.

Reference this post also:
[http://ubuntuforums.org/showpost.php?p=9123753&postcount=6]("http://ubuntuforums.org/showpost.php?p=9123753&postcount=6")

And make sure you've gone through this post completely:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by crashus on 2010-04-15
Yes! That solved it!
I now can play everything in mplayer!

Thanks to both lidex and Temüjin for helping me solve this!

---

### Post by crashus on 2010-04-16
Ok so even thought these topic is solved I would like to ask you to help me with another problem. I don't want to start another topic for 2 reasons- one: similar topics already exist, however there is still no solution, and two: to let you know the history of my sound problem, so as not to corrupt my current settings.

So here is another problem I have:

When playing 3d games like Scorched 3D and Warzone 2100 the sound is distorted and scratchy right from the beginning. There might be a period when the sound is ok, but not for long. After a while there is no sound whatsoever and when that happens if I try to exit the game my computer certainly freezes and I have to restart by force.

Any of you having the same problems or know how to fix this?

---

### Post by Yellow Pasque on 2010-04-16
Older versions of openal are known to be problematic when using pulseaudio. I don't see any PPA's with update libopenal1. Maybe I'll take a try at building an updated version.

---

### Post by crashus on 2010-04-16
So it's the openal problem? But if it was this, wouldn't that mean that everybody has the same problem as I do?

---

### Post by Yellow Pasque on 2010-04-17
Well, you can try an updated openal:
32-bit: [https://launchpad.net/~dtl131/+archive/mediahacks/+files/libopenal1_1.12.854-2_i386.deb](https://launchpad.net/~dtl131/+archive/mediahacks/+files/libopenal1_1.12.854-2_i386.deb)
64-bit: [https://launchpad.net/~dtl131/+archive/mediahacks/+files/libopenal1_1.12.854-2_amd64.deb](https://launchpad.net/~dtl131/+archive/mediahacks/+files/libopenal1_1.12.854-2_amd64.deb)

---

### Post by crashus on 2010-04-17
Yup that did it for me! no more scratchy sound and crashes!!

THANK YOU!

---

