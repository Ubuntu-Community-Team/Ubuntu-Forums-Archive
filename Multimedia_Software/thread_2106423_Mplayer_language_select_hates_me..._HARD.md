---
title: "Mplayer language select hates me... HARD"
date: 2013-01-19
forum: Multimedia Software
---

### Post by Silent Warrior on 2013-01-19
I'm having a problem with MPlayer: Whenever I go into Settings and try to set any of the language options, it breaks my desktop. What I see is that the terminal appears, shortly after which I'm sent back to my display manager (log-in screen - if anyone knows why the bleep we call it 'display manager', PM me, PLEASE!). As soon as I click the button that opens (or SHOULD open) a dialog or drop-down menu - my current GTK theme makes it difficult to tell - it crashes instantly. No warnings, no delay beyond reloading the display manager. It occurs regardless of whether I play anything or not.
dmesg gives:
```
gnome-mplayer[24618]: segfault at 517040f0 ip 00007f360ed2485f sp 00007fff95bb9410 error 4 in libglib-2.0.so.0.3400.1[7f360ecc2000+f5000]
```
(... Now, THAT'S a filename and a half!)

Has anyone come across this before, or have an idea on how to solve it?

System info:
Distribution: Mint 14 Cinnamon, completely up to date
(I know, this isn't Ubuntu, but since the version of Mplayer I have appears to be in Ubuntu's care, I thought I'd ask here first.)
Mplayer version: 2.0-554-gf63dbad-1ubuntu0.1
Display manager: KDM 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa2
DE version: 1.6.7+Nadia
libglib version: 2.34.1-1ubuntu1
xserver-xorg version: 1:7.7+1ubuntu4
(My reason for using KDM instead of MDM is that MDM won't let me choose desktops easily enough. Since I polydesk :) I think I have ended up with just about every display manager available to choose from.)

---

### Post by andrew.46 on 2013-01-19
Do you have the same issues with the other MPlayer frontend SMPlayer?

---

### Post by Silent Warrior on 2013-01-21
This doesn't happen using SMPlayer, no. (Add the latest available GNOME Shell environment to the list of affected ingredients. I also picked a new Gtk+ theme, and still get the crash.)

---

