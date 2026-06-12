---
title: "MPlayer and VLC  playback problems"
date: 2009-06-20
forum: Multimedia Software
---

### Post by StrangersInTheDark on 2009-06-20
Hi, I have been running Ubuntu for a while. So I decided to throw it on my laptop. I have my laptop hooked up to my bigger monitor screen. I was watching videos fine and then the next day neither Mplayer or VLC worked...

When I open up a mpeg, avi, xvid etc in Mplayer or VLC player it opens for 1 second and automatically closes.

I don't understand why it is doing this and I been at it for a few hours. However, if I play an mp3 file it works fine (weird? Yes) haha

Sometimes after the 3rd attempt at opening a video file with VLC it will stay open and I can hear sound, however the picture is just a bluescreen. 

Any feedback would be appreciated.

----Basic run down for Mplayer and VLC problems ------

Open video file and within 1 second the application automatically closes.

---

### Post by mc4man on 2009-06-20
When players open and close quickly (crash) most times it's the audio and or video output being used.
You could try opening vlc - tools - preferences and click the video icon, for 'output' maybe try  changing from 'default' (which most likely is Xv)    to X11 and click save.

If that works then for mplayer that depends if by MPlayer you mean Movie player (totem-gstreamer) or mplayer

For totem (which I never use) the setting is probably in multimedia selector (an option in System -> Preferences that's not enabled by default 
Go alacarte in a terminal and highlight system -> preferences and enable in r. side column, then open from System -> Preferences menu (under video tab, change from 'autodetect to X window system (no Xv)

Or just run from a terminal
> gstreamer-properties

---

### Post by StrangersInTheDark on 2009-06-20
Awesome man! Awesome!!! Thanks a lot for the help. It worked for both Mplayer and VLC player... I program a lot but I need my movie breaks. You know what I mean? Or else I will flip out hahah 

Thanks again!

---

