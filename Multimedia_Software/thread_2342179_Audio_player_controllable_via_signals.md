---
title: "Audio player controllable via signals?"
date: 2016-11-04
forum: Multimedia Software
---

### Post by cbraxton on 2016-11-04
Is there an audio player available that can be launched from the command line, run in the background, and controlled via software signals from another process? This would be to do basic functions like play the next or previous file in a playlist. (Obviously any player can be terminated by sending  SIGKILL (9) or SIGTERM (15).) I've looked at the man pages for several players and don't see anything about using signals.

---

### Post by TheFu on 2016-11-04
Know about a few tools that can be remotely controlled. How they do it isn't something I know - doubt they use signals.  Probably a REST protocol or JSON-RPC or named-pipe.
Clementine is one.  
[https://www.mopidy.com/](https://www.mopidy.com/) is another that uses mpd ... 

mpd is a standardized protocol for this stuff. [https://www.musicpd.org/clients/](https://www.musicpd.org/clients/)

Of course, I could be completely missing the point since you want to control via signals.

---

### Post by cbraxton on 2016-11-04
I was looking for an easy way to control playback from a wrapper program, and signals seemed like a simple way to do it if there were a player that used them.  A possible alternative method might be to use cmus.  Its companion program cmus-remote controls cmus playback via a socket.  Also pretty simple.

---

### Post by TheFu on 2016-11-04
named-pipes are really easy to use for that purpose. REALLY SIMPLE.  The writer is the controller. The reader does what the cmds request. Very simple.

---

### Post by kostkon on 2016-11-04
Actually, many players nowadays implement the [MPRIS interface]("https://specifications.freedesktop.org/mpris-spec/latest/") which is a freedesktop standard to control media players over D-Bus, which in turn is more or less the default IPC in Linux (for now, since the Linux kernel will soon have its own IPC and will render D-Bus obsolete at some point, but that's another story).

D-Feet is a useful app in this case because it will allow you to experiment with D-Bus and MPRIS in particular before writing any code.

If you want to use bash, then there is dbus-send for that same purpose, just
```
man dbus-send
```
for more info.

Hope that helps.

---

### Post by gordintoronto on 2016-11-05
This doesn't answer your question, it's an alternative approach.

I bought an HP 5189 keyboard used for $4, and it has a complete set of playback control keys. Audacious and VLC respond to those keys, even when they are in the background.

---

### Post by TheFu on 2016-11-05
> **gordintoronto said:**
> This doesn't answer your question, it's an alternative approach.

I bought an HP 5189 keyboard used for $4, and it has a complete set of playback control keys. Audacious and VLC respond to those keys, even when they are in the background.

We can remap any key or chord of keys to run any program on Linux.  **xdotool** is one way, but many WMs will let us run whatever programs we like.  I have volume controls for mute, increase/decrease tied to Super-F-keys.
```
amixer -q sset Master 3%+
amixer -q sset Master 3%-

```
Same for LCD brightness. 
```
xbacklight + 10
xbacklight - 10

```
My chromebook doesn't have a DELETE key (drives me crazy!), so Ctl-Bksp is DELETE.
```
xdotool key --clearmodifiers Delete
```

Anything you can imagine is probably possible, if it can be done without using a mouse. ;)  Which reminds me, I need a way to restart pulse audio, since it crashes all the time.

---

