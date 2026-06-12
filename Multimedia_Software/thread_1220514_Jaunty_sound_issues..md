---
title: "Jaunty sound issues."
date: 2009-07-22
forum: Multimedia Software
---

### Post by Phaeic on 2009-07-22
Hey guys, I made a clean install of jaunty on a HP Pavilion dv5-1225et laptop. 

The sound devices are correctly recognized, afaik. (More data below)

It seems the system tries to use OSS to playback sound, but I've used the sound tool to test every single device on the system, none of them work. Nothings muted on Alsamixer.

```

doddy@DPC:~$ sudo lshw -C multimedia
[sudo] password for doddy: 
PCI (sysfs)  
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

```

doddy@DPC:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

doddy@DPC:~$ lspci
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
...

```


Thanks for any help you can give, guys.

---

### Post by Phaeic on 2009-07-23
Nobody knows the issue?

---

### Post by igorzwx on 2009-07-23
you may try to aks Martin,
but he is busy, perhaps.

---

### Post by igorzwx on 2009-07-23
[http://ubuntuforums.org/showthread.php?t=1219650](http://ubuntuforums.org/showthread.php?t=1219650)

---

### Post by igorzwx on 2009-07-23
it is OSS4, but you may try something similar
[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)

---

### Post by Phaeic on 2009-07-24
Thanks. I'll try those. =)

---

### Post by igorzwx on 2009-07-24
you may read this too:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by markbuntu on 2009-07-24
There is some listings for fixing the DV5 here

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by Loose_Cannon on 2009-07-24
After HOURS of fooling around with sound settings I got it working on my account.  On a second account there is no sound.  (audio is enabled in user privileges)

One thing I found odd was that PulseAudio Manager reports the server Host Name as "main-desktop" for both users.  I tried adding both users to the pulse_access and pulse_rt groups but that did not help.

---

