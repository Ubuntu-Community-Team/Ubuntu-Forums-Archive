---
title: "Soundcard /dev/dsp problems"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by mzdsb on 2007-08-24
Hi, i've been playing with ubuntu for almost 2 years now, and never got a single problem... until last night:

I was testing compiz-fusion, qhen i opened googleearth, now i now that was a mistake, it seems that compiz-fusion does not support opengl aplications right now(at least my compiz-fusion), so my X got frozen. i tried to restart the X, but without success, so I rebooted manually.

now the sound issue:

after that unexpected reboot, i came back to my system, and oh, no more music plays. crap.
maybe the rebooted muted my soundcard, i thought. so I run alsamixer and...

```
mz@gantz:/dev$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

after panicing for i while, i decided to take a look at /dev, and then i realized that my soundcard wasn't there anymore.



some optups that may come in handy for helping me:
```
mz@gantz:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

mz@gantz:~$ asoundconf list
Names of available sound cards:
SAA7134    (that's my tv card)
```


any help would be appreciated
thanks

pd: the soundcard works perfectly on other OS.

---

### Post by mzdsb on 2007-08-24
hmm... i ¿solved? it.

i've purged my kernel (2.6.22-10) and now i'm using 2.6.20-15, and the sound is back.
but the nvidia acceleration is gone, and when i try to install it (sudo aptitude install nvidia-glx) it says that kernel 2.6.22-10 must be installed again... if i choose to install that kernel my sound stops working.

so, 2 posible solutions:
first: is there a way to install nvidias drivers from the repos without upgrading the kernel?

second: how can i completly remove kernel 2.6.22-10 so i can install it again without sound problems?

---

### Post by Jeek Elemental on 2007-08-24
Ive no idea what causes your problem, but why not install the normal nvidia driver?

if you want it done with minimum fuss try:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

or just grab the pack from nvidia, Ive used it on both 32bit feisty and 64bit gutsy with no problem, and Im a gnub :)
its pretty painless, have a look at one of the guides if unsure how to proceed.

if the sound disappears again, it might be that theres no default card set.
try:
asoundconf list

if your card is there, do:

asoundconf set-default-card <your card>

where <your card> is the name "asoundconf list" output.

---

