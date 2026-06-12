---
title: "K3B Locks Up Computer"
date: 2009-06-13
forum: Multimedia Software
---

### Post by dharvell on 2009-06-13
As the title states, whenever I attempt to use K3B for ANY reason (ripping, burning, copying, etc), the entire computer locks up.  To test to see if I could do ANYTHING at this point, I:

attempted to click off the K3B window to another application (the result was NO result)
repeatedly pushed the Num Lock button on keyboard (Num Lock did not blink)
attempted to open the Application Launcher by clicking it (nothing happened)

I attempted to remove and reinstall K3B, but this did not solve the issue.

If anybody has any ideas as to correct this problem (or has an alternative burner that is as feature rich as K3B), I would love to hear them!  All suggestions appreciated!

---

### Post by ajgreeny on 2009-06-13
Start it from terminal and see if you get any useful error messages that could help solve the problem.

---

### Post by dharvell on 2009-06-13
> **ajgreeny said:**
> Start it from terminal and see if you get any useful error messages that could help solve the problem.

Can't seem to.  When I try, it says that it cannot connect to the X server.  Since I've never run K3B from a command line, are there any specific options I need to run?  I read the man page, but it didn't give me any good information on running it from the command line.

---

### Post by ajgreeny on 2009-06-13
Very strange!  It should at least start the application as it does on my setup.  Perhaps you should "completely remove" k3b not just remove it, ie purge it from the system, as it could be a config that is wrong.

I also wonder if the problem is something to do with kubuntu using kde4, but k3b only being a kde3 version, I think.  Mind you, I run gnome, not kde, and k3b is always and has always been my burner of choice with no problems at all; I'd even use it on windows if possible, not that I run windows any more, but I'm sure you know what I mean!

---

### Post by dharvell on 2009-06-13
> **ajgreeny said:**
> Very strange!  It should at least start the application as it does on my setup.  Perhaps you should "completely remove" k3b not just remove it, ie purge it from the system, as it could be a config that is wrong.

I also wonder if the problem is something to do with kubuntu using kde4, but k3b only being a kde3 version, I think.  Mind you, I run gnome, not kde, and k3b is always and has always been my burner of choice with no problems at all; I'd even use it on windows if possible, not that I run windows any more, but I'm sure you know what I mean!

Yeah... it is the strangest thing.  I switched back to Kubuntu from Windows Vista (gack!) just over 2 weeks ago.  For the first 10 days, K3B worked beautifully... long enough for me to fall in love with the program.  Then, just a few days ago, I opened K3B to rip a few songs from a CD I just recorded in order to make a demo to shop to various record companies.  During the rip process, the computer locked hard.  I had to reboot.  When I rebooted, I noticed that the files did rip, successfully.  Since all looked good, I inserted a blank CD-R to burn the first of 4 demos... during the burn process, the computer locked.  When I restarted, I found that the burn was, again, successful.  I verified that by playing the newly burned CD on several CD players.  All was good.  

I went back in to copy the demo... during the copy process, the computer locked up, again.

As far as I know, there aren't any changes to the computer that would cause this to happen (unless a few security updates for Apache server would cause K3B to die).  So yeah... I'm stumped.

Question - when you start K3B from the prompt, what is the complete command you enter in (for example... when you want to rip a CD)?  I'll compare what you enter to what I enter... see if there's a difference.

Thanks!

---

### Post by dharvell on 2009-06-13
Well... let's add to the strangeness.

I just ended up burning 3 copies of my demo... without locking up.  Perhaps it was just some sort of anomaly that happened for a couple day stretch, then cleared itself up?

Worst type of computer problem, right there... one that clears itself up with no obvious fix.

Thanks for the input!

---

