---
title: "Stop screensaver when MPlayer is in fullscreen mode."
date: 2015-06-18
forum: Multimedia Software
---

### Post by Rytron on 2015-06-18
Hi.

I use MPlayer sometimes to play videos at e.g. 1.21x speed. In full screen, the screen dims (screensaver). This never happens with VLC.

I am using MATE.

Is the best option to add line(s) to '~.mplayer/config'?

Thanks.

---

### Post by papibe on 2015-06-18
Hi Rytron.

A few thoughts:

If you use SMplayer, which is just a GUI for mplayer, you can disable by going to:
```
Opions -> Preferences -> General -> Video -> Disable screensaver
```
(unless there a regression to a bug in 2010, the should work).

If that's doesn't work, or you want to stick to plain mplayer, I've had success in the past by using the 'heartbeat-cmd' option on the mplayer config file.

Either this:
```
heartbeat-cmd="gnome-screensaver-command -d"
```
or this:
```
heartbeat-cmd="xscreensaver-command -deactivate"
```
should work depending on the screen saver you are using.

Hope it helps. Let us know how it goes.
Regards.

EDIT: apparently things have change since I did this. The gnome-scereensaver option now is -d not -p.

---

### Post by Rytron on 2015-06-19
Hi papibe.

I decided to add these 2 lines also to the mplayer config file:
```

heartbeat-cmd="mate-screensaver-command -d"
heartbeat-cmd="mate-screensaver-command -deactivate"

```

I'd use SMPlayer if it could play videos at speeds such as 1.25, etc.

---

### Post by Rytron on 2015-06-28
@papibe

Ok, last night I watched a movie to test this out. No joy. I even tried 'Caffeine Plus' but still no joy.

By the way, I looked in Synaptic and it says I have **mplayer2** installed. Would this matter that it is that and not **mplayer** installed?

This is my mplayer config contents:

```
# Write your default config options here!
zoom=yes
vo=x11
ao=alsa

vf=screenshot

#heartbeat-cmd="gnome-screensaver-command -d"

heartbeat-cmd="mate-screensaver-command -d"

heartbeat-cmd="mate-screensaver-command -deactivate"

#heartbeat-cmd="xscreensaver-command -deactivate"

# From Manjaro Wiki:
[default]
ao=pulse
vo=vdpau
dr=1
use-filedir-conf=1
noquiet=1
msglevel=all=5
noslices=1
double=yes
framedrop=0
hardframedrop=0
vsync=1
ac=ffmpeg,ffmp3,mad,mp3acm,mpg321,
srate=48000
format=s16le
channels=6
cache=8192
cache-min=50
softvol=yes
volstep=2
volume=50
softvol-max=50
```

:mad:

---

### Post by mc4man on 2015-06-29
> **Rytron said:**
> 

I'd use SMPlayer if it could play videos at speeds such as 1.25, etc.
It can play at any speed you wish, either thru the menu item  Play > Speed or thru keyboard bindings 
(by default +- 10% is already set @ [ or ],  other % bindings can be set (Options > Preferences > Keyboard & Mouse

---

### Post by Rytron on 2015-06-29
> **mc4man said:**
> It can play at any speed you wish, either thru the menu item  Play > Speed or thru keyboard bindings 
(by default +- 10% is already set @ [ or ],  other % bindings can be set (Options > Preferences > Keyboard & Mouse
 
Ah, nice one. I stand corrected. Cheers mc4man. Kudos.

---

