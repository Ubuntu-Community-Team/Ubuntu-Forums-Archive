---
title: "DISPLAY CORRUPTION with ATI's 8.25.18 driver"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by abstractgray on 2006-05-30
All the other 8.25.18 threads are filled with people having problems installing it so I'm making a new one. I got 8.25.18 installed with no problems, but experience display corruption with DRI turned on. There are no obvious error messages in the X logs, the kernel module works, the Dapper update didn't break anything, everything looks fine except the display. ;)

Radeon X1600 AGP (DRI Enabled):

- When I drag windows, the screen doesn't get updated properly. The window gets replaced by desktop where the desktop should be revealed, but the window texture isn't actually written in the new location.

- When I scroll a webpage, the region of screen where new parts of the page are exposed is updated, but the rest isn't.

- Running any OpenGL application, even glxgears, immediately causes a hard lock.

Radeon X1600 AGP (DRI Disabled):

No display corruption, but since there's no DRI the desktop is sluggish and OpenGL/XV don't work.

Radeon 9600 AGP (DRI Enabled):

Works just fine, OpenGL too!


8.24.8 worked without this kind of trouble on the X1600. Unfortunately it had a number of other issues so I've put the 9600 in and stayed with 8.25.18. I'd really like to get it working on the new card because it's shiny and faster and the DVI port has less digital noise.

---

### Post by alanrr_sr on 2006-05-31
You are really lucky..at you could put ir to work...

HIS X1600 XT PCI-X (DRI ENABLED)
Black screen when X starts and System hungs.

HIS X1600 XT PCI-X(DRI DISABLED)
Just fine, but no tv, no 3d ... 

Dapper, always the last... (I've tried everything)... and every driver... 8.24.8 didn't work too.

---

### Post by Wancewot on 2006-06-11
I'm having the same issue, with the same card AbstractGrey.
Any luck in resolving this one?

---

### Post by fadeh on 2006-06-11
Hi, 

I've proposed a solution to black screen + hang up with fglrx and dri. Look here: [http://www.ubuntuforums.org/showthread.php?t=193116&highlight=fadeh](http://www.ubuntuforums.org/showthread.php?t=193116&highlight=fadeh)


Bye, 

fadeh

---

### Post by Wancewot on 2006-06-11
Commenting out extmod simply prevents GL from loading. 
It doesn't solve the main problem (screen corruption), just causes GL to not load. 

Vesa works fine, ati doesn't work at all, and fglrx gives me the screen corruption.

For now I guess I'm not using accelration. Ah well.

---

### Post by fadeh on 2006-06-11
You're not right man, comment extmod don't prevent GL to work. In fact i can run xgl, tux race and so on.


Bye,

fadeh

---

### Post by Wancewot on 2006-06-12
glxgears fails, and I receive an error when I attempt to run fglrxinfo as well. I'll post them when I get home tonight.

---

### Post by skerg on 2006-06-12
[QUOTE=abstractgray]
- When I drag windows, the screen doesn't get updated properly. The window gets replaced by desktop where the desktop should be revealed, but the window texture isn't actually written in the new location.

- When I scroll a webpage, the region of screen where new parts of the page are exposed is updated, but the rest isn't.

- Running any OpenGL application, even glxgears, immediately causes a hard lock.
[/QUOTE]

Same problems for my x1600.

---

### Post by speirs on 2006-07-17
both my desktop (x700 pro agp) and laptop (x1600) are suffering from the same problem too.
i have tried ubuntu, suse, fedora with fglrx version 8.24.8, 8.25.18, 8.26.18.

thanks to myself that i dont really use any 3d software for work or play...
will Ati ever notice us and fix it in the near future? :confused:

---

### Post by ltmon on 2006-07-18
I have a laptop with Radeon Mobility x1600 which performs with no problems at all.

It even manages to suspend and resume about 80% of the time, which is good for anyone using fglrx.  This is out of the box with no tweaks.

I'm increasingly beginning to think that I must have got the special "magic" fglrx drivers, but in reality really I just got them from the Dapper repository.

Posting my xorg.conf so hopefully it helps someone here get theirs going.

L.

---

### Post by jrjr on 2006-07-19
My system with X1600 is ok too, at least with these troubles. Im still having a bit of trouble with big desktop though. Mouse won't scroll to second screen after log in. 

Desktop
P4 2.8 Northwood
X1600
512 Crucial memory
Gigabyte Mb

Here is my xorg too in case it will help you with your troubles...  good luck!

---

