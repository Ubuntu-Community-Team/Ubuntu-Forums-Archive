---
title: "Low volume level returns to normal only after resuming from suspend"
date: 2011-12-25
forum: Multimedia Software
---

### Post by hooluupog on 2011-12-25
The system volume of my notebook is too low comparing with using headphone or runing it on windows7. I can hardly hear the sound even if the volume slider was moved to maximum. Today after I had used my laptop for half a day or so ,I opend mplayer to listen mp3 and found the sound is so loud and clear. i ' m so excited. I tried many times to play kinds of movies,mp3 and flash to make sure it's not a cheat. Yep, the sound became loud and clear,it is true.Then I restarted my computer to verify the inconceivability appearance. The sound returned back to low level as before .After trying many times now I can confirm the problem:

The volume is too low to tolerant all the time. Only after resuming from suspend the sound becomes loud and clear enough.But it becomes to low again after restarting or resuming from hibernation. Have you got any suggestions? Thanks in advance.

FYI,

$sudo head -1 /proc/asound/card0/codec#0
Codec: IDT 92HD81B1C5
$aplay -l
List of PLAYBACK Hardware Devices **
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog] Subdevices: 1/1 Subdevice #0: subdevice #0
Alsamixer -c 0
[IMG]http://i.imgur.com/vZKbf.png[/IMG]

---

### Post by hooluupog on 2011-12-26
Is there anyone here? :(

---

