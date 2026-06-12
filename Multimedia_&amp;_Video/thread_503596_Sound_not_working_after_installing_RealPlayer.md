---
title: "Sound not working after installing RealPlayer"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by mm.ie on 2007-07-18
Hello everybody,
Like David Bowie I am an absolute beginner.  I have only been using Ubuntu now for a couple of weeks.  I have installed Feisti,

I have installed Real Player and ever since the sound has stopped working.  I am afraid that I don't even know where to stop so any basic stuff that I have failed to do would also be appriciated.

My sound button gives me two options - 
0: HDA Intel (alsa mixer)
1;Realtek ALC 260 (oss mixer)

Constant fiddling with these two has only acheived one thing; Now I have no notion where it was when I started!

The machine is a HP processor Intel(R) Pentium 4 cpu 2.80GHZ dual.

Real annoys me in windows with its efforts to take over my machine and my life, like a friend you invite to the house and he insists on sleeping in your room and maybe even your wife!  Phah!

any help appreciated.

mm.ie

---

### Post by dragonwings on 2007-07-19
try

sudo asoundconf list 
to get a list of soundcards you have ,take note of them

now
sudo asoundconf set-default-card (here is where you put your sound card name)


eg" for mine i put 
       sudo asoundconf set-default-card Audigy2

good luck

---

### Post by ubanchaos on 2007-07-19
do u mean just regular sound or just mp3..if its mp3 just use amorock and get the plugings its pretty straight forward

---

### Post by mm.ie on 2007-07-23
dragonwings

take a bow.  That worked.

thanks very much.  many beans flowing your way.

mm

---

