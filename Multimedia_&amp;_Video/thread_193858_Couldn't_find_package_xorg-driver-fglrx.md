---
title: "Couldn't find package xorg-driver-fglrx"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by AntiKris on 2006-06-10
Hey folks,
   I've trolled around to try and answer my own question before breaking down and crying out for help.  I've got an x800 that I can't even get the GDM working on.  I'm noobish in the extreme, so be gentle.

    I'd like to try the fglrx driver that I've heard about, at least to get started, so I load to recovery and login as root.  When I try to install fglrx with the command apt-get install xorg-driver-fglrx, I get the response "Couldn't find package xorg-driver-fglrx".

    What ridiculously simple step am I missing?

---

### Post by _simon_ on 2006-06-10
I can see it in Synaptic (see screenshot). Try synaptic instead?

Just hit SEARCH and type in fglrx

---

### Post by AntiKris on 2006-06-10
[QUOTE=_simon_]I can see it in Synaptic (see screenshot). Try synaptic instead?

Just hit SEARCH and type in fglrx[/QUOTE]

Hey, I'd love to use Synaptic, but as I said, I can't even get the GDM working.  No xserver, just the ugly old root terminal!

---

### Post by _simon_ on 2006-06-10
very sorry! I read that but my brain didn't register :( ](*,)

---

### Post by _simon_ on 2006-06-10
This might help you..

[http://www.ubuntuforums.org/showthread.php?t=191944&highlight=x800](http://www.ubuntuforums.org/showthread.php?t=191944&highlight=x800)

Looks like you need to use the vesa driver in xorg.conf to begin with...

---

### Post by AntiKris on 2006-06-10
[QUOTE=_simon_]This might help you..

[http://www.ubuntuforums.org/showthread.php?t=191944&highlight=x800](http://www.ubuntuforums.org/showthread.php?t=191944&highlight=x800)

Looks like you need to use the vesa driver in xorg.conf to begin with...[/QUOTE]

Thanks--I saw that thread, but haven't tried it--largely because it still references apt-getting the xorg-driver-fglrx, which I seem unable to do.  What I'm really wondering is, is there a repository or something that I should be enabling?  If so, how do I do that from root term?

While I'm at it, is there a synaptic-esque tool for the terminal?  I seem to recall something like it the last time I screwed around with Ubuntu (many moons ago.)

---

### Post by sparhawk on 2006-06-10
have you tried editing the xorg.conf file and changing the Device driver for the vid card from "fglrx" to "ati" or "vesa"? That should get you to the gdm.

Did you try the ATI tutorial? I think you don't need the gdm. Here is the link.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Why do you boot to recovery? Doesn't the system boot to the terminal when the gdm fails to load. If you get a blank screen or something just type CTRL-ALT-F2 and that should give you a terminal even though x-server did not start. then log in as your regular user and sudo all root required commands. 

Let me know if that works for ya.

---

