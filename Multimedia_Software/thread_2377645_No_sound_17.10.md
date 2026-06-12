---
title: "No sound 17.10"
date: 2017-11-15
forum: Multimedia Software
---

### Post by abader on 2017-11-15
I tried the generic troubleshooting but nothing works. I was excited to see a recent "solved" forum post on this exact topic. Unfortunately the solution of rebooting a few times has not proven to work for me. This is a new work machine, built by the local expert in our group (although not a Linux expert so to speak). It dual boots in windows and ubuntu.  Sound works fine in windows, so I'm pretty sure it's a linux interface problem. I'm new to ubuntu, having used opensuse for the last 5 or so years, and fedora redhat before then.    

Here's the diagnostic information: 
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


     information from alsa-project is here:  [http://www.alsa-project.org/db/?f=a81e35cfebee392ab2cafd63e8279f5121d1c4ba](http://www.alsa-project.org/db/?f=a81e35cfebee392ab2cafd63e8279f5121d1c4ba)

---

### Post by Yellow Pasque on 2017-11-15
```
snd_hda_intel: model=pch position_fix=1
snd_hda_intel: single_cmd=1
snd_hda_intel: probe_mask=1
snd_hda_intel: model=basic

```

Is it possible to remove these lines and get the info again? Were any of them necessary to get the device to show up in aplay, or were you just adding them because you thought it would solve your issue?

---

### Post by abader on 2017-11-16
The lines were not necessary to show up in aplay. They were one of the  things that I saw online somewhere that fixed the problem for someone. I  also updated the kernel to 4.14, but that didn't solve the issue  either.

Here's the new output from alsa:

[http://www.alsa-project.org/db/?f=816fde39983b087bf8476dc7683d6eb8c9405d8d](http://www.alsa-project.org/db/?f=816fde39983b087bf8476dc7683d6eb8c9405d8d)

Thanks for your help.

---

### Post by Yellow Pasque on 2017-11-16
It seems folks are having issues with these Creative codecs under both Windows and Linux: [http://forum.gigabyte.us/thread/775/gigabyte-aorus-z270x-gaming-problem](http://forum.gigabyte.us/thread/775/gigabyte-aorus-z270x-gaming-problem)

Have you tried headphones in the front jack (assuming you connected the case's HD Audio plug into the mobo)?

---

### Post by abader on 2017-11-16
I tried both the front headphone jack and the back jack. Neither produced any sound under linux, but both work in Windows. So I'm pretty sure at least that the sound card works and that the front jack is connected correctly.

---

### Post by attobot on 2017-11-22
Does this output any sound? 
**aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv **

Is there any error when you start pulseaudio?
** start-pulseaudio-x11**

---

### Post by abader on 2017-11-27
[B]aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv


[/B]does not output any sound, I can post output if that would help.[B]

start-pulseaudio-x11

[/B]produces: 
Failure: Module initialization failed 

But it produces no error message when I run under sudo, i.e.

 **sudo start-pulseaudio-x11**

---

### Post by llanitedave on 2017-12-02
I'm having a similar issue.  I've tried it on both Ubuntu and Kubuntu, in version 17.10.  When I click on the audio icon, the message is "No output or input devices found".

My aplay -l command gives similar results to that of the OP.  I went to synaptic and re-installed every file associated with pulseaudio, but it made no difference.

One difference is that when I do the start pulseaudio, the feedback is 

[FONT=monospace][COLOR=#000000]Connection failure: Connection refused[/COLOR]
pa_context_connect() failed: Connection refused


If I had any more hair, I'd pull it out.[/FONT]

---

### Post by attobot on 2017-12-04
> **llanitedave said:**
> I'm having a similar issue.  I've tried it on both Ubuntu and Kubuntu, in version 17.10.  When I click on the audio icon, the message is "No output or input devices found".

My aplay -l command gives similar results to that of the OP.  I went to synaptic and re-installed every file associated with pulseaudio, but it made no difference.

One difference is that when I do the start pulseaudio, the feedback is 

[FONT=monospace][COLOR=#000000]Connection failure: Connection refused[/COLOR]
pa_context_connect() failed: Connection refused


If I had any more hair, I'd pull it out.[/FONT]

I had the same error when trying to start pulseaudio and  I have fixed the issue by editing /etc/pulse/default.pa to load the drivers statically and on my system I had to change hw:1,0 with hw:0,0

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
load-module module-alsa-sink device=hw:0,0
load-module module-alsa-source device=hw:0,0
load-module module-null-sink
load-module module-pipe-sink

Then executed

```
sudo alsa force-reload  
pulseaudio -k  
start-pulseaudio-x11 
```

---

