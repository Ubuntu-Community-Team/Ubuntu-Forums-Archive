---
title: "NVidia sound on biostar AMD motherboard board  doesn't work"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by FloSynergy on 2007-06-21
Hey all,

have just set up feisty 7.04 on a new machine:
Biostar NF61V Micro AM2 Motherboard
AMD Athlon 64x2 3800+ CPU
2 Gb RAM
80Gb HDD

I managed to install the Nvidia drivers and get on-board chips recognised thanks to Envy.

really very keen to start vibing to some decent music and perhaps even play one or two games...

but:

I can't get sound to work at all. the sound chip is a realtek alc861-vd. i have sleuthed around various posts and have followed the guide [here]("http://ubuntuforums.org/showthread.php?t=205449") as far as possible - to no avail. 

aplay -l yields:
> florian@florian-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer shows various channels:
headphones
pcm
front
front mic
line
mic iec958
capture
input source

however, headphones does not react at all to any manipulation, neither does iec958, capture, or input source.

when i enter the system > preferences > sound  section, i can request a sound test. this yields nothing, and the progress bar freezes at about 25%.

i've really tried to figure this one out, and have fiddled and tweaked the settings in this gui.

just can't get the system to produce as much as a whisper.

please, folks, if you have any idea how to get my sound pumping, pleeease lemme know?

ok, be well,

flo

---

### Post by FloSynergy on 2007-06-22
hey folks,

thanks for the ref re hi-def cards.

i've been struggling for 3 days to get my sound to work...

then, sd-plissken pointed out [this]("http://ubuntuforums.org/showthread.php?t=239995&page=5") thread (it's what i used in the end) and [this]("p://ubuntuforums.org/showthread.php?t=455147") and [the wiki]("https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29").

now, i'm rocking to my favourite marley-tunes 

get-up - stand-up.....feel dem spirit!:guitar:

gigathanks,

flo

---

