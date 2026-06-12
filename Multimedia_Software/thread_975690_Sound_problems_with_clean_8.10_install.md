---
title: "Sound problems with clean 8.10 install"
date: 2008-11-08
forum: Multimedia Software
---

### Post by patch0_ on 2008-11-08
Hi,

I've read through some posts here, but I'm new to linux and am a bit confused. I did a clean install of 8.10 on a newly built machine and the sound just doesn't seem to work, its sometimes crackly and echoing. Sometimes just not there at all.

Does anyone have any help?

---

### Post by sreekanth27 on 2008-11-08
Facing a similar problem myself. I just did a clean install too of 8.10 but for some reason there is no sound on my creative speakers. I used soundmax drivers for my windows but nothing on UBUNTU..

---

### Post by sreekanth27 on 2008-11-08
I was following this link:

[http://www.fixya.com/support/t850063-ubuntu_sound_problem](http://www.fixya.com/support/t850063-ubuntu_sound_problem)

and keep getting this error.. I also realise that I keep getting this piece in executing several other packages too..
Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)


I realise If I can fix the above error I should be able to fix the sound error.



I have captured the detailed error below..
root@ubuntu:/home/sree# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/sree# 

I even tried the steps in the link:[http://ubuntuforums.org/showthread.php?t=302544](http://ubuntuforums.org/showthread.php?t=302544)

but to no avail..

---

### Post by Yellow Pasque on 2008-11-08
If you're looking to compile ALSA, use: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Make sure your alsa-base file is configured: [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
Also, consider OSS4 if ALSA still fails: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by sreekanth27 on 2008-11-09
Hello,

I am still facing problems... I have creative 4.1 speaker system and use soundmax drivers in my windows box..

Switched recently to UBUNTU and man it has been difficult.. thank you for taking your time to help me.. still having trouble..

HEre are the o/p from the commands:

root@ubuntu:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@ubuntu:~# 

***********
root@ubuntu:~# cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
root@ubuntu:~# 

********
added this line after:
gksudo gedit /etc/modprobe.d/alsa-base
##new line by sree
options snd-hda-intel model=ICH5

--anything else that you think will help

---

### Post by sreekanth27 on 2008-11-09
let me try if this link that you sent me will help.. will update you with my findings..
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by sreekanth27 on 2008-11-09
i see this error a lot.. any ideas why..

Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~#

---

### Post by sreekanth27 on 2008-11-09
the same error again:
root@ubuntu:~# sudo apt-get install -y libesd0 libsdl1.2debian-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libesd-alsa0 libsdl1.2debian-alsa
The following NEW packages will be installed:
  libesd0 libsdl1.2debian-oss
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 229kB of archives.
After this operation, 4096B disk space will be freed.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libesd0 0.2.40-0ubuntu1 [19.3kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libsdl1.2debian-oss 1.2.13-2ubuntu1 [210kB]
Fetched 229kB in 6s (32.8kB/s)                                                 
dpkg: libesd-alsa0: dependency problems, but removing anyway as you request:
 ekiga depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 libgnome2-0 depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 esound-clients depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 libarts1c2a depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 gnome-settings-daemon depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 ekiga depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 libgnome2-0 depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 esound-clients depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 libarts1c2a depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
 gnome-settings-daemon depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is to be removed.
  Package libesd0 is not installed.
(Reading database ... 117331 files and directories currently installed.)
Removing libesd-alsa0 ...
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-2ubuntu1) | libsdl1.2debian-all (= 1.2.13-2ubuntu1) | libsdl1.2debian-esd (= 1.2.13-2ubuntu1) | libsdl1.2debian-arts (= 1.2.13-2ubuntu1) | libsdl1.2debian-oss (= 1.2.13-2ubuntu1) | libsdl1.2debian-nas (= 1.2.13-2ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-2ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libesd0.
(Reading database ... 117317 files and directories currently installed.)
Unpacking libesd0 (from .../libesd0_0.2.40-0ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl1.2debian-oss.
Unpacking libsdl1.2debian-oss (from .../libsdl1.2debian-oss_1.2.13-2ubuntu1_i386.deb) ...
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libesd0 (0.2.40-0ubuntu1) ...

Setting up libsdl1.2debian-oss (1.2.13-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~#

---

### Post by patch0_ on 2008-11-09
> **Temüjin said:**
> If you're looking to compile ALSA, use: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
Make sure your alsa-base file is configured: [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)
Also, consider OSS4 if ALSA still fails: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I've tried a few things, sound has gone from crackly to non-existent. I'm sorry to say I'm a total noob here, can anyone point me to a guide to sound in ubuntu thats written for a three year old?

---

### Post by sreekanth27 on 2008-11-11
i upgraded the ram, reinstalled ubuntu and now the installation looked fine. but still no sound. please do help..

---

### Post by sreekanth27 on 2008-11-12
i went ahead and uninstalled pulse audio too but still no sound.. bohoo :(..

---

### Post by zwaardmeester on 2008-11-12
Try rightclick on volume-icon, "Open Volume Control". In the Playback tab goto preferences and select all output (playback) channels and all switches. Put them all on 100%. Goto Switches tab and put them all on. 

Now play the .ogg file in you home folder and check if you hear something. 

If not, tell us your soundcard type (if it's an onboard, the mobo name).

---

### Post by zwaardmeester on 2008-11-12
Oh just to be sure, select ALSA under menu System->Preferences->Sound

---

