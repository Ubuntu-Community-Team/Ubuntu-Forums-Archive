---
title: "sound issue"
date: 2008-12-01
forum: Multimedia Software
---

### Post by ~cyrus~ on 2008-12-01
Release 8.10
Kernel Linux 2.6.27-9-generic
GNOME 2.24.1

After doing a search for sound related issues, I am more confused than ever, and open this thread to try and find a solution for no sound with any video eg. youtube. The picture is playing, but the sound is dead.

Further information that was asked in related topics is given below:

desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

desktop:~$ sudo alsamixer
[sudo] password for xxxx: 
ALSA lib pulse.c:272: (pulse_connect) PulseAudio: Unable to connect: Connection terminated
alsamixer: function snd_ctl_open failed for default: Connection refused

desktop:~$ lspci -v
(for sound I picked up):
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: NEC Corporation Device 81a7
	Flags: bus master, medium devsel, latency 168, IRQ 18
	I/O ports at 1400 [size=256]
	I/O ports at 1080 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

Appreciate your guidance.

---

### Post by IQRules on 2008-12-01
Check this,

[http://ubuntuforums.org/showthread.php?p=3732575](http://ubuntuforums.org/showthread.php?p=3732575)

---

### Post by ~cyrus~ on 2008-12-01
Followed the steps as under:

> SOLUTION:
(Tested on Gutsy Gibbon 7.10)

1st: sudo gedit /etc/modprobe.d/alsa-base
find "options snd-intel8x0 index=-2" and set it to "=0"

2nd:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

3rd: Reboot
The sound should be working by now.

On sudo m-a a-i alsa after about 50% I got:

> &#9472;&#9508; module-assistant, interactive mode &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
       &#9474; Build of the package alsa-source failed! How do you wish to   &#9474; 
       &#9474; proceed?                                                      &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;       VIEW     Examine the build log file                     &#9474; 
       &#9474;       CONTINUE Skip and continue with the next operation      &#9474; 
       &#9474;       STOP     Stop processing the build commands             &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;                <Ok>                    <Cancel>               &#9474; 
       &#9474;                                                          

The buildlog file is huge, and CONTINUE takes me back to my terminal. I rebooted, but still no sound. So, continued with the direction:

sudo apt-get install linux-backports-modules-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

That's as far as I got!

---

### Post by IQRules on 2008-12-01
Check this link, [http://ubuntuforums.org/showthread.php?t=997506&highlight=interpid+sound](http://ubuntuforums.org/showthread.php?t=997506&highlight=interpid+sound)

Do you know rmmod and modprobe?

---

### Post by ~cyrus~ on 2008-12-01
Really appreciate your assistance.

That last link sorted me out.

You get a 'thanks' from me!

---

