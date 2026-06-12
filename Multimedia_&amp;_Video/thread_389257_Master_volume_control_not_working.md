---
title: "Master volume control not working"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Korrontean on 2007-03-20
Hi there, I've read through the Comprehensive Sound Problems Solutions Guide, but I haven't found a sollution to my problem.

I have problem with volume control.

Chancing the “Master” control doesn't work, not even turning it to mute. I have to change the controls “Headphone” or “PCM” to turn volume up or down.

It's not a big problem, but this way I can't use the shortcuts in my keyboard, that only turn up/down the “Master” volume. And it forces me to always having open the volume control by double click.

Anyone has an idea of what I can do? THANK YOU VERY MUCH FOR YOUR HELP.

---

### Post by Syke on 2007-03-26
Sounds like I'm having the same problem, but don't have fixed yet. What sound device do you have?

---

### Post by n_hall on 2007-03-26
mine started doing this too. before i would just have to restart and it would be okay. but now it's always like this. so now i can't use my keyboard buttons either.

---

### Post by n_hall on 2007-03-27
mine is fixed now. i did the update through terminal because i was bored and now it works. and i got a newer version of firefox. try it see what happens.

sudo apt-get update

sudo apt-get upgrade

---

### Post by n_hall on 2007-03-28
okay, so it didn't stay working. it's now back to not doing anything. i don't have any more ideas.

---

### Post by Korrontean on 2007-04-10
Hi!

Thank you for the ideas. What I did is changing the options of the volume control in the desktop, so it changes the PCM volume and not the master. This way I can quickly change the volume with the mouse pointer, but still not by using my keyboard's shortcuts.

Good luck!

---

### Post by hanexar on 2007-04-16
I always had this problem. I drag it from Breezy to Feisty, and I made a fresh install in between. I'd appreciate if someone could get my master volume control to work.

---

### Post by n_hall on 2007-04-16
okay, for mine if i start my computer with my ss-headphones on my volume won't do anything. but if i plug my speakers in it will work. in general my volume control doesn't work with my headphones plugged it, i guess it sees them as headphones and changes something because in alsamixer it has a headphone volume section. so try to plug-in some different speakers/headphones. it seems to work for me.

---

### Post by hanexar on 2007-04-17
So Alsamixer recognize my speaker as headphone? That make perfect sense since the headphone control works, and the speaker are really old with an headphone jack. I don't have another set of speaker, so is there any other way I can get the master volume to overwrite the other control? It would do the trick.

---

### Post by n_hall on 2007-04-17
right click on the volume icon and go to preferences. then change it to headphone instead of master or whatever it happens to be set to. if that doesn't work i don't really know, sorry. but if it does...awesome.

---

### Post by hanexar on 2007-04-17
I already done that. Quite usefull, but still, It can't let me use the quick key on my keyboard...  

Anyway, I guess it will stay the way it always was.

Thanx for your time.

---

### Post by hanexar on 2007-04-20
problem solved : [http://ubuntuforums.org/showpost.php?p=2495954&postcount=5](http://ubuntuforums.org/showpost.php?p=2495954&postcount=5)

---

### Post by Jump on 2007-04-29
> **hanexar said:**
> problem solved : [http://ubuntuforums.org/showpost.php?p=2495954&postcount=5](http://ubuntuforums.org/showpost.php?p=2495954&postcount=5)

This worked for me too. Awesome

---

