---
title: "Can't unmute using amixer"
date: 2011-07-04
forum: Multimedia Software
---

### Post by soulspit on 2011-07-04
Alright folks, here is the situation. I want to make a program that *prevents *me from muting or turning down my computer's sound (this is for an alarm clock program - I'm a heavy sleeper and I'm trying [polyphasic sleep]("http://www.google.com/search?q=polyphasic+sleep") so I really need a clever and good alarm). The way I want to do this, rather hackishly, is to just run a little script that loops forever unmuting the sound every second.

The only problem is that ```
amixer -c 0 set Master 100% unmute
``` doesn't work. If I mute using amixer, then unmute using amixer is successful: it unmutes. However, if I mute my computer using my *laptop's* mute button, amixer doesn't appear to do anything.

What's strange is that it *appears* to work. For example, if I press the mute button on my keyboard, I can do this:```
toby@tensile:~$ amixer get Master
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 57 [89%] [-5.25dB] [off]
toby@tensile:~$ amixer set Master 100% unmute
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
```You can see that, after having pressed the mute button, I can using amixer get to show the status of Master, and it shows the volume at 89% and that it is switched off - muted. When I issue the second command, it sets the volume to 100% and seems to think it has switched it on. But I hear no sound.

I have tried increasing the volume by an increment, using 'toggle' and everything else I can think of, but nothing works. Modifying the volume works fine - if I turn down the volume using my laptop's volume control, I can successfully turn it back up with amixer. What's the deal? Any help would be very appreciated!

---

### Post by soulspit on 2011-07-04
Oh! I fixed it. Turned out that the mute button on my keyboard was doing a lot more than just muting the Master channel. It was also muting the Headphone and Speaker channel. Strangely, if I hit the mute keyboard while alsamixer was open, it *didn't* show this, but if I muted and *then *opened up alsamixer, I saw that the other channels were muted.

In addition, when I turn the volume down all the way using my keyboard's volume control, it only affects the Master channel, except when the volume turns to 0%, the PCM channel's volume goes to 0%, so in order to turn the volume back up, that needs to be dealt with as well.

If anyone is interested, here is my "don't let the user mute or turn down the volume!" script:

```
#!/bin/bash 

# takes a volume level from 0 to 100, inclusive, as command line argument
# every second, this program unmutes various channels and sets the Master volume to that volume, ensuring that the user hasn't turned the sound off or down

while true; do
  amixer set Master $*% unmute > /dev/null # $* gets volume from command line arg
  amixer set Headphone unmute > /dev/null
  amixer set Speaker unmute > /dev/null
  amixer set PCM 100% unmute > /dev/null
  sleep 1
done 
```

Marking this thread as solved. Thanks Ubuntu Forums, you're great to bounce ideas off of!

---

### Post by aeiah on 2011-07-04
why dont you invoke your script via crontab just before your alarm is due to go off? probably less messy than changing the volume every second of the day (or night)

---

### Post by ayourk on 2011-12-05
I was reading some other posts and found the correct solution:

```
amixer -c 0 set Master **playback** 100% unmute
```

The key is to use the word **playback** in the command line otherwise it will touch the other mutable mixers.

---

### Post by klo on 2012-06-19
In case anyone is still having problem with this in 12.04 (Precise) and looking for a one-liner to assign to a hotkey:
```
/bin/bash -c 'amixer set Master unmute && amixer set Headphone toggle'
```

---

### Post by xdzzz on 2013-01-05
I had the same exact problem.
After muting using 'toggle', unmuting was impossible.
Although, I discovered a really simple workaround.

Instead of using the following to mute:
**amixer -c # sset Master toggle**

Use:
**amixer -c # sset Master 0%**

Then, to unmute, simply raise the volume up:
**amixer -c # sset Master 5%+**

** # is the device number.

---

### Post by mutz on 2013-05-20
The following works to toggle all channels via pulse, 

```

amixer -D pulse set Master toggle 
```

[Adapted from the end of [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496354](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496354) ]

---

