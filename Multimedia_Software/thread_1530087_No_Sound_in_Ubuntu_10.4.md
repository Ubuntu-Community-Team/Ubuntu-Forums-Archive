---
title: "No Sound in Ubuntu 10.4"
date: 2010-07-13
forum: Multimedia Software
---

### Post by Hexonica on 2010-07-13
Hi all, Ive recently switched to Ubuntu from Windows XP and me and a friend had finally got things going for me, with everything running pretty darn well. A couple days ago we decided to install VirtualBox with Windows 7 and for a day everything worked well enough but yesterday I discovered that I had no sound whatsoever on Ubuntu but oddly Win 7 on VB had audio running without any discrepancies.

Any help will be deeply appreciated.

---

### Post by Hexonica on 2010-07-13
Guys, some help here.

---

### Post by Hexonica on 2010-07-13
Ok now, the audio in VB (win7) isnt working either. Ive tried restarting the ALSA sound server but nothing really happened. For some odd reason Im unable to 'kill' pulseaudio.

This is what I get when I try to kill pulseaudio:
```
hexonica@Aurelius:~$ sudo pulseaudio -k
E: core-util.c: Home directory /home/hexonica not ours.
E: main.c: Failed to kill daemon: Permission denied

```

This is my soundcard, as told by 'lspci' : Intel Corporation 5 Series/3400 Series Chipset High Definition Audio.

---

### Post by Hexonica on 2010-07-13
Well suddenly everythings just working and I dont know how :confused:
):P

---

### Post by lidex on 2010-07-14
It's magic!! Are you prone to running your system as root?

---

