---
title: "Mic doesn't work Conexant CX20561 (Hermosa)"
date: 2012-01-13
forum: Multimedia Software
---

### Post by alfaceor on 2012-01-13
Hi people
I need some help to solve this problem, i can't make work the microphone in my laptop toshiba satellite M305D-S4829 this is the information

```

shentasa@rosaveronica:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid

shentasa@rosaveronica:~$ uname -a
Linux rosaveronica 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux

shentasa@rosaveronica:~$ grep "Codec:" /proc/asound/card*/codec*
Codec: Conexant CX20561 (Hermosa)

shentasa@rosaveronica:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

shentasa@rosaveronica:~$ sudo lshw -C multimedia
[sudo] password for shentasa: 
  *-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:17 memory:f0000000-f0003fff
shentasa@rosaveronica:~$ 


```

I already try the solution in this post.

[http://ubuntuforums.org/showthread.php?t=1472937&highlight=conexant+cx20561](http://ubuntuforums.org/showthread.php?t=1472937&highlight=conexant+cx20561)

ugrade the kernel and still doesn't work, help please :confused:

---

### Post by MoreOrLess on 2012-01-13
Add this line to your /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=toshiba
```
Reboot. Let me know if it works.

---

### Post by alfaceor on 2012-01-16
doesn't work :S

---

### Post by MoreOrLess on 2012-01-16
Okay, change the model to 'ideapad' instead of toshiba. Then:
```
sudo alsa force-reload
pulseaudio -k
```

---

### Post by alfaceor on 2012-01-25
Thanks for your replies but still not working, i seee in others post that this maybe help

So i run this script 

```
shentasa@rosaveronica:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh


```

And here is the url 
[http://www.alsa-project.org/db/?f=e44dbc5c0d013f1b22e13d3b5dcb3af74b6e7d22]("http://www.alsa-project.org/db/?f=e44dbc5c0d013f1b22e13d3b5dcb3af74b6e7d22")

Please any help would be really appreciated.

---

