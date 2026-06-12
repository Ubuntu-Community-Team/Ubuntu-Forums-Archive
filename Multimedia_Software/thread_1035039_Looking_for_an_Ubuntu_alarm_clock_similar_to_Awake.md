---
title: "Looking for an Ubuntu alarm clock similar to Awaken or Aurora on Mac"
date: 2009-01-09
forum: Multimedia Software
---

### Post by br0d on 2009-01-09
Really what I want to build is a reliable morning alarm clock that can gradually wake me up to some sort of progressively brightening video of some sort of nature scene or soft light, using a playlist of ambient electronica.

I'm looking for:
- Decent interface, easily configurable
- Music can fade in and fade out for any length of time
- Can be told to play a playlist
- Can be set to any sort of scheduling with multiple alarms 
- And here is the hard part: audio component can interface with a video presentation or screensaver of some sort, blanking overnight and then gradually increasing at the alarm time.

Not necessarily looking for freeware either, good software is worth paying for. There is apparently nothing like this for Windows either, only Mac. If I could code it up myself I would and market it and take the $$$.

(Please don't recommend me something like the ubuntu built in alarm. I've already used that with the audacious alarm plugin. Don't like em. The alarm fade is buggy, it crashes, and they have to be chained to trigger one another, and there is no video component.) 

Tschüss!

---

### Post by br0d on 2009-01-23
Le Bump

---

### Post by wejde on 2009-04-21
Sounds like a great idea - had any feedback?

---

### Post by kerry_s on 2009-04-21
script it. use crontab for the times, and a script for your preferred player.

example crontab("crontab -e" to edit, "crontab -l" to list):
```
#<minute> <hour> <day> <month> <day-of-week> <command>
00 7 * * 1-5 $HOME/Scripts/alarmclock
```

sample script:
```
#!/bin/sh
export DISPLAY=:0
amixer set Master 100% unmute
alsaplayer -S ~/Scripts/alarm.wav
amixer set Master 50%

```

---

### Post by wejde on 2009-04-22
Sounds great, man. I'll sleep on it ;-)

---

### Post by chewearn on 2009-10-01
Even though this thread is a couple of months old, I thought a better answer might be useful.  I found this one:
[http://alarm-clock.pseudoberries.com/](http://alarm-clock.pseudoberries.com/)

---

