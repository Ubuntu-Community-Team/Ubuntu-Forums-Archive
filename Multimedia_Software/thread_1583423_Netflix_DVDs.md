---
title: "Netflix DVDs?"
date: 2010-09-27
forum: Multimedia Software
---

### Post by pivotraze on 2010-09-27
How can I watch a Netflix DVD on linux? I got Book of Eli in my mail, and when I try to open it in VLC, it just blinks the name then dissappears. So I then try to open it in Movie Player and it says "Can't read from resource."

What do I do D: I wanna watch it on my comp!

System Specs:
Version of Ubuntu: 10.10 Maverick Meerkat Alpha 3
Version of VLC: 1.1.4
Graphics Card: Intel 965GM
Sound Card: SigmaTel HD Audio
RAM: 1GB

---

### Post by darkstarbyte on 2010-09-27
For this problem I would suggest either going to the package manager and finding libdvdcss the newest version or opening the terminal, and typing 

```

sudo apt-get install libdvdcss 

```

It will ask for your password.

I hope this helps.

---

### Post by pivotraze on 2010-09-27
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss' has no installation candidate


So I searched with Synaptic Package Manager and it turned out to not exist? It doesn't find it..

---

### Post by Banned. on 2010-09-29
> **pivotraze said:**
> So I searched with Synaptic Package Manager and it turned out to not exist? It doesn't find it..

I would just try this command:
sudo apt-get update

and then:
sudo apt-get install libdvdcss

---

### Post by Zuul47 on 2010-09-29
this works, ive tried it already...update and you can also find it in ubuntu software center as well

:guitar:

---

### Post by tommcd on 2010-09-29
> **pivotraze said:**
> So I searched with Synaptic Package Manager and it turned out to not exist? It doesn't find it..
You have to add the **medibuntu** repository to your /etc/sources.list.d/ directory to get libdvdcss, the w32 codecs, and a few other things See this:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Write back if you need more help.

---

### Post by myt on 2011-01-30
yet another example of how the Ubuntu community is fantastic.  Thanks to all who posted on this.

---

### Post by nmaster on 2011-01-30
have you seen these links?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by Colper on 2011-02-10
Thank you for this post. Your first link worked for my Audio and Video, when using VLC.

(One more checked box on "Tasks that Ubuntu needs to to be able to do before I uninstall Windows 7")

---

