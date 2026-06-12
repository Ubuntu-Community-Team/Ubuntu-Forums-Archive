---
title: "Sound output redirects to input"
date: 2011-06-09
forum: Multimedia Software
---

### Post by Daneel.Olivaw on 2011-06-09
Ok this is driving me mad. I'm just over a month old in this ubuntu thingy so please bear with me. 
For some reason my soundcard is recording every playback sound. This become apparent when I was trying to make a Skype call and the other people couldn't hear me. I checked my sound preferences and noted that the input was recording what they say (they could hear an echo). Also if I played back anything it would redirect to them. This has never happened to me and I've made a lot of calls in the past. 

I tested with Audacity and it records fine, but when I play back the recording, it redirects to the input channel so it's not a problem with Skype. 

Please tell me which information I should post here (my soundcard is a VIA VT1708B 8-Ch). Somewhere I read that the output of aplay -l is useful. Here it is:

tarjeta 0: Intel [HDA Intel], dispositivo 0: VT1708B Analog [VT1708B Analog]
  Subdispositivos: 2/2
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
tarjeta 0: Intel [HDA Intel], dispositivo 1: VT1708B Digital [VT1708B Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Thanks in advance!

---

### Post by lidex on 2011-06-09
What is your amixer output:
```
amixer
```

---

### Post by Daneel.Olivaw on 2011-06-10
There may also be otherThis:

```

Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.50dB] [on]
  Front Right: Playback 25 [81%] [3.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-40.25dB] [on]
  Front Right: Playback 31 [100%] [14.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 27
  Mono: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [0.00dB] [on]
  Front Right: Playback 27 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [10.50dB] [on]
  Front Right: Playback 29 [94%] [10.50dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.50dB] [on]
  Front Right: Playback 25 [81%] [3.50dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 14 [70%] [24.50dB] [on]
  Front Right: Capture 14 [70%] [24.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 13 [65%] [22.75dB] [off]
  Front Right: Capture 13 [65%] [22.75dB] [off]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Rear Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Rear Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [14.00dB] [off]
  Front Right: Playback 31 [100%] [14.00dB] [off]
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
```

---

### Post by lidex on 2011-06-10
Could you enclose that in code tags please? Use the # in editing toolbar.

---

### Post by Daneel.Olivaw on 2011-06-10
Ups. Sorry. Edited.

---

### Post by Daneel.Olivaw on 2011-06-11
Bump!

---

### Post by lidex on 2011-06-12
Yeah, not as easy as I thought it might be. Need a little more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Daneel.Olivaw on 2011-06-12
Thanks for your time :) Here's the link:

[http://www.alsa-project.org/db/?f=85e334a4c460f0456437a785f6fabed083ca13b6](http://www.alsa-project.org/db/?f=85e334a4c460f0456437a785f6fabed083ca13b6)

---

### Post by lidex on 2011-06-12
Try changing your input using alsamixer:
```
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Rear Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Rear Mic'
```

---

### Post by Daneel.Olivaw on 2011-06-12
In alsamixer I seem to have "rear mic" as my input:

[IMG]http://i.imgur.com/lBs9S.png[/IMG]

But I'm still getting the same feedback.

---

### Post by Daneel.Olivaw on 2011-06-12
Bump again :(

---

### Post by lidex on 2011-06-13
Toggle the right-hand option using up/dn arrow keys.

---

### Post by Daneel.Olivaw on 2011-06-13
I've been trying. I have "CD", "Line", "Front Mic", "Rear Mic" and "Stereo mixer". Of course the only setting that allows me to record is "rear mic" since my microphone is connected to that plug. But in every option it repeats the same behaviour (except "CD".. and "Line" seems to redirect a lower volume signal). 

As a reference here's how it looks:

[IMG]http://i.imgur.com/opfXV.png[/IMG]

"1º rec" was me saying "hello". "2º rec" is the result of just recording with playback (no input from mic). As you can see, it records what it's playing. 

This is puzzling.


PS: Again, thank you for your time :)

---

### Post by lidex on 2011-06-14
I guess it could be pulseaudio. 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Daneel.Olivaw on 2011-06-14
Thanks, but regrettably it didn't work. 
Could it be that I have some other utility messing things up? I could remove all audio utilities and reinstall only the essential. I don't know if that would help, though. If you think it's worth the try, just tell me which apps should I install.

---

### Post by lidex on 2011-06-15
If you don't have paprefs (pulse audio preferences) installed, get it and check config options there:
```
sudo apt-get install paprefs
```
Look for the launcher in your System > Preferences menu.

---

### Post by Daneel.Olivaw on 2011-06-16
Yep. It's installed. No option is activated, though.

---

