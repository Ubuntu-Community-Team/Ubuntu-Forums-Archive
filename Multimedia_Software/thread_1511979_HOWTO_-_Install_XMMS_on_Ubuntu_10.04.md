---
title: "HOWTO - Install XMMS on Ubuntu 10.04"
date: 2010-06-17
forum: Multimedia Software
---

### Post by asbesto on 2010-06-17
As I red on [http://www.shicho.net/lamp/?p=88]("http://www.shicho.net/lamp/?p=88") (thanks to Lamp):

```

I went to:

* https://launchpad.net/ubuntu/hardy/i386/libglib1.2ldbl/1.2.10-19build1

Downloaded and installed:

    * libglib1.2ldbl_1.2.10-19build1_i386.deb

Went to:

* https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2/+build/484191

Downloaded and installed (in this order):

    * libgtk1.2-common_1.2.10-18.1build2_all.deb
    * libgtk1.2_1.2.10-18.1build2_i386.deb

Went to:

* https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2

Downloaded and installed:

    * xmms_1.2.10+20070601-1build2_i386.deb

Amazingly, this seemed to work!

```

Hope it can help other users!

Why use XMMS instead of XMMS2 or other software? Because they simply doesn't work, or use too much memory or cpu, or they are not so intuitive to use.

Really I can't understand why not supporting xmms into Ubuntu; I know that is not supported anymore but there are MILLIONS of people still using it in the world; a query on google will show this. Also, eliminating the old GLIB 1.2.2 is a very bad thing. 

):P

---

### Post by AlphA_ZA on 2010-07-31
Brilliant - worked off the bat! 

Thanks for sharing.

---

### Post by vicsar on 2010-08-29
Thank you asbesto. This solved my problem.

---

### Post by minosi on 2010-09-22
@asbesto THANKS! I was going crazy from audacious ... 

For anyone interested, here is a full procedure for 64-bit Lucid:
```

cd /tmp
wget http://launchpadlibrarian.net/10815906/libglib1.2ldbl_1.2.10-19build1_amd64.deb
wget http://launchpadlibrarian.net/11167863/libgtk1.2-common_1.2.10-18.1build2_all.deb
wget http://launchpadlibrarian.net/11167856/libgtk1.2_1.2.10-18.1build2_amd64.deb
wget http://launchpadlibrarian.net/11173506/xmms_1.2.10%2B20070601-1build2_amd64.deb

sudo gdebi libgtk1.2-common_1.2.10-18.1build2_all.deb
sudo gdebi libglib1.2ldbl_1.2.10-19build1_amd64.deb
sudo gdebi libgtk1.2_1.2.10-18.1build2_amd64.deb
sudo gdebi xmms_1.2.10+20070601-1build2_amd64.deb

```
get some basic skins:
```

wget http://launchpadlibrarian.net/1433551/xmms-skins_0.6-1_all.deb
sudo gdebi xmms-skins_0.6-1_all.deb

```
Add Skins dir: [ALT+S] -> 'Add Directory' -> browse to /usr/share/xmms/Skins

Classic Winamp2 skin:
```
wget -P ~/.xmms/Skins http://gnome-look.org/CONTENT/content-files/64790-Winamp.tar.gz
```


[WARNING] Following recommendation may be specific to my setup - Realtek ALC889A: [/WARNING]

After install, run XMMS and select eSound as Audio output plugin:
[CTRL+P] -> 'Audio I/O Plugins' -> 'Output Plugin' -> 'eSound Output Plugin'

On my setup OSS is deaf and ALSA plugin brokes playlist advance.
So despite what XMMS FAQ and website say, you need to go for esd/eSound.

---

### Post by mvelte54 on 2010-09-25
OMG! This is fantastic now I just need to figure out how to play a m3u.

UBUNTU ROCKS!

---

### Post by minosi on 2010-09-26
> **mvelte54 said:**
> OMG! This is fantastic now I just need to figure out how to play a m3u.

UBUNTU ROCKS!
Open folder in Nautilus -> Right-click m3u file -> open with -> Other ... -> scroll to xmms -> check "Remember this application ..."

