---
title: "Webcam Logitech C310 &amp; Skype"
date: 2011-02-15
forum: Multimedia Software
---

### Post by merinette on 2011-02-15
Hi there,

I'm having problems getting my Logitech C310 webcam to work with Skype(latest/2.1.0.81) in Kubuntu. I have video in Cheese. Skype detects the camera but I have no audio or video; also no audio or video in flash chat. Can anyone help me diagnose and solve this problem? 

merinette@merinette-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid
merinette@merinette-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:2f11 Hewlett-Packard PSC 1200
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 002: ID 045e:00b8 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 046d:081b Logitech, Inc. <!-- webcam -->
Bus 001 Device 006: ID 05e3:0716 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by lukeiamyourfather on 2011-02-15
Does it work in other applications, like Cheese? I'd start there so you know if this is a Skype problem or a larger problem.

---

### Post by merinette on 2011-02-15
Yes, I have video in Cheese. Also, after uninstalling a package that was conflicting with PulseAudio, the camera has audio and video in Skype on my Lenovo laptop running Kubuntu 10.04. So, it's not the camera. Thanks though :)

---

### Post by lukeiamyourfather on 2011-02-15
For some reason I read your first post as video in Chinese, I don't know why... ):P

---

### Post by vbjornsson on 2011-02-23
> **merinette said:**
> Yes, I have video in Cheese. Also, after uninstalling a package that was conflicting with PulseAudio, the camera has audio and video in Skype on my Lenovo laptop running Kubuntu 10.04. So, it's not the camera. Thanks though :)

Just curious, what package did you uninstall? I just got the C310 and video works in Cheese but when I do a test call in Skype, theres no audio.

How could I test the audio outside of Skype?

---

### Post by vbjornsson on 2011-02-23
Nevermind, figured it out.

All I had to do was going into System/Preferences/Sound/Input and choose the Analog Mono option. Doh!

---

### Post by jlinkels on 2011-03-25
Can someone PLEASE mention the name of the package that had to be uninstalled? I have video in MPlayer, not in Skype 2.1 Beta.

jlinkels

---

