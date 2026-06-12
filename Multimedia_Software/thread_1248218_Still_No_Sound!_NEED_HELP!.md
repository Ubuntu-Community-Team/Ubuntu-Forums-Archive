---
title: "Still No Sound! NEED HELP!"
date: 2009-08-23
forum: Multimedia Software
---

### Post by c5vetter on 2009-08-23
otay - tried another step in the HOW-TO Sound Guide

Ubuntu does NOT recognize any soundcard on my HP Pavilion

so typed in terminal:  sudo modprobe snd-hda-intel

got the following back:

aleshire@ubuntu:~$ sudo modprobe snd hda-intel
[sudo] password for aleshire: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 4: ignoring bad line starting with 'grep'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with 'cat'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 4: ignoring bad line starting with 'grep'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with 'cat'
FATAL: Error inserting snd (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd
aleshire@ubuntu:~$ 


so, gurus - what do I do next!?

---

### Post by j7%&lt;RmUg on 2009-08-24
I think you missed a "-" between snd and hda.

---

### Post by c5vetter on 2009-08-24
otay - reran the cmd and this is what I got - tell where to go from here, as I obviously screwed something up and NO SOUNDCARD being recognized nor am I able to seeminly be able to something else?


sudo modprobe snd-hda-intel
[sudo] password for aleshire: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 4: ignoring bad line starting with 'grep'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with 'cat'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 4: ignoring bad line starting with 'grep'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with 'cat'
FATAL: Error inserting snd (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by Struki on 2009-08-24
I have Hp6735s and the only thing i needed to do was edit my alsa-base.conf file by adding: **options snd-hda-intel model=laptop **line at the and of the file, reboot and it works fine.
I'm not sure that is the same with your card, but try anyway.

---

### Post by c5vetter on 2009-08-24
so, you added your laptop model instead of the word laptop or you added the line exactly like you indicated?

---

### Post by c5vetter on 2009-08-24
how do I find the alsa-base.conf - reason I ask, am NEWB and not sure of what cmd to type to do what you suggest

---

### Post by Struki on 2009-08-24
Well I'm noobish to but learning...
Anyway if ur runing ubunutu 9.04:

In terminal first type:
[I]
sudo su[/I]

You will be asked 4 your password and then you will be logged as root and you will be shown where are you in the dir tree atm.
You need to be root cause I'm guessing you dont have premission to save the changes in the alsa-base.conf file as a user.

Now  you have to navigate your way (in terminal here is some site with most of commands if u dont know them: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)) to the folder:
[B][I]
/etc/modprobe.d[/I][/B]

That is the folder where the alsa file is, now run in terminal: 

*sudo gedit /etc/modprobe.d/alsa-base.conf *

The file should open and there should be whole lot of code and stuff, don't bother you just scroll all the way down and add at the end:

**options snd-hda-intel model=laptop** (yes as it is just copy/paste the line)

Reboot

I'm not saying that this will solve ur problem, but this is how I solved my sound issue step by step and it worked, so i hope i helped.

GL!

---

