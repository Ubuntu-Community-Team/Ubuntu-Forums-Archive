---
title: "Web Audio Recording Software?"
date: 2011-10-07
forum: Multimedia Software
---

### Post by xdarkknight on 2011-10-07
Hello,
Lately, I have been missing a program I used in Windows called *Audials Tunebite*.  If anyone knows of a comparable program, PLEEEEZE let me know.
I originally purchased it to convert my DRM files to straight MP3 so I could listen to them on my MP3 player. I felt it a little redundant owning a device that wouldn't play it's intended media.
Audials was able to convert from most recognized audio formats to another recognized audio format.  Pretty cool.  I didn't realise this until after I bought it, but the program also records any audio (or video) streaming online through your system. so if you're watching a you-tube clip, it'll record it AND it'll record the title of the clip! This, I later found, made studying easier as I could let it record multiple streams for a while and pop it onto my MP3 device and listen to it at a later time (ie: walking, driving, whatever...).

I've seen a few recorders that sucked up anything audio online, but it wasn't as seamless or as proficient as the original program I'd purchased.
As I said before, if you know of something that works on Lx/Ub11.10, I'd be Much Obliged!

Oh, and I attempted to use wine with the old program. it shows up in the apps menu, but when clicked, it shows the load-up screen, which disappears, then <nothing>.  very frustrating.

Thanks all!
xDk

---

### Post by ajgreeny on 2011-10-07
Look at streamtuner and streamripper, which will do exactly what you want to record streaming audio.

YouTube is a different matter as the "terms of use" you agree to by using it do not permit recording unless the specific clip allows it.

For any sound going through the sound card of a machine you can use ```
arecord filename
```which will record a file as wav.  See ```
man arecord
``` for all the options etc etc.

You can also use mplayer to record streams silently (ie without you hearing them at the same time) as mp3s with the command ```
/usr/bin/mplayer <URL> -dumpstream -dumpfile stream.mp3
```where <URL> is that of the stream, of course.  I use this in a shell script called by cron to time-record some occasional concerts.

---

