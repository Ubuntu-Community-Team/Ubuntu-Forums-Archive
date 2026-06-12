---
title: "New Nvidia card low screen resolution and can't install driver"
date: 2009-06-15
forum: Multimedia Software
---

### Post by ozguitarplayer on 2009-06-15
Hi,
I have just had the motherboard replaced and a new graphics card fitted, a Nvidia GeForce 9400GT.
Without the driver installed I get very low screen resolution of 640x480.
I have found the correct driver from the Nvidia site, however part way through the installation I get a message saying that I have to exit xserver, how do I do this and is it OK to exit the xserver?

---

### Post by izizzle on 2009-06-15
Well you could just install the drivers from Ubuntu restricted extras...

But, to exit the xserver, you have to boot into a shell prompt (no gui) and execute the driver installation from there.

---

### Post by ozguitarplayer on 2009-06-15
Thnaks izizle,
I would prefer to install the driver from the restricted extras, however there are so many there I don't know which one to use, are you able to help me with which one to choose?

---

### Post by izizzle on 2009-06-15
Since you have a 9400GT (fairly new card), choose the latest option. I believe it is 180.XX

---

### Post by ozguitarplayer on 2009-06-15
Well I think I'm being a bit slow here, cause I can't find it. I entered Nvadia in synaptic and got a heap of 'linux restricted modules' none of which refered to 180.xx

Am I looking in the wrong place or am I in the correct place and just not looking properly?

---

### Post by RedRat on 2009-06-16
Might want to try EnvyNG. It is in synaptic. You can run it from the GUI or the command line. It finds the correct driver(s) and you pick what to install.

---

### Post by ozguitarplayer on 2009-06-16
thanks RedRat, I wont be able to try that for a few hours, however I'll let you know how it goes.

---

### Post by izizzle on 2009-06-16
I don't run GNOME, but from what I remember there should be an option under System > Administration > Hardware Drivers. It should list a few Nvidia drivers and you should install the 180.xx version (or the latest version listed).

---

### Post by ozguitarplayer on 2009-06-16
That's where I first looked and there was nothing there, this is why I strarted looking for other methods to install it...still having no luck

---

### Post by izizzle on 2009-06-16
Weird, there was nothing there....You should probably try EnvyNG, it's the nest easiest method.

---

### Post by ozguitarplayer on 2009-06-16
Just had success with EnvyNG...thanks....I had a look in Hardware Drivers and still no listing, infact there is nothing listed at all. Is this normal? and does this mean I won't be able to disable Nvidia if I want/need to?

---

### Post by izizzle on 2009-06-16
Actually, yes, this is a bit unusual. How long has it been since you applied updates to your system? I believe you will still be able to disable Nvidia if you ever have to, just not by using a GUI.

---

### Post by ozguitarplayer on 2009-06-16
Updates are current, maybe the card I have is too new, (Nvidia 9400GT) though it is listed as being one that is recognized by Linux.

However when I opened EnvyNG I was ubable to install using (Automatic Hardware Detection) as I was told that the card wasn't recognized so I installed using (Manual Detection of the Driver) and the closest choice of three was version 173.14.12 and mine card is 185.18.14
so far all seems good, hope I didn't do the wrong thing?

---

### Post by izizzle on 2009-06-16
It's definitely not a problem of recent technology, because people have gotten GTX cards to work. The 173 diver version is very old, it will work, but not to your card's full extent. I don't know what's going on, but a full system reinstall should do the trick because it will install the latest drivers for the new mobo that you put in. However, it's up to you.

---

### Post by ozguitarplayer on 2009-06-16
I have Hardy Heron on two seperate partitions, one of which was a new install after the new motherboard and new video card was fitted and still only the 173 driver was recognized. 
I had downloaded the 185 driver from Nvidia but was unable to install it as part way through I was told I had it exit xserver which I did and tried to install again however this time was told that the driver couldn't be found. I might try again with exiting xserver, I guess it'll be OK if it works and 185 is installed over 173?

---

### Post by izizzle on 2009-06-17
Nope, you would have to remove the 173 version if you plan on installing 185. My personal experience with manually installing the driver's hasn't been too good. Manually installing the nvidia drivers replaces some of the OpenGL libs that come with Ubuntu, and it causes problems while gaming. If you don't game much, I'd say you *should* be fine.

---

### Post by ozguitarplayer on 2009-06-17
I'm starting to think it is an age thing and 185 isn't suited to Hardy Heron..maybe I'll try Jaunty

---

