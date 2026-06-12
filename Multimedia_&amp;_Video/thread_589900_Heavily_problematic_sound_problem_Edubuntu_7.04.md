---
title: "Heavily problematic sound problem Edubuntu 7.04"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Daedhel on 2007-10-24
Hi guys!

I usually find solutions on my own by searching on the boards. But my situation seem really complicated and I can't find any answers.

What is installed---
1- I have a Edubuntu server 7.04. 
2- I have installed the KDE desktop on it. 
3- I have VMWare server installed on it.

What I wan't---
1- I would like to be able to have multiple applications to use sond simultaneously. 
2- I would like to hear sound from the VMWare machines
3- I would like my LTSP clients to be able to hear sound

What I have done until now
1- I have followed this guide

[HTML]http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa+sound+system[/HTML]

But when I got the the part where I have to start the alsamixer, I get thi message from my console:
```
jordan@serveur:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

```

2- I have followed this guide for the VMWare problem.

[HTML]http://ubuntuforums.org/showthread.php?t=331175&highlight=what+is+the+best+sound+server[/HTML]

But when I start my VMWare machines, I get this message:

```
Failed to open sound device /dev/dsp: Connection refused
Failed to connect virtual device sound.
```

Your help would be HIGLY appreciated, since i have run out of my own ressources...

Thanks a lot!
Jordan

---

### Post by Daedhel on 2007-10-25
Hi, I am reposting on the thread,since I got no answer and i also haven,t found any answers to my questions elsewhere.

Jordan

---

### Post by gandrews on 2007-11-05
Here is the answer I found (although I use a slightly different configuration):

I'm running Fedora 7 as my system OS. I have VMWare Server installed on that, and several virtual machines (including Ubuntu) configured as guest operating systems.

I determined that the problem was definitely at the host system level (affecting all VMs with no sound device available). After some Google research, I found a simple change to the host's Sound configuration was all that was needed:

System -> Preferences -> Hardware -> Sound (in Fedora 7 Gnome); select the second tab("Sounds"); uncheck the box at the top of the panel (Enable software sound mixing (ESD) ).

In your case, I would guess the only thing different is the Hardware folder is not there and you'd go directly to the Sounds applet. I run Gnome on both the Fedora 7 system and the Ubuntu guest, but I'd imagine KDE would be similar.

Just remember that this is an adjustment at the host level and not a modification to the guest OS.

I hope this works for you!

--George
:cool:

---

