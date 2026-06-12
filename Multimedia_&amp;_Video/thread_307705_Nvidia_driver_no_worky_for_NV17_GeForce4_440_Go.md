---
title: "Nvidia driver no worky for NV17 GeForce4 440 Go"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by gitargr8 on 2006-11-27
I've really given it an honest effort, but I simply can't get the nvidia driver to work on my Dell Inspiron 8200, with NV17 GeForce4 440 Go grapics. 

I've tried getting nvidia-glx from adept, I've tried installing the driver manually from nvidia's website, and I've even tried the envy script, but they all result in a blank screen. Then I have to go into xorg.conf and change the driver back to nv.

Is there anything else to try before I just give up on this and say screw it to OpenGL? Perhaps the legacy driver will work?

Any help is appriciated,
~Ryan

---

### Post by gitargr8 on 2006-11-27
bump...

---

### Post by drphilngood on 2006-11-27
See [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") for dapper and [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy") for edgy.

Pay close attention to **point 7 of the PROBLEMS SECTION**.

---

### Post by gitargr8 on 2006-12-10
Tried all that for Edgy, tried all the suggestions in the problems section, and nothing worked. The Kubuntu logo comes up for a few seconds, and then just a blank screen with a blinking underscore. Have to go to the terminal and restore the backup of xorg.conf and restart kdm. 

Does ndiswrapper work with display drivers?? :D 

~Ryan

---

### Post by konungursvia on 2006-12-17
Well, I have precisely the same Inspiron 8200 and NV GeForce4 440 as this gentleman. I installed the legacy drivers from the NVIDIA website, no change. Used Envy to do it, and still I am running 1024.768 on a 1280.1024 monitor, which looks slightly fuzzy, and the graphics are only okay-ish. What am I missing? Do I have to go into terminal and edit some configuration file?

---

### Post by acegolfer on 2007-01-02
> **drphilngood said:**
> See [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") for dapper and [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy") for edgy.

Pay close attention to **point 7 of the PROBLEMS SECTION**.

I also tried that. It did not work for my MX 440. I regret ebaying off MX 400. Is there any workarounds?

---

### Post by blodian on 2007-01-03
I also have been unable to make any sense out of getting my GeForce4 440 MMX card working with Ubuntu, I have tried allsorts of HOWTO guides, both official and unofficial but I get the same result as everyone else. What I find hard to grasp is that to get the same system up and running with OPEN GL and a fully working Compiz using Suse 10.1 was simply a case of installing the NVidia driver from the NVidia website.

---

### Post by tseliot on 2007-01-03
> **acegolfer said:**
> I also tried that. It did not work for my MX 440. I regret ebaying off MX 400. Is there any workarounds?
Try point 4 of the Problems Section of that guide

---

### Post by acegolfer on 2007-01-03
> **acegolfer said:**
> I also tried that. It did not work for my MX 440. I regret ebaying off MX 400. Is there any workarounds?

I forgot to mention mine is MX 440 AGP not MX 440 Go.

I found 97xx didn't work for my MX 440. But 9629 did the trick. I downloaded it from nvidia.com and followed METHOD2 word to word.

I also got Beryl working in this setup. Pretty happy now.

---

