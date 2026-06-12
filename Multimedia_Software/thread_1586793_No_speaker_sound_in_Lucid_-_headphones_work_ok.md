---
title: "No speaker sound in Lucid - headphones work ok"
date: 2010-10-02
forum: Multimedia Software
---

### Post by joham34 on 2010-10-02
hello everybody 
I have bought a laptop 2 months ago with pre installed windows7 and installed Ubuntu 10.04 64bit but still didnt get sound from the speakers. With headphones everything is OK . I have unmuted everything and searched forums but nothing so far. In windows I get speaker sound so it is not hardware problem. In alsamixer it appears I have 2 soundcards, one HDA -intel (chip Realtek ALC272) and a second one HDA nvidia ( a virtual one propably from my nvidia VGA ) that lacks controls . With lspci -v , it appears both use the same driver :	Kernel driver in use: HDA IKernel modules: snd-hda-intel . Tried to disable the first one from bios but it didnt help I also tried sound adjustment in preferences -> sound and gnome-alsamixer, nothing 
From gnome alsamixer, when I mute speakers, the headphones also get mute so may be the system doesnt recognize speakers and headphones separately ?
May be it has to do with config files but my linux knowledge is low , so please help!

---

### Post by lidex on 2010-10-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by joham34 on 2010-10-03
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

thank you for you immediate reply 
Well ```
:wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh :
```

```
Your ALSA information is located at http://www.alsa-project.org/db/?f=4dcab3fbc2e765bc8b2b8a1a1067d39d911ac8f1
```

---

### Post by lidex on 2010-10-03
Remove your config files:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf /etc/modprobe.d/alsa-base.conf
```
Now re-install alsa:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
Report your results.

---

### Post by joham34 on 2010-10-03
> **lidex said:**
> Remove your config files:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf /etc/modprobe.d/alsa-base.conf
```
Now re-install alsa:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
Report your results.



I did . ~/.asound and /etc/asound.conf files did not exist , the others 2 did . Unfortunately the problem persists , nothing has changed. What to do now ?

---

### Post by Pablo_F on 2010-10-03
You "amixer" output says:

Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: **Playback 0 [0%] [-64.00dB]** [on]
  Front Right: **Playback 0 [0%] [-64.00dB]** [on]


Run in a terminal:

alsamixer 

and rise the level of the Front channels. 

What is your laptop model?

---

### Post by joham34 on 2010-10-03
It is a Turbo-X laptop ( a small Greek company) 
I have raised the level of the front channels , by default for some reason when rebooting speaker level was to 0 and I had to raise the volume level every time. Though, this didnt gave any sound . Now , amixer returnes
 
```

```amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 57 [89%] [-7.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 61 [95%] [-3.00dB] [on]
  Front Right: Playback 61 [95%] [-3.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 61 [95%] [-3.00dB] [on]
  Front Right: Playback 61 [95%] [-3.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 242 [95%] [-2.60dB]
  Front Right: Playback 242 [95%] [-2.60dB]```

```
and yet I get only headphone sound 
Any idea?

---

### Post by Pablo_F on 2010-10-03
Try the following:

sudo gedit /etc/modprobe.d/alsa-base.conf

At the end of the file, add the line:

options snd-hda-intel model=auto


And reload the alsa modules with:

sudo alsa force-reload

or just reboot the computer.


Cheers! Pablo

---

### Post by joham34 on 2010-10-03
> **Pablo_F said:**
> Try the following:

sudo gedit /etc/modprobe.d/alsa-base.conf

At the end of the file, add the line:

options snd-hda-intel model=auto


And reload the alsa modules with:

sudo alsa force-reload

or just reboot the computer.


Cheers! Pablo

Dear Pablo thanks for your interest in helping me 
I did as you adviced but unfortunately nothing changed It is driving me crazy slowly and steadily  grrrrr

---

### Post by lidex on 2010-10-03
Please run the alsa-info script again.

Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by joham34 on 2010-10-03
ok, I did and got 
 Your ALSA information is located at [http://www.alsa-project.org/db/?f=d3742c5fcb37173377f706e8f6b52f1ffe7f0cc8](http://www.alsa-project.org/db/?f=d3742c5fcb37173377f706e8f6b52f1ffe7f0cc8)

Please inform the person helping you.

---

### Post by lidex on 2010-10-03
> **joham34 said:**
> ok, I did and got 
 Your ALSA information is located at [http://www.alsa-project.org/db/?f=d3742c5fcb37173377f706e8f6b52f1ffe7f0cc8](http://www.alsa-project.org/db/?f=d3742c5fcb37173377f706e8f6b52f1ffe7f0cc8)

Please inform the person helping you.

Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by sailorboy on 2010-10-03
It seems you have been told all the 'elaborate' checks - however if it hasn't become really jacked up- the solution I found for my new laptop that did this (I googled it) was to to install a small Synaptic package called 'audio backports plug-ins' or similar. It apparently needed a script to properly read the headphone jack 'status' to switch on the speakers. Good Luck!

---

### Post by joham34 on 2010-10-04
OK :
```

```cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=auto```

```

---

### Post by joham34 on 2010-10-04
> **sailorboy said:**
> It seems you have been told all the 'elaborate' checks - however if it hasn't become really jacked up- the solution I found for my new laptop that did this (I googled it) was to to install a small Synaptic package called 'audio backports plug-ins' or similar. It apparently needed a script to properly read the headphone jack 'status' to switch on the speakers. Good Luck!

It sounds very reasonable to me. Could you please give me the exact name of the package?

---

### Post by Crazedpsyc on 2010-10-04
If none of that turns out well (or even if it does) try installing padevchooser (Pulse audio device chooser) and run it from Apps>Sound & Video>PulseAudio Device Chooser. It will open an applet in the top right. click it and select Volume Control. switch to the Output Devices tab and change the "Port: " to "Analog Speakers" (at least that's what mine says)

---

### Post by joham34 on 2010-10-04
Well at last ! I hear sound now after updating my alsa to 1.0.23 ( I got 1.0.21 when updating -upgrading from the terminal) . I followed the instructions here : [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Thank you all for your help

---

### Post by sailorboy on 2010-10-10
Well, checked back- appears solved but for others , it was called 'jacksense' audio backport plug-ins

---

