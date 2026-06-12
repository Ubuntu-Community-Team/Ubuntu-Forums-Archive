---
title: "linux-preempt"
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-05-28
Is linux-preempt being depreciated or is it just a temporary hold up...?

---

### Post by taavikko on 2010-05-28
```
 linux 2.6.34-4.11
.
.
* [Config] Removed amd64 preempt flavour
```

---

### Post by zika on 2010-05-28
> **taavikko said:**
> ```
 linux 2.6.34-4.11
.
.
* [Config] Removed amd64 preempt flavour
```;( But, thank You... :)

---

### Post by xeizo on 2010-05-29
Lolz, and me who switched to 64 because Ricotz ONLY hade 64-bit preempt, now the situation is reversed, someone is mocking me  ;)

---

### Post by gnomeuser on 2010-05-29
It is fairly likely that preempt and rt one day will become runtime variables or at least boot time parameters for the running kernel. It seems like the right way to do it and everyone is really pushing to get -rt merged somehow. It's really popular with embedded vendors and preempt itself is useful in certain desktop scenerios.

I think it is the right decision to drop the extra kernel flavor, it currently didn't bring us much and it exposed a ton of packaging problems in the repos and in key ppas.

---

### Post by plun on 2010-05-29
> **gnomeuser said:**
> 
I think it is the right decision to drop the extra kernel flavor, it currently didn't bring us much and it exposed a ton of packaging problems in the repos and in key ppas.

Can you please explain above ???  "tons of packaging problems" ??

From Pulse Audios mailing list.

> 1) For ****s sakes: get your bloody kernels fixed. [B]Enable preempt, set
   HZ to 1000.[/B] Get rid of low-quality drivers that block the
   CPU. Latencies of 210ms is *REALLY NOT NECESSARY*.

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html)



---

### Post by gnomeuser on 2010-05-29
> **plun said:**
> Can you please explain above ???  "tons of packaging problems" ??

From Pulse Audios mailing list.

I did a lot of testing when it first came out. Basically a lot of packages hardcoded the -generic part of the package name. E.g. the xorg-edgers ppa did this for the nouveau module and there were a number of other similar issues in the repos. You can go over the bugs filed with my launchpad account, that should display a few of them at least.

These are fairly easy to fix, but annoying none the less. I think we got most of them though, I know it certainly is possible to run a -generic free system now, it wasn't when -preempt was introduced.

As for Lennarts Pulseaudio commandments, I've run both and on my setup there was little if any actually difference between audio on each kernel for average desktop use. That is not to say there isn't any, but it's not the great wonderful audio fix we have been waiting for. That will still have to come in the form of better drivers.

I think the most likely scenerio is that eventually the -preempt defaults might be merged into -generic. There does appear to be some benefits from running like this on a desktop, but we lack hard data to justify either having it as a separate option or as the default. Currently my guess is that not enough exists to justify the additional work.

Also that specific low quality driver Lennart referres to which you didn't emphasis.. guess which popular proprietary video card driver is generally meant here. Ridding oneself of that problem would also solve a lot of latency problems.

---

### Post by plun on 2010-05-29
Well, I don't understand how you can bring in the Nouveau crap to this :confused:

The preempt function is just a setting, never had any problems with a real nVidia driver and preempt.

---

### Post by xeizo on 2010-05-29
Nouveau is extremely immature and shouldn't be seriously mentioned as an alternative as of yet, it's experimental at most. Anyone with a Nvidia-card want's to run Nvidias binary blob which is really good, especially in 3D.    On the ATI side of open source things looks brighter, the free driver is actually really usable except it lacks 3D for newer cards. Instead the situation is completely reversed, ATI:s non free drivers aren't very good, in particular not very compatible.    Intels driver is quite ok, a pity the hardware isn't.    About pre-empt, for normal desktop use I haven't noticed any big improvements using it BUT I have as a partly goal to be able to seriously use a Linux box as an audio production workstation. That is not possible without pre-empt, as you can't monitor in realtime while recording using a generic kernel.    Then of course, talking about audio production things get much more complicated than the kernel, the Linux audio stack(s) is currently a mess with Alsa, Pulse, OSS, Jackd etc there should be a single interface for controlling audio which hides all the different subsystems under the hood from the user. There could be a hundred subsystems, I don't care as long as I don't have to see and config all them myself. One audio, one control applet, including controlling low latency audio.

---

