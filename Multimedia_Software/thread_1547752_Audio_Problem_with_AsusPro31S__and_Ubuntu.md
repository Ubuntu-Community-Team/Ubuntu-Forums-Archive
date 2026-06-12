---
title: "Audio Problem with AsusPro31S  and Ubuntu"
date: 2010-08-07
forum: Multimedia Software
---

### Post by Bracchesimo on 2010-08-07
Hi guys,

It is about 2 days the I am struggling with my laptop: it has no sound. 

I have the latest version of caelinux: [http://caelinux.com/CMS/index.php?option=com_content&task=view&id=48&Itemid=40](http://caelinux.com/CMS/index.php?option=com_content&task=view&id=48&Itemid=40)

which uses the ubuntu version of linux.

The sound card is: intel corp 82801H (ich8 family).

Of course the sound is not muted and all the diagnostics from  System->Preferences->sound are green flagged.

the command:
aplay -l

returns
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I am new to linux, I have read several threads that made me modify some text file but no success. I stopped because I was unaware of what
  I was doing and I was afraid to cause some more serious problem.

Can you please tell me what should I check? or what should I do? 

Sorry for my poor english, if you need any more infos please just ask.

Thanks in advance for help!

---

### Post by ajgreeny on 2010-08-07
I recall there being some problem with a conflict between drivers for sound and modem in some systems in the past, so it may be worth disabling the modem if you don't need it, either in the BIOS or in ubuntu.

Do a a search in the forums and see if you can find any more info.  Search in [www.googlubuntu.com](www.googlubuntu.com) as well; it's very good at ubuntu searches on websites of all types.

---

### Post by Bracchesimo on 2010-08-07
thanks for your quick reply!

is there an easy way to disable the modem drivers? I am new to linux!

or there some simple tutorial?

I will make this try.

---

### Post by ajgreeny on 2010-08-07
Sorry, I have no idea as I have never had a modem to deal with in my ubuntu time.

---

### Post by Bracchesimo on 2010-08-08
Thanks anyway,

I got it on another forum:

> blacklist snd-hda-codec-si3054

but it doesn't work.


Does any anibody has another solution?

maybe It may be useful to know that a few days ago I had on of the latest ubuntu installed and everything worked fine.

---

### Post by utilitytrack on 2010-08-08
> **Bracchesimo said:**
> I have read several threads that made me modify some text file but no success.

Hello, what files did you modified and how. Also give on forum more diagnostic info:

```
$ uname -r
$ dpkg -l alsa-*
$ lspci -nn | grep Audio
$ cat /proc/asound/card0/codec#0 | grep Codec
$ cat /proc/asound/devices
$ cat /etc/modprobe.d/alsa-base.conf
$ grep -e audio /etc/group
# hwinfo --sound

```
and your PC/laptop model

---

### Post by Bracchesimo on 2010-08-08
Here are the additional info you asked. A guy made me modify the file 
alsa-base.conf adding the only line can you see below. My laptop is an Asus Pro31 S as specified in the header. 

>  uname -r
2.6.24-28-generic> dpkg -l alsa-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.16-0ubuntu ALSA driver configuration files
ii  alsa-firmware- 1.0.15-2ubuntu ALSA software loaders for specific hardware
un  alsa-headers   <none>         (no description available)
ii  alsa-oss       1.0.15-1       ALSA wrapper for OSS applications
ii  alsa-source    1.0.16-0ubuntu ALSA driver sources
ii  alsa-tools     1.0.15-2ubuntu Console based ALSA utilities for specific ha
ii  alsa-tools-gui 1.0.15-2ubuntu GUI based ALSA utilities for specific hardwa
ii  alsa-utils     1.0.15-3ubuntu ALSA utilities> lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)>  cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC660-VD
> cat /proc/asound/devices   0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer

> cat /etc/modprobe.d/alsa-base.conf
 options snd-hda-intel model=asus >  grep -e audio /etc/group
audio:x:29:pulse,caelinux

---

### Post by utilitytrack on 2010-08-08
Hello again.

```
uname -r
2.6.24-28-generic
```

It's very bad (with respect to the sound)

```
dpkg -l alsa-*
ii alsa-base 1.0.16-0ubuntu ALSA driver configuration files
ii alsa-firmware- 1.0.15-2ubuntu ALSA software loaders for specific hardware
un alsa-headers <none> (no description available)
ii alsa-oss 1.0.15-1 ALSA wrapper for OSS applications
ii alsa-source 1.0.16-0ubuntu ALSA driver sources
ii alsa-tools 1.0.15-2ubuntu Console based ALSA utilities for specific ha
ii alsa-utils 1.0.15-3ubuntu ALSA utilities
```

It's very bad (for the same reason)

> cat /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=asus

Remove it.

Well, I would advice you upgrade your CAELinux to the latest version. But I think that it does not help because as I guess that you already have the latest. Also I can give advice switch to fresh Ubuntu. But it is not right for you for professional reasons.

So that all you can do is try to upgrade ALSA subsystem. Follow these instructions for that: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by Bracchesimo on 2010-08-09
Problem solved guys, that's enough to upgrade to the latest version of alsa drivers.

DOwnload from the top right of page: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
 **alsa-lib** and **alsa-utils** .

the copy the archives in your home directory and run the following code:

> sudo apt-get install build-essential gettext ncurses-dev linux-headers-`uname -r` xmlto
tar xvpjf alsa-driver*
cd alsa-driver*
./configure --with-cards=hda-intel
make
sudo make install
cd
tar xvpjf alsa-lib*
cd alsa-lib*
./configure --with-cards=hda-intel
make
sudo make install
cd
sudo ln -s /usr/lib/libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so 
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so 
sudo ln -s libncursesw.so.5 /lib/libncursesw.so
tar xvpjf  alsa-utils*
cd alsa-utils*
./configure --with-cards=hda-intel
make
sudo make install
sudo alsaconf

---

### Post by utilitytrack on 2010-08-09
Please mark thread as solved.

---

