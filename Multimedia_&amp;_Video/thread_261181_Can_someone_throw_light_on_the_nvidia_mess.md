---
title: "Can someone throw light on the nvidia mess?"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by alexsb on 2006-09-19
Hi,

I am having troubles with my nvidia drivers, probably someone can help me. I searched a lot and found different statements made at different times so I am no longer sure what is right and wrong.

Right or Wrong:

* The right version of the drivers should be automatatically installed when installing the linux-restricted-modules-386
* The current kernel version (2.6.15-27-386) generally works with the drivers on the repositories
* I need to install nvidia-glx (which depends on 2.6.15-23)
* NVida works fine with the latest xorg server

My nvidia card has not been woking since the xorg update killed it a few weeks ago, I used nv drivers instead and had no time to look into the issue. Now I will have to do some OpenGL Programming and need the NVidia drivers again.

At the moment I have no libGL.so file, I definitly don't have nvidia drivers installed (but I have the restricted modules installed).

I am really sorry when I am annoying anyone with this question, but there is so much info out there that contradicts itself - thanks to all that help :)

---

### Post by alexsb on 2006-09-21
No one out there who can answer this questions :( ?

---

### Post by MetalMusicAddict on 2006-09-21
What kernel are you currently using?

---

### Post by alexsb on 2006-09-21
As stated above: 2.6.15-27-386 - but I am thinking about going back to the 23 associated with nvidia glx (which I already removed)

---

### Post by alexsb on 2006-09-21
I just updated my repositories - and suddenly the latest nvidia driver does no longer depend on an old kernel. Now everything works fine!

Thanks anyway!

Alex

---

### Post by Krpano on 2006-09-22
I dont understand how did you fix the problem.

Me too, since the kernel 2.6.15-26 and now with the 2.6.15-27 my "nvidia" kernel module wont load.
I need to set it to "nv".
Ive tried to update al the nvidia files with Synaptic but i have no luck so far.

If i use the old kernel 2.6.15-23, my xorg will load perfectly.


Please, someone give me any idea here.
:(

---

### Post by tseliot on 2006-09-22
> **alexsb said:**
> Right or Wrong:

* The right version of the drivers should be automatatically installed when installing the linux-restricted-modules-386
Partially right. That is only the kernel module. You will also need nvidia-glx

> **alexsb said:**
> * The current kernel version (2.6.15-27-386) generally works with the drivers on the repositories
right

> **alexsb said:**
> * I need to install nvidia-glx (which depends on 2.6.15-23)
right

> **alexsb said:**
> * NVida works fine with the latest xorg server
right


> **alexsb said:**
> My nvidia card has not been woking since the xorg update killed it a few weeks ago, I used nv drivers instead and had no time to look into the issue. Now I will have to do some OpenGL Programming and need the NVidia drivers again.

At the moment I have no libGL.so file, I definitly don't have nvidia drivers installed (but I have the restricted modules installed).

I am really sorry when I am annoying anyone with this question, but there is so much info out there that contradicts itself - thanks to all that help :)

Try with:
```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```
```
sudo apt-get install nvidia-glx
```

---

### Post by BLTicklemonster on 2006-09-22
Check out tseliots sig and get his envy script. if you ever upgrade and the drivers don't work, just type envy and you're back in business.

---

### Post by Cashel on 2006-09-24
The 2.6.15-27 update on my AMD64 machine seems to work fine with nvidia's latest drivers. However, since the update Wolfenstein Enemey Territory seems to crash an aweful lot. I suspect the newer kernel update broke something for myself. I'm not going to abandon the new kernel just yet in hopes of figuring out the problem. That being said, anyone else having similar problems? Perhaps you can save me a bit of work.

 Personaly I have NEVER had accelerated X using the repository nvidia drivers from Dapper or ealrier releases. It's not too hard to fix tho and Ubuntu is definetly worth it :)

Cashel

---

