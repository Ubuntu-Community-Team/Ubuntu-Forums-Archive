---
title: "Keyboard volume button - how to adjust increment"
date: 2011-01-22
forum: Multimedia Software
---

### Post by Ubuntered on 2011-01-22
I have a HP Model # (5187URF2+) keyboard and was wondering if there is way to adjust the increment of volume increase/decrease  when using the keyboard volume buttons. 
For example: if 0=mute and 100=max volume, my current setting would be equal to an increase of about 10. I would like to decrease this to around 2 if that makes sense :?:. I just can't seem to find that sweet spot when I use my keyboard to adjust the volume, its always to loud or to quiet. I went through the sound preferences and keyboard options but couldn't find anything to make that adjustment. Thanks 


Ubuntu 10.04 LTS
Keyboard HP Model#  5187URF2+

Hardware:

Internal Audio
*1 Output/ 1 Input*
*Analog Stereo Duplex*

Radeon HD 3870 Audio device
[I]1 Output
Digital Stereo (HDMI) Output[/I]

---

### Post by cozman69 on 2011-06-22
You are looking for this: 

[http://sprayfly.com/2009/06/01/ubuntu-change-volume-control-increments/](http://sprayfly.com/2009/06/01/ubuntu-change-volume-control-increments/)

> 
After a bit of research I found out that the size of volume increments can be changed in gconf-editor:

Alt + F2 –> gconf-editor
Apps –> gnome_settings_daemon –> volume_step

Change the volume step value to something more appropriate – the smaller the value the smaller the change in volume each time you hit the button.

---

### Post by Us1ingaeph on 2011-09-16
Hi, does anyone know how to achieve this in Ubuntu 11.04?

Thank you.

---

### Post by kid1000002000 on 2011-10-19
subscribe to this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133)

---

