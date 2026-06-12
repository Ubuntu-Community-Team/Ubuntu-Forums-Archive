---
title: "HDMI Sound Issue"
date: 2010-05-08
forum: Multimedia Software
---

### Post by daxer on 2010-05-08
Hello, 

I've been tearing my hair out with a sound issue I'm having. I've recently built a small media PC using an ASUS AT3IONT-I motherboard. 

I have installed ubuntu 10.4 with no problems apart from the lack of any audio through the hdmi output. I have checked that the volumes are up and everything is unmuted in alsamixer - various guides say I should be looking for a IE958 switch, but there isn't one in alsamixer.

The sound configuration is set to use 'Digital Stereo (HDMI) Output'.

I tried performing an alsa upgrade as shown in a guide on this form, which completed without a problem, but didn't provide me with sound. I've since done an apt-get remove alsa & pulseaudio and installed them since with no joy. 

Here's the output from aplay:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

If anyone has any ideas I'd really appreciate it!

---

### Post by daxer on 2010-05-08
Any idea on this one? :(

Thinking I might just send back the mobo and get something else.

---

### Post by lidex on 2010-05-08
Since you re-installed alsa you went back to the original lucid version. Your best bet for hdmi support, especially with nvidia, is an upgrade to the latest available, 1.0.23

First make sure your system is upgraded to the latest kernel.
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.

Use the edit in this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")
and the link provided.

---

