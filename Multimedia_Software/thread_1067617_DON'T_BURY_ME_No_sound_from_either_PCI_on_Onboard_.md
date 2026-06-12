---
title: "DON'T BURY ME: No sound from either PCI on Onboard sound"
date: 2009-02-12
forum: Multimedia Software
---

### Post by Quirriff on 2009-02-12
I installed Ubuntu 8.10 64 bit on my system after disabling the Onboard Sound in the BIOS.

I have an Audigy Value Sound Card and it's detected, my speakers are plugged in properly.

I have also connected a digital output monitor that appears to have audio out, and it appears in the audio devices.

I'm getting no sound out of my speakers whatsoever, even after re-enabling Onboard sound in the BIOS, and using the motherboard's sound ports.

---

### Post by kostkon on 2009-02-12
Set you sound playbacks in *System &#8594; Preferences &#8594; Sound* to Autodetect (and if you want your sound inputs to *PulseAudio*) and then install the *PulseAudio Device Chooser*. Run it (it'll be in *Applications &#8594; Sound & Video*) and then left-click on its icon in your tray and select *Volume Control*).

There you will be able to set the default input and output device (in *Input Devices* and *Output Devices* tab. Right-click on the device and enable the *Default* option) among other things.

In the *Playback* tab you should see the audio streams of the various applications running that produce audio. You will be able to send the audio streams of the applications from the one device to another in real-time by right-clicking on them and selecting *Move Stream...*, etc.

Thus, you don't necessarily need to disable your on-board sound card.

Hope that helps.

---

### Post by Quirriff on 2009-02-12
Problem is I tried that.

I've tried all preference and pulse audio settings and nothing is working.

Enabled everything, maxed out volume on everything.

Changed devices, even tried giving up and switching to onboard sound but that didn't work either.

Call me paraniod but I think there might be a conflict because of the monitor.

PS: I'm going to see if it's anything to do with 64-bit, So i'll boot with a 32-bit live CD (Since a 64 bit live CD didn't work either)

---

### Post by kostkon on 2009-02-12
OK.

But, have you checked your volume levels? I mean, right-click on your speaker icon in your system tray and select *Open Volume Control...* To add more volumes, select *Edit &#8594; Preferences*. To change the sound card that is selected, select *File &#8594; Change Device*.

Also since you have an *Audigy*, make sure that the *analog/digital* switch is disabled.

Or, you can access your volumes using *alsamixer*, by giving in a terminal
```
alsamixer -Dhw:0
```
and
```
alsamixer -Dhw:1
```
since you have two sound cards.
Also, press F4 to access more volumes.


Also, check these guides for some more info, you may find something useful for you.

- [PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")
- [Multiple Sound Solution (ALSA w Pulseaudio)]("http://ubuntuforums.org/showthread.php?t=843012")

---

### Post by Nickedynick on 2009-02-12
I don't know if this will help, but I found that my sound didn't work by default on my Audigy 2 card - this fixes it.

Go to the volume icon on the top right, right click and go to 'Open Volume Control'. Go to the Switches tab and uncheck 'Audigy Analog/Digital Output Jack'. If the tab isn't there, try searching for it with the Preferences button.

As I say, I'm not sure if this will be useful since I'm not familiar with the Audigy Value cards but I thought I'd throw it out there :)

---

### Post by Quirriff on 2009-02-12
I decided to eliminate some variables.

Since I changed the Hardware configuration on this Computer by adding a Video Card, Sound Card, and a DVI monitor, and disabled my onboard sound before reinstalling ubuntu. I couldn't be sure what was causing the problem.

So I removed all the hardware I added, and readded them one by one.

The problem seems to be the Sound Card, I havn't readded it yet, but the onboard sound works well ATM.

But it was strange, The exact same sound card worked fine in my Old Xeon, and that was running ubuntu 8.10 and all I needed to get it working was disable the onboard sound since changing the preferences did nothing.

The only real difference was this system was 64 bit, and the old one was 32 bit.

I'll try those suggestions tomorrow after physically installing the Card again, Because I've worked for days on this problem, and now that I have at least onboard sound. I want a rest.

Thanks for the help.

---

