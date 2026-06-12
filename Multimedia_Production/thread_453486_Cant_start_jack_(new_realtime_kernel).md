---
title: "Cant start jack (new realtime kernel)"
date: 2007-05-24
forum: Multimedia Production
---

### Post by js72 on 2007-05-24
I know this might be "no issue" to someone of you (at least i hope).

This what i get when trying to start jack via qjackctl:

Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210194240, from thread -1210194240] (1: Operation not permitted)
cannot create engine
20:18:56.954 JACK was stopped successfully.
20:18:56.954 Post-shutdown script...
20:18:56.954 killall jackd
jackd: ei lopetettuja prosesseja
20:18:57.170 Post-shutdown script terminated with exit status=256.
20:18:59.024 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by js72 on 2007-05-24
Hi! i noticed that when itook the x out of realtime jackd started ok. ?

---

### Post by MetalMusicAddict on 2007-05-24
> **js72 said:**
> Hi! i noticed that when itook the x out of realtime jackd started ok. ?

No. You need that.

Run this command:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
```
Logout/in. Start JACK.

---

### Post by js72 on 2007-05-24
Im on my way! Thanks

---

### Post by jjalocha on 2007-10-03
I just had the same problem with jack on Gutsy with linux-rt. The previous addition was not enough, as described in a comment to [Bug #108718]("https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/108718"):

```

$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
$ sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

```

After that, I got an error about not being able to create '/dev/shm/jack-1000' because of some missing permissions. I somehow sorted this out by:

```

$ sudo mkdir -p /dev/shm/jack-1000/default
$ sudo chmod -R 777 /dev/shm/jack-1000

```

I don't think this is safe or advisable, --but it worked for me... Let's hope the developers can fix this problem!

---

### Post by Mr.Johnny on 2007-11-02
It didn't work for me... :( what else could I try?

edit: nevermind, it worked, it seems I can start it from the command prompt, but not with qjackctl (unable to connect to jack server...) - what could it be?

---

### Post by Endolith on 2008-05-07
Uhh... can you explain what these cryptic command lines do before I copy and paste them and hose my system?

[This]("https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/108718/comments/1") says:
```

 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
```
Meanwhile [this]("https://help.ubuntu.com/community/UbuntuStudioPreparation#head-65151de671e4c5f7a362c970e2c55f035084534a") just lists these two:

```

 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

```

It was apparently [removed for Hardy]("https://help.ubuntu.com/community/UbuntuStudioPreparation?action=diff&rev2=21&rev1=20")?

---

### Post by Mr.Johnny on 2008-05-07
If I'm not mistaken, they just increase the priority of the processes executed by the "audio" group. :)

---

### Post by Endolith on 2008-05-07
> **Mr.Johnny said:**
> If I'm not mistaken, they just increase the priority of the processes executed by the "audio" group. :)

That's what I see elsewhere, too.  I think they allow programs run by people in the audio group to request realtime mode?  Any idea why the memlock one was removed for Hardy?

---

### Post by Endolith on 2008-05-07
Found a description:

> The rtprio setting is the maximum priority a user of the audio group can run a task. The memlock setting is the maximum amount of memory that a member of the audio group can lock with a realtime task. This should be less than the maximum physical amount of memory, some recommend it to be half. nice is the minimum &#8220;nice level&#8221; a task can be run as (the willingness of a task to give up it's cpu time). - [http://www.alsa-project.org/main/index.php/Low_latency_howto#PAM](http://www.alsa-project.org/main/index.php/Low_latency_howto#PAM)

Also see [http://tapas.affenbande.org/wordpress/?page_id=73](http://tapas.affenbande.org/wordpress/?page_id=73)

So a one-size-fits all command will not work here.  The memlock line needs to be tailored to the size of memory you have.  I don't know why all of this isn't handled automatically.  You would think that Ubuntu Studio would work out of the box.

---

### Post by Endolith on 2008-05-07
I added the memlock line (300M) and it seems to work fine now, but Ardour gives me an warning:

> WARNING: Your system has a limit for maximum amount of locked memory. This might cause Ardour to run out of memory before your system runs out of memory. You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf

---