Just make sure you have valid m3u's - some m3u playlist generated on windows tend to have non-complaint format or unrecognizable characters.

Here is how a proper m3u shall look like:
```

#EXTM3U
#EXTINF:255,Nelly Furtado  Whoa, Nelly!   1 - Hey, man!
01 - Hey, Man!.mp3
#EXTINF:234,Nelly Furtado  Whoa, Nelly!   2 - ....On the radio
02 - ...On The Radio.mp3
#EXTINF:226,Nelly Furtado  Whoa, Nelly!   3 - Baby girl
03 - Baby Girl.mp3
...

```
As you can see the file paths are fully relative - that way they will work the same way on Win and Linux.
Absolute paths are mess most of the time, so avoid unless a specific case warrants it.

---

### Post by qstraza on 2011-01-09
Thanks.

Im gonna try this on 10.10.

I too, dont get, why XMMS is not supported, Amarok and xmms2 just dont cut it. Just tried xmms2, and my cpu usage went on 25 % (I got phenom quad 2.5 ghz).
Amarok is even hungrier. Cpu jumps to 100% if I do any sudden move with it. Very sad.

Although, I play 200gb of music. But xmms plays it like a charm with max of 10% of cpu.

---

### Post by robertm43 on 2011-01-28
Thanks for this .. worked well on ubuntu 10.04

---

### Post by shantiq on 2011-01-29
thanx asbesto  


nice to see one more possibly shorter route


 linked it on my [earlier page]("http://ubuntuforums.org/showthread.php?t=1525072") which also has much info and extra plugins for the **unique/best player/cannot believe they ditched it from the repos:KS XMMS**

---

### Post by baldeante on 2011-06-23
Found this on google


[http://tombott.com/install_xmms_on_ubuntu_8.04_8.10_9.04_9.10_10.04_last.fm_scrobble](http://tombott.com/install_xmms_on_ubuntu_8.04_8.10_9.04_9.10_10.04_last.fm_scrobble)

Seems Easier ...

---

### Post by Superkuh on 2011-06-28
I use 10.04 AMD64. I have installed XMMS from the [http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu](http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu) repository, but it also does the below when I compile it from source. I use the eSound plugin for pulseaudio. 

At seemingly random times the volume suddenly plays at 100% regardless of the XMMS volume shown. When it does this, the volume slider in XMMS will not change. By stopping and restarting the track the volume will resume at the shown level.

The application specific listing of volumes in System->Preferences->'Sound Preferences'->Applications gives a hint. Normally the XMMS application volume slider controls the '**xmms - plugin (pid-instance#)**' volume slider in 'Sound Preferences'->Applications. 

[img]http://i.imgur.com/ajcBS.png[/img]

After each track played a new instance of the plugin will be made and the old will disapear (screenshot taken before this happens so both are shown). The instance number shown will increment +1. Normally this new instance to pulseaudio will inherit the sound level from the previous one. The volume will not change.

[img]http://i.imgur.com/KLzrB.png[/img]

But occasionally the new instance *will not* inherit the volume settings and stays at 100% until either the XMMS track playing is stopped and restarted, the next track starts, or sometimes (but not always) when the volume slider in XMMS is touched. The instance still only increments by +1.

[img]http://i.imgur.com/BkDZe.png[/img]
[img]http://i.imgur.com/brPwG.png[/img]

These **jumps from, say, 40% volume to 100% volume are very annoying for me and my neighbors 2:00 in the morning**. It also tends to wake me up if I attempt to play quiet music while I sleep. I am at a loss on how to further diagnose the issue with esound plugin instances not inheriting volume level.

ALSA is not an option. When I try to use the ALSA plugin it fails to load the next playlist entry at the end of each song (also reported by others) This is unusable and is new to 10.04 vs 8.04. But I digress... 

Has anyone else had this issue? Is it even an XMMS issue, or a more general pulseaudio/ubuntu implementation problem? Perhaps there is there a known solution, or a series of keywords with which to search for more hints? Anything would be appreciated.

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

superkuh@limbo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

