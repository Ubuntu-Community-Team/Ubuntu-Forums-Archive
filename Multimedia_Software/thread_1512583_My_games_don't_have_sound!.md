---
title: "My games don't have sound!"
date: 2010-06-18
forum: Multimedia Software
---

### Post by BurningSludge on 2010-06-18
[FONT=Comic Sans MS][SIZE=3]List of games that don't have sound.
[/SIZE][/FONT]
[LIST]
[*][FONT=Comic Sans MS][SIZE=3]Abuse[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Airstrike
[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Alex The Alligator 4[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Atomic Tanks[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Block Attack - rise of the blocks[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Free Civ[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]KQ[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Metal Blob Solid[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Nibbles[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Powder[/SIZE][/FONT]
[/LIST]
[FONT=Comic Sans MS][SIZE=3]
List of games that had there sound problem resolved.
[/SIZE][/FONT]
[LIST]
[*][FONT=Comic Sans MS][SIZE=3]Free Civ[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Metal Blob Solid[/SIZE][/FONT]
[*][FONT=Comic Sans MS][SIZE=3]Block Attack - rise of the blocks [/SIZE][/FONT]
[/LIST]
 
[FONT=Comic Sans MS][SIZE=3]Help me resolve sound problems of the games that are not already on the resolved list.[/SIZE][/FONT]

---

### Post by BurningSludge on 2010-06-18
[FONT=Comic Sans MS][SIZE=3]This is a Bump![/SIZE][/FONT]

---

### Post by Yellow Pasque on 2010-06-18
It looks like you have an issue with sound from apps using SDL. If you're running pulseaudio, make sure you:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```

---

### Post by BurningSludge on 2010-06-18
> **Temüjin said:**
> It looks like you have an issue with sound from apps using SDL. If you're running pulseaudio, make sure you:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```

[FONT=Comic Sans MS][SIZE=3]Nope, I already have the newest version of that.[/SIZE][/FONT]

---

### Post by lidex on 2010-06-18
Run this command in a terminal and post the output:
```
dpkg -l | grep "sdl"
```

Here's mine:
```
dpkg -l | grep "sdl"
ii  libsdl-image1.2                                         1.2.10-2                                                            image loading library for Simple DirectMedia Layer 
ii  libsdl-mixer1.2                                         1.2.8-6build1                                                       mixer library for Simple DirectMedia Layer 1.2
ii  libsdl-net1.2                                           1.2.7-2                                                             network library for Simple DirectMedia Layer
ii  libsdl-ttf2.0-0                                         2.0.9-1build1                                                       ttf library for Simple DirectMedia Layer with FreeT
ii  libsdl1.2debian                                         1.2.14-6ubuntu2                                                     Simple DirectMedia Layer
ii  libsdl1.2debian-pulseaudio                              1.2.14-6ubuntu2                                                     Simple DirectMedia Layer (with X11 and PulseAudio o

```

---

### Post by BurningSludge on 2010-06-19
```
rc  libsdl-gfx1.2-4                       2.0.20-1                                        drawing and graphical effects extension for SDL
ii  libsdl-image1.2                       1.2.10-1                                        image loading library for Simple DirectMedia Layer 1.2
ii  libsdl-image1.2-dev                   1.2.10-1                                        development files for SDL 1.2 image loading libray
ii  libsdl-mixer1.2                       1.2.8-6build1                                   mixer library for Simple DirectMedia Layer 1.2
ii  libsdl-mixer1.2-dev                   1.2.8-6build1                                   development files for SDL1.2 mixer library
ii  libsdl-net1.2                         1.2.7-2                                         network library for Simple DirectMedia Layer
ii  libsdl-pango1                         0.1.2-4                                         text rendering with Pango in SDL applications (shared library)
ii  libsdl-sound1.2                       1.0.3-3build1                                   Decoder of several sound file formats for SDL
ii  libsdl-ttf2.0-0                       2.0.9-1build1                                   ttf library for Simple DirectMedia Layer with FreeType 2 support
ii  libsdl1.2-dev                         1.2.14-4ubuntu1.1                               Simple DirectMedia Layer development files
ii  libsdl1.2debian                       1.2.14-4ubuntu1.1                               Simple DirectMedia Layer
ii  libsdl1.2debian-pulseaudio            1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and PulseAudio options)
ii  sdlbrt                                0.0.20070714-3                                  BASIC interpreter for game development - runtime interpreter

```[FONT=Comic Sans MS][SIZE=3]Here it is.[/SIZE][/FONT]

---

### Post by lkjoel on 2010-06-21
You could try to use [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig, but check if your soundcard is supported first?

---

### Post by jhahoneyk on 2010-07-16
Hi, even I have the same problem. Anything that uses SDL fails to play audio. For example, neverball complains "No available audio device". Earlier everything worked perfectly, but unfortunately I've no idea since when the problem started to occur.

For me it is-

```
ii  gstreamer0.10-sdl                           0.10.18-1ubuntu1                                GStreamer plugin for SDL output
ii  libsdl-image1.2                             1.2.10-1                                        image loading library for Simple DirectMedia
ii  libsdl-image1.2-dev                         1.2.10-1                                        development files for SDL 1.2 image loading 
ii  libsdl-net1.2                               1.2.7-2                                         network library for Simple DirectMedia Layer
ii  libsdl-sound1.2                             1.0.3-3build1                                   Decoder of several sound file formats for SD
ii  libsdl-ttf2.0-0                             2.0.9-1build1                                   ttf library for Simple DirectMedia Layer wit
ii  libsdl1.2-dev                               1.2.14-4ubuntu1.1                               Simple DirectMedia Layer development files
ii  libsdl1.2debian                             1.2.14-4ubuntu1.1                               Simple DirectMedia Layer
rc  libsdl1.2debian-alsa                        1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
ii  libsdl1.2debian-pulseaudio                  1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and Pulse
```

I tried [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but it doesn't deal with SDL/OSS problems

Any idea how to fix/troubleshoot this?

---

### Post by lkjoel on 2010-07-16
> **jhahoneyk said:**
> Hi, even I have the same problem. Anything that uses SDL fails to play audio. For example, neverball complains "No available audio device". Earlier everything worked perfectly, but unfortunately I've no idea since when the problem started to occur.

For me it is-

```
ii  gstreamer0.10-sdl                           0.10.18-1ubuntu1                                GStreamer plugin for SDL output
ii  libsdl-image1.2                             1.2.10-1                                        image loading library for Simple DirectMedia
ii  libsdl-image1.2-dev                         1.2.10-1                                        development files for SDL 1.2 image loading 
ii  libsdl-net1.2                               1.2.7-2                                         network library for Simple DirectMedia Layer
ii  libsdl-sound1.2                             1.0.3-3build1                                   Decoder of several sound file formats for SD
ii  libsdl-ttf2.0-0                             2.0.9-1build1                                   ttf library for Simple DirectMedia Layer wit
ii  libsdl1.2-dev                               1.2.14-4ubuntu1.1                               Simple DirectMedia Layer development files
ii  libsdl1.2debian                             1.2.14-4ubuntu1.1                               Simple DirectMedia Layer
rc  libsdl1.2debian-alsa                        1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
ii  libsdl1.2debian-pulseaudio                  1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and Pulse
```I tried [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but it doesn't deal with SDL/OSS problems

Any idea how to fix/troubleshoot this?
For OSS problems, use Fix my sound! in my sig.
It will repair/install OSS.

---

### Post by jhahoneyk on 2010-07-16
hey lkjoel thanks for the link, but that article is written to replace ALSA by OSS, which I don't want to do. As far as I understand, ALSA provides OSS emulation so I don't need to install OSS.
When I use a Lucid LiveCD, the sound works fine, I can play all games such as Neverball. So clearly I don't need to switch to OSS. There is something wrong with my installation.
However, I did try some OSS commands and here's the output of ossinfo-

```

Version info:   (0x00000000) 
Platform: Linux/i686 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (hunny-laptop)

Number of audio devices:        0
Number of audio engines:        0
Number of MIDI devices:         0
Number of mixer devices:        0


Device objects

MIDI devices (/dev/midi*)

Mixer devices

Audio devices

Nodes
  /dev/sndstat -> /proc/asound/oss/sndstat

```

(its the same for the LiveCD)

* osstest goes into some kind of infinite loop trying to test device # -1
* though playsound (uses SDL) doesn't work, ossplay works :confused: So I guess if there's a way to tell SDL to use ALSA instead of OSS, that should fix my problem.

I tried to restart ALSA and it shows that its loading the OSS sound driver modules-

```

hunny@hunny-laptop:~$ sudo alsa reload
/sbin/alsa: Warning: Processes using sound devices: 1846(knotify4) 2589(kmix). 
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

These are all stuff I tried, any suggestions? Thanks :)

EDIT: Its fixed, I just needed to install libsdl1.2debian-alsa :)

---

### Post by lkjoel on 2010-07-16
> **jhahoneyk said:**
> hey lkjoel thanks for the link, but that article is written to replace ALSA by OSS, which I don't want to do. As far as I understand, ALSA provides OSS emulation so I don't need to install OSS.
When I use a Lucid LiveCD, the sound works fine, I can play all games such as Neverball. So clearly I don't need to switch to OSS. There is something wrong with my installation.
However, I did try some OSS commands and here's the output of ossinfo-

```

Version info:   (0x00000000) 
Platform: Linux/i686 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (hunny-laptop)

Number of audio devices:        0
Number of audio engines:        0
Number of MIDI devices:         0
Number of mixer devices:        0


Device objects

MIDI devices (/dev/midi*)

Mixer devices

Audio devices

Nodes
  /dev/sndstat -> /proc/asound/oss/sndstat

```(its the same for the LiveCD)

* osstest goes into some kind of infinite loop trying to test device # -1
* though playsound (uses SDL) doesn't work, ossplay works :confused: So I guess if there's a way to tell SDL to use ALSA instead of OSS, that should fix my problem.

I tried to restart ALSA and it shows that its loading the OSS sound driver modules-

```

hunny@hunny-laptop:~$ sudo alsa reload
/sbin/alsa: Warning: Processes using sound devices: 1846(knotify4) 2589(kmix). 
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```These are all stuff I tried, any suggestions? Thanks :)

EDIT: Its fixed, I just needed to install libsdl1.2debian-alsa :)
Glad to know it is fixed.
That happens all the time to me.
I have problems... until I install the correct package.

---

