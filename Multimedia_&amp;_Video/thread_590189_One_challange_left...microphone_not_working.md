---
title: "One challange left...microphone not working"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Psylocke on 2007-10-24
I recently installed a fresh ubuntu 7.10

Almost everything is working, except one thing, and i'm stuck on it:
- My microphone isn't working
- The module snd_ice1724 is loaded for my soundcard (onboard one with shuttle SN25P)
- Alsa says Card: Shuttle SN25P, Chip: VIA Technologies VIA1617A
- I've attached my alsamixer output
- I have done some research (forum/google) and did enable my microphone

Anyone know what i'm doing wrong?

---

### Post by Psylocke on 2007-10-25
Ok, I've fixed the problem. For the ones who want to know how:

- I compiled and installed alsa-drivers-1.0.15
- I did sudo /etc/init.d/alsa-utils reset
- I installed kubuntu-desktop, in KDE the sound worked fine...
- After this I remove kubuntu-desktop and ubunutu-desktop
- I removed all .gnome related folders and files in my home dir
- I reinstalled ubuntu-desktop, after starting gdm and logged into gnome, sound was working

Only thing now, I have to reinstall most applications...

---

