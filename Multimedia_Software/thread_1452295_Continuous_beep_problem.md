---
title: "Continuous beep problem"
date: 2010-04-11
forum: Multimedia Software
---

### Post by Evamgeline on 2010-04-11
hi

yesterday i found out that there was a problem with my mic, so i tried doing something.. n being new to ubuntu.. i started following a post which told me to make some changes in  /etc/esound/esd.conf and the i was asked to type in  sudo /etc/init.d/alsa-utils restart.. which i did.. as soon as i did this, a continuous beep started on my system for which i had to mute my system. i tried changing bak to original, but beep was still there.. even aftr reboot, the beep is there.. i donno wat to do.. please help me..

thanks

---

### Post by WinterRain on 2010-04-11
Did you try
```
sudo /etc/init.d/alsa-utils stop
```?

---

### Post by Evamgeline on 2010-04-11
tried it just now.. after reading ur post.. but no luck.. the beep is still there
:(

---

### Post by wojox on 2010-04-11
What does this produce when you run it in the terminal:

```
cat /etc/esound/esd.conf
```

---

### Post by Evamgeline on 2010-04-11
# autospawning is not recommended, since it can't really be done
# right. If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=


when i had changed , i changed it to auto spawn=1 and spawn_options=-terminate -nobeeps -as =1

but aftr dat i changed it bak to original..but no change..

---

### Post by wojox on 2010-04-11
What version of Ubuntu are you using?

---

### Post by Evamgeline on 2010-04-11
im using ubuntu 9.04 on 3000N100 lenovo laptop

---

### Post by Evamgeline on 2010-04-11
even strange..i clicked on hibernate.. n it was in d process of hibernation, and d beep started..! then i plugged in d earphone to stop it.. n then when i switched it on ..while waking up, again d beep started.. for which i had to again insert the earpiece..!
:(

---

