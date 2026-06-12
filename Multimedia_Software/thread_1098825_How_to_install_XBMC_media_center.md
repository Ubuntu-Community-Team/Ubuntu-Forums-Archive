---
title: "How to install XBMC media center"
date: 2009-03-17
forum: Multimedia Software
---

### Post by Firidan on 2009-03-17
I have Ubuntu 8.10 x64 and I'm trying to install XBMC media center (xbmc.org). Elisa does the work but XBMC looks a lot better. I followed the instructions ([http://xbmc.org/forum/showthread.php?p=185738](http://xbmc.org/forum/showthread.php?p=185738)), added XBMC repository, imported the key but could not find it in Ubuntu Add/Remove software. What do I do to install this media center?

---

### Post by cariboo on 2009-03-17
Did you update the sources list after adding the repositories and keys? You might be better off using synaptic instead of add/remove progreams.

Jim

---

### Post by lovinglinux on 2009-03-17
Since you already added the xbmc repository and the key, then just update the repositories then run the following command:

```
sudo apt-get install xbmc
```

---

### Post by w1ljam35 on 2009-03-18
I have the same issue but without 64 bit version. I did update the sources and I also looked in Synaptic but I can't find any trace of xbmc. I will install via command line but I want to understand why it's not showing up in the package manager. Any ideas? Thanks.

---

### Post by w1ljam35 on 2009-03-18
When I tried to do the command line install, I discovered the package was not installed at all. After going through it again step-by-step, I discovered I had copied a non-ascii character to the apt field in the software sources entry. I cut the bad character out (had to scroll to the right to see it), saved and reloaded sources. I noticed right away the message changed from downloading 42 to 47. I still had to go to Synaptic to see xbmc. Add/remove didn't show it.

---

### Post by ningenity on 2009-08-12
Had the same problem: followed the steps to install XBMC up through 'search for "xbmc"', which failed.  Then (eventually) I remembered that Synaptic's 'Quick search' does not search by package name.  Apparently "xbmc" is not found in whatever fields Quick search does look in.

So.  The XBMC installation instructions should probably read as follows (suggested changes in red).


[LIST]
[*]      Search for "xbmc"[COLOR=Red], not in Quick search, but through the menu: Edit -> Search... -> Look In: Name.[/COLOR]
[/LIST]
 
You've probably solved your problem by now, but, hope this helps, for anyone.

---

### Post by ubu-for on 2009-09-22
> **ningenity said:**
> So.  The XBMC installation instructions should probably read as follows (suggested changes in red).


[LIST]
[*]      Search for "xbmc"[COLOR=Red], not in Quick search, but through the menu: Edit -> Search... -> Look In: Name.[/COLOR]
[/LIST]
 
You've probably solved your problem by now, but, hope this helps, for anyone.

Thanks for your hint but doesn't solve the problem.

I've copied the following source from the XBMC HowTo but Synaptic can't find any packages.

```
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ jaunty main
```

Maybe you have another source and the one above is offline?

---

### Post by ubu-for on 2009-09-22
> **lovinglinux said:**
> Since you already added the xbmc repository and the key, then just update the repositories then run the following command:

```
sudo apt-get install xbmc
```

The command line installation works!

No idea why Synaptic can't find the packages.

---

### Post by dshosu on 2009-10-16
> **ubu-for said:**
> The command line installation works!

No idea why Synaptic can't find the packages.

Same here. I refreshed sources in both the Add/Remove programs menu and in Synaptic, neither of which displayed XMBC when I searched for them. But it's installing via  command line in Terminal.

---

### Post by jmb2012 on 2009-10-21
Anyone know why after installing xbmc it took over my laptop. Now it start up with xbmc. I have no clue how to fix this I want it gone. plz help

---

### Post by doppis on 2009-10-27
> **lovinglinux said:**
> Since you already added the xbmc repository and the key, then just update the repositories then run the following command:

```
sudo apt-get install xbmc
```

Worked for me...thanks!

---

### Post by vinutux on 2009-10-28
plz...mark thread SOLVED under **[COLOR="Red"]thread tools[/COLOR]** [top right]

---

