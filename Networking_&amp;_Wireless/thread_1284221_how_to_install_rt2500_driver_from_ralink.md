---
title: "how to install rt2500 driver from ralink"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Wcupp on 2009-10-06
this  is driving me crazy i've been at this for the past 3 hours if any one can give me a good tutorial that would be great

---

### Post by foxy123 on 2009-10-06
> **Wcupp said:**
> this  is driving me crazy i've been at this for the past 3 hours if any one can give me a good tutorial that would be great

rt2500 is natively supported out of the box in Ubuntu. Sadly its performance in Karmic is quite poor. It works much better with ndiswrapper at the moment.

---

### Post by iladw on 2009-10-06
Hello Wcupp

Use the official drivers distributed by Ralink themselves.
```
http://www.ralinktech.com/support.php?s=2
```

Locate, extract and read the instructions inside the package.
```
tar xvfz *.tar.gz -C /home/$USER
```

---

### Post by Wcupp on 2009-10-06
```
billy@billy-desktop:~/Desktop/random crap/rt2500-cvs-2009041204/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
make[1]: *** No rule to make target `crap/rt2500-cvs-2009041204/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

```what does it mean by no rule to make target??
and why did rt2500.ko fail to build??

---

### Post by pdc on 2009-10-07
would this post be of any help?

[http://ubuntuforums.org/showthread.php?t=1047374](http://ubuntuforums.org/showthread.php?t=1047374)

you need to check if you have Installed the kernel sources using apt / aptitude / synaptic / whatsoever but it only puts the compressed source code into /usr/src. 

You need to uncompress the sources: all as described in this post

and this other post also covers what it feels should be installed

[http://ubuntuforums.org/showthread.php?t=91969](http://ubuntuforums.org/showthread.php?t=91969)

> sudo apt-get install build-essential

---

### Post by thecow on 2009-10-07
You might need to do a './configure' before you try and make

---

### Post by Wcupp on 2009-10-07
> **thecow said:**
> You might need to do a './configure' before you try and make
im not near my computer right now but i have tried that and im sure i  get an error message sayin that ./configure is not a valid directory 



```
ill edit this to be absolutely sure later
```

---

### Post by Wcupp on 2009-10-07
> **thecow said:**
> You might need to do a './configure' before you try and make
ok tried it got this

```
billy@billy-desktop:~/Desktop/random crap/modules/rt2500$ './configure'
bash: ./configure: No such file or directory
```and my kernel and all is at the highest it can go for now

---

### Post by Wcupp on 2009-10-09
ok i got it working i did a fresh install of ubuntu with out the hardware attached put the hard ware in and boom it was working

---

