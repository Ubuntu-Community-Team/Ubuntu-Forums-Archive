---
title: "Multi user/app sound issues."
date: 2011-08-02
forum: Multimedia Software
---

### Post by phalantice on 2011-08-02
Just got 11.04 due to flash issues hosing up 10.04 and a new drive.  I set the preferences in sound to use alsa instead of pulse which for the most part allows multiple apps to coexist a bit.    I remember when I set 10.04 up it took a bit of work before I got the multi source working right.  When I did if I switched user sound would be reset for that user. aka radio by user1 doesnt bother user2 watching hulu etc...  Right now either 1 user or the other has control of the sound device and it doesnt matter which is currently using the screen.  any suggestions would be appriciated.

---

### Post by lovinglinux on 2011-08-03
See the fifth item at [http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

---

### Post by jejones3141 on 2011-08-19
> **lovinglinux said:**
> See the fifth item at [http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

Tracing that back to [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio), the part about setting up /etc/asound.conf has the comment "This section only applies to old, unsupported versions of Ubuntu. Ubuntu 8.04 and higher installs PulseAudio by default and no extra configuration is needed." I have added myself to pulse and pulse-access, and will see whether that suffices, since I'm running 11.04.

---

