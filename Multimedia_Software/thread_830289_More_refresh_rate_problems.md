---
title: "More refresh rate problems"
date: 2008-06-15
forum: Multimedia Software
---

### Post by Rhapsody on 2008-06-15
I have a PC here that I've called Chihiro. I'll skip my feelings of loathing and hatred for this PC, and get down to business.

I just installed Ubuntu 8.04 on it, and Ubuntu is insisting that the monitor and video card can handle 640x480 or 800x600 at 61Hz, and nothing higher. I have run this combination at 1024x768 at 85Hz for a full year, so I know this is a lie. Previously, I was able to run 'dpkg-reconfigure xserver-xorg' and manually reconfigure X.org to use whatever resolution and refresh rate I deemed fit. But now, despite the only change being going from Kubuntu 7.10 to Ubuntu 8.04, this no longer works. It just asks questions about the keyboard, then exits without letting me change the resolution or refresh rate settings.

A GUI solution seems impossible, as nothing in GNOME lets me actually tell it what monitor I'm using. Does anyone know how I can force Ubuntu to use the resolution and refresh rate I want it to?

---

### Post by Pjotr123 on 2008-06-15
gksudo displayconfig-gtk

---

