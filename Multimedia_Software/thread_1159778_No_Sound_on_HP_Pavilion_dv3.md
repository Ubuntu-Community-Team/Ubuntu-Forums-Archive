---
title: "No Sound on HP Pavilion dv3"
date: 2009-05-15
forum: Multimedia Software
---

### Post by Aperl on 2009-05-15
I am having trouble getting my sound to work on my laptop. Everything worked right out of the box except my sound, my ATI drivers even installed, i find the 3 different audio devices hella confusing. Any help would be much appreciated. By the by i am using Jaunty, has anyone had similar problems?

---

### Post by dallag on 2009-05-19
I have the same problem with the HP Pavilion DV3 the rest everything works without any command line.


Hp Pavilion DV3 very happy.

---

### Post by jdunn on 2009-05-20
I'm having a similar problem with my Pavillion dv5 laptop.  I can only get sound through the headphones.  Also, the sound control buttons on the laptop aren't working.  I am using Jaunty.  I didn't have these problems on 8.10.

---

### Post by Jakovasaur on 2009-05-20
I have a HP dv3t and the following worked for me:

Do what **cbender** did near the bottom of this post:
[http://ubuntuforums.org/showthread.php?t=1140477&highlight=hp+laptop+no+sound](http://ubuntuforums.org/showthread.php?t=1140477&highlight=hp+laptop+no+sound)
[B]
REBOOT!!!!!!!!!![/B]

_Here are my System->Preferences->Sound (Sound Preferences)_:

**Sound Events**
[INDENT]Sound playback: ALSA - Advanced Linux Sound Architecture
[/INDENT]**Music and Movies**
[INDENT]Sound playback: ALSA - Advanced Linux Sound Architecture[/INDENT]**Audio Conferencing**
[INDENT]Sound playback: ALSA - Advanced Linux Sound Architecture
Sound capture: ALSA - Advanced Linux Sound Architecture
[/INDENT]**Default Mixer Tracks**
[INDENT]Device: HDA Intel (Alsa mixer)
[/INDENT]
Still no sound:

Upgrade to Alsa (1.0.20):
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

---

### Post by Aperl on 2009-05-21
It worked! Thanks for the help. :)

---

### Post by jdunn on 2009-05-24
> **Jakovasaur said:**
> I have a HP dv3t and the following worked for me:

Do what **cbender** did near the bottom of this post:
[http://ubuntuforums.org/showthread.php?t=1140477&highlight=hp+laptop+no+sound](http://ubuntuforums.org/showthread.php?t=1140477&highlight=hp+laptop+no+sound)
[B]
REBOOT!!!!!!!!!![/B]



It worked!  Thanks.

---

### Post by fajerpeter on 2009-05-24
Also fixed problems with Dell Latitude 6400 running 9.04   
(not a microphone though)

---

### Post by jdunn on 2009-05-24
> **fajerpeter said:**
> Also fixed problems with Dell Latitude 6400 running 9.04   
(not a microphone though)

Yeah, although the fix gives me sound through speakers and allows me to control sound with the laptop buttons, the mic doesn't work.  I can live without the mic until 9.10 but would like to see it working now, if possible.

---

### Post by jimmux on 2009-07-02
Success! Thankyou.

I tried every other method I could find before coming back to this. I can't believe I wasted all that time.

---

### Post by Jackelope King on 2009-07-02
This worked perfectly on my dv3510nr as well. Thanks!

---

### Post by c5vetter on 2009-08-24
otay, have an HP Pavilion 8200 or something like that - loaded Jaunty via Wubi and got everything running except NO SOUND! have been trying to follow the NO SOUND Guide and run into huge problems - decided to follow Jakovasaur's advice above about upgrading ALSA - well followed steps and everything seemed to load but when I ran the cmd:

cat /proc/asound/version 

got return of NO SUCH FILE OR DIRECTORY

so, Ubuntu gurus, where do I go from here!? looks like Ubuntu is NOT recognizing my sound card! but, I do get sound when doing shuitdown!

---

### Post by Walpy on 2011-02-28
This did the thing for me for Ubuntu 10.04 on my HP G62 laptop

```

~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic

```and reboot!

(found the solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1570060](http://www.uluga.ubuntuforums.org/showthread.php?t=1570060))

---

