---
title: "Moonlight / Silverlight installation - How does this work?"
date: 2009-02-23
forum: Multimedia Software
---

### Post by crunchfighter on 2009-02-23
Has anyone gotten Silverlight to work?  Don't see this addressed in the forum.

Background:
I'm trying to listen to a local radio station that uses Silverlight for their internet stream.  (Running Intrepid 64 bit)

What I've done so far:

From the Synaptics Package Manager, I installed:
mono-smcs and associated packages (found with a search for Silverlight)
I tried to access the radio stream w no luck: "You need Silverlight..."
I went to this wiki: [http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight](http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight)
and added the repositories:

deb [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main 

Did another search of the repositories for Silverlight or Moonlight, but only came up with the mono-smcs package (like it should as I understand Intrepid has the Moonlight package already)

I do not see Silverlight or Moonlight in the Applications or System menus.  Do I need to run a terminal command of some sort to get this running?

I also tried adding it as an add-on to Firefox, but I don't see anything listed.  

If anyone has an idea to get this project moving, I'd appreciate hearing it.
Thanks.

---

### Post by cb951303 on 2009-02-23
I just installed the addon through here [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)
and it works.

Not that there are too many pages that still uses SL 1.0 :D

---

### Post by crunchfighter on 2009-02-23
Wow.  That was easy.

Thanks.

SOLVED.

---

### Post by directhex on 2009-02-23
> **crunchfighter said:**
> deb [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu) intrepid main 

Did another search of the repositories for Silverlight or Moonlight, but only came up with the mono-smcs package (like it should as I understand Intrepid has the Moonlight package already)

You seem to suck at adding repositories:
```
jms@destiny:~$ apt-cache search moonlight plugin
moonlight-plugin-core - Free Software clone of Silverlight 1.0 - plugin core components
moonlight-plugin-mozilla - Free Software clone of Silverlight 1.0 - Xulrunner 1.9 plugin
```

The package is now part of Jaunty.

---

### Post by directhex on 2009-02-23
Oh, for reference, smcs is a compiler to produce Silverlight 2.0 content

---

### Post by wyth on 2010-03-09
> **directhex said:**
> You seem to suck at adding repositories

Sheesh... I just found this thread while searching for info on the latest moonlight.

You seem to suck at tact.

---

### Post by checoimg on 2010-12-30
Thanks!!!

---

