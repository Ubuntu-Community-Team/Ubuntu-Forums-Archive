---
title: "Flash-movie in fullscreen: bad sound quality"
date: 2011-12-04
forum: Multimedia Software
---

### Post by tillie on 2011-12-04
The sound of movies I play on youtube, novamov, sockshare, putlocker or any other website showing flash movies give me the following problem:

-Bad sound when playing fullscreen
-Not being able to use buttons like play/pauze in fullscreen mode. 

Sound works with VLC-player and grafic card seems to be supported:
[http://www2.ati.com/drivers/linux/linux_8.24.8.html](http://www2.ati.com/drivers/linux/linux_8.24.8.html)
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X1400](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X1400)

System discription:
IBM (Lenovo) Thinkpad T60
- Intel® Core Duo T2400 processor (1.83Ghz)
- 1,5GB geheugen DDR2 SDRAM 667 MHZ (1024 MB+ 512 MB)
- ATI Mobility Radeon X1400 grafische kaart, 128 MB dedicated memory
- Kubuntu 11.10
- Chromium & Firefox as webbrowsers

Tried:
- all the non-sense like shutdown and restart
- re-installing flash in many ways, including with flash-aid. 

I've been searching for weeks without an answer, so please help me.

---

### Post by cariboo on 2011-12-05
What sound chipset does your system use?

If you aren't sure, open a terminal and run the following command:

```
lspci | grep Audio
```

and paste the output in your next post.

---

### Post by tillie on 2011-12-05
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```

---

### Post by drreid on 2012-01-03
I'm having the same issue with the same sound chipset since my upgrade to oneiric.  Does someone have a solution?  I didn't see one in this thread or elsewhere.

Thanks In Advance,

---

### Post by devauda on 2012-01-06
I also have the problem since upgrading to 11.10.

devauda@devauda-ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

---

### Post by ialiullov on 2012-01-16
I have the same problem with sound in fullscreen webbrowser video. Please anyone help?

I'm using 11.04

Sound is like hoarse...

---

### Post by Unlimited1 on 2012-01-22
I changed over to cinnamon desktop and it resolved my audio issues.  Any time I switch my session back to Ubuntu the audio issues are still there..  seems something like a resource constraint or something with the new Unity desktop.

---

