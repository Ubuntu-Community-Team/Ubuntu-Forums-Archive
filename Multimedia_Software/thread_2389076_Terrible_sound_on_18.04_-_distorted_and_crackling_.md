---
title: "Terrible sound on 18.04 - distorted and crackling after a few minutes"
date: 2018-04-11
forum: Multimedia Software
---

### Post by voycey on 2018-04-11
Hi,

I am a long time user of Linux and Ubuntu (since v6) but have never needed to post anything that I havent been able to find online / solve myself.

I have recently upgraded to 18.04 due to a catastrophic failure of a hard drive, I am aware it is still in Beta but I have not experienced anything like this so far.

My setup is an Alienware 17 R3, Virtualbox 5.2.2 with Ubuntu (using xubuntu-desktop) guest on Windows 10 Host.

If I play music inside of the virtual machine it starts off just fine but quickly degrades over probably 1-2 minutes if I use the computer for anything else into a complete mess of sound (and doesn't recover)

It seems if I simply leave the audio application open and don't do anything else it runs fine for much longer.

I have tried disabling pulseaudio and running solely through Alsa - the same thing happens so I think I can rule out Pulseaudio as a problem, however I am not sure where to start looking next?

Some output from various commands to help:

```
dan@dan-VirtualBox ~> aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have run alsactl init and alsactl store - neither of these helped.

I have also upgraded my kernel to the latest Mainline version in the hope it was something fixed.

Any ideas on where to look next?

---

### Post by voycey on 2018-04-11
I'll just add to this that if I play a WAV the sound will still heavily distort but it wont remain distorted, it coughs and splutters a bit but then continues playing.

I think it is MP3's that seem to just decay into madness after whatever triggers it!

---

### Post by Yellow Pasque on 2018-04-11
The first thing I would try is the latest stable version of Virtualbox (5.2.8), especially with all of the audio fixes noted in the changelog: [https://www.virtualbox.org/wiki/Changelog](https://www.virtualbox.org/wiki/Changelog)

---

### Post by voycey on 2018-04-11
Sorry i should add that I started out with the latest version of virtualbox which has some horrible problems with 18.04, 5.2.3 and the latest ubuntu had some other problems that meant things were only working with 3d acceleration enabled (which again caused more problems).....

But you make a good point - I think these are probably related, I will need to make a backup of my (hefty) virtual machine before trying to upgrade virtualbox - round in circles :(

---

