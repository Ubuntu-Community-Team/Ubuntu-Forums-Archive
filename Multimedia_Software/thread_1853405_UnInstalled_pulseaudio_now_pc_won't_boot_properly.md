---
title: "UnInstalled pulseaudio now pc won't boot properly"
date: 2011-10-02
forum: Multimedia Software
---

### Post by CARTER141 on 2011-10-02
Hey I removed everything related to pulseaudio. Now when I boot the pc, it has a similar look and colour scheme to windows classic. When I log in all I get is a small terminal in the corner of the screen. Am I able to fix this?

---

### Post by mörgæs on 2011-10-02
Why did you remove Pulseaudio?

---

### Post by CARTER141 on 2011-10-02
Unfortunately I thought it was just an extra. Didnt realise it was required. It drives me up the wall.

---

### Post by mörgæs on 2011-10-02
Pulseaudio is a deeply integrated part of the system, so I don't think it is easy to fix.

I don't know of any solution besides a reinstall (half an hour, problem solved), but let's see if anyone in Multimedia & Video has another suggestion. Thread moved.

---

### Post by headvampyre@hotmail.co.uk on 2011-10-02
Try booting your system up, then at the login screen press CTRL+ALT+F1, You'll come to a CLI.
Then type in your username + password (It won't look like your typing the password, don't worry, it's a security feature).
Then type:
> 
sudo apt-get install pulseaudio projectm-pulseaudio paprefs padevchooser paman pavumeter pavucontrol ubuntu-restricted-extras



Hopefully that should work :)

---

