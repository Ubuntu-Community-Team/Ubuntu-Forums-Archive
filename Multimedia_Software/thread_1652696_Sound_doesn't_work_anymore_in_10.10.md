---
title: "Sound doesn't work anymore in 10.10"
date: 2010-12-25
forum: Multimedia Software
---

### Post by Lykanthrop on 2010-12-25
Hi

I've got a very annoying problem since I updated my Kubuntu to maverick a few days ago.
The sound actually does work, but I don't get surround anymore and phonon as well as Kmix are detecting my soundcard as "Internal Audio Analog Stereo".
With Kubuntu 10.04 I never had these problems. Phonon showed my soundcard as "HDA Nvidia" and I could configure every single chanel in KMix (front, rear, pcm, lfe). Now KMix only shows one chanel, which is the masterchannel. No pcm or anything.
When I start alsamixer in terminal, it detects HDA Nvidia and I'm able to configure LFE, Front and so on (see screenshot). Sadly, wenn I change the volume with Kmix everything is reseted and again Front chanel is turned to 0 and LFE turned to 100. Very annoying.

Detecting my soundcard in terminal gives this result:
```
marc@marc:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xefff0000 irq 20

```

Codec is detected as following:
```
marc@marc:~$ head -n 1 /proc/asound/card0/codec* 
Codec: Analog Devices AD1988B

```

Also Kubuntu sometimes tells me, that it recognises "removed sound devices" where it lists my HDA Nvidia sounddevice. A bit strange, since I never removed it. (you can see this also an the screenshot)

What can I do, to get my surround sound back?

Thanks and Greets
Lykanthrop

---

### Post by lidex on 2010-12-25
Sounds like a regression. Let's try this and see what happens.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

You'll note the model is blank above as it relies on info I do not have. Here are your options:
```
AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack	6-jack
  6stack-dig	ditto with SPDIF
  3stack	3-jack
  3stack-dig	ditto with SPDIF
  laptop	3-jack with hp-jack automute
  laptop-dig	ditto with SPDIF
  auto		auto-config reading BIOS (default)
```

---

### Post by Lykanthrop on 2010-12-25
Already tried this. Didn't work for me. At least not with model=6stack, model=6stack-dig and model=auto... :(

---

### Post by lidex on 2010-12-25
> **Lykanthrop said:**
> Already tried this. Didn't work for me. At least not with model=6stack, model=6stack-dig and model=auto... :(

You have six audio jacks?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Lykanthrop on 2010-12-25
> **lidex said:**
> You have six audio jacks?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

I have 3 jacks. But 6 'slots' (I don't know the english word for it, hope you know, what I mean), so 3 of it with a jack in it and 3 empty.

Here's the link: [http://www.alsa-project.org/db/?f=4196ca7f13d9662659c1c95b0b450c7dda364c75](http://www.alsa-project.org/db/?f=4196ca7f13d9662659c1c95b0b450c7dda364c75)

---

### Post by lidex on 2010-12-25
If you only have 3 jacks, then 3stack is the correct option.

---

### Post by Lykanthrop on 2010-12-25
Well, I tried now with model=3stacks but this also didn't get my soundcard to work properly. Still nothing changed in KMix. When I go to systemsettings KDE shows a notification, that there were some audiodevices REMOVED and lists HDA Nvidia.

Still wondering, because in **alsamixer** **I am able to choose "HDA Nvidia"** and to adjust every chanel (but still annoying that alsamixer resets my adjustments at that time I change the volume with KMix).
Seems like Alsa detects my correct sounddevice but Phonon doesn't..

Here's my [FONT="Lucida Console"]/etc/modprobe.d/alsa-base.conf[/FONT]:
```
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

options snd-hda-intel model=3stack

```

And in the screenshot you can see, the error I receive, when I go into the Phonon/Audio-Settings.

---

### Post by Lykanthrop on 2010-12-26
Well, I solved the problem now by removing PulseAudio. Sound works fine, now.

---

### Post by lidex on 2010-12-26
> **Lykanthrop said:**
> Well, I solved the problem now by removing PulseAudio. Sound works fine, now.

That's good. Not sure why they're including pulseaudio in kubuntu now - didn't need it before. Sorry I wasn't of more help. I'm just not that familiar with kde.

---

### Post by Lykanthrop on 2010-12-26
> **lidex said:**
> That's good. Not sure why they're including pulseaudio in kubuntu now - didn't need it before. Sorry I wasn't of more help. I'm just not that familiar with kde.

Maybe you still can help me, without being familiar with KDE.
I just recognised, that the jacks have other slots under linux than under windows. For example the jack for the front speakers is in the red slot under windows, but in the green slot under Kubuntu. Oo

Not THAT bad, but a bit annoying since I have to change the jacks everytime I boot up the other system. Seems very bizarre to me... oO

If anyone has any idea, how to change this, I'd be very happy about it.. :/ In 10.04 the jacks always were the same as under win.

---

### Post by lidex on 2010-12-26
Sounds like a regression. My first thought is changing the model in alsa-base.conf and seeing how that affects the pinouts. Alsa seems to be selecting the auto model for you. It's likely not right. You can also try updating your alsa modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Another step is installing a later kernel from the mainline builds to see if it's corrected upstream. You can follow the procedure outlined here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by Viper1971 on 2011-04-02
Hi, I just wanted to say I had the same issue with my Audigy2 ZS card and followed the advice posted earlier and removed pulse audio, now my card and all its surround channels are seen and is working properly, thanks for the info. :)

---

