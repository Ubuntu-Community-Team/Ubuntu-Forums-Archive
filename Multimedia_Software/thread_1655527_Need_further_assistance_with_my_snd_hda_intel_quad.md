---
title: "Need further assistance with my snd_hda_intel quadraphonic sound not working"
date: 2010-12-29
forum: Multimedia Software
---

### Post by miekrand on 2010-12-29
Edit: [SOLVED]

Hello, I cannot get my ALC888 internal sound on Ubuntu 10.10 to output sound to my Rear Left and Right Speakers which are plugged into the black colored port labeled "rear" at the back of my HP aa6734f Pavilion Desktop.  Can someone please assist me further.  Sorry for the bad formating.

I have followed the instructions on the following threads:

> Comprehensive Sound Problem Solutions Guide v0.5e (t=205449)
AlsaScript Upgrade (t=6589810)
snd_hda_intel options database (t=1043568 )"**speaker-test -Dplug:surround51 -c6 -l1 -twav**" produces sounds only on Front Left and Right ignoring my Rear speakers.

Note that the Hardware Tab under Sound Preferences lists my Internal audio as having only one output set to 4.1 Analog surround Output.

"**uname -r**" == "**2.6.35-24-generic**"
"**cat /proc/asound/version**" == "**Advanced Linux Sound Architecture Driver Version 1.0.23.**"

Also note that Hp says I have the ALC888 chip-set while "**aplay -l**" claims otherwise. (ALC1200).  Indications are however that my system is using the snd-hda-intel driver for sound.

I have tried the following options in ***/etc/modprobe.d/alsa-base.conf***

[B]options snd-hda-intel model=6stack-dig probe_mask=1
options snd-hda-intel model=6stack-hp[/B]

Rebooting each time with "sudo shutdown -r 0"

In troubleshooting I used Synaptic to install "**linux-backports-modules-alsa-maverick-generic**" and again a reboot did not solve my problem.

> Following are my "aplay -l" outputs

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0> 
Outputs from "cat /proc/asound/card0/codec#* | grep Codec"

Codec: Realtek ALC1200

Not the ALC888 that HP says my a6734f Desktop uses.alsamixer is set for 100% on everything except Mic, Mic_Boost and Beep.

> When upgrading alsa as per instructions from t=6589810 

sudo ./AlsaUpgrade-1.0.23-2.sh -d was successfull but
sudo script -a -c "./AlsaUpgrade-1.0.23-2.sh -c" ../AlsaUpgrade-1.0.23-2_c.log

Produced:
...
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed
***************************************************************************
Script done, file is ../AlsaUpgrade-1.0.23-2_c.log
miek@miek-FQ618AA-A2L-a6734f:~/Documents/Tshooting/AI figure that the new driver was not able to compile.

I am now at a stand still, I do however suspect something to do with jack detection because my front speakers are plugged into the lime green jack while the back set is pluged into the black jack labled rear.  And sound preferences indicate one output, should that not say two?

I am a Newbie (TM) as you could probably ascertain so please be gentle, after all I did try relay hard to document my steps.

---

### Post by miekrand on 2010-12-29
Ok well I have since solved the problem, I think that all that was necessary is me writing about my problem and having a relaxer.  My solution was simple, the output and input jacks at the back of my bass speaker box was inverted.  I had the input going to the left and right rear speakers and the output going to my computer.  It really should have darned on me that the problem only occurred after moving my room around.

Lesson learned.  I still don't know why the AlsaUpgrade script fails to compile however so if you still want to help you could help me to get that script working so I can keep alsa updated.

---

