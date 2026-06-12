---
title: "can't play movies in dual monitor setup"
date: 2010-07-22
forum: Multimedia Software
---

### Post by slackthumbz on 2010-07-22
This is, perhaps, a slightly odd problem. I recently got a signal conversion box so I could route my netbooks monitor-out port to my TV. The idea being that I could effectively set the TV up as a separate monitor for watching movies on whilst I worked using the netbooks own monitor. It seemed to work initially, the Monitors dialog box could easily detect and setup the TV as if it were just an external monitor however I can't seem to play any kind of video on either screen when this is set up. All I get in Totem, Mplayer, VLC and skype is just a black area within the applications window. The sound works fine so this is clearly just a video problem. 

It only seems to occur when I configure the system to use the TV as a separate monitor. If I tell it to display the same thing on both monitors all video output works fine.
 
Anyone else had this issue?

---

### Post by Akavashi on 2010-07-22
Hey mate,
I unfortunately get the exact same problem too on my Eee PC 1000HA with UNR 10.04 ... I found that with using GNOME Mplayer, I can watch videos with dual screens. Although, as soon as I run any of the above you suggested, I get the same thing.

I'm assuming that those programs check the X Server and since we're running Intel's GMA drivers, it has a hissy. Although, I could be wrong ;)

P.S. Do you, slackthumbz, by any chance get a flash of a white screen at login?

---

### Post by slackthumbz on 2010-07-22
I can't remember if there's a flash of white at login, I reboot so rarely :)

---

### Post by Akavashi on 2010-07-22
Haha, oh well... worth a try...
The closest solution to our problem that I can find on the forums is [thread=1224147]**[COLOR="DarkOrange"]here[/COLOR]**[/thread].
Sigh... That might work for you in MPlayer, since you can choose X11 as a video output in that. I wouldn't know how to change it in Totem or the rest though :(

And the main reason why I think that it would be an X Server problem is that when you use this code (turns off the default monitor and makes the secondary monitor the primary):
```
xrandr --output VGA1 --auto --output LVDS1 --off
(Where VGA1 and LVDS1 are determined by running "xrandr -q")
```
Running Totem then reverts the X Server back to the previous settings >.< It is very very annoying and confusing.

---

### Post by slackthumbz on 2010-07-22
Thanks for the tips, I'll give it a go tonight and report back any progress :)

---

### Post by slackthumbz on 2010-07-22
awesome, switching the video out driver to X11 worked brilliantly :D

---

