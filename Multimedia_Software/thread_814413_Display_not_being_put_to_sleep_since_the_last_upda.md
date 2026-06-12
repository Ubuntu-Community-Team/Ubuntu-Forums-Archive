---
title: "Display not being put to sleep since the last updates / 8.04"
date: 2008-05-31
forum: Multimedia Software
---

### Post by ariel on 2008-05-31
I noticed that my display (lcd panel) is no longer being put to "sleep" by ubuntu 8.04 since a couple of days ago (last update they rolled out)

The sleep function worked just fine with Hardy up to then (and with all previous ubuntu versions).

I didn't change anything in my powermanager config. Powermanager shows: "Put display to sleep when inactive for: 35 minutes" (on AC power, this is a desktop machine).

The Screensaver is set to launch after 30 minutes of inactivity, with a "Blank Screen", and also to lock the session. The screensaver does launch. But the lcd monitor stays "on" forever.

Anyone having the same issue? hints? 

This is with NVIDIA 8600 / glx-new (accelerated) driver, and currently with Metacity (no compiz).

---

### Post by huczek on 2008-06-04
Power Management Preferences is set to turn off display after definied time. My display doesn't put to sleep when inactive. I use CRT display and nvidia-glx driver for GeForce4 MX 4000.

---

### Post by ariel on 2008-06-04
> **huczek said:**
> Power Management Preferences is set to turn off display after definied time. My display doesn't put to sleep when inactive. I use CRT display and nvidia-glx driver for GeForce4 MX 4000.

I found out that if I activate compiz (desktop effects), then the display is indeed put to sleep after 35 minutes of inactivity.  Weird that this fails with metacity. Anyways, compiz is really very stable in 8.04

---

### Post by huczek on 2008-06-17
> **ariel said:**
> I found out that if I activate compiz (desktop effects), then the display is indeed put to sleep after 35 minutes of inactivity.  Weird that this fails with metacity. Anyways, compiz is really very stable in 8.04
Your answer doesn't solve my problem.

Compiz doesn't work with my graphic card if the card's model is mentioned in xorg.conf Although my card supports compiz effects well. I must edit manually xorg.conf in order to run compiz properly. So it's not stable.
I set up sleep time of my display after 7 minutes I hope that's no problem with compiz :) It looks better when I run compiz.
[LIST=1]
[*]But still sometimes - I don't know when - I can't find a path - there's a problem and my display is not put to sleep. I don't have such a problem with windows xp.
[*]Another thing: I **do not need** compiz.
[/LIST]

---

