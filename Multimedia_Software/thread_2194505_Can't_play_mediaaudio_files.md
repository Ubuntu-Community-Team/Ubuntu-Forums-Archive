---
title: "Can't play media/audio files"
date: 2013-12-18
forum: Multimedia Software
---

### Post by kristen2 on 2013-12-18
My computer is a Chromebook and I've installed Ubuntu on it by downloading Crouton ([https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)). So, it's a little odd sometimes. I've downloaded it before and didn't have this problem. My computer crashed yesterday so I've had to reinstall Ubuntu, but the developer has made some changes apparently so some things aren't working the way they were before.


I can't get SMPlayer to work, nor anything that plays audio/video for that matter. It won't play any files (I'll open SMPlayer and open a file then press play but it doesn't begin. I'm not talking about not having sound, I mean the file just doesn't begin) and audio mixer also gives me this error: 
GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.


May I have some help, please? Thank you so much.

---

### Post by entw on 2013-12-19
Try 'alsamixer' and check if it can detect your 'Card' and 'Chip'.

---

### Post by Iowan on 2013-12-19
Threads merged.

---

### Post by kristen2 on 2013-12-19
I open alsamixer in terminal and before, in my previous install of Ubuntu, I was seeing volume bars for "master" "headphones" "speaker" and 2 others, but now I'm only seeing a volume bar for "master"
I don't know how to check if it can detect my Card and Chip....

---

### Post by kristen2 on 2013-12-19
Sorry. It says
Card: CRAS
Chip: CRAS

---

### Post by entw on 2013-12-19
Well it seems that AlSA is not working.
Check the following articles:
[https://wiki.ubuntu.com/Audio/HDAGeneric](https://wiki.ubuntu.com/Audio/HDAGeneric)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by kristen2 on 2013-12-19
Thank you.
I looked at the SoundTroubleshooting link and did a few commands in terminal to check if my sound card is being recognized by the system, and it looks like it is. I don't want to go further on my own because I don't want to play around with things and mess up my computer
```
(precise)laptop@localhost:~$ sudo aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````


(precise)laptop@localhost:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.4.0/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.4.0/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.4.0/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.4.0/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.4.0/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.4.0/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.4.0/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.4.0/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.4.0/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.4.0/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.4.0/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.4.0/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.4.0/kernel/sound/core/snd-timer.ko
/lib/modules/3.4.0/kernel/sound/core/snd-pcm.ko
``````

(precise)laptop@localhost:~$ lspci -v | grep -A7 -i "audio"
bash: lspci: command not found
```

---

### Post by kristen2 on 2013-12-19
```
(precise)laptop@localhost:~$ grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC269VB
/proc/asound/card0/codec#3:Codec: Intel PantherPoint HDMI

```
Maybe that also helps

---

### Post by kristen2 on 2013-12-19
Okay, so...
In my web browser, with flash installed, I can listen to audio and watch videos
but multimedia software still won't work. I'm trying to listen to an mp3 in SMPlayer and it won't play.
I went into preferences and "pulse" was selected for the output driver and I switched it to alsa.
After switching to alsa, I could listen to the mp3 in SMPlayer, but it's still weird. Like, the timer doesn't work. It doesn't count how far into the audio it is. Do you know what I'm saying? Like, as I'm listening to the mp3, it doesn't show the position in time. It's weird and annoying :/
Am I missing pulse audio? How do I check? And would it make a difference, do you think?

---

### Post by kristen2 on 2013-12-20
If I plug in my earphones, the audio still comes out of the speaker and there's no sound in my earphones

---

### Post by monkeybrain20122 on 2013-12-21
Since flash works it is not a problem with your sound card or sound settings. Open smplayer and go to Options > Preferences > audio > output driver. What is the entry?


Edited: sorry missed your last post, did you install pulseaudio? It should be installed by default in stock Ubuntu, but not in some flavours like lubunu.
Easy way to check if you have it installed, just open a terminal and type
sudo apt-get install pulseaudio
if it wasn't install, it will install it, otherwise it will tell you that it is already in the latest version and do nothing

---

### Post by kristen2 on 2013-12-21
Hi monkey,
Thank you for your help.
I ran the command in terminal, and it tells me pulseaudio is already the newest version. But isn't it weird that when I have pulse set as my output driver in SMPlayer, it does nothing?
It will play when I have alsa set as my out put driver, although there's still something wrong with ALSA, I think. I just don't know what to do about it.
[IMG]http://wiki.audacityteam.org/w/images/3/35/Alsamixer_main.png[/IMG]
That's more what alsa is supposed to look like, and this is what mine looks like right now:
[IMG]http://i43.tinypic.com/286zsew.png[/IMG]

The card and chip are both wrong, but I don't understand it. I don't know what CRAS is but I know the card should be Intel something


Oh, and when I press F6 to select sound card there are no options. There is only "default", which is what you see.

---

### Post by kristen2 on 2013-12-22
helpppp

---

### Post by andrew.46 on 2013-12-22
SMPlayer should give you access to both MPlayer and SMPlayer logs, could you post these for the failed playback?

---

