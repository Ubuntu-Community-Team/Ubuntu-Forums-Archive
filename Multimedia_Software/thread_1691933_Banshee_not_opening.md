---
title: "Banshee not opening"
date: 2011-02-20
forum: Multimedia Software
---

### Post by Johnny420 on 2011-02-20
I installed Banshee a few weeks ago and all was working fine. Today I tried to start it and it will not open. My mouse spun showing that something was working but it still never opens. I uninstalled and reinstalled and still not working. I like banshee more than rythmbox.

---

### Post by howefield on 2011-02-21
Try opening it via the terminal, you might get a clue in the output as to what is wrong.

---

### Post by Johnny420 on 2011-02-21
That was a great idea...Duh *forehead slap*....the only problem is that I got no return. The insertion point moved to the next line and stayed blinking as if it was working. I waited a few minutes and when I tried to close the terminal I was told that a process was running. But banshee still has not opened.
so I opened a terminal typed
banshee
 then opened another terminal typed 
ps -e
and the only reference I found was
 2510 ?        00:15:18 banshee-1
I am still new to Linux and appreciate the help

---

### Post by wyth on 2011-02-22
Might want to check out some of the ppa's -- are you using the standard Banshee for 10.10, or the unstable or daily build? There are some good differences between them, but I can't really say where the problem is. I've had it happen on all three versions on multiple machines. In the bugzilla, they suggest using the latest from unstable (which isn't all that unstable), but results vary.

For instance, my regular old standard one was crashing. I went back and forth between versions, and right now am running the latest unstable. It does what you describe every few times. However, I have the same version installed on my dad's PC, and it never starts. I only upgraded to unstable because his standard vanilla Banshee was crashing on start, but the upgrade didn't help.

So he's using Rhythmbox now.

[Banshee Team PPA]("https://launchpad.net/~banshee-team/+archive/ppa")

[Banshee Unstable]("https://launchpad.net/~banshee-team/+archive/banshee-unstable")

[Banshee Daily]("https://launchpad.net/~banshee-team/+archive/banshee-daily") (this ppa also recommends adding the Banshee Team ppa)

---

### Post by Johnny420 on 2011-02-23
_@ Wyth_ and Howefield : Thanx for your help and I am still having intermittent problems. I Will play around with the different versions and see what I can figure out.

---

