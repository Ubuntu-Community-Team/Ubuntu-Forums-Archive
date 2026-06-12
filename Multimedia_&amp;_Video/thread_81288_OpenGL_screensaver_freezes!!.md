---
title: "OpenGL screensaver freezes!!"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by paolino73 on 2005-10-24
Hello!!
I have a problem!
When the screensaver enters in function the PC freezes.
I have a ATI 9600se installed correctly
Which it is the problem? It's a bug?
Thanks!!

---

### Post by Pablo_Escobar on 2005-10-24
Post here what "fglrxinfo" spits out.

---

### Post by paolino73 on 2005-10-24
paolo@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

---

### Post by Pablo_Escobar on 2005-10-24
It looks good. Does the PC stalls when it enters screensaver mode ?

---

### Post by paolino73 on 2005-10-24
The PC is frozen after some minute that enters in function the screensaver and I must press the  reset key.
Excuse for my bad english but I'm italian.

---

### Post by paolino73 on 2005-10-24
It can be legacy to the OpenGL?  I have had a similar problem with Suse after to have activated the 3D acceleration

---

### Post by Pablo_Escobar on 2005-10-24
My 3D screensavers work flawlessly with my ATI 9550 card.
I can't seem to figure out what can freeze Your system, maybe some powersaving features (they're in Screensaver panel also).

---

### Post by paolino73 on 2005-10-24
The Display Power Management is disable

---

### Post by paolino73 on 2005-10-24
I have uncovered that before that the computer freezes the monitor goes in standby 
even if the options of power managment are set up of default

---

### Post by corny on 2005-11-16
i had the same problem.
apt-get install xorg-driver-fglrx
and it was gone.

---

### Post by jaredwhitehead on 2006-01-10
[QUOTE=corny]i had the same problem.
apt-get install xorg-driver-fglrx
and it was gone.[/QUOTE]


Nice! This totally worked. Thanks!

---

