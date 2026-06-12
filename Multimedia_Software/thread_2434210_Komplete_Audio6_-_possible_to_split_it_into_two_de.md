---
title: "Komplete Audio6 - possible to split it into two devices for Pulse Audio?"
date: 2020-01-01
forum: Multimedia Software
---

### Post by milanoan on 2020-01-01
Hi
The Komplete Audio 6 audio interface has 4 output channels that I'd like to be able being used by two different programs -  one stereo output each.
How can I configure that.
[Here]("https://ubuntuforums.org/showthread.php?t=1821115&page=3") is already a solution to configure various output configurations, but this is only available globally for all applications.
Would it be possible to have two different audio devices addressing that same interface, so that for example clementine could use channel 1+2 and vlc channel 3+4?
Thanks
Milan

---

### Post by milanoan on 2020-01-03
Here is what I've tried:
Created udev rules file:
```
/lib/udev/rules.d/91-komplete-audio6.rules

```
With this content
```
SUBSYSTEM!="sound", GOTO="pulseaudio_end"
ACTION!="change", GOTO="pulseaudio_end"
KERNEL!="card*", GOTO="pulseaudio_end"

SUBSYSTEMS=="usb", ATTRS{idVendor}=="17cc", ATTRS{idProduct}=="1001", ENV{PULSE_PROFILE_SET}="native-instruments-komplete-audio6.conf"

LABEL="pulseaudio_end"
```
Then created
```
/usr/share/pulseaudio/alsa-mixer/profile-sets/native-instruments-komplete-audio6.conf
```
with the appropriate content, see [this]("https://ubuntuforums.org/showthread.php?t=1821115&page=3") thread 

So far this is what ubu_dynamite has proposed in the linked thread.
Then I duplicated these files with an attached B to the filename and a changed number: ```
92-komplete-audio6B.rules
native-instruments-komplete-audio6B.conf
```.
I also adapted the udev rule's content like this:
```
ENV{PULSE_PROFILE_SET}="native-instruments-komplete-audio6B.conf

```
In the two native-instruments-komplete-audio6()/(B).conf-files I changed settings for channel 1/2 and 3/4 respectively for () / (B)-variant, only audio inputs for the ()-one
Result is that the B-files are used, the others ignored (overwritten while pulseaudio -k execution??)

Unfortunately, I don't understand very well what happens between udev, alsa and pulseaudio, and how they have to be configured to achieve my goal.
I'm grateful for any fructual hint!

---

