---
title: "Black screen in Webcam in xubuntu 13.04(Asus k50af)"
date: 2013-08-22
forum: Multimedia Software
---

### Post by rusik on 2013-08-22
Hi all, i have a black screen or fast slow image(one per 3-4 minutes for example in cheese or skype) and can't fix it : 
**I tried to download and install the latest UVC driver from** [here]("http://git.linuxtv.org/media_build.git") but it doesn't help 
[B]Also , i tried
lslub:(doesn't show camera)[/B]
> Bus 002 Device 002: ID 13d3:5130 IMC Networks 
Bus 004 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[B]but shows here :
cat /proc/bus/input/devices | grep Name[/B]
> N: Name="Lid Switch"
N: Name="Sleep Button"
N: Name="Power Button"
N: Name="Power Button"
N: Name="AT Translated Set 2 keyboard"
N: Name=" USB OPTICAL MOUSE"
N: Name="Asus Laptop extra buttons"
N: Name="Video Bus"
N: Name="HDA ATI SB Mic"
N: Name="HDA ATI SB Headphone"
**N: Name="USB 2.0 Camera"**
N: Name="ETPS/2 Elantech Touchpad"

What can be a problem? Please, help , i can't find the decision!:confused:
(And of'course , it work's fine on windows:()

---

