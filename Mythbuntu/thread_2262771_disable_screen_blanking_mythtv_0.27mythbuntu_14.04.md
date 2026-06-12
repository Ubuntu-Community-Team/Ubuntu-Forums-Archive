---
title: "disable screen blanking mythtv 0.27/mythbuntu 14.04"
date: 2015-01-27
forum: Mythbuntu
---

### Post by ceesquared on 2015-01-27
When I am in menu (not watching live tv or recording) the screen goes blank after 10 mins. Screensaver is disabled in desktop so this appears to be a Mythtv function. How can I stop it blanking? I do not appear to have gnome-screensaver ( I have tried gnome-screensaver-preferences but it says not found) and I do not have an xorg.conf. I know that the screensaver in mythtv is a common winge. :mad:

---

### Post by ajgreeny on 2015-01-27
If **lightlocker** is installed in mythbuntu it could be that as well.  Try **light-locker-settings** in terminal to see if anything comes up, and configure it as you want it.

---

### Post by ceesquared on 2015-02-06
Thanks, but light-locker not installed. I have since found that it applies when I am in desktop, so it could be a ubuntu(not mythbuntu) problem. I will try playing with X11 when I get chance.

---

### Post by khPWXxF on 2015-02-08
Out of interest, what's your concern about screen-saving?  Why suppress it?
Phil

---

### Post by ceesquared on 2015-02-09
Simple, visitor calls, pause Live TV or recording, 10 mins into conversation screen blanks and TV automatically switches from HDMI input to normal TV and you get audio which you then have to mute. A nuisance, and when it is all over my wife has to work out how to get back to where she was.

---

