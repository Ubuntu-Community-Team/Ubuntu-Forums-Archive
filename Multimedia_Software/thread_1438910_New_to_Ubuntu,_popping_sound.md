---
title: "New to Ubuntu, popping sound?"
date: 2010-03-25
forum: Multimedia Software
---

### Post by Toyojake on 2010-03-25
Hello, I just installed Ubuntu 9.10 (kermic I think) AMD64 version on my HP DV2617US this morning, first time ever using any thing Linux so I'm fairly new at this. I'm having a sound issue, my speakers keep popping like they are being plugged in, muting does nothing. I have searched and all Ive been able to find were a couple of threads like this:
[http://ubuntuforums.org/showthread.php?t=1311262&highlight=popping+speaker](http://ubuntuforums.org/showthread.php?t=1311262&highlight=popping+speaker)

I don't know how to use this though, I tried a driver.. but to no avail. How do I add this code into my OS to stop this popping sound?

My system:
Core 2 duo 1.5GHz
4.0 GB PC25300 RAM
320GB 7200 rpm WD HDD

Thanks

---

### Post by wojox on 2010-03-25
You want to open you're terminal Applications > Accessories > Terminal and copy and paste this in:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

It will ask for your password. Just type it in. You won't see any alpha numerics because echo is off.

Look for **options snd-hda-intel power_save=10 power_save_controller=N**

and change the **10** to a **0** save the file and reboot. ;)

---

### Post by Toyojake on 2010-03-25
Thanks a lot, I appreciate it. Seems to have fixed the issue. :D

---

### Post by wojox on 2010-03-25
Welcome. :p

---

### Post by Toyojake on 2010-03-25
One more question I've got, I'm trying to use rythembox for my music, and when I dragged all of my music over to the program, the songs that were organized into folders will not play. It keeps telling me I am missing plug ins and doesn't seem to want to install them. Am I missing something here, is there another program I can use on Linux for music that is better...(maybe itunes? lol) or do I just need to organize all of my songs into one folder first?

Thanks

---

### Post by wojox on 2010-03-25
For plug-ins did you install:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Toyojake on 2010-03-25
No I didn't, I assume I copy that into my terminal again?

---

### Post by wojox on 2010-03-25
Sure do.

---

### Post by Toyojake on 2010-03-25
Just tried to install that plug in, and terminal says 11: Resource temporarily unavailable unable to lock the list directory

---

### Post by wojox on 2010-03-25
Do you have anything open like Synaptic or Software Center? If so close them down.

---

### Post by Toyojake on 2010-03-25
I did have that open, I think it installed now. Just moved all my music back into the program.

---

