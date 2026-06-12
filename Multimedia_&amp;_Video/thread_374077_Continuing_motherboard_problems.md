---
title: "Continuing motherboard problems"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-03-02
I've recently gotten a new PC, with integrated graphics and sound. Despite being cheap, it's better than my old PC, however Kubuntu seems to be having difficulty getting everything out of it.

The motherboard is an "ASRock K8NF6G-VSTA" with "Integrated NVIDIA GeForce6-class graphics DX9.0 VGA" for the graphics and "Realtek ALC861VD/ALC883 7.1 channel audio CODEC with High Definition audio" for the sound.

The first problem was with my refresh rate (Kubuntu wouldn't let me set it higher than 60Hz in any resolution, despite my monitor supporting much higher) but I fixed that by editing xorg.conf and forcing it to let me user higher refresh rates.

The second problem is that I can't seem to get hardware acceleration. I tried installing the NVIDIA drivers (like I successfully did with the GeForce4 MX in my old PC) but that just killed X.org, forcing me to restore xorg.conf to get the GUI back.

Finally, Kubuntu completely fails to detect my sound hardware. KMix says "Mixer cannot be found" and alsamixer says "alsamixer: function snd_ctl_open failed for default: No such device". It's like there's nothing there. A desktop CD of the same version of Kubuntu I'm using now (Edgy Eft) does exactly the same.

Additionally, Add/Remove Programs won't let me install MPlayer Movie Player or Xine extra plugins. They're also not listed in Adept. I was able to do that with the same version of Kubuntu on my old PC, so I'm assuming this has something to do with one of the problems listed above. I'd like to install both if at all possible, as I typically make fairly heavy use of them.

I'm sure this PC can be productive and enjoyable, but it's difficult without it detecting my hardware properly.

Addendum: The entire post above is quoted directly from a [previous topic](http://ubuntuforums.org/showthread.php?t=367902) of mine that got no replies, since I have not been able to get any more information on these problems. I am currently counting at least two months with absolutely no sound from my PC.

---

### Post by chewearn on 2007-03-02
A year ago, I got into quite a similar situation.  I just got a new PC, at around the time when Dapper was released.  The PC was has integrated GeForce6100, Realtek 5.1 audio.  It took me a fair amount of tinkering to get nVidia driver installed.  More time spend to enable widescreen resolution (I have a widescreen LCD).  I was never able to get sound to work properly.  After a couple of weeks, I gave up and went back to Windows.  Six months later, Edgy was released, and everything worked right after installation.

In terms of addressing your problems, I suggest you start a thread for each specific problems.  I got mine resolved one by one, but in the end, I just need to get my PC working and be productive.

Now, I am more careful when getting a new PC; I make sure the model has been in the market for at least six months; no bleeding edge hardware.

Feisty Fawn in due out in April.  Maybe you might get lucky.

And, I am not sure whether it has to do with Gnome or KDE.  Maybe you can try Ubuntu instead of Kubuntu?

---

### Post by Rhapsody on 2007-03-02
> **AstalaVista said:**
> A year ago, I got into quite a similar situation.  I just got a new PC, at around the time when Dapper was released.  The PC was has integrated GeForce6100, Realtek 5.1 audio.  It took me a fair amount of tinkering to get nVidia driver installed.  More time spend to enable widescreen resolution (I have a widescreen LCD).  I was never able to get sound to work properly.  After a couple of weeks, I gave up and went back to Windows.  Six months later, Edgy was released, and everything worked right after installation.

I did get the idea that this may be down to the motherboard being too new. The manual does boast about it being "Windows Vista Home Basic ready", suggesting to me that it's no more than a few months old.

> **AstalaVista said:**
> In terms of addressing your problems, I suggest you start a thread for each specific problems.  I got mine resolved one by one, but in the end, I just need to get my PC working and be productive.

I may try that next, if I get nothing from this topic.

> **AstalaVista said:**
> Now, I am more careful when getting a new PC; I make sure the model has been in the market for at least six months; no bleeding edge hardware.

This hardly feels like bleeding edge hardware. It only cost £270. I can't really get anything else either. We hardly had the money to get this hardware, any upgrades or changes are pretty much out of the question. Any changes must happen in software.

> **AstalaVista said:**
> Feisty Fawn in due out in April.  Maybe you might get lucky.

That is a possibility, but that means spending another month and a bit without any sound or real multimedia capabilities. I'd really like to get this stuff working on Edgy Eft for now, since it's still current.

> **AstalaVista said:**
> And, I am not sure whether it has to do with Gnome or KDE.  Maybe you can try Ubuntu instead of Kubuntu?

I doubt it has to do with either, hardware detection is generally down to the kernel, Ubuntu and Kubuntu being essentially identical aside from the desktop environments. But I may try it anyway. Anything to get sound working again.

---

### Post by Chunghau on 2007-03-17
Rhapsody,

Feisty Fawn Herd 5 works pretty well with the K8NF6G-VSTA, which I just installed.

I'm running 32-bit Kubuntu with the generic kernel.  After install, adept will want to get more updates.  That's fine and actually improved a lot of the stability of the apps.  However, The newer kernel 2.6.20-11 caused my sound to disappear (everything plays but I don't hear anything).  I just rebooted with the Herd 5 kernel 2.6.20-9 and my sound has returned.

I haven't tried the binary nvidia driver yet.  Will do that sometime later.

---

### Post by AnRa on 2007-03-20
I've answered some of your questions in your previous thread.

---

