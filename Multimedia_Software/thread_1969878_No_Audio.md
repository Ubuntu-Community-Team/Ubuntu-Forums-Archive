---
title: "No Audio"
date: 2012-04-30
forum: Multimedia Software
---

### Post by Halsafar on 2012-04-30
Not alone.

Following the steps at: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Here is my ALSA-INFO:
[http://pastebin.com/YuBN9t3z](http://pastebin.com/YuBN9t3z)

This command does generate sound:
aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav

Added the default PCM line to asound.conf, did not fix anything.

No users get sounds, XBMC no sound, VLC no sound.  I can't even use the System Settings -> Sounds -> Hardware Tab -> Test speakers, none of the options can produce sound.

This is a HTPC, running an upgrade from 11.10 to 12.04.

---

### Post by Halsafar on 2012-04-30
I will add, the sound indicator icon does not appear once logged in.  I've used alsamixer to make sure nothing of importance is muted.

---

### Post by Halsafar on 2012-04-30
Adding the following to rc.local

killall pulseaudio; rm -r ~/.pulse*


This fixed ALSA, oddly, which makes no sense.  VLC can properly stream over ALSA and my hw1,7 device (NVIDIA HDMI).

Pulse seems toast, no sound indicator in gnome, XBMC won't play anything on any setting.

---

### Post by BicyclerBoy on 2012-04-30
Forget the built-in gnome sound applet..
You don't need to fiddle with asound.conf because alsa is working okay..
I would remove your re-definition of default..

The HDMI audio codecs are found (aplay -l)
alsa works (aplay)
Hot plug HDMI events okay
ELD for TV okay..(check /proc/asound/card1/eld#1.0)

Pulse audio or the stupid gnome sound applet is at fault.
Run pavucontrol & see if your HDMI codec is listed..

Do you want system wide sound over HDMI?

You can point VLC & XBMC directly at hw:1,7..
vlc --aout alsa --alsa-device hw:1,7 (or similar)

System wide &/or make appear in pulse:
If pulse/pavucontrol does not list your HDMI out device then you can edit
#/etc/pulse/default.pa
load-module module-alsa-sink device=hw:1,7
#must be only one entry module-alsa-sink in file..

---

