---
title: "sound problems after update (20-12-2009)"
date: 2009-12-20
forum: Multimedia Software
---

### Post by roddyguk on 2009-12-20
hi, i know theres alot of posts already about this problem but ive been going though them all day and cant solve my problem.

i have sound when i listen to music through rhythmbox or watch vids through vlc. 

but i get no sound in totem, 
ive lost the volume control from the top panel, 
my volume control on the laptop doesnt do anything,
and if i go to system/pref/sound all i get is a box that says "waiting for the sound system to respond" and it will stay there until i click cancel!

everything was working until i did a system update this morning.

if anyone can help i would be very grateful

im running ubuntu 9.10
if more system info is needed please let me know how to obtain it

cheers rod...

---

### Post by roddyguk on 2009-12-21
after poking around and looking through some logs i came across user.log and every couple of seconds it says

Dec 21 17:40:55 ubuntu-laptop pulseaudio[15785]: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:1,0"): initialization failed.
Dec 21 17:40:55 ubuntu-laptop pulseaudio[15785]: main.c: Module load failed.
Dec 21 17:40:55 ubuntu-laptop pulseaudio[15785]: main.c: Failed to initialize daemon.
Dec 21 17:40:55 ubuntu-laptop pulseaudio[15783]: main.c: Daemon startup failed.


maybe someone out there knows how i could go about fixing it
cheers rod

---

### Post by roddyguk on 2009-12-22
Iv fixed it :-)

just thought i would share so if anyone else has the same problem they can try this solution

all i did was comment out ".fail" in the default.pa 
the file can be found at /etc/pulse/default.pa

---

### Post by Levo on 2009-12-28
> **roddyguk said:**
> Iv fixed it :-)

just thought i would share so if anyone else has the same problem they can try this solution

all i did was comment out ".fail" in the default.pa 
the file can be found at /etc/pulse/default.pa

This is more a workaround than a fix, but thanks for posting. That didn't work for me. Did you comment out only the ".fail" line? Can you post an example of your default.pa file?

---

