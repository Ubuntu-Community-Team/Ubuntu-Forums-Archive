---
title: "Microphone not recording"
date: 2011-06-21
forum: Multimedia Software
---

### Post by nychng on 2011-06-21
Hi all,

**Problem:**
I can hear myself speak in the mic but Ubuntu is not recording/capturing the sound.  

**Actions Taken:**
I followed all the steps listed [here]("http://ubuntuforums.org/showthread.php?t=1681577") for the Alsa update script

I've also tried changing my **/etc/modprobe.d/alsa-base.config** file with the following configurations one at a time.

```
options snd-hda-intel model=auto
options snd-hda-intel model=acer
options snd-hda-intel model=3stack
options snd-hda-intel model=generic
```

I am at a loss of what to do. Thanks for your time.

**Other info:**

Im running Ubuntu Natty Narwahl dual booted with Win7 on a Acer Aspire 5542G laptop. 

```
cat /proc/asound/card0/codec#* | grep Codec

Codec: Realtek ALC888
Codec: Conexant ID 2c06
```

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```

ls -l /dev/snd

drwxr-xr-x  2 root root       80 2011-06-21 20:51 by-path
crw-rw----+ 1 root audio 116,  8 2011-06-21 20:51 controlC0
crw-rw----+ 1 root audio 116, 11 2011-06-21 20:51 controlC1
crw-rw----+ 1 root audio 116,  7 2011-06-21 20:51 hwC0D0
crw-rw----+ 1 root audio 116,  6 2011-06-21 20:51 hwC0D1
crw-rw----+ 1 root audio 116, 10 2011-06-21 20:51 hwC1D0
crw-rw----+ 1 root audio 116,  5 2011-06-21 21:34 pcmC0D0c
crw-rw----+ 1 root audio 116,  4 2011-06-21 21:56 pcmC0D0p
crw-rw----+ 1 root audio 116,  3 2011-06-21 21:34 pcmC0D1p
crw-rw----+ 1 root audio 116,  2 2011-06-21 20:51 pcmC0D2c
crw-rw----+ 1 root audio 116,  9 2011-06-21 21:34 pcmC1D3p
crw-rw----+ 1 root audio 116,  1 2011-06-21 21:34 seq
crw-rw----+ 1 root audio 116, 33 2011-06-21 20:51 timer

```

My capture settings are 'on' in alsamixer as in they are in red with the words CAPTURE underneath it.

---

### Post by nychng on 2011-06-22
Anyone please?

---

### Post by kkrueger on 2011-06-22
Hey
    It sounds like the microphone is just working fine, but if you want to be recording yourself are you using a program/utility to do so?

---

### Post by nychng on 2011-06-26
It doesnt work in Skype or sound recorder for instance.

---

### Post by lidex on 2011-06-26
> I've also tried changing my /etc/modprobe.d/alsa-base.config file with the following configurations one at a time.
It's actually alsa-base.conf although I think alsa, at least for now, reads everything in that directory.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by nychng on 2011-06-26
> **lidex said:**
> It's actually alsa-base.conf although I think alsa, at least for now, reads everything in that directory.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

This is the link to the output [http://www.alsa-project.org/db/?f=50c1e4993a5ee7c65be71e614f463753b6ebbd0b]("http://www.alsa-project.org/db/?f=50c1e4993a5ee7c65be71e614f463753b6ebbd0b")

Thanks for replying!

---

### Post by lidex on 2011-06-27
```

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture [COLOR="Red"]8[/COLOR] [26%] [-4.50dB] [on]
  Front Right: Capture [COLOR="Red"]8[/COLOR] [26%] [-4.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Line'
  Item0: [COLOR="Red"]'Mic'[/COLOR]  
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: [COLOR="Red"]0[/COLOR] [0%] [0.00dB]
  Front Right: [COLOR="Red"]0[/COLOR] [0%] [0.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
 [COLOR="Red"] Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB][/COLOR]
```
You should try tweaking the values in red above. 
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

---

### Post by nychng on 2011-06-27
> **lidex said:**
> ```

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture [COLOR="Red"]8[/COLOR] [26%] [-4.50dB] [on]
  Front Right: Capture [COLOR="Red"]8[/COLOR] [26%] [-4.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Line'
  Item0: [COLOR="Red"]'Mic'[/COLOR]  
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: [COLOR="Red"]0[/COLOR] [0%] [0.00dB]
  Front Right: [COLOR="Red"]0[/COLOR] [0%] [0.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
 [COLOR="Red"] Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB][/COLOR]
```
You should try tweaking the values in red above. 
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

There are 3 devices to choose from on the 'Input Devices' tab. 
Analog Microphone, Analog Line-in and Internal Microphone. I tried each one to no avail.

I've maxed out all the volume settings for gnome-alsa mixer as well. 

Still doesn't work I'm afraid.

---

### Post by lidex on 2011-06-27
> **nychng said:**
> There are 3 devices to choose from on the 'Input Devices' tab. 
Analog Microphone, Analog Line-in and Internal Microphone. I tried each one to no avail.

I've maxed out all the volume settings for gnome-alsa mixer as well. 

Still doesn't work I'm afraid.

What is your amixer output now:
```
amixer
```

---

### Post by nychng on 2011-06-28
> **lidex said:**
> What is your amixer output now:
```
amixer
```

```
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Line'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Line'
  Item0: 'Line'
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]

```

[IMG]http://imgur.com/xr1ed.png[/IMG]

---

### Post by lidex on 2011-06-29
Change this one to internal mic:
```
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Line'
  Item0: 'Line'
```

---

### Post by nychng on 2011-07-03
> **lidex said:**
> Change this one to internal mic:
```
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Line'
  Item0: 'Line'
```

I've tried all different combinations including internal mic and it didnt work.

---

### Post by Arthur Millar on 2011-07-31
I am using an Aspire 5542G with similar mic problems.

in ubuntu sound preferences under input tab, there is only one device the "Internal Audio Analog Stereo".
There is also an option to select 3 devices from Connector: Line-in , Microphone 1, Microphone 2.

Line-in and Mic1 are jack inputs,
microphone 2 is the Internal Mic, and it works 
until I activate the webcam. 

any help would be appreciated

---

### Post by lidex on 2011-08-17
> **Arthur Millar said:**
> I am using an Aspire 5542G with similar mic problems.

in ubuntu sound preferences under input tab, there is only one device the "Internal Audio Analog Stereo".
There is also an option to select 3 devices from Connector: Line-in , Microphone 1, Microphone 2.

Line-in and Mic1 are jack inputs,
microphone 2 is the Internal Mic, and it works 
until I activate the webcam. 

any help would be appreciated

Internal or external webcam?

---

