---
title: "PulseAudio is to Montague as ALSA is to Capulet, as far as Skype is concerned"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Kevanx on 2010-05-08
Yet another Microphone issue.
Skype has worked perfectly with both PulseAudio and Alsa running on my system, but somewhere along the line it broke.
Currently running lucid lynx 64-bit.

I've spent about 5 hours on this so far, and I've looked high and low for a solution.

Microphone won't work at all, unless I run:
```
alsamixer
```
and bump the "front mic boost" to 50% or more, but then the static is horrible.

Under Skype preferences, I can't choose anything except "PulseAudio server (local)", which I believe to be at the heart of the problem.

I've tried the following:
1. Installing padevchooser and pavumeter (wasn't sure how to choose other devices, or if it should be automatic).
2. Uninstalling pulseaudio altogether (purge), with reboot.
3. Selecting different audio inputs, fiddling with both alsamixer and pavumeter controls.
4. Coudn't find a 2.0 build of skype AMD64 to downgrade, nor could I find it in repositories after enabling medibuntu.

The only time the volume ever sounded clean was after uninstalling PulseAudio, but it was FAR too quiet to be useful, and it broke my media keys, as well as Emerald/Compiz, strangely enough.

Oh, and Soundrecorder works fine, naturally.
Thanks in advance.

---

### Post by lidex on 2010-05-08
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Reboot.

---

### Post by Kevanx on 2010-05-09
Followed the commands you gave to the T, no errors in installing, but it didn't work.

I'm not sure what it was supposed to accomplish, but I still only have PulseAudio Server (local) as a choice in skype, and still no recording without crazy static.

Thanks for your help. Any other suggestions?

---

### Post by j-dowsett on 2010-05-12
I've just created this problem for myself!

[background - in case someone has any ideas!]
I had awful sound quality after upgrading to 10.04, even though 5.1 was selected in hardware sound would be some awful stereo unless I selected a non-5.1 option and then reselected 5.1.  However as soon as a new track started it would resort to bad stereo.  And even when it was 5.1 there was a bad background hiss to it - never sounded as good as in 9.04
[/background]

Just ran the alsa update script and proper sound is now restored, but it's disabled Pulseaudio (so I've no panel volume control....), and so Skype no longer works as it indeed only lists PulseAudio in the hardware options.

Any suggestions to get Skype to use Alsa?

---

### Post by lidex on 2010-05-12
Kevanx: Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Kevanx on 2010-05-14
I have a System76 Serval Performance (SERP3) laptop purchased ~March 08. Let me know if you want particular component details, apart from what's listed below.

```

uname -a
Linux ubuntu-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

aplay -l
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May  8 2010 for kernel 2.6.32-22-generic (SMP).

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC268

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054
```

Thank you so much for your help on this - I hope at some point I can pay it forward!

---

### Post by lidex on 2010-05-14
Do you have the system76 driver installed?
[http://planet76.com/repositories/]("http://planet76.com/repositories/")

---

### Post by Kevanx on 2010-05-18
Yes, I have the system76 driver installed, and it's up to date.

BTW, I just installed the update:
linux-alsa-driver-modules-2.6.32-22-generic

but it didn't solve the problem.

Thanks.

---

### Post by lidex on 2010-05-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

If that doesn't work try:
```
options snd-hda-intel model=3stack
```

---

### Post by Kevanx on 2010-05-19
Before I noticed this post, I solved the sound issue myself!

In the linux-alsa-driver-modules-* update, it installed a heap of utilities, namely:
alsamixergui

In opening that, I found that the sound levels were way off on the "capture" variable - the left channel was max, the right was almost muted. It didn't respond when I tried to adjust it either - it wasn't locked, but it seemed to jump to different volumes at random when I tried to adjust it, regardless of whether the levels were locked together or not.

Once I got those even, and down to about 50%, alsamixer was able to adjust the sound levels properly, and skype works fine now!

Thanks for your help and attention, lidex! Hopefully if someone else has the same problem, one of these solutions will work.

---

