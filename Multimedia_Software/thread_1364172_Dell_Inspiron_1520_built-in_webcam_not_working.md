---
title: "Dell Inspiron 1520 built-in webcam not working"
date: 2009-12-25
forum: Multimedia Software
---

### Post by cmac_the_great on 2009-12-25
Edit 2013-03-21:
In a fresh install of 13.04 (beta) the webcam works without any modifications / *Mörgæs*.
= = = = = 


The on-board webcam for my Dell Inspiron 1520 has stopped working. I'm running Karmic, and until yesterday everything worked fine. I'm really not sure what has changed, but I use Skype frequently as well as Cheese, and until yesterday my webcam worked fine. But all of the sudden my system does not detect my on-board webcam. Any suggestions?

---

### Post by ItalOz on 2009-12-25
doesn't it start again even on reboot?
on my 1525 I can make my camera restart issuing
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

also I try if it works with a program called
cheese

---

### Post by cmac_the_great on 2009-12-25
Rebooted - no dice.
Rebooted again - still nothing.
Rebooted again - worked.

Whatever.

---

### Post by ILuvMontyPython on 2010-01-03
I have the same problem with my 1525, it works in Ubuntu with cheese but not in Kubuntu

I tried your method of rebooting it and this is what I got 

[PHP]
user@rose:~$sudo rmmod uvcviedo
[sudo] password for user:
ERROR: Module uvcviedo does not exist in /proc/modules
user@rose:~$ sudo modprobe uvcviedeo
FATAL: Module uvcviedeo not found.
[/PHP]

I did it again multiple times (to make sure everything was correct and the only output was this)

---

### Post by ILuvMontyPython on 2010-01-03
never mind I entered them together and I got it to turn on. 

sorry I'm a new Linux User :)

---

### Post by vlotoshnikov on 2010-01-04
> **cmac_the_great said:**
> Rebooted - no dice.
Rebooted again - still nothing.
Rebooted again - worked.

Whatever.

This is exactly what I have with my Dell Inspiron 13 and Ubuntu 9.10 (same with 9.04).

Any suggestions, please?

Seva

---

### Post by emergingtechnologies on 2010-01-24
> **cmac_the_great said:**
> Rebooted - no dice.
Rebooted again - still nothing.
Rebooted again - worked.

Whatever.

MANY thanks!  This worked perfectly for my Inspiron 1525.  Cool.  Didn't take much time to search up. Thanks a lot.

---

### Post by IsraeliHawk on 2010-07-31
> **ItalOz said:**
> doesn't it start again even on reboot?
on my 1525 I can make my camera restart issuing
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```



your code solved it and saved me a reboot (again, after 2 reboots) - and the camera is on and working fine, using Lucid 10.04 32-bit (but I had the same issue on 64-bit, so it should be fine there too) on a Dell Inspiron 1525

thanks alot! =D>

---

### Post by Mistbubble on 2011-03-27
Hey guys, 

I'm kinda brand new with linux. I am running ubuntu 10.10 on inspiron 1520 and my built-in webcam and mic are not recognized.:( Skype mic tester and a camera viewer program (guvcview) tell me that they are either not connected or i don't have the corect drivers. 

Have any idea what i should do?!?!

---

### Post by Mistbubble on 2011-03-27
ok, so I gave it a try and used the code above. and the webcam WORKS!!! :KS yey!! but the mic is still not working... HELP, please !:confused:

---

### Post by android272 on 2011-04-26
> **ItalOz said:**
> doesn't it start again even on reboot?
on my 1525 I can make my camera restart issuing
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```also I try if it works with a program called
cheese

worked grate thanks

---

### Post by pk_rulz on 2011-08-08
> **ItalOz said:**
> doesn't it start again even on reboot?
on my 1525 I can make my camera restart issuing
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```


cheese

A reboot after this ... worked like a charm ...
Dell Inspiron 1520
Ubuntu 10.10 - Maverick Meerkat

---

