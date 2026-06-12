---
title: "Shut down with sound muted, now it's gone"
date: 2011-05-24
forum: Multimedia Software
---

### Post by thedolphindude on 2011-05-24
I've seen loads of threads about this sound issue, and I've experienced/fixed it before (after HOURS of searching), but this time it's worse. I'm running Maverick. I accidentally muted my sound and shut down with it muted. Upon restart, no sound is present through headphones, speakers, anything. The sound card still shows up in the options. Sound also has been disabled on my LIVE DISC OF 11.04#-oThese sound problems are the absolute worst part of Ubuntu. I'm almost ready to jump ship back to...vista *shudder*

---

### Post by papibe on 2011-05-24
Try to unmute them with [alsamixer]("http://alsa.opensrc.org/Alsamixer"). Check [this]("http://www.patheticcockroach.com/mpam4/index.php?p=62").

Run it like this:
```
$ alsamixer
```
Unmute the speakers, test them. When you get the results you're going for, save the settings like this:
```
$ alsactl store
```
Regards.

---

### Post by thedolphindude on 2011-05-24
I've already checked that; it's definitely not the problem. everything is unmuted.

---

### Post by papibe on 2011-05-24
I understand that you are dual booting with Windows? An idea would be to boot on Windows and check what's going on there. Maybe you can solve it there (better sound drivers), or can confirm a hardware problem.

Just an idea.
Regards.

---

### Post by thedolphindude on 2011-05-24
Everything works correctly in windows.

---

### Post by lidex on 2011-05-24
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by thedolphindude on 2011-05-24
Lidex, here's the link:
[http://www.alsa-project.org/db/?f=7a77f74e5b32d3d7b43f1f3f6c8b82dd2a4f0201](http://www.alsa-project.org/db/?f=7a77f74e5b32d3d7b43f1f3f6c8b82dd2a4f0201)

---

### Post by lidex on 2011-05-25
Have you tried a suspend/resume cycle?
You have four devices, which are you using for output? Onboard analog, digital, hdmi, or the soundblaster?

---

### Post by thedolphindude on 2011-05-25
I have done multiple suspend/resume cycles. I use the sound blaster.

---

### Post by lidex on 2011-05-25
See this:
[http://ubuntuforums.org/showpost.php?p=10784896&postcount=38](http://ubuntuforums.org/showpost.php?p=10784896&postcount=38)

Also add this to alsa-base.conf:
```
alias snd-card-0 snd-ca0106
alias sound-slot-0 snd-ca0106
alias snd-card-1 snd-hda-intel
alias sound-slot-1 snd-hda-intel
```

To edit:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by thedolphindude on 2011-05-25
It's still not working.

---

### Post by lidex on 2011-05-25
Post these outputs please:
```
aplay -l
```
```
amixer
```

---

### Post by thedolphindude on 2011-05-25
Here's aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And here's amixer
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 19 [61%] [-18.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
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
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
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
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
```

---

### Post by lidex on 2011-05-25
Did you reboot? Alsa is defaulting to your onboard audio. Try disabling it in bios.

---

### Post by thedolphindude on 2011-05-25
I disabled the onboard audio in the BIOS and there's still no sound. Here's the new aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And here's the new amixer:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 255
  Mono: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Line in',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 255 [100%] [24.00dB]
  Front Right: Capture 255 [100%] [24.00dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB]
  Front Right: Playback 207 [81%] [0.00dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB]
  Front Right: Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 207 [81%] [0.00dB] [on]
  Front Right: Playback 207 [81%] [0.00dB] [on]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Mic'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: cenum
  Items: 'Line in' 'Mic in'
  Item0: 'Mic in'
```

---

### Post by lidex on 2011-05-25
See this:
[http://ubuntuforums.org/showpost.php?p=10784896&postcount=38](http://ubuntuforums.org/showpost.php?p=10784896&postcount=38)

---

### Post by thedolphindude on 2011-05-25
When I open alsamixer, that switch isn't there.

---

### Post by lidex on 2011-05-26
Try gnome-alsamixer
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

---

### Post by thedolphindude on 2011-05-27
Alright, I did a bit of hunting, and found out that the switch I needed is called IEC95. Turned it off, and everything worked. Thanks!

---

