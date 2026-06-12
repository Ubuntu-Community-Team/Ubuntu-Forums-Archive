---
title: "Getting sounds to play simultaneously"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by vladk2k on 2007-03-05
Hello.
I have a C-Media 6501B on-board soundcard and a pari of USB headphones. I am experiencing some troubles playing sound simultaneously, even though I use ALSA (such as the comprehensive sound problem guide suggests)

If I start up XMMS, configured to use ALSA, I cannot play any other sound through my on-board soundcard. For example, if I start a youtube video, the sound goes to m headphones. Likewise, Rhythmbox does not start playing until after I stop XMMS. After I start playing a melody with Rhythmbox (having stopped XMMS) I cannot resume XMMS from playing (It tells me another application is using the soundcard)

What is curious is that I can play overlapping sounds from the sound control application (System -> Preferences -> Sound) and also from two or more youtube videos, without any problem.

Another (smaller problem): If I use any other player than VLC, I get distorted sounds on videos, like, robotized and multiple frequencies overlapping (however the videos play correctly on the headphones). I have tried Totem, Mplayer, gxine, they all do the same (or, if I play with the audio controls, sound becomes OK but video framerate drops horribly).

It is important that I get simultaneous sound from music playing applications and things like gaim... Any ideas?

---

### Post by panch0 on 2007-03-05
To get simultaneous sound you need to set up ALSA to use the dmix plugin, search on dmix and asoundrc.

Then tell each program to use the dmixed output, like in KPlayer you would go to Settings - Configure KPlayer - Audio and set the driver to ALSA and the device to the dmixed device you've set up. Other programs should have similar options.

Once you are sure everything works like you want it, you can make that device the default so that all programs use it.

---

### Post by vladk2k on 2007-03-15
I have made a capture of the sound problem (crazy audio!)

The sound is the intro theme to family guy, and obviously it shouldn't sound like that.
[ATTACH]27491[/ATTACH]
[COLOR="Red"]EDIT[/COLOR]: the file in the archive should be named dumb_sound.ogg (i can't figure out why the extension disappeared)
Thing is, on my headphones it sounds just right. They are also connected via usb:
```
vladk2k@AthlonuXP:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 08bb:2900 Texas Instruments Japan 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e3 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  

```

and they are seen correctly through aplay:
```
vladk2k@AthlonuXP:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default_1 [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I use PnP Audio Device (that is my onboard audio card) and USB Audio CODEC is the headphones. Also, any Idea on how to switch them so that PNP is the first? They both use the snd-usb-audio driver so...

---

### Post by kerry_s on 2007-03-15
Was that the chipmonks? :lolflag: (yes, i know the show)
I use esound for my setup. Just install "esound, esound-clients, esound-common"
then
gksu gedit /etc/libao.conf

change or comment out

#default_driver=alsa09
to
default_driver=esd

---

### Post by vladk2k on 2007-03-21
I have tried esound, with no luck.
This strange noise is only audible for video files, AFAIK mp3s and ogg sound very good.
Also it looks like a software problem, since the recording was made using PCM as input device. Still can't figure out why it doesn't affect the headphones, as they use the same driver (snd-usb-audio) AND the manufacturing company ("Gembird") sounds more of a no-name than C-Media

---

