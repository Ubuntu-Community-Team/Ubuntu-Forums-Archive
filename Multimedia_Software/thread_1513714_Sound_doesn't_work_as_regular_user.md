---
title: "Sound doesn't work as regular user"
date: 2010-06-19
forum: Multimedia Software
---

### Post by conman124 on 2010-06-19
Hello,

EDIT2:  Uh oh.  The sound just stopped working as root.  I don't know what I might have done, but I'll try to fix that.

**EDIT3: I got it to start working again.  The sound now works completely.  For future reference, I did "sudo apt-get remove pulseaudio* alsa*" and then "sudo apt-get install alsa-base alsa-oss" and "sudo apt-get install pulseaudio pavumeter paman paprefs" and then messed around a bit with the pulseaudio config.  Linux really needs some serious work on getting sound to work out of the box!**

I am having a problem with sound.  If I run
```
**sudo** exaile
```I am able to play sounds just fine.

However, if I run
```
exaile
```**as a normal user**, I cannot play sounds.  I do not get any error messages, it just does not play.

I am using pulseaudio.  The output of "groups connor"
```
connor : connor adm dialout cdrom floppy audio dip video plugdev lpadmin pulse pulse-access admin sambashare
```I **am** a part of the audio, pulse, and pulse-access groups.

I think part of the problem is that as a normal user, I am unable to see the sound card.  The output of the command "aplay -l" **as a normal user** is
```
aplay: device_list:223: no soundcards found...
```but as root it is
```
**** List of PLAYBACK Hardware Devices ****
Home directory /home/connor not ours.
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I have been banging my head against the table for a couple of hours over this, so any help would be greatly appreciated!

EDIT: I just tried adding myself to the root group (temporarily). ** It still does not play sounds!!** However, I get the same output for "aplay -l" as I did as root.  I realize this is horribly insecure, and I don't want this to be part of the solution.

Thank you,
Connor

---

