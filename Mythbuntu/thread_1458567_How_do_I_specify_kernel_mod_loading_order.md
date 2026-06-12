---
title: "How do I specify kernel mod loading order?"
date: 2010-04-20
forum: Mythbuntu
---

### Post by falcon15500 on 2010-04-20
Hi there,

  I have found on my new install of 10.04 B2, that each time I boot up the order of two specific modules (snd_hda_intel & nvidia) swap around.  When the snd module loads first, the nvidia driver fails to work properly for X.  When nvidia loads first, everything is fine.

  Consequently I need to make sure that the nvidia module loads first.  Is there any way I can specify that?

Regards,

M.

---

### Post by klc5555 on 2010-04-20
> **falcon15500 said:**
> Hi there,

  I have found on my new install of 10.04 B2, that each time I boot up the order of two specific modules (snd_hda_intel & nvidia) swap around.  When the snd module loads first, the nvidia driver fails to work properly for X.  When nvidia loads first, everything is fine.

  Consequently I need to make sure that the nvidia module loads first.  Is there any way I can specify that?

Regards,

M.

There may be several ways, dealing with module parameters, udev rules and the like. I don't know. One simple and barbaric way to try first would be to add your snd_hda_intel module to the blacklist, so that it can't autoload at boot, and then add a modprobe line to the end of your /etc/rc.local file: 

modprobe snd_hda_intel

If your snd_hda_intel driver has options (listed in /etc/modprobe.d/alsa-base) that are specific to your hardware, these _may_ (or may not) have to be added to the end of the modprobe line (but without the word "options") that you append to rc.local. A list of such options are treated in this thread: 
[http://74.125.113.132/search?q=cache:DsnXAlrPzG4J:ubuntuforums.org/showthread.php%3Ft%3D1043568+snd_hda_intel+options&cd=2&hl=en&ct=clnk&gl=us](http://74.125.113.132/search?q=cache:DsnXAlrPzG4J:ubuntuforums.org/showthread.php%3Ft%3D1043568+snd_hda_intel+options&cd=2&hl=en&ct=clnk&gl=us)

Since the NVidia driver will have loaded before rc.local runs, you may be OK. If, however, you end up with no sound because (for whatever reason) the intel sound driver can't be properly loaded this late in the boot process, then you undo your two changes to return everything to its original state, and move on to plan "B"

---

### Post by ZedThou on 2010-04-20
Have you tried listing the nvidia module in /etc/modules ?

---

### Post by falcon15500 on 2010-04-21
Thanks all for the replies... Unfortunately it seems my hypothesis about the root cause of my problem was premature.  I have just taken logs where the two modules loaded in the order I thought would work - and it didn't. :(

So I am left with a problem where intermittently, Myth fails to boot into X, saying that "Failed to initialize GLX extension (Compatible NVIDIA X driver not found)".

I will poke around some more and see what I can find.  Thanks again.

M.

---

### Post by klc5555 on 2010-04-21
> **falcon15500 said:**
> Thanks all for the replies... Unfortunately it seems my hypothesis about the root cause of my problem was premature.  I have just taken logs where the two modules loaded in the order I thought would work - and it didn't. :(

So I am left with a problem where intermittently, Myth fails to boot into X, saying that "Failed to initialize GLX extension (Compatible NVIDIA X driver not found)".

I will poke around some more and see what I can find.  Thanks again.

M.

There are known virtual memory allocation at boot issues with NVidia drivers (usually seen when a Hauppauge 1600 is present in the system). It could be that, under optimal circumstances, your NVidia driver has sufficient virtual memory to load correctly at boot; at other times not. You didn't mention the tuner(s) you were using.

The normal procedure (with grub 0.97) was to increase available virtual memory at boot by adding vmalloc=256M to the kernel line in the menu.lst file. In installations using grub 2 this ought to go into the grub.cfg

---

### Post by falcon15500 on 2010-04-21
> **klc5555 said:**
> There are known virtual memory allocation at boot issues with NVidia drivers (usually seen when a Hauppauge 1600 is present in the system). It could be that, under optimal circumstances, your NVidia driver has sufficient virtual memory to load correctly at boot; at other times not. You didn't mention the tuner(s) you were using.

The normal procedure (with grub 0.97) was to increase available virtual memory at boot by adding vmalloc=256M to the kernel line in the menu.lst file. In installations using grub 2 this ought to go into the grub.cfg

Hmmm... Thanks for the pointer!  The tuners I am using are both Leadtek WinFast DTV1000T.  Even though not Hauppauge, I will give anything a try. :)

M.

---

