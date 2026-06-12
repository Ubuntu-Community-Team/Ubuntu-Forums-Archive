---
title: "Audio problem with NVidia nforce 630 on Gutsy"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by dempl_dempl on 2008-02-08
Hi folks,

I've just installed Gutsy at my firend's computer.  After  some  nearding and geeking  I've managed to setup   USB ADSL connection. 

But this really gives me a headache...  There is no sound at all.   

Chipset is   nforce 630  .

Drivers on Nvidia site don't work [ I can't remember the exact reason ,  but those damn'  drivers always complain  about wrong kernel version  :-)   ]

The distro is Kubuntu Gutsy  , and I geuss   that sound system is ALSA :-).  

I have kUbuntu for over a year now,   and I'm using Linux  more than five years.   
That means: I don't need a step-by-step tutorial :-)   , I just need some directions.

Thanks in advance

---

### Post by fordp on 2008-02-09
I have installed the NVidia drivers a few months ago, and they do work. I know the wrong kernel version you are talking about and it was down to me needing the right kernel headers installed I think.

The build-essentials package only gives you the compiler but you need the kernel sources too, or at least the headers.

It is a while since I did it so I cannot help you further at the moment.

It is strange you did not get any audio however as recent versions do give some sound with an Intel driver.

I Install the NVidia driver to as the built in audio is very buggy when it comes to spdif output, and therefore barely works for that use.

Good Luck.

---

### Post by dempl_dempl on 2008-02-09
Ok..  I'll try finding Intel driver for onboard audio .

If don't mind ,  just put link to it, in case I dont :-D

---

### Post by chefbram77 on 2008-02-12
Try these options:

[http://www.filledvoid.com/2007/12/11/7/](http://www.filledvoid.com/2007/12/11/7/)

And this might give you some hints: 
[https://answers.launchpad.net/ubuntu/+question/22924](https://answers.launchpad.net/ubuntu/+question/22924)

I have a nVidia Chipset 630 too, with ALC888 .
I got my video working with nvidia Beta 169.04, but my audio is weird..,Only works in Totem...

Good luck( plus let me know if you figure it out!)

Bram

---

### Post by dempl_dempl on 2008-04-26
> **fordp said:**
> I have installed the NVidia drivers a few months ago, and they do work. I know the wrong kernel version you are talking about and it was down to me needing the right kernel headers installed I think.

The build-essentials package only gives you the compiler but you need the kernel sources too, or at least the headers.

It is a while since I did it so I cannot help you further at the moment.

It is strange you did not get any audio however as recent versions do give some sound with an Intel driver.

I Install the NVidia driver to as the built in audio is very buggy when it comes to spdif output, and therefore barely works for that use.

Good Luck.

Ok. I've solved the problem for my friend with one very usefull trick:

I've bougth her new sound card for her birthday :)

Cheers!

---

