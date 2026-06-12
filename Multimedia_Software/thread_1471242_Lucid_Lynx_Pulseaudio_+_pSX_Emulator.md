---
title: "Lucid Lynx Pulseaudio + pSX Emulator"
date: 2010-05-03
forum: Multimedia Software
---

### Post by DieZiege on 2010-05-03
Hey everybody :) 

First of all i have to say that i am from Germany so my English may not be that good.

I'm having some issues with Pulseaudio and running the pSX PlayStation 1 Emulator.

It works like a charm! But only if there are not other Programs(Like Chrome-> YouTube, VLC Media Player) running and playing sound.

I can only have the pSX sound working, but nothing else works then.

I've tried different solutions but nothing did work for me, i really raped everything out of Google but couldn't find anything similar to my Problem. 

Because like all the other Threads on the Internet, it runs on my machine very very good. But only if there are no other Programs open which use Sounds.

I also tried to use the OSS Wrapper to run pSX but i get the same results: Only pSX sound, nothing else.

Maybe someone can help me, i would really appreciate it :)

p.S: Ubuntu by itself runs extremely smooth and nice on the machine! Praise the Programmers.

---

### Post by DieZiege on 2010-05-03
#bump

---

### Post by DieZiege on 2010-05-03
#bump again :/

---

### Post by DieZiege on 2010-05-04
3rd bump...

dont know it its too much

---

### Post by rhandsome on 2010-06-27
I've searched high and low for a reasonable solution to using the PSX emulator within Ubuntu Linux and none of them seemed to help.  So I finally used VMWare and ran a Windows guest, I downloaded the latest windows PSX version with the appropriate dll's and called it a night.  I used VMWare Workstation 7 and a Windows & guest.  My host is Ubuntu 10.04 64bit running on a Dell Precision M6400 so speed and performance for me is not an issue.  This may not the purest solution, but it's only a game emulator.

---

### Post by Yellow Pasque on 2010-06-28
If you want sound from multiple apps, everything needs to be routed through pulseaudio (including apps that use ALSA directly like psX and Flash): [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

