---
title: "No Sound On Old Computer"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by johnficca on 2006-08-12
Hi I just Install Ubuntu Dapper drake on my old IBM Aptiva P II, I first installed 5.10 then I upgraded to 6.06 because I could not get 6.06 to live boot. I have no sound at all, when I click the sound icon I get this: 
No volume control GStreamer plugins and/or devices found.
someone told me to try this aadebug thing and this is what it says.


ALSA Audio Debug v0.1.0 - Sat Aug 12 15:34:44 CDT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux emanarie 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name      : Pentium II (Deschutes)
cpu MHz         : 451.070

RAM -------------------------------------------------------
MemTotal:       126436 kB
SwapTotal:      361420 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)

thea@emanarie:~$

If someone could please help that would be great.
Thanks John Ficca

---

### Post by az on 2006-08-12
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

and the live cd will not run without 256 megs of ram.

---

### Post by johnficca on 2006-08-12
Hey thanks for that, but i've been there before and i can't figure out what to do. i tried to look at the sound card but i can't see any thing cuz it's intgrated and has nothing on it.

---

