---
title: "ffmpeg list_devices has been removed apparently. Can devices be listed? How?"
date: 2013-06-23
forum: Multimedia Software
---

### Post by LeFou on 2013-06-23
ffmpeg's documentation:
[http://ffmpeg.org/ffmpeg-devices.html#Examples-5](http://ffmpeg.org/ffmpeg-devices.html#Examples-5)

Says that 
ffmpeg -list_devices true -f dshow -i dummy

will list devices. But it doesn't
Unrecognized option 'list_devices'

I'm trying to record my screen with sound, as in:
[http://qubodup.wordpress.com/2012/01/03/this-is-how-i-record-my-screen-on-linux/](http://qubodup.wordpress.com/2012/01/03/this-is-how-i-record-my-screen-on-linux/)

which says:
ffmpeg -f alsa -i pulse -f x11grab -acodec pcm_s16le -r 30 -s 1280x720 -i :0.0+1280x720 -vcodec libx264 -crf 0 -preset ultrafast -threads 0 out.mkv

but "-i pulse" isn't valid because "pulse" is not a device, even though pulseaudio is running. I wondered what devices were valid, and that's how I found out about the list_devices option, which has been removed.

Listing devices seems like a useful thing for a multimedia recorder/transcoder to do. Is it still possible?

---

### Post by FakeOutdoorsman on 2013-06-23
I believe "-list_devices" is a private option for the dshow and openal input devices meaning that it is only used with those input devices. Please also show the complete ffmpeg console output for your encoding command and use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) so it displays nicely.

---

### Post by mc4man on 2013-06-23
While I use an ffmpeg laucher that has various scripts (in the quicklists) for screen capture, your command isn't that different.
Ex. of one with audio- 
```
#!/bin/bash
NOW=$(date +"%b-%d-%y-%H:%M")
gnome-terminal --geometry=20X4  -x ffmpeg -f alsa -i pulse -f x11grab -r 24 -s 1280x800 -i :0.0 -c:v libx264 -preset ultrafast -crf 0 -c:a pcm_s16le  ./Videos/screens/$NOW.mkv
```

What you do need to  is do a one time setup of pulseaudio, there's likely a thread about that may describe how in detail & any variance for 'what you hear' vs. a mic.

In any event it needs to be done in pavucontrol, not sound setting. Basically just start ffmpeg recording with sound, then open pavucontrol > recordings & switch to the 'monitor of ...' option.
You only need to do this once, from then on 'monitor of ..' will be auto-selected for ffmpeg ( at least the real FFmpeg
screen shows
(pavucontrol is not default installed on Ubuntu

---

