---
title: "Yahoo! Games don't load."
date: 2010-10-08
forum: Multimedia Software
---

### Post by Stray Wolf on 2010-10-08
When I look at my content plugins in Firefox and the list of IcedTea plugins is 29 items long.  Is this my problem or do Java Applets just not work in Lynx?

---

### Post by Yellow Pasque on 2010-10-08
If you can't get it to work with open-source java (openjdk/icedtea), then uninstall that stuff, enable the ubuntu "partner" repository and install the official Sun Java plugin (sun-java6-plugin).

---

### Post by Stray Wolf on 2010-10-08
> **Temüjin said:**
> If you can't get it to work with open-source java (openjdk/icedtea), then uninstall that stuff, enable the ubuntu "partner" repository and install the official Sun Java plugin (sun-java6-plugin).

I'm assuming you mean the "Canonical" Partner repository or is there an actual "Ubuntu" Partner repository?  I'll proceed under my assumption.

Okay, I couldn't find sun-jav6-plugin in the repository so I did sudo apt-get install and several items installed.  I still don't see it in my list of pluins in mozilla.  Many of the Icedtea plugins are still there too...I'll try to delete those through synaptic.

I don't see any Icedteas checked in Synaptic.  I do see a folder in /home.icedteaplugins.  Should I delete that?

---

### Post by Stray Wolf on 2010-10-08
Well, I didn't delete the .icedplugin in my home folder but I did install java through the terminal and Yahoo games worked right away.  I personally didn't need it.  I've been installing Ubuntu on systems for people who can't afford Windows and all the problems.  They're simple end-users who didn't even know what an operating system is.  The poor people I try to get out from under Windows thanks you!

---

