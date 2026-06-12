---
title: "Sound not detected in 13.10 with Radeon HD 6000 Series - I've broken it"
date: 2013-12-28
forum: Multimedia Software
---

### Post by irvingdave1 on 2013-12-28
Hi,

I'm running ubuntu 13.10. Everything was going amazingly well until a chain of events (caused by me) broke my sound:

- I installed the proprietary radeon driver
- I couldn't get sound with it so I removed it (following the instructions with the uninstall script)
- Things then seemed to work well again, until a few days later:
- I did an apt-get upgrade

Following this, there is no sound, and only a 'Dummy output' device is in my Sound settings. 
Dmesg seems to indicate something isn't happy:

[  795.770630] snd_hda_codec_realtek: Unknown symbol snd_hda_gen_free (err 0)
[  795.773464] hda-codec: No codec parser is available

aplay -l doesn't show any devices:

aplay -l
**** List of PLAYBACK Hardware Devices ****

lspci shows:

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series

I've put a few more details here: [http://paste.ubuntu.com/6651833/](http://paste.ubuntu.com/6651833/)

Is there any way for me to reinstall sound drivers / configuration etc back to defaults? I've got some lovely new speakers coming tomorrow and I would love to get to use them! :P

Any help greatly appreciated!

Dave

---

### Post by irvingdave1 on 2013-12-28
Alsa info here: [http://www.alsa-project.org/db/?f=88c813182c19198e7d4ca3efdf42f80edadf8145](http://www.alsa-project.org/db/?f=88c813182c19198e7d4ca3efdf42f80edadf8145)

---

### Post by JDorfler on 2013-12-28
Try ```
alsamixer
``` and see what comes up.  Sometimes you have to mess with alsamixer to get sound.

---

### Post by irvingdave1 on 2013-12-28
Tried alsamixer - Its just showing card: HDA Intel PCH with one control. 

If I F6: Select sound card - I can see:
- Default
0 HDA Intel PCH
1 HDA ATI HDMI

Switching to HDA ATI HDMI just says: "This sound device does not have any controls". I dont think this was the case before (I was using HDMI audio).

---

### Post by JDorfler on 2013-12-28
Interesting.  Try the following;
```
sudo aptitude reinstall fglrx fglrx-amdcccle
sudo amdconfig --initial

```

Reboot and see what happens.

---

### Post by irvingdave1 on 2013-12-28
hmmm - didnt seem too happy while trying to install:

```
sudo apt-get install fglrx fglrx-amdcccle
......
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a13.101-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a13.101-0ubuntu3_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a13.101-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by JDorfler on 2013-12-28
Very interesting.  You might have some deeper issues, but I could be wrong.  Can you do a
```
sudo fglrxinfo
```?

---

### Post by irvingdave1 on 2013-12-28
Command not found.
Tried fglrx install again - and got a bug report pop up :(

Looks like a dupe of this:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1198442](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1198442)

Completely lost :(

Is there anyway to just get rid of all traces of fglrx and go with the stock open source drivers?
I want to avoid a complete re-install at all costs if I can

---

### Post by irvingdave1 on 2013-12-28
Ah-ha - I think I'm getting at least _somewhere_ ....

So, I said that it was after an apt-get upgrade that I lost sound....
The upgrade moved my kernel version from 3.11.0-12-generic to 3.11.0-14-generic.
From grub I booted in to 3.11.0-12-generic.
I had a black screen, but whatever - I could still ssh in to the box. 

And guess what?

```
aplay -l
****List of PLAYBACK Hardware Devices ****
card0: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3Analog]
  Subdevices:1/1
  Subdevice#0: subdevice #0
card1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices:1/1
  Subdevice#0: subdevice #0
```

Also, no errors in dmesg about no hda-codec parser available / unknown symbol.

Back to 3.11.0-14-generic and the problem's back:

```
aplay -l
****List of PLAYBACK Hardware Devices ****

```

```
dmesg | grep codec
...
[    8.716295] snd_hda_codec_realtek: Unknown symbol snd_hda_gen_free (err 0)
[    8.717637] hda-codec: No codec parser is available
[    8.719368] hda-codec: No codec parser is available
...
```

Any thoughts? I don't really know where to look next.....

---

### Post by irvingdave1 on 2013-12-28
```
sudo apt-get remove oem-audio-hda-daily-dkms
```

Problem solved.

---

