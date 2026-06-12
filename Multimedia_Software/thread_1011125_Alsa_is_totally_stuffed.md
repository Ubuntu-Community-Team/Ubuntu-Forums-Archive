---
title: "Alsa is totally stuffed"
date: 2008-12-14
forum: Multimedia Software
---

### Post by sonicb00m on 2008-12-14
Intrepid

Today my alsa just stopped working out of the blue I got this annoying message when testing it in the manager.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

Totally hopeless.

:mad:

First my Terratec 2496 card stopped working so I tried reconfiguring, purging etc, reinstalling but no go. So I took the card out and enabled the onboard which is an Intel ICH8 or something and it's the same problem.

I have gone through a few guides on the net but nothing is working, now I'm so stuffed not even the sound cards are appearing in the sound manager anymore, even the usb-audio one is not appearing.

I'm getting really pissed off with my sound doing this every once in a while and am fed up wasting time on it.

How can I force the alsa to be returned exactly as on first setup? As if I just installed Ubuntu, as it always used to work out of the box.

I am suspicious that some update permanently broke it.

---

### Post by linux_tech on 2008-12-14
Check this reference for some useful troubleshooting info,
including a way to restore ALSA to the Ubuntu default-
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

this will reset alsa settings-
```
sudo /etc/init.d/alsa-utils reset
```

---

### Post by sonicb00m on 2008-12-14
yeah thanks for replying but i've been through that guide already and no show.

I even tried booting the current intrepid build and it actually wouldn't play back either!

I know it works because I 710 installed on another partition and the sound was playing back fine.

I am suspecting an update has rendered my particular set up useless.

---

### Post by benerivo on 2008-12-14
Have you also tried it ouside of a desktop session. If you log out and Ctrl+Alt+F1 and use this command, it should try to play using alsa```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

---

### Post by Richard-g8jvm on 2008-12-14
Hi
pulseaudio could well be the culprit, I've had major problems as I run two cards.
Disabling pulseaudio allows me to use both cards, especially as the delta 66 uses alsa as the back end.
Pulseaudio is difficult to disable as  its dependant on other apps, the easiest way to check if Pulseaudio is the culprit, find the binary and alter the permissions so it cant run, then reboot.

HTH its quick and dirty but its an easy way too find if pulseaudio is the culprit.


Richard

---

### Post by markbuntu on 2008-12-14
For a quick guide to getting Intrepid sound working:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For more extensive help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have 2 sound card and another 2 usb audio devices. Pulseaudio is the only easy way I found to have control over them all individually or together. I also use pulseaudio with jack seamlessly integrated which you can find out how to do in the link above.

---

### Post by vikigal on 2008-12-14
Hi, 
I am running 8.04 Hardy, Kernel Linux 2.6.24-22-generic, GNOME 2.22.3  Hardware memory: 495.0 MiB
Processor 0: Intel(R) Pentium(R) 4 CPU 3.00 GHz   Processor 1: Intel(R) Pentium(R) 4 CPU 3.00 GHz  available disk space: 60.4 GiB


I am also having sound problems. I can hear from any input except my cd drive. In sound preferences running the various test sounds I can hear from everything except the audio conferencing, sound capture device playback. I get a slight scratching sound on some devices, nothing on others, when I run the test sound.

 When I checked group this is what I found:

oldgal1@user-desktop:~$ grep 'audio' /etc/group
audio:x:29:oldgal1,pulse

As a novice, I am curious about pulse being in there. Could it be causing the problem?

I had bad sound, scratchy, so I uninstalled-reinstalled alsamixer via the terminal following directions but still no fix. Now it refuses to mount the drive at all and keeps telling me there are no media files. I tried mounting manually but I didn´t do it right because it lost it.

Would removing pulse from this group change anything? How do I do it if so? 

Thank you for your patience.

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cfba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9730     1486012+   5  Extended
/dev/sda5            9546        9730     1485981   82  Linux swap / Solaris
oldgal1@user-desktop:~$ 


oldgal1@user-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

See anything wrong here?  I welcome any and all comments, suggestions, and help.

vicky

---

