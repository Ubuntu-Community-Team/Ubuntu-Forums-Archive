---
title: "Sound stops randomly (regardless of player, files, format, etc)"
date: 2011-02-24
forum: Multimedia Software
---

### Post by Pnux on 2011-02-24
This is an issue ive been experiencing in both Debian (with KDE) and Ubuntu (GNOME).

About two years ago, this problem started on Debian Squeeze (testing at the moment), and a year ago i moved back to [SIZE=1]windows[/SIZE] and the problem stopped. When Squeeze became stable, i moved back to Debian, only to find out i still had it. So i moved to Ubuntu in the hope i wouldnt have this issue and its more user-friendly than Debian (with that i mean users are taking more consideration, thus media is improved). After a week of working, the issue started again. I did some testing and found that using flash increased the chances of sound stopping, so i uninstalled (purged actually) it. However, the issue still happens.

Its important that you remember that sound stops randomly, not that i cant play sound at all. Media player still play the file, both audio and video (if it has), i just cant hear it. Speakers work properly; its a stereo and i use the AUX input. If the problem happens, i just switch it to radio and i can listen to the radio normally.

Given the times ive asked, to no avail, help in #debian@freenode.net this will not be a "post a solution or get ignored" thread; I need this to be more interactive, so everything you tell me to do, ill do it (always applying common sense, so no sudo chmod 111 /etc/sudoers).

You can see a video of this issue back 1 year and a half ago. Nothing seems to have changed. [http://www.youtube.com/watch?v=S4cAzq0CVCo](http://www.youtube.com/watch?v=S4cAzq0CVCo)

A few starting specs..

Ubuntu 10.10, GNOME, default installation

```
n@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
n@ubuntu:~$ hwinfo --sound
22: PCI 1f.5: 0401 Multimedia audio controller                  
  [Created at pci.318]
  Unique ID: W60f.Ir55ZHpczO3
  SysFS ID: /devices/pci0000:00/0000:00:1f.5
  SysFS BusID: 0000:00:1f.5
  Hardware Class: sound
  Model: "Intel 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x24d5 "82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x0210 
  Revision: 0x02
  Driver: "Intel ICH"
  Driver Modules: "snd_intel8x0"
  Memory Range: 0xffa80400-0xffa805ff (rw,non-prefetchable)
  Memory Range: 0xffa80800-0xffa808ff (rw,non-prefetchable)
  IRQ: 17 (26816 events)
  Module Alias: "pci:v00008086d000024D5sv00008086sd00000210bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```I will update the thread as more things arise.

Thanks in advance.

---

### Post by Pnux on 2011-02-27
A little update. I just purged alsa-base (didnt reinstall) and this issue still happens. Other than that, i havent done much except keep testing the different possibilities in the sound preferences in the hardware tab, but that doesnt make it better.

---

### Post by HeadHunter00 on 2011-02-27
did you try using oss? oss is known for its hardware support. try this: [http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html#more-8089](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html#more-8089)

---

### Post by Pnux on 2011-02-28
Done, im testing it as i type this. Will update in a couple of hours.

UPDATE: after 15 minutes of playing without problems, it started happening again. However, instead of stopping all together, it seems to play only a couple of miliseconds in a second, so it makes a sound like an helicopter's blades while running.

```
n@ubuntu:~$ lsof /dev/dsp
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
vlc     1887    n   24w   CHR  249,4      0t0 7261 /dev/oss/oss_ich0/pcm0
```

Stopped VLC, ran 'osstest', same issue. (been running for like a minute and its still checking the left speaker)

```
n@ubuntu:~$ sudo lsof /dev/dsp
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/n/.gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
osstest 1975    n    4w   CHR  249,4      0t0 7261 /dev/oss/oss_ich0/pcm0
```

---

### Post by Pnux on 2011-03-03
So.. rechecked that link, and everything was done like it says there. But this still happens. VLC on verbose level 2 (max), reports this while the issue is happening.

```
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]output date isn't PTS date, requesting resampling (89225)[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (208141), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (182141), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (156141), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (130141), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]output date isn't PTS date, requesting resampling (89316)[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (192457), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (166457), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (140457), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]output date isn't PTS date, requesting resampling (89308)[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (203765), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (177765), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (151765), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (125765), dropping buffer[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]output date isn't PTS date, requesting resampling (89470)[/COLOR]
[COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR][COLOR=#000000]audio drift is too big (189235), dropping buffer[/COLOR]
```


[COLOR=#000000]Something i find weird, is that this very same thing happens with that short sound in the login screen.
[/COLOR]

---

### Post by Pnux on 2011-03-04
So.. a little update..

```
root@ubuntu:/home/n# aptitude search pulseaudio | grep ^i
root@ubuntu:/home/n# aptitude search alsa | grep ^i
root@ubuntu:/home/n# lsmod | grep -i alsa
root@ubuntu:/home/n# lsmod | grep -i pulseaudio
root@ubuntu:/home/n# 
```After purging everything related to alsa and pulseaudio (even changed libsdl1.2debian) it played for like 20 minutes (a record, i must say), but it started happening again. Grooveshark's flash player just stopped playing (the bar doesnt move), youtube plays video with no sound, and VLC still plays, but dont reproduce any sound.

VLC's debug messages say.

```
[COLOR=#00008b]*mpgatofixed32*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]libmad error: bad main_data_begin pointer[/COLOR][COLOR=#00008b]*oss*[/COLOR][COLOR=#ff0000]* error: *[/COLOR][COLOR=#000000]write failed (Input/output error)[/COLOR]
[COLOR=#00008b]*oss*[/COLOR][COLOR=#ff0000]* error: *[/COLOR][COLOR=#000000]write failed (Input/output error)[/COLOR]
```
[COLOR=#000000]In addition to the "auio drift is too big".


```
n@ubuntu:~$ ls -l /dev | grep dsp
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp -> /dev/oss/oss_ich0/pcm0
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp0 -> /dev/oss/oss_ich0/pcm0
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp_ac3 -> /dev/oss/oss_ich0/pcm0
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp_in -> /dev/oss/oss_ich0/pcm0
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp_mmap -> /dev/oss/oss_ich0/pcm0
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp_multich -> /dev/oss/oss_ich0/pcm0
lrwxrwxrwx  1 root root          22 2011-03-04 17:25 dsp_out -> /dev/oss/oss_ich0/pcm0
```
[/COLOR]

---

