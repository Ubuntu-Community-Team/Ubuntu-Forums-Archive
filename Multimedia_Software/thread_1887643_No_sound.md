---
title: "No sound"
date: 2011-11-27
forum: Multimedia Software
---

### Post by Kr1551 on 2011-11-27
Yesterday I had put last lts version of Ubuntu on my laptop and the sound did not work, only with headphones did it work. now I just booted lubuntu. No sound, not even with headphones.

Can someone help me out?

---

### Post by tersogar on 2011-11-27
Go to sound preference to see if the hardware is in order.

---

### Post by Kr1551 on 2011-11-27
> **tersogar said:**
> Go to sound preference.
In preferences, I can't find anything related too sound or audio.

It's like the audio is not installed or something stupid.

---

### Post by tersogar on 2011-11-27
You can try removing and reinstalling ALSA and see if it automagically finds your cards from a clean state.


(1) Remove the ALSA packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
Code:

sudo apt-get install gdm ubuntu-desktop

(3) Reboot

This work for me.

---

### Post by Kr1551 on 2011-11-27
> **tersogar said:**
> You can try removing and reinstalling ALSA and see if it automagically finds your cards from a clean state.


(1) Remove the ALSA packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
Code:

sudo apt-get install gdm ubuntu-desktop

(3) Reboot

This work for me.
This did not work for me :(

---

### Post by tersogar on 2011-11-27
Sorry to hear that. I´m sure that some other member would be able to help you.

---

### Post by Kr1551 on 2011-11-27
> **tersogar said:**
> Sorry to hear that. I´m sure that some other member would be able to help you.
Yes, thank you very much for your help tough it did not work ;)

And yes I hope someone is able to help.

---

### Post by Chav on 2011-11-27
I'm having a similar issue after an update last week. 

It appears to be a pulse audio issue based on running the following from the terminal:

```
tail /var/log/syslog
``` 

```
kernel: [  138.172355] pulseaudio[3058]: segfault at 1b86 ip 0000000000001b86 sp 00007fffbac590d8 error 14 in pulseaudio[400000+13000]
```

---

### Post by Kr1551 on 2011-11-27
> **Chav said:**
> I'm having a similar issue after an update last week. 

It appears to be a pulse audio issue based on running the following from the terminal:

```
tail /var/log/syslog
``` 

```
kernel: [  138.172355] pulseaudio[3058]: segfault at 1b86 ip 0000000000001b86 sp 00007fffbac590d8 error 14 in pulseaudio[400000+13000]
```

So how can I get my sound?

---

### Post by The Eight-Bit Link on 2011-11-27
Ditto with the sound problem. It appears it detects my devices, and I hear pops and clicks occasionally, but otherwise nothing. Reinstalling alsa didn't help, and I'm really close to ditching Ubuntu.

---

### Post by Kr1551 on 2011-11-27
> **The Eight-Bit Link said:**
> Ditto with the sound problem. It appears it detects my devices, and I hear pops and clicks occasionally, but otherwise nothing. Reinstalling alsa didn't help, and I'm really close to ditching Ubuntu.I am really close ditching lubuntu right now.

---

### Post by Kr1551 on 2011-11-27
> **Kr1551 said:**
> I am really close ditching lubuntu right now.Is there no one that can help?

---

### Post by mwa2012 on 2011-12-21
Make sure you were not muted in windows when you last exited(if in a dual boot scenario). That was my situation on a Toshiba Satellite A105 and Ubuntu 11.10 and had no sound upon Ubuntu boot. Removed mute in windows and applied change, booted Ubuntu and works fine. Real simple and took 8 hours of trying various suggested fixes around the internet to get there.

---

### Post by Worp8d on 2011-12-22
I have lubuntu installed fine on my laptop (and I love it - happy to put up with a bug or two while it matures) but I have just installed it on a friend's netbook and I have the no sound problem. I'm not very familiar with hardware management in linux.

