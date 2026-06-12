---
title: "Getting JACK up and running"
date: 2010-04-01
forum: Multimedia Software
---

### Post by demibatard on 2010-04-01
Hello, I am a complete beginner when it comes to Ubuntu/Linux. Recently I bought an Asus EeePC 1005HAB netbook and after being convinced by various friends to ditch the pre-installed Windows 7 starter, I installed Xubuntu 9.10 i386. I want to run SuperCollider and Ardour on this netbook for compositional ideas on the go. 

I first started out by trying to install JACK. After I installed JACK on my system I launched the application, but upon starting the JACK transport, I was confronted with this message:

12:23:52.269 Patchbay deactivated.
12:23:52.272 Statistics reset.
12:23:52.335 ALSA connection graph change.
12:23:52.526 ALSA connection change.
12:23:53.719 Startup script...
12:23:53.721 artsshell -q terminate
sh: artsshell: not found
12:23:54.125 Startup script terminated with exit status=32512.
12:23:54.126 JACK is starting...
12:23:54.127 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
12:23:54.131 JACK was started with PID=2432.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1215428928, from thread -1215428928] (1: Operation not permitted)
cannot create engine
12:23:54.497 JACK was stopped successfully.
12:23:54.498 Post-shutdown script...
12:23:54.499 killall jackd
jackd: no process found
12:23:54.928 Post-shutdown script terminated with exit status=256.
12:23:56.171 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Can someone please help me get this thing up and running - I am really itching to make some music on this cool little netbook!

Thanks for the help.

demibatard

---

### Post by demibatard on 2010-04-02
It seems like this has something to do with the audio card? Any help would be greatly appreciated, as I am completely new at this.

---

### Post by demibatard on 2010-04-02
I guess no one here can help me. I will look elsewhere. THANKS A BUNCH.

---

### Post by cchhrriiss121212 on 2010-04-02
Still there?

You just need to edit a system file using some terminal commands:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
sudo adduser <username> audio
```

Replace username with your own user name. This is from the ubuntu studio prep guide which you might want to read:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

The reason you did not get many replies is that audio production comes under the ubuntu studio forum section. Let me know how much you can get running on a netbook with ardour (no. of tracks, plugins etc.) as I'd be interested to know on those specs.

---

### Post by demibatard on 2010-04-02
Thanks, Chris. However, despite successfully entering the commands you listed and adding my user name to the group 'audio', it did not correct the problem. I am still receiving the same problematic message: "cannot use real-time scheduling [...]"

Any other ideas??

---

### Post by demibatard on 2010-04-03
Aha! Thanks, Chris. It seems I just needed to restart my system to get the changes to take effect. Now JACK is functioning as it should!

Thanks.

---

### Post by omegvermelho on 2010-10-02
Although you have it running if you don´t have a RT (real time) kernel running jackd server will not run with RT priority....

---

### Post by cchhrriiss121212 on 2010-10-02
> **omegvermelho said:**
> Although you have it running if you don´t have a RT (real time) kernel running jackd server will not run with RT priority....
That is not correct, realtime priority and rt kernel are separate things. An rt kernel is still useful for audio though.

---

### Post by omegvermelho on 2010-10-02
> **cchhrriiss121212 said:**
> That is not correct, realtime priority and rt kernel are separate things. An rt kernel is still useful for audio though.


Sorry my bad what i should´ve said is that jackd will still run with RT priority....regardless if RT is present or not...i mean it´s like watching a color movie on a Black&White TV ....

---

