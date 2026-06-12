---
title: "HOWTO: Control Hardware PC Speaker Beep"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by komputes on 2008-01-18
:-\" This is a How to for controlling the Hardware PC Speaker, this is not the same as your audio controller which plays sound from music, video etc. This is a loud annoying BEEP. Weather you want to listen to the beep, make it beep from the command line or remove it completely this is how it's done.

[B]My machine beeps loudly from the hardware PC speaker integrated/attached to the motherboard.
[/B]In this case I could recommend many ways of turning this BEEP off.

1) Double click on the volume icon and mute PC Speaker
2) Go to System > Preferences > Sound and disable System Beep (from the system beep tab)

Terminal:
1) Command line style: ```
xset b off
``` if you're in an X session

Console:
1) Command line console style: ```
setterm -blength 0
``` (Console mode no GUI i.e. CTRL-ALT+F1)

**I would like to make the computer beep to test if the PC Speaker is on (or just to really annoy someone)**
In this case you can use one of two commands, one which is echo is included on all systems I know of the other one which is beep is more configurable but needs to be downloaded. I rely mostly on tools which come with most linux distros.

1) In a terminal type: ```
echo -e "\a"
```To explain:
 -e     enable interpretation of backslash escapes
\a     alert (BEL)

2) You can download, install and read the manual for the package "beep" like so:
```
sudo apt-get install beep
man beep
```This is particularly fun when you want to say something nasty but want to censor yourself! :)

Example: BEEEEPin Bug#1! Beep those Beep-in Beep-ers :lolflag:

Notes: Now if someone knows how to turn on/off the beep at the POST stage, that would be useful for this HOWTO as well. I believe that some BIOS may give you the option to turn it on and off, but since mine doesn't any insight is welcomed!

komputes

---

