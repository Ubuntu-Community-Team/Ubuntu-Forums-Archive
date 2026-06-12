---
title: "HDMI Audio out is skipping/distorted on NVIDIA GeForce 7100 / nForce 630i"
date: 2013-10-31
forum: Multimedia Software
---

### Post by uzair.rock on 2013-10-31
Hi guys,

I recently installed ubuntu 13.10 on PC with ASUS P5N -EM HDMI Motherboard. It is running with 4GB Ram and Core 2 duo processor. My setup is that My PC is connected to my LG LED TVs HDMI Port for Video and Audio. I performed a clean installation followed by the following steps to install the latest nVidia video drivers:

- sudo apt-add-repository ppa:xorg-edgers/ppa

- sudo apt-get update

- sudo apt-get install nvidia-current nvidia-settings

- sudo reboot

Once rebooted the system cam up very smoothly without any errors. Next I unmuted the S/PDIF in the alsamixer menu. After doing that i went in *Settings --> Sound --> Selected "HDMI/Display Port"* as default sound device.
After doing that I went into youtube.com to play a video to test the audio. I was able to hear audio but it was _**"skipping" and "distorted"**_.
Now I am confused on what should I do next and the right thing to make my audio work properly without any skipping or distortion. I have several methods mentioned over the internet but someway messed up my configuration and ended up re-installing Ubuntu 13.10.

Following is the output aplay -l command:

[COLOR=#696969][I]uzair@Uzair-Ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
uzair@Uzair-Ubuntu:~$ [/I][/COLOR]

[COLOR=#696969][I]uzair@Uzair-Ubuntu:~$ uname -a
Linux Uzair-Ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/I][/COLOR]

Please let me know if you require output of any command or any more information to help me out on this as I am almost there to setup my ubuntu PC completely. Thanks!!

---

### Post by Yellow Pasque on 2013-10-31
Tried this? [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by uzair.rock on 2013-10-31
I havent, I will try it today and will get back to you with the results.

---

### Post by uzair.rock on 2013-10-31
So the above did not solve my problem. I noticed that the video is running smoothly but the audio is skipping i.e. audio -- gap -- audio -- gap --audio -- gap.... Is there any codec issues?

---

### Post by Yellow Pasque on 2013-10-31
Did you reboot after making the change?

---

### Post by uzair.rock on 2013-10-31
[FONT=arial]Yes rebooted exactly the way it said in the instructions. 

- added the first line in /etc/modprobe.d/alsa-base.conf file[/FONT][FONT=arial]*options snd-hda-intel position_fix=1 *
rebooted

It didnt work so I removed the above line and added the below one:

[I]options snd-hda-intel position_fix=1
rebooted[/I]

This didnt work as well, so I changed the line in /etc/pulse/default.pa to:

from 
*load-module module-udev-detect*[/FONT][FONT=arial]to 
[/FONT]
[FONT=arial]*load-module module-udev-detect tsched=0*

rebooted.

Still the same issue.
[/FONT]

---

