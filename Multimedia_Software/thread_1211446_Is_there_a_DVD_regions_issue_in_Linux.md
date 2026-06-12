---
title: "Is there a DVD regions issue in Linux?"
date: 2009-07-12
forum: Multimedia Software
---

### Post by oxf on 2009-07-12
I use my laptop when I travel a lot and one issue I came across in Windows was having to change the region code for my DVD drive. Apparently you can only change it five time after which it becomes locked.  That seems rather a restriction of my rights to use my laptop and legal CD's in more than one continent but I wont get going on that now!

For now I'm wondering if the same issue exists within Linux? If it does is there any way of getting around it? E.G someone once said they thought that (in windows at least) it was possible to contact the manufacturer of the DVD drive and override the lock after five changes. I dont know if this is true or not. However,  I am curious if the same issues and possible solutions exist when using linux?

---

### Post by SuperSonic4 on 2009-07-12
I think that some drives do and some drives do not.I don't think my HP drive has it

---

### Post by mc4man on 2009-07-12
> it was possible to contact the manufacturer of the DVD drive and override the lock after five changes.

Technically yes, the manufacturer can provide a way to reset the drive, practically, good luck there.

No open source, unlicensed player or linux distro will enforce region coding, you can play disks from any region, with any type of rc. Most drives don't enforce either, with the notable exception of many Matshita laptop drives.

In that case when the drive detects a region mis-match it will refuse access to encryted sectors (no drive authentication

There is nothing to be done in such a case, no matter what the Os or player
(the only possibility would be a rc1 firmware flash and there is virtually none available for laptop drives, in particular Matshita.


sudo lshw -C disk should tell you the drive model

---

### Post by oxf on 2009-07-12
> **mc4man said:**
> Technically yes, the manufacturer can provide a way to reset the drive, practically, good luck there.

No open source, unlicensed player or linux distro will enforce region coding, you can play disks from any region, with any type of rc. Most drives don't enforce either, with the notable exception of many Matshita laptop drives.

In that case when the drive detects a region mis-match it will refuse access to encryted sectors (no drive authentication

There is nothing to be done in such a case, no matter what the Os or player
(the only possibility would be a rc1 firmware flash and there is virtually none available for laptop drives, in particular Matshita.


sudo lshw -C disk should tell you the drive model

*-cdrom
       description: DVD writer
       product: UJ-840D
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

Well I guess I'm screwed then!!!!
Over the last 18 months I've traveled many times between N America and EU. In windows I just switched it back to region 2. i,e Europe and I got the msg "last time"
Not  an issue for me right now as I'm not going anywhere for a while but since I do have a laptop with a Matshita drive it looks like I'll never ever be able to use it outside Europe again! 

Maybe I'll should think about purchasing and installing a different drive?
This makes me so mad that I dont have the choice of using MY pc to play LEGAL videos when I travel!

---

### Post by oxf on 2009-07-13
Well since it looks like I'm essentially screwed then, having used up my five "go's" what about recomendations for DVD drives that I should replace it with when the time comes?
Thanks

---

### Post by mc4man on 2009-07-13
The 2 major makers of laptop dvd drives are Mat'****'a and Lg. (HL-DT-ST.....)
The Lg's are fine (as are Pioneer and NEC and Toshiba and LiteOn

Ideally you get one designed for your laptop, better fit and finish. Unfortunately many laptop drives have a 'custom' shaped outer plate on the tray drives that you may not find on a generic replacement drive.

So I quess I'd start with the laptop's maker and see, though the $ may be excessive. (and you don't want another matshita (*panasonic")

Actually I'd call tech support for your laptops maker and see what they say

((last year me and my son got got the same laptops from dell about 3 wks. apart, I got a matshita, he got an hl....., so you never know what the laptop maker may be using atm without asking.

This is what mine will say in vlc with a R 2 disk, plays fine on my son's

> .....clipped
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: [COLOR="Blue"]Assertion `0' failed.[/COLOR]


---

### Post by vinutux on 2009-07-13
i think noproblem with vlc with libdvdcss

---

### Post by vinutux on 2009-07-13
i think vlc and libdvdcss helps to overcome that prob

---

### Post by oxf on 2009-07-14
> **mc4man said:**
> The 2 major makers of laptop dvd drives are Mat'****'a and Lg. (HL-DT-ST.....)
The Lg's are fine (as are Pioneer and NEC and Toshiba and LiteOn

Ideally you get one designed for your laptop, better fit and finish. Unfortunately many laptop drives have a 'custom' shaped outer plate on the tray drives that you may not find on a generic replacement drive.

So I quess I'd start with the laptop's maker and see, though the $ may be excessive. (and you don't want another matshita (*panasonic")

Actually I'd call tech support for your laptops maker and see what they say

((last year me and my son got got the same laptops from dell about 3 wks. apart, I got a matshita, he got an hl....., so you never know what the laptop maker may be using atm without asking.

This is what mine will say in vlc with a R 2 disk, plays fine on my son's

Thanks for the advice. Not an issue today but will eventually be in the future. Maybe just for amusement I should have a go at Mat****a first and  see what they say LOL!

---

### Post by ticket on 2010-01-03
From what I can tell, all DVD drives these days have region locking.  You have to flash the drive firmware to remove the locking - effectively making it an "rpc1" drive.  There is software to do this, but you typically have to run it under DOS or Window$.

Look up "Dangerous Brothers" - they have some DOS s/w to do flashing.

Beware - a bad flash can render a drive useless.

Firmware flashing without using DOS appears to be something Linux lacks.
(don't try it with Wine - no idea if that can work)

---

