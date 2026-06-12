---
title: "Nvidia"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by nonex on 2006-08-18
People help please, I put the driver nvidia and at me why that the monitor works at once not 1024x768_85Mhz and _75Mhz as though it to correct??

---

### Post by meng on 2006-08-18
You may need to rephrase your question, I'm finding it difficult to understand what you're asking. How did you install nvidia?

---

### Post by tseliot on 2006-08-18
Which refresh rate is the right one?

---

### Post by nonex on 2006-08-18
Forgive for my English, I use the translator, I have established so sh NVIDIA-Linux-x86--1.0-8762-pkg1.run-q and still why that does not work OpenGl only Direct3D: ((

---

### Post by meng on 2006-08-18
You're probably better off using
sudo aptitude install nvidia-glx

---

### Post by nonex on 2006-08-18
Yes costs at me nvidia-glx and in xorg.conf Driver "nvidia" it is written!

---

### Post by meng on 2006-08-18
> **nonex said:**
> Yes costs at me nvidia-glx and in xorg.conf Driver "nvidia" it is written!
Um, again could you rephrase/retranslate? I'm not sure if the problem has been solved or not.

---

### Post by nonex on 2006-08-18
At me all is established, a problem in other if I in xorg.conf write driver nv that at me 1024x768_85mhz and if I write driver nvidia that 1024x768_75mhz!! ](*,)

---

### Post by meng on 2006-08-18
Okay, obviously the problem isn't solved. But unfortunately I don't think the translator is working very well.

---

### Post by tseliot on 2006-08-18
> **nonex said:**
> At me all is established, a problem in other if I in xorg.conf write driver nv that at me 1024x768_85mhz and if I write driver nvidia that 1024x768_75mhz!! ](*,)

I got it! You mean that if you use the "nv" driver you can use a refresh rate of 85Hz while if you use the "nvidia" driver the refresh rate is set to 75Hz.

If so, try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)


Then IF and ONLY IF that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by nonex on 2006-08-18
Many thanks Tseliot! You will be in Moscow, I shall help with the guide:)

---

### Post by nonex on 2006-08-18
And 1 more problem, does not work OpenGl what to do?

---

### Post by tseliot on 2006-08-18
> **nonex said:**
> And 1 more problem, does not work OpenGl what to do?

Which guide and method did you follow to install the driver?

---

### Post by nonex on 2006-08-18
And is hawto how it is necessary to establish correctly?

---

### Post by tseliot on 2006-08-18
> **nonex said:**
> And is hawto how it is necessary to establish correctly?

Ok, try my Envy, it will install the driver for you:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by nonex on 2006-08-18
I have made through yours envy and all the same there is no Opengl still an offer will be?

---

### Post by tseliot on 2006-08-19
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by nonex on 2006-08-21
Has put nvidia fire wood 8762 and is not present OPenGl???
](*,) 
](*,) 
](*,) 
](*,) :confused:

---

### Post by tseliot on 2006-08-21
I'm merging these threads.

---

### Post by tseliot on 2006-08-21
There's no need to start more threads.

Did you ask for help on that forum as I suggested?

---

### Post by nonex on 2006-08-21
That you gave that envy, have not helped

---

### Post by tseliot on 2006-08-21
> **nonex said:**
> That you gave that envy, have not helped

I suggested to ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Nvidia's staff will help you there

---

