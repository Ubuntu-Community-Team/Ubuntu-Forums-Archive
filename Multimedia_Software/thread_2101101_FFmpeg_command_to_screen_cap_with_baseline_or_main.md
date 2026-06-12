---
title: "FFmpeg command to screen cap with baseline or main profile?"
date: 2013-01-03
forum: Multimedia Software
---

### Post by mc4man on 2013-01-03
To test a break in totem would like a command that uses anything but I currently get with ffmpeg screen caps which is always - 
"Format profile  : High 4:4:4 Predictive@L3.2"

(or a command to re-encode ^ using another profile, -  baseline, main or high, anything but the above

---

### Post by FakeOutdoorsman on 2013-01-03
You're probably making a lossless output with libx264. main and baseline are not compatible with lossless, so you can re-encode if you want a difference profile.

```
ffmpeg -i input -c:v libx264 -crf 24 -preset medium -profile:v baseline -c:a copy output.mkv
```

Might want to add "-pix_fmt yuv420p". I recall some ffmpeg versions will  automatically convert to 4:2:0 and others will try to do less sub-sampling depending on the input, but although technically "good" it can result in an output that won't work in crappy players like Quicktime.

You generally don't have to declare a profile unless your playback device is restricted to certain profiles.

See [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for some more info.

---

### Post by mc4man on 2013-01-03
It's just to test at what point, (profile), totem stops decoding, not that I really care about totem but some may be using totem.

Normally for caps that I do to pass along to some friends I'm using a launcher icon to run a small script.
The command for ffmpeg in the script  would be - 
```
ffmpeg -f x11grab -r 24 -s 1280x800 -i :0.0 -c:v libx264 -preset medium -crf 24  ./Videos/screens/$NOW.mp4
```
This ^ always produces High 4:4:4 Predictive@L3.2

The above won't accept -profile:v baseline or -profile:v <anything other than high444>

If I was to try to re-encode from above using basically what you posted get the same fail - 

x264 [error]: baseline profile doesn't support 4:4:4
[libx264 @ 0x3320bc0] Error setting profile baseline.
[libx264 @ 0x3320bc0] Possible profiles: baseline main high high10 high422 high444

So I'm gathering - 
can't do a direct cap using a -profile:v <anything other than high444>, at least how written in script
&
can't re-encode something done as High 4:4:4 Predictive@L3.2 to another profile

not that it matters but script is below, script is then the Exec= on launcher

```
#!/bin/bash
NOW=$(date +"%b-%d-%y-%H:%M")
gnome-terminal --geometry=20X4  -x ffmpeg -f x11grab -r 24 -s 1280x800 -i :0.0 -c:v libx264 -preset medium -crf 24  ./Videos/screens/$NOW.mp4
```

---

### Post by mc4man on 2013-01-05
> Might want to add "-pix_fmt yuv420p". I recall some ffmpeg versions will automatically convert to 4:2:0 and others will try to do less sub-sampling depending on the output....

Think I finally got the idea or near enough for this limited use case (screen cap that works with totem. 
If using a -profile:v <something> you need to use a compatible  -pix_fmt <something> in command. 

(seems atm totem support goes to 'high' level*

---

