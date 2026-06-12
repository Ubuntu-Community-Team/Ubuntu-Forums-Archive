---
title: "Linux Commands..."
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by Mercurybird on 2006-01-01
Where can I DL a complete, or nearly so, list of Linux commands? I want to get around in Ubuntu at the prompt so I can deal with the video issue I have with the ATI Radeon driver.

I've DL the "ati-driver-installer-8.20.8-x86_64.run.txt" and its on my Windows XP desktop. I want to burn it to a CD, then use the Ubuntu prompt to grab it from the CD to install it properly.

Oh wait a minute, Ubuntu resides on my XP box, on a seperate drive. So I can't Putty into right? Well if I drop the drive into another computer and make it a standalone, I could then couldn't I?

What do I need to do? I have some threads bookmarked to follow. I just need to get to the file on my XP desktop. My Ubuntu boots up to chaos. So the prompt is my only way to go. Unless I can Putty in. Or maybe WinSCP.

EDIT...

Oh I guess I could build a system with some very simple and straight forward hardware. That would work would it? A simple video card, etc..

Heeeeeeelp! :p :p :D :p :p

---

### Post by rjwood on 2006-01-01
[LinuxCommand.org: Learn the Linux command line. Write shell scripts.]("http://www.linuxcommand.org/index.php")

---

### Post by lunatech on 2006-01-01
They are already installed, from a xterm just do " info coreutils"  to get started.  Have a look at this page [http://dtil.info/index.php/Finding_Help_in_Linux](http://dtil.info/index.php/Finding_Help_in_Linux) for more

---

### Post by Mercurybird on 2006-01-01
[QUOTE=lunatech]They are already installed, from a xterm just do " info coreutils"  to get started.  Have a look at this page [http://dtil.info/index.php/Finding_Help_in_Linux](http://dtil.info/index.php/Finding_Help_in_Linux) for more[/QUOTE]

Okay I mucked around at the prompt enough to know that it knows I have an ATI Radeon 9200. But when I try to launch xterm it tells me that it can't because the Display is not set.

Does this point to the fact that I need to resolve the ATI problem? Or does this indicate something much simpler?

---

### Post by lunatech on 2006-01-02
[QUOTE=Mercurybird]
Does this point to the fact that I need to resolve the ATI problem? Or does this indicate something much simpler?[/QUOTE]

Sorry my mistake :-(

xterm is a gui terminal emulator.  If you are already on a terminal, just do 'man coreutils'

---

