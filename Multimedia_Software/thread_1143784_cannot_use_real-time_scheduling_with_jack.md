---
title: "cannot use real-time scheduling with jack"
date: 2009-04-30
forum: Multimedia Software
---

### Post by smaring on 2009-04-30
I've had horrible audio problems with Ubuntu since I got this laptop, an HP Pavilion dv7, about 8 months ago.  I get audio dropouts and skips associated with ANY cpu usage.  So, I'm now determined to fix it and get more control and ability to run more than one audio app at a time with realtime JACK.

I'm getting this when I try to start from qtjackctl ...

```
08:00:51.943 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -m
08:00:51.946 JACK was started with PID=5774.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -2120620304, from thread -2120620304] (1: Operation not permitted)
cannot create engine
```

I have linux-rt and linux-headers-rt installed on a 64-bit fully updated Jaunty and I believe that my user has permissions ...

```

root@lappy:~# cat /etc/security/limits.conf | grep @audio
@audio          -       rtprio          99
@audio		-	memlock		unlimited
@audio		-	nice		-19
root@lappy:~# cat /etc/group | grep audio
audio:x:29:pulse:smaring

```

anybody know what else I can try or look at to solve this?

Thanks,
Steve Maring

---

### Post by markbuntu on 2009-04-30
Are you a member of the group audio?

---

### Post by duffrecords on 2009-05-01
You're running JACK at 64 frames/period.  This is a very low setting for a laptop's integrated sound card (which I'm assuming you're using).  With professional or prosumer gear you can achieve this sort of performance easily, but I recommend experimenting with higher settings first and then working your way down.  Try 1024 frames/period and see if that makes an improvement.  It will increase your latency but it will greatly reduce xruns (which cause the dropouts).  Also, people with Intel sound cards commonly report that using 3 periods/buffer helps.  To find out if yours is an Intel chip, type:```
sudo lshw -C multimedia
```
One other thing--be sure restart the system after configuring /etc/security/limits.conf so the settings are applied to your session the next time you log in.

---

### Post by edm1 on 2009-05-01
What soundcard and drivers are you using?

---

### Post by gengiskanhg on 2009-08-27
$ uname -r
2.6.24-24-rt

Ubuntu 8.04 - the Hardy Heron

$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

For me works the question of are you in the sound group? but not exactly so.

I change two things in my user and groups configuration. Now I really do not know exactly what of this action make sense. I will prove them one by one in next reboots.

The actions were (both in Users and groups GNOME menu):
1. Give to my user the privilegies for use audio equipment. I do not undestand this really because I use audio in my laptop as normal users for 10 months.
2. In the group option I have added to the three groups which names starting with "pulse" my user (enable the check square).

I rebooted and the jack server starts with out problems.

Regards.

---

### Post by stilllife on 2013-03-24
> In the group option I have added to the three groups which names starting with "pulse" my user (enable the check square).
This is what I was missing, thanks!!

---

### Post by wildmanne39 on 2013-03-25
Thread closed. Please do not post in old threads.

---

