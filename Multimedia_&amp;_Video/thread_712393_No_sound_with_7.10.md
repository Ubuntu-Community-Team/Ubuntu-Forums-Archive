---
title: "No sound with 7.10"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by gwatts on 2008-03-01
Dual boot Ubuntu 7.10 with Vista on laptop.

I installed some intel package.

sudo apt-get install linux-ubuntu-modules-2.6.22-14-386 
sudo modprobe snd-hda-intel
Now I get:
gg@linux2:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

gg@linux2:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

gg@linux2:~$ asoundconf list

Names of available sound cards:

Intel

gg@linux2:~$ NVidia

bash: NVidia: command not found

gg@linux2:~$ asoundconf set-default-card intel

gg@linux2:~$ lspci | grep -i audio

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

gg@linux2:~$ lspci | grep -i audio

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev

The purchase order indicates a NVIDA GF 8600M.

MP3s play  but no sound.

Any advice will be appreciated.

---

### Post by carking on 2008-03-01
I dont have any sound on my computer either 
I read this post and decided to try installing
 apt-get install linux-ubuntu-modules-2.6.22-14-386 
and it messed up my screen resulation how can I uninstall this.

thanks

:confused::(:mad:

---

