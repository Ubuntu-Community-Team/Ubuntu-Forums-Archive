---
title: "Front Headphone Jack not working - 12.04 - CM690 Case"
date: 2014-01-15
forum: Multimedia Software
---

### Post by J.L.C. on 2014-01-15
Hi,

I'm hoping someone can help with my sound issue. I am struggling to get sound completely working. All rear jack works fine and the front microphone jack works fine, but I can't get the front headphone jack to work.

When I connect headphones to the front port, the rear-connected speakers are not muted. When I go into alsamixer i can here a very quiet "pop" when I mute and unmute the front headphone jack, but I cannot ever get sound to play regardless of how I set "sound settings" or "pavcontrol".

Here is my alsamixer info:
[http://www.alsa-project.org/db/?f=d635c2d23ce2a1bfd8a1fe374d84d638440e3cb3](http://www.alsa-project.org/db/?f=d635c2d23ce2a1bfd8a1fe374d84d638440e3cb3)

Thanks for any help!

---

### Post by Yellow Pasque on 2014-01-15
The first thing to try is newest kernel module. Either install the lts-saucy kernel or use oem-audio-hda-daily-lts-quantal-dkms package as described here: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by J.L.C. on 2014-01-15
I have installed the 3.5.0-45 kernel and installed the latest [COLOR=#333333][FONT=Ubuntu Beta]daily-lts-quantal-dkms[/FONT][/COLOR] package for 12.04 and that has definitely made things worse!

Now I have no sound anywhere and both "sound settings" and pavcontrol show "dummy output" as the only available output device.

This is my new alsamixer info:
[http://www.alsa-project.org/db/?f=9046a4f731148c7d167b2c50bc513d7516e8109d](http://www.alsa-project.org/db/?f=9046a4f731148c7d167b2c50bc513d7516e8109d)

---

### Post by J.L.C. on 2014-01-15
I booted into Windows 7 on the same machine with the same hardware and BIOS settings and the front headphone jack works. So it has to be a software issue.

I booted into an older kernel 3.2.0-58 and removed the oem-audio daily package completely

Then used these commands:
sudo apt-get remove --purge alsa-base pulseaudio

sudo apt-get install alsa-base pulseaudio

sudo alsa force-reload

Rebooted and was able to at least play sounds though my rear-connected speakers. But, to get the sound indicator back I had to:
sudo apt-get install indicator-sound

then

sudo apt-get install indicator-sound

This gave me the indicator back, but the speaker test did not work until I installed another package:

sudo apt-get install libcanberra-pulse 

Now I'm back where I started, rear-connected speakers work, front-connected mic works, but no sound from font-connected headphones. 

With headphones connected, if I choose them in "sound settings" and do the sound test, the test sounds "front left" and "front right" are played though the rear-connected speakers, not through the headphones. 

Here is my latest also info: [http://www.alsa-project.org/db/?f=7fe05e3f8edb81df73db51fcb410185084950e7b](http://www.alsa-project.org/db/?f=7fe05e3f8edb81df73db51fcb410185084950e7b) 

Any help is greatly appreciated![COLOR=#DDDDDD][FONT=monospace]
[/FONT][/COLOR]

---

### Post by J.L.C. on 2014-01-15
Another update!

Booting into the 3.2.0-58 kernel and installing the daily dkms package has fixed the headphone output. But only for that kernel.

Booting into the 3.5.0-45 kernel still had the same problem, no output from front headphone jack. Installing the 3.5 daily dkms package, once again resulted in only "dummy output" being available, so it completely breaks sound.

Any suggestions for getting things working with 3.5.0-45?

---

