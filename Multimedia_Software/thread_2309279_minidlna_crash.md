---
title: "minidlna crash"
date: 2016-01-09
forum: Multimedia Software
---

### Post by quiquednst on 2016-01-09
Recently I bought a wifi speaker, a Bose Soundtouch 10, which plays music directly from the web but it also may access to your library on a NAS or on your computer.
 As server I'm using xubuntu 14.04, up to date, and minidlna server.

 The speaker sees my server but each time it tries to look at it minidlna crashes.
 Even if I put 'log_level=debug' on minidlna.conf the log file doesn't report anything about the crash.
 I tested my minidlna server accessing from another computer (vlc on xubuntu 14.04 too) and from a smartphone (AllConnect app) and both work ok.
 I would appreciate any help.

---

### Post by quiquednst on 2016-01-13
Nobody gets minidlna crashes?
How may I discover the reason for the crash?
Thanks in advance

---

### Post by fastdruid2 on 2016-02-01
It doesn't help much but I'm seeing exactly the same with minidlna (1.1.2) and a Bose SoundTouch 20 on DietPi (A debian based Raspberry Pi distro).

Plays fine through Windows or my phone, as soon as the ST hits it - instant crash.

I tried running it as a non-daemon / debug mode but that seg faults

/usr/bin/minidlnad -f /etc/minidlna.conf -d
Segmentation fault

What version are you running? 

Seeing as there is a later version (although only available as source) I'm going to compile it and see if that works.

---

### Post by fastdruid2 on 2016-02-02
Again this doesn't help with the crashing but after compiling 1.1.5 from source it works perfectly. No crashes, plays from the SoundTouch a treat.

I'd check your version, and update to the latest, compiling from source if need be.

If you're already on the latest then might be worth reporting to the package maintainer or doing a rebuild of the package yourself.

---

### Post by quiquednst on 2016-02-03
Thanks for your help.
I'm using 1.1.2 too, so you are showing me the way to get a solution.
I will try it. Thanks again.

---

### Post by quiquednst on 2016-02-04
I downloaded, compiled and installed minidlna 1.1.5 (on xubuntu 14.04 up to date) and it works. My Bose SoundTouch 10 doesn't crash minidlna.
By the way, I also tested minidlna 1.1.5 with a Beovision 11 (TV) which used to crash minidlna 1.1.2 too. It works.

---

