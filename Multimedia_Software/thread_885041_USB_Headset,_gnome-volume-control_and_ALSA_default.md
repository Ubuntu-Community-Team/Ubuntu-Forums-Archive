---
title: "USB Headset, gnome-volume-control and ALSA defaults..."
date: 2008-08-09
forum: Multimedia Software
---

### Post by cult hero on 2008-08-09
I've been wracking my brain today trying to mess with the sound configuration in Ubuntu. (For the record, I updated everything this morning so I'm running the latest and greatest in Hardy.) Here's what I've noticed and I'm trying to see if any sound experts can at least explain things (I know google is my friend, but... issue #3 makes searching really complicated). I have two sound devices: a USB headset for gaming and my onboard audio. In my tinkering I noticed one thing in particular that was odd to me.

Issue #1: While attempting to figure out some issues related directly to my USB headset, I rebooted my machine, went into the BIOS and completely disabled my sound card. I wanted my USB headset to be the only sound device on the machine as a sort of clean slate to try and troubleshoot. At first, I had no sound at all. I changed the settings in administration->sound and could hear the test tones fine, but that didn't make Pidgin or Flash in Firefox work at all. I then tried running alsamixer from the command line and got an error. By default it wants to load "card 0" and even with my sound card completely disabled, my USB headset was still card 1. I did some looking and used the command "asoundconf set-default-card Headset." That solved the problems for the most part EXCEPT that when I boot up, I still get no sound until my user settings load. No big deal but I'm curious, where is the conf file or whatever that remembers my sound card even after it's disabled? I have no /etc/asound.conf. Or if it's not a conf file, does ALSA automatically set a USB device to a nonzero position?

Issue #2: gnome-volume-control is broken with my USB headset. I've seen this error reported all over the place but I haven't seen any actual solutions. I can adjust the volume just fine from alsamixer, but if I try from gnome-volume-control my left channel always drops down to no sound and jumps around like crazy. In fact, if gnome-volume-control is open at all, trying to adjust the sound in alsamixer produces the same results. Close gnome-volume-manager and all is well. Is there somewhere I should report this problem or has someone finally found a solution?

Issue #3: This one is kind of weird. When I pull up alsamixer for my USB headset, I have two items in playback, not one as I would have thought. In the first slot of "Playback" I have "Mic" (mono) and in the second I have "Speaker" (stereo). Why is "Mic" listed in playback? I have "Mic Capture" available in the "Capture" as well. This is particularly annoying because if I use the buttons built on top my headset to adjust the volume or the volume keys on my keyboard, it affects the "Mic" setting, which seems to do nothing, rather than the speaker setting. (Of course, as a result of #2, it wouldn't work anyway, but I'm still wondering how to work around this presuming #2 is ever solved.)

Let me add, for the record, that I have had no sound issues when using my onboard sound (an older nForce chipset) and everything worked wonderfully out of the box. This came as the result of seeing that Dark Crusade works under Wine and I wanted to test some Linux gaming for fun. The headset is so I can use Teamspeak or something similar. Ubuntu is working great and I simply don't want anyone to get the idea that this is some massive grievance, but it is a curiosity.

---

### Post by markip on 2008-08-20
so, in short version, did you manage to have any sound in firefox with the usb headset? Or only with the sound card? If you did manage to have sound with the usb headset, how you did it?

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers. In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb headset, your laptop speakers will take over.  In order to re-establish contact with the usb headset, you will need to (plug it back in) restart the system.

---

### Post by markbuntu on 2009-09-08
If you are using hardy you should read this


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For more on multiple sound hardware devices read this

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

