---
title: "Audio randomly stops working.  Have to reboot to get it back."
date: 2008-12-18
forum: Multimedia Software
---

### Post by xl_cheese on 2008-12-18
So my audio randomly quits working on my PC.  Started occuring after I upgraded to IBEX.

I can get it back simply by rebooting.  However, I don't like rebooting my computer everday.  Is there a way I can either fix it or restart the sounds stuff?

Thanks.

---

### Post by markbuntu on 2008-12-18
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by xl_cheese on 2008-12-30
> **markbuntu said:**
> Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Thanks, but none of that worked.

It seems that applications randomly quit working at different times.  Never had this problem till I upgraded to Ibex.

---

### Post by sarang on 2008-12-30
Try grace-killing pulseaudio and restarting it manually.
```

killall pulseaudio

```
 and then 

```

pulse-session

```

If this does not work, try force-killing it:

```

killall -9 pulseaudio

```
and then
```
pulse-session
```

---

### Post by xl_cheese on 2008-12-31
> **sarang said:**
> Try grace-killing pulseaudio and restarting it manually.
```

killall pulseaudio

```
 and then 

```

pulse-session

```

If this does not work, try force-killing it:

```

killall -9 pulseaudio

```
and then
```
pulse-session
```

Thanks.  I'd really like a permanant solution tho if anyone can help.

---

### Post by xl_cheese on 2008-12-31
nope that didn't work anyway.

This kind of blows.  When the sound dies on rhythmbox it will crash if I try to start or stop the music.

Pigeon just seems to stop making chimes, but doesn't crash.

---

### Post by markbuntu on 2008-12-31
What hardware are you using?

---

### Post by xl_cheese on 2008-12-31
> **markbuntu said:**
> What hardware are you using?

I never had this problem on gutsy or hardy.  I'm not sure the hardware is the problem.

---

### Post by markbuntu on 2009-01-01
Some of the alsa 1.0.17 drivers in Intrepid are causing problems with some hardware, that's why I asked.

---

### Post by xl_cheese on 2009-01-01
> **markbuntu said:**
> Some of the alsa 1.0.17 drivers in Intrepid are causing problems with some hardware, that's why I asked.

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by xl_cheese on 2009-01-05
bump

---

### Post by markbuntu on 2009-01-05
OK, try this. It is a very comprehensive troubleshooting guide. Do not forget to follow the links if there is a chance one of them might help.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by xl_cheese on 2009-01-11
> **markbuntu said:**
> OK, try this. It is a very comprehensive troubleshooting guide. Do not forget to follow the links if there is a chance one of them might help.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

thanks, but I can't seem to find a fix there.

I've found that  

killall -9 pulseaudio
pulse-session

will bring audio back if I close the app first.  Rhythmbox and pideon are the two apps that loose sound often.  It is random and they loose sound independent of each other.

This is really just becoming annoying because I like to use rhythmbox to listen to music all the time.

---

### Post by sickenmcsluggets on 2009-01-18
I'm having the same problem. Sound will randomly quit working, and it will freeze quod libet, beep media player, and flash videos. The killall -9 pulseaudio does work for me too , however, that is a temporary fix. I tried the thread here [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506) , I guess I'll see if that works.

---

### Post by gwk on 2009-01-21
I'm having the same issue, and I've noticed that closing the applications and then killing the pulseaudio process does indeed bring back the audio.  This was an upgrade from Hardy Heron; no audio problems while on Hardy.

---

### Post by theMayor on 2009-01-27
> **sarang said:**
> Try grace-killing pulseaudio and restarting it manually.
```

killall pulseaudio

```
 and then 

```

pulse-session

```

If this does not work, try force-killing it:

```

killall -9 pulseaudio

```
and then
```
pulse-session
```


Awesome, thanks so much for this.

I was having this problem for quite some time(same hardware even) on both hardy and intrepid and begrudgingly thought I'd have to just deal with it. 

Wanted to add one other thing, I found that I needed to close all the applications that needed audio first, run these commands, and then reopen. It worked like a charm.

Again, thanks so much for this.
-theMayor

---

### Post by xl_cheese on 2009-02-17
Anyone else ever find a permanent solution?

---

### Post by pbpersson on 2009-03-12
Has someone reported this bug?

Is it being worked on?

I rely on Pidgin being able to notify me if someone is posting, even if I am in another part of the house.

Please let me know what the ETA is for this or if I need to re-partition the hard drive and go back to Hardy Heron.

I installed II on this new machine thinking all the bugs had been ironed out but I guess I was wrong.  :(

---

### Post by StaticIp on 2009-03-22
Same problem here, thanks for the temp fix

---

### Post by nhale25 on 2009-03-23
Ditto for me... same problem, the above fix works.  Is there an open bug report on this?  Would be good if the sound didn't arbitrarily keep stopping working :P

---

### Post by xl_cheese on 2009-04-13
Ugh?!

I'm sooo sick of this problem.  I'm tired of closing firefox, rhythmbox, et al and having to kill pulse and restart it.

I'm hope the upgrade to jaunty will fix it.

---

### Post by nhale25 on 2009-04-13
My rather hackish solution is make a shell script like this:
```

#!/bin/bash

killall firefox
killall rhythmbox
killall -9 pulseaudio

pulse-session
```

and then create a launcher for it on the panel.  I suppose a cleverer script should restart firefox etc. if they were running before, but I'm rubbish at shell scripting

---

### Post by xl_cheese on 2009-05-12
This problem is fixed after upgrading to Jaunty.

---

### Post by cjsteele on 2009-05-12
> **xl_cheese said:**
> So my audio randomly quits working on my PC.  Started occuring after I upgraded to IBEX.

I can get it back simply by rebooting.  However, I don't like rebooting my computer everday.  Is there a way I can either fix it or restart the sounds stuff?

What chipset?

---

