---
title: "Old version of VLC player"
date: 2010-12-17
forum: Multimedia Software
---

### Post by DerbyLoco on 2010-12-17
Hello - When I tried upgrading Ubuntu 9.04 to 9.10 I lost my installation of vlc-0.8.6d. Unfortunately the latest version that can be installed does not work very well on my computer, nor did 9.10, because it is an old system I think, so I reinstalled 9.04.

Is it possible to obtain a compiled version of vlc-0.8.6d that I can run on Ubuntu 9.04.

I have tried to compile vlc-0.8.6d from a Tarball but I don't really know what I am doing and it did not work as I could not solve one of the ./configure errors.

I hope someone can help as I have a load of captured mpeg4 music video clips I enjoy playing.

---

### Post by BicyclerBoy on 2010-12-17
Search for VLC ppa for ubuntu 9.04...

My advice is get the last version you can..
You will need to add a private ppa & key to your package manager (synaptic).

You would be well served by getting your OS to a LTS release like 10.04 Lucid.
*buntu 9.04 is past end of life.

Why problems did 9.10 cause ?
What's the hardware ?
There are many kernel options to work around old h/w.

---

### Post by DerbyLoco on 2010-12-17
I only have 245MiB of Ram with a Pentium 1.60GHz processor and I was thinking of installing Hardy Heron rather than going upwards.

My system just ran very slowly when playing the clips with the latest version of VLC and I see that old versions are available for Windows systems hence my question.

---

### Post by lykeion on 2010-12-17
You can do this:
1. uninstall current version of VLC
2. download deb package for old version of vlc from packages.ubuntu.com, 0.86 version found [here]("http://packages.ubuntu.com/hardy-updates/vlc")
3. install deb package by double-clicking it
4. lock update manager to not automatically update VLC, like this:
System > Administration > Synaptic
Search for vlc package and select it, then select from menu Package > Lock Version

BTW I agree with BiciclerBoy that using an old version of VLC is probably not the way to solve your issues. And also that you should update Ubuntu to 10.04. Contrary to Windows, updating to a later version of Ubuntu does not necessarily mean higher system requirements, actually it often means more support for old and new hardware.

---

### Post by BicyclerBoy on 2010-12-17
The windows distribution does not use any package management so old archives are all over the web.
I'm sure you will find a ppa for VLC on an older *buntu.

Well the processor is still faster than an atom in my netbook...
But this is running *buntu netbook edition.

Get more RAM ..the type you need is basically free to a good home.
A cell phone has more RAM than this...

There is a netbook-remix that has very low system requirements.
The desktop GUI is not same as Gnome, but works well.

VLC runs okay on atom 270 doing simple stuff. Most netbooks are crippled by intel graphics.

---

### Post by linux18 on 2010-12-17
you could switch to a lighter variation rather than an older one, I'm running [Lubuntu 10.10]("http://lubuntu.net/") from a 4 GB usb stick on my main computer (HDD crash) right now, my ram usage is 70MB, my CPU averages 3% usage, and the newest vlc plays fine

---

### Post by DerbyLoco on 2010-12-17
Thank you all - I can see that I am going down the wrong path.

I will upgrade to 10.10 and continue to explore Ubuntu, (with some more memory).

I now know about PPA's and how to find old versions so I think we can say my question is answered and the issue solved - can I mark it so?

Once again many thanks for the help.

---

### Post by ron999 on 2010-12-17
> **DerbyLoco said:**
>  my question is answered and the issue solved - can I mark it so?


Yes, go into '[COLOR="Red"]Thread Tools[/COLOR]' at the top.

---

