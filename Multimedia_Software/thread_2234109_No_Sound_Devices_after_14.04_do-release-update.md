---
title: "No Sound Devices after 14.04 do-release-update"
date: 2014-07-12
forum: Multimedia Software
---

### Post by TheFu on 2014-07-12
Updated the XBMC machine here from 12.04 to 14.04 today.  Everything was working before on 12.04.
* AMD APU E350 w/ Radeon HD 6310
```
* $ aplay -l
aplay: device_list:268: no soundcards found...
* $ lsmod |grep snd
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
snd_hda_intel          52355  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
* $ lspci |egrep -i audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audi
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)

```
What I've tried so far:
* completely removed fglrx - didn't help. Still on F/LOSS version now.
* removed previously blacklisted snd modules - these were midi.
* removed ~/.asoundrc settings. Without alsa working, it doesn't matter anyway.
* pavucontrol only shows a dummy driver.

No errors or warnings in dmesg output.

According to the XBMC Gotham page, on Ubuntu 14.04 HDMI audio with AMD chips should just work. Guess it is just this machine that doesn't work? Analog audio doesn't work either.

The machine doesn't have a keyboard or mouse. I ssh in to run commands and use XMBC with a remote to control XMBC/Plex.

So - any ideas?

---

### Post by Yellow Pasque on 2014-07-12
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by TheFu on 2014-07-12
> **Temüjin said:**
> Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=d612f7f298b2ec9f70e21130505e70d11b9ff7ec](http://www.alsa-project.org/db/?f=d612f7f298b2ec9f70e21130505e70d11b9ff7ec)

I'm stumped.  Drivers appear to be loaded, but no sound cards are seen by aplay?

---

### Post by Yellow Pasque on 2014-07-12
Try this command sequence (replacing "user" with your user's name):

```
sudo setfacl -m u:user:rw /dev/snd/*
rm -r ~/.config/pulse
pulseaudio -k
aplay -l
```

---

### Post by TheFu on 2014-07-13
> **Temüjin said:**
> Try this command sequence (replacing "user" with your user's name):

```
sudo setfacl -m u:user:rw /dev/snd/*
rm -r ~/.config/pulse
pulseaudio -k
aplay -l
```

Thanks Temüjin!

I was already a member of the "audio" group - seems the issue was pulseaudio (which I normally purge, but forgot to do after the new install).
Life is good! THANKS!
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Arvanitidis_Christ on 2015-03-09
Dear guys, 

I'm using KDE UBUNTU 14.04 since a month or so. 
I had no sound problems until yesterday I made the last update.

Therefore, I tried to make the solutions No 3, 4, proposed in [https://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](https://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) work for my PC without success.
Then, I came to your comment and I tried to run the first of the commands you give above in my konsole and I get this message: 

christos@chrisBook:~$ sudo setfacl -m u:user:rw /dev/snd/*
[sudo] password for christos: 
setfacl: Option -m: Invalid argument near character 3

How do I proceed?

Thanks a lot for your support!

---

### Post by Arvanitidis_Christ on 2015-03-09
I don't believe this :O 
My sound is now fixed!
I did nothing else since I sent my message.

Can't explain it but all is good.
Cheers.

---

### Post by TheFu on 2015-03-09
Well, if you didn't replace "user" with the correct userid (christos?), it didn't do anything.

---

### Post by lt-i on 2015-03-30
> **Temüjin said:**
> Try this command sequence (replacing "user" with your user's name):

```
sudo setfacl -m u:user:rw /dev/snd/*
rm -r ~/.config/pulse
pulseaudio -k
aplay -l
```

Is there any way I dont have to do this every time I start my computer.

Sound will not work after boot unless I do the following command

```
sudo setfacl -m u:user:rw /dev/snd/*
```

---

### Post by mike4ubuntu on 2015-04-14
I don't see what the solution is.  I have two different servers running 14.04 where sound works on one and doesn't on the other.  It used to work on both of them, but after a software update, it stopped working on one of them.  So clearly some update corrupted the sound system.  Is it a permission issue, device driver issue, alsa issue, pulseaudio issue?  the above commands

> 
sudo setfacl -m u:user:rw /dev/snd/*
rm -r ~/.config/pulse
pulseaudio -k
aplay -l


didn't help, and I changed the "user" to my user name of course.

```

$ aplay -l
aplay: device_list:268: no soundcards found...

$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation C600/X79 series chipset High Definition Audio Controller (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fb720000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: oss_hdaudio

00:1c.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 (rev b6) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fb500000-fb5fffff
	Capabilities: <access denied>
--
02:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 353e
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at fb080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

03:00.0 RAID bus controller: 3ware Inc 9750 SAS2/SATA-II RAID PCIe (rev 05)
	Subsystem: 3ware Inc Device 0001

```

---

### Post by mike4ubuntu on 2015-04-14
Ok, so it's a driver problem.  This is some sloppy build management if you ask me.  Some update from Canonical libraries breaks sound completely.  At any rate this is what I did to resolve the problem:

go here to find the latest driver [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages")

you have to get the right version for you, based on which version of Ubuntu you have installed.

these are the steps:

```

$ aplay -l
aplay: device_list:268: no soundcards found...

$ sudo modprobe -v snd-hda-intel
modprobe: FATAL: Module snd-hda-intel not found.


$ wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201504140646%7Eubuntu14.04.1_all.deb
--2015-04-14 15:28:38--  https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201504140646%7Eubuntu14.04.1_all.deb
Resolving code.launchpad.net (code.launchpad.net)... 91.189.89.224, 91.189.89.225
Connecting to code.launchpad.net (code.launchpad.net)|91.189.89.224|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://launchpadlibrarian.net/203191888/oem-audio-hda-daily-dkms_0.201504140646%7Eubuntu14.04.1_all.deb [following]
--2015-04-14 15:28:38--  https://launchpadlibrarian.net/203191888/oem-audio-hda-daily-dkms_0.201504140646%7Eubuntu14.04.1_all.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 242492 (237K) [application/x-debian-package]
Saving to: ‘oem-audio-hda-daily-dkms_0.201504140646~ubuntu14.04.1_all.deb’

100%[==========================================================================================================================================>] 242,492      301KB/s   in 0.8s   

2015-04-14 15:28:39 (301 KB/s) - ‘oem-audio-hda-daily-dkms_0.201504140646~ubuntu14.04.1_all.deb’ saved [242492/242492]

$ sudo dpkg -i oem-audio-hda-daily-dkms_0.201504140646~ubuntu14.04.1_all.deb
Selecting previously unselected package oem-audio-hda-daily-dkms.
(Reading database ... 693892 files and directories currently installed.)
Preparing to unpack oem-audio-hda-daily-dkms_0.201504140646~ubuntu14.04.1_all.deb ...
Unpacking oem-audio-hda-daily-dkms (0.201504140646~ubuntu14.04.1) ...
Setting up oem-audio-hda-daily-dkms (0.201504140646~ubuntu14.04.1) ...
Loading new oem-audio-hda-daily-0.201504140646~ubuntu14.04.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-30-generic
Building for architecture x86_64
Building initial module for 3.13.0-30-generic
Done.

...some more output...

depmod.....

DKMS: install completed.


$ sudo modprobe -v snd-hda-intel
insmod /lib/modules/3.13.0-30-generic/kernel/sound/soundcore.ko 
install /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } 
insmod /lib/modules/3.13.0-30-generic/kernel/sound/core/snd.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/sound/core/snd-page-alloc.ko 
install /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } 
insmod /lib/modules/3.13.0-30-generic/kernel/sound/core/snd-pcm.ko 
insmod /lib/modules/3.13.0-30-generic/updates/dkms/snd-hda-core.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/sound/core/snd-hwdep.ko 
insmod /lib/modules/3.13.0-30-generic/updates/dkms/snd-hda-codec.ko 
insmod /lib/modules/3.13.0-30-generic/updates/dkms/snd-hda-controller.ko 
insmod /lib/modules/3.13.0-30-generic/updates/dkms/snd-hda-intel.ko 


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