There is no volume icon on the task bar. Alsamixer appears to recognise the sound device. Nothing is muted, though I don't seem to be able to change volume in alsamixer.

Audacious comes up with the error "ALSA error - No suitable mixer found."

I'd really like to get this working 'cause if I do then there's one more non-techy linux convert.

---

### Post by Worp8d on 2011-12-22
I found [this thread]("/media/0B3E-67Bhttp://forums.debian.net/viewtopic.php?f=7&t=558366/100 Percent Trance") which seems to point to the problem - that the sound module is not being loaded first.

When I open alsamixer and press F6 to select the sound card the options are

```
- (default)
0 - HD-Audio Generic
1 - HDA ATI SB 

```

Using alsa-info.sh found on [this page]("http://forums.debian.net/viewtopic.php?f=16&t=53708") I found out that ALSA is loading the snd_hda_intel module twice.

I put ```
options snd_hda_intel index=0
``` into /etc/modprobe.d/alsa-base but no joy. Also tried ```
options snd_hda_intel index=1
```.

Then I tried ```
apt-get install --reinstall alsa-base
``` with no effect.

Officially out of ideas.

---

### Post by davidafranklin on 2011-12-23
Hello,

I also have a sound problem but a little bit different. I can hear all the videos but I cannot have a sound working on my Gmail notifier (Firiefox addon) or on the Thunderbird notifier. This is bizare that only some sound do not play. These are wav files. They work fine when I click directly on them and play them with the media player, they just do not play within a program.

Any suggestions?

David
Ubuntu 11.10

---

### Post by dentaku65 on 2011-12-24
I've suggest to edit your alsa-base.conf
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
and at the end of file put:
> #My card
options snd-hda-intel model=auto
Reboot.

---

### Post by davidafranklin on 2011-12-24
I tried and no results.
When putting the 2nd code at the end, nothing seems to happen.
I am not sure if I should try to do all the steps you have mentioned previously as my issue is not exactlky the same. I do have sound (Videos stream, skype...), i just do not have sound thru Thunderbird or Gmail notifier.
Thanks

---

### Post by dentaku65 on 2011-12-24
> **davidafranklin said:**
> I tried and no results.
When putting the 2nd code at the end, nothing seems to happen.
I am not sure if I should try to do all the steps you have mentioned previously as my issue is not exactlky the same. I do have sound (Videos stream, skype...), i just do not have sound thru Thunderbird or Gmail notifier.
Thanks

Can you show the output of:

```
lspci -v |grep audio
```

---

### Post by davidafranklin on 2011-12-24
here you go:

    Subsystem: Toshiba America Info Systems Toshiba Satellite A100-796 audio (Realtek ALC861)

it is bizarre it says this as my laptop is aToshiba  Satellite-M115 S8094

---

### Post by dentaku65 on 2011-12-24
> **davidafranklin said:**
> here you go:

    Subsystem: Toshiba America Info Systems Toshiba Satellite A100-796 audio (Realtek ALC861)

it is bizarre it says this as my laptop is aToshiba  Satellite-M115 S8094


Try this (keeping the modprobe-alsa.conf as I suggested)
```
lsof /dev/snd/*
```
and kill any PIDs
```
sudo killall -9 *PID*
```
Then
```
sudo rmmod snd_hda_intel
```
and
```
sudo modprobe snd_hda_intel
```

---

### Post by davidafranklin on 2011-12-24
tried that, did not work.

---

### Post by MoreOrLess on 2011-12-24
Do you have pulseaudio installed? Actually, post the output from this if you can: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by davidafranklin on 2011-12-25
here you go:

Your ALSA information is located at [http://www.alsa-project.org/db/?f=adfdd818180e558413f9ffd0c77058880c4c6598](http://www.alsa-project.org/db/?f=adfdd818180e558413f9ffd0c77058880c4c6598)

I do not have pulse audio installed, I did not download anything additional to 11.10.

BTW, Merry Xmas All!

---

