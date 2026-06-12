---
title: "My alsa problem in edgy.."
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by nik1111 on 2007-01-08
Hi guys. I have the alc883 chip built in my laptop. Recently i tried to update the alsa drivers and for some reason i lost all sound because the soundcard cannot be detected anymore.

lspci says
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The drivers,the libs and the utils, compile and install without errors but when i try to modprobe the snd-hda-intel module i get 

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-10-generic/extra/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and dmesg gives me lines like that

[17183137.272000] snd_hda_intel: disagrees about version of symbol snd_hda_build_pcms
[17183137.272000] snd_hda_intel: Unknown symbol snd_hda_build_pcms

but i cannot really understand what that means for me..could anyone help?i tried the comprehensive guide as well but no luck.

---

### Post by play0r on 2007-01-08
i may have found a fix for you by searching notebookforums.com

append the following line into /etc/modprobe.d/alsa-base

```
options snd-hda-intel position_fix=1 model=3stack
```

then run

```
sudo update-modules
```

or just reboot if you want.
according to the alsa documentation, which i also decided to read before posting, it should work.
hopefully this sorts it out for you. 

ez,
play0r

p.s.
i think there's some posts within this forum concerning pretty much the same subject, with the same solution to the issue at hand.

---

### Post by nik1111 on 2007-01-08
Thanx for your answer but i tried it and its not working..This is becoming very frustrating..I also tried to install alsa the way alsa docs describe for my chipset but  nothing came out..modprobe fails and i dont have a clue why.
If you have any more suggestions please let me know.
btw nice avatar;)

---

### Post by play0r on 2007-01-08
hrmm well then. :-# 
you may try following the method described in this post:
[http://www.linuxquestions.org/questions/showthread.php?t=503714](http://www.linuxquestions.org/questions/showthread.php?t=503714)

hopefully this time you'll be sorted out! ;) 

ez,
play0r

p.s.
thanks! i'm a retro gamer, so i found it quite fitting. it was either this nes controller or an atari joystick. the nes controller looks a lot nicer as an avatar imo.

---

### Post by nik1111 on 2007-01-08
ok i ll check that method and report back, it seems to be exactly for my chipset.

ps i used to have an atari,a nes,a snes,and a game boy;)

---

### Post by nik1111 on 2007-01-08
Ok i did it and i still have the same problem. modprobe fails. but there is a guy there called mithic that had the same problem but says he fixed it..any idea what he did?

---

### Post by play0r on 2007-01-08
try...

```
sudo modprobe -r snd-hda-intel; modprobe -r snd-pcm-oss; modprobe -r snd-mixer-oss; modprobe -r snd-seq-oss
```

---

### Post by nik1111 on 2007-01-08
now that one doesnt fail, but nothing happens as well..also sudo alsaconf finishes with success but again running alsamixer says the card is not installed..strange..i ll try to reboot..in the meantime if you have any more ideas i ll be happy to try them.

i also used this for alsa-base 

options snd-hda-intel model=laptop

---

### Post by play0r on 2007-01-08
[http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda)
^^try using the different models in the wiki & then run sudo update-modules.

ez,
play0r

---

### Post by nik1111 on 2007-01-08
not working.i used model=acer but nothing. i am exhausted!..

---

### Post by play0r on 2007-01-08
acer isn't a valid model.
these are the possible models you can use...

```

3stack
3stack-digout
5stack
5stack-digout
6stack
6stack-digout
w810
z71v
asus 
uniwill
F1734

```

---

### Post by nik1111 on 2007-01-08
i dont think it will work..but i ll try the options..it should be something else though..and about the acer option, it is valid according to the alsa documentation in the arsa kernel/docs files..

---

