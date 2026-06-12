---
title: "help I screwed up x (sorta)"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by loserboy on 2007-02-13
ok so long story short, i did the kernel updates at work and everything seemed to go ok, so i ran them at home and it broke X cuz of the nvidia drivers thing and stupid me did a 

```
dpkg-reconfiure xserver-xorg
```

cuz thats all i knew to do, well that got me back up sorta but now everythings goofy, resolution is off and beryl is freaked out and refresh rates, who knows what else and i still had to go back the the previous kernel.

So where should i start to get things back like before, is there any chance of retrieving the old xorg or what, i don't really wanna do all the settings over again, i can't even remember what all i changed (suppose if i've forgotten i don't need them right?).

anyway can someone tell me what to do, or even give me a pat on the back and say everything is going to be all right? /cry


oh and 
nvidia 7800 pci-e
32-bit edgy

---

### Post by K.Mandla on 2007-02-13
If you're using the *nvidia-glx* driver from the repositories, just install *linux-386* and you should be back on your feet after a reboot.

```
sudo aptitude install linux-386
```
You might have to dpkg-reconfigure xserver-xorg again, after your video is back, but that's a small price to pay. ;)

The problem occurs when the upgrade installs the *linux-generic* package, and not the *linux-386* package. *linux-generic* has no nvidia kernel module, so the nvidia-glx driver has no place to "attach" to (for lack of a better way of explaining it :rolleyes: ).

---

### Post by RudolfMDLT on 2007-02-13
Every time you reconfigure the Xorg.conf file a backup is made, unless you edited it by hand? check your X11 folder for backups?

---

### Post by loserboy on 2007-02-13
oh i see, well i'll see what i can do when i get home from work.

thanks, i'll let you know

---

### Post by loserboy on 2007-02-13
ok well after installing the linux-386 i can actually boot into the newest kernel now, but still the graphic drivers arent working right, i went to synaptic and re-installed the nvidia-glx but that didnt help.... so what now?

---

### Post by loserboy on 2007-02-14
i installed envy, ran it, graphics are great...better than before even.

so now if i can just get beryl and my sound back up....  :(

---

### Post by Thyme on 2007-02-14
Hi :)

I'd just like to share my experience with the recent kernel and nvidia update debarcle.

Firstly, I found that removing the linux-generic,linux-restricted-modules (and the others that will automatically be removed, I can't remember the names) as well as the nvidia-glx, nvidia-settings and nvidia-xconfig packages obtained from the repositories, helped by removing clutter, old configuration files etc...

Secondly, downloading the driver from nvidia's website and manually installing it fixed the problem (for me anyway). I can only deduce that an incompatibility between the various packages needed when downloading the driver via repositories resulted in the breakage.

---

