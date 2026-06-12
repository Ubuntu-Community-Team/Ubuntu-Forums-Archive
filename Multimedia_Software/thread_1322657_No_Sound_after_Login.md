---
title: "No Sound after Login"
date: 2009-11-11
forum: Multimedia Software
---

### Post by shubhadipdatta on 2009-11-11
Hi Friends, 
I am new in Ubuntu. Few weeks ago I had installed Jaunty Jakalope (9.04).....Everythings were goining ok. But today I have faced a problem that no sound is coming from my PC. At the logn time when the username and password box is coming, the sound of Question mark is coming clearly.......But after Login there is no more sound.....
After seeing a thread I have changed the sound as OSO instead of ALSA.....But in that case VLC, Movie player doesn't produce any sound......
So Help me to solve this problem...
Advance Thanx......

---

### Post by kelvin.illa on 2009-11-11
> **shubhadipdatta said:**
> Hi Friends, 
After seeing a thread I have changed the sound as OSO instead of ALSA...

I don't get this part.

Try to install 'gnome-alsamixer' (_via terminal:_ type "sudo apt-get install gnome-alsamixer;" or _via synaptic package manager:_ search "gnome-alsamixer," check the box and apply) and fire it up (most direct way via terminal: type "gnome-alsamixer") to see various volume levels.

Post your settings here.

---

### Post by shubhadipdatta on 2009-11-11
I am posting the screen shoot after running the gnome-alsamixer in the terminal.....

---

### Post by kelvin.illa on 2009-11-12
I don't anymore; sorry. I was expecting that some level just got muted somehow -- this was my experience when I installed Karmic Koala. And I'm not very familiar anymore with Jaunty's sound manager since it changed in Karmic. I'll try to help you through it anymore like how I would do it myself.

If I'm getting you correct, you're saying that the post-login sound (the percussions) don't play anymore. Maybe you should check your login screen settings if you might have accidentally turned of the post-login sound. I don't think ALSA's the problem.

This is all I have so far.

---

### Post by kelvin.illa on 2009-11-12
I doubt if this will work, but something "might" -- in the least probable sense -- happen if you uncheck the "headphones" in the sound manager. I'm just spitballing here.

---

### Post by shubhadipdatta on 2009-11-12
Thanx [kelvin.illa]("http://ubuntuforums.org/member.php?u=895011") for ur valuable information.....
I have not ever turn off the post login sound.....And How can i turn on this post login sound? In login screen option there is no such type of option......
I have unchecked headphone option but still same problem.....

---

### Post by hansum_rahul on 2009-11-12
May be this might help:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=ubuntu+sound+problem](http://ubuntuforums.org/showthread.php?t=766683&highlight=ubuntu+sound+problem)

---

### Post by hansum_rahul on 2009-11-12
or this:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=ubuntu+sound+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=ubuntu+sound+problem)

---

