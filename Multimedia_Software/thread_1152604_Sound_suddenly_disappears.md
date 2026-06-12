---
title: "Sound suddenly disappears"
date: 2009-05-08
forum: Multimedia Software
---

### Post by alikebabay on 2009-05-08
I was just playing Counter Strike 1.6, which I have got installed using WINE (newest version). In Counter Strike I use Alsa as an audio system. Sound has gone...
However there is sound in flash, I have it when I open youtube videos. I am not sure Counter Strike is a reason, as this problem would pop out even without me playing it. Reboot usually solves this problem, however I would like to know if there is a simpler solution. 
My system: Ubuntu 8.04 on Sony Vaio FZ21M. Dual boot with Windows Vista.
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
Regards.

---

### Post by coleyman on 2009-05-08
I was going through some of the same things with Ubuntu 8. I could listen to movies or wav or mp3 just fine. Then if I watched something on Youtube, it worked, but when I'd try to listen to mp3s and all, there would be no sound until I rebooted. Just messing around with Jack, I found that when it did that, I could go into setup and change the device preset from default to Ubuntu, then click on "start" on Jack, then click on "stop" on Jack and the sound would work again, as long as I just minimized Jack instead of quitting it. If I hit "quit", the sound wouldn't work. Drove me crazy. Never figured it out, but did a clean upload of Ubuntu 9 and everything works great. Just checked setup on Jack and it only has the default preset, not the Ubuntu preset. Go figure.

---

### Post by alikebabay on 2009-05-08
Jack is an editing software? Any solutions for the whole system? I hate to reboot every time I am out of sound. 9 has trouble with nvidia card btw, my one never works, so I stick to 8.04.

---

### Post by alikebabay on 2009-05-08
I have found the solution:
All I needed to do is to go in the terminal and type:
killall pulseaudio
This will let other programms access the sound.
Source:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/236052](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/236052)
Hope it will help other people as well.

---

