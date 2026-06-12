---
title: "No 64-bit for Netbook?"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xebian on 2010-10-06
Newer netbooks are now 64-bit and multicores as well.  But where is the 64-bit version?

---

### Post by mhgsys on 2010-10-06
[https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64](https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64)

---

### Post by seeker5528 on 2010-10-06
> **xebian said:**
> Newer netbooks are now 64-bit and multicores as well.  But where is the 64-bit version?

[Kubuntu](https://wiki.kubuntu.org/MaverickMeerkat/RC/Kubuntu)

> What's New

Combined Desktop/Netbook ISO image

Later, Seeker

---

### Post by xebian on 2010-10-06
> **seeker5528 said:**
> [Kubuntu](https://wiki.kubuntu.org/MaverickMeerkat/RC/Kubuntu)



Later, Seeker

I know [COLOR="RoyalBlue"]**Kubuntu**[/COLOR] has it.  We are talking about [COLOR="Sienna"]**Ubuntu**[/COLOR] here.

---

### Post by uRock on 2010-10-06
Use the 64bit minimal installer, then run the command to install the netbook edition package.

---

### Post by FuturePilot on 2010-10-06
> **mhgsys said:**
> [https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64](https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64)

Ugh, that looks like a mess. An easier way would be to use the 64bit Minimal ISO and select the netbook interface when prompted.

---

### Post by seeker5528 on 2010-10-07
> **xebian said:**
> I know [COLOR="RoyalBlue"]**Kubuntu**[/COLOR] has it.  We are talking about [COLOR="Sienna"]**Ubuntu**[/COLOR] here.

Well.... It's 64 bit, it's for netbook. Just takin' things literally. :P

Later, Seeker

---

### Post by VMC on 2010-10-07
> **seeker5528 said:**
> Well.... It's 64 bit, it's for netbook. Just takin' things literally. :P

Later, Seeker

LOL. Quite right.

Odd though, that Kubuntu has one, and Ubuntu doesn't. Usually its the other way around.

---

### Post by seeker5528 on 2010-10-07
> **VMC said:**
> Odd though, that Kubuntu has one, and Ubuntu doesn't. Usually its the other way around.

To me, from one perspective, if you consider that for the stock Ubuntu they still suggest running the 32 bit version on the download page, 64 bit netbooks are in the minority, and adding yet another ISO means more time building the ISO and doing QA, it's not all that strange.

From another perspective the bulk of stuff necessary to support a netbook, tablet, laptop, and desktop PC is the same, you need window management, compositing FX, ability to run without compositing if the hardware doesn't support it, some way to launch applications and permanent quick access to some amount of relevant information, and the ability to switch between running applications. If you build for flexibility (from a developer standpoint) instead of form factor you could account for all of these by having a small amount of stuff that shows different looks and options based on screen size, whether there is a keyboard attached, how much memory there is, etc... Gnome-shell doesn't provide this, Unity doesn't provide it, but if you consider they both use Mutter and Clutter, there could be potential for creating an ISO that supports both a normal desktop and a netbook, with or without Gnome-shell on the desktop side. 

If I select the ubuntu-netbook package in Synaptic on my desktop installation, it indicates 67.8 MB will be used. Several of those packages would be part of a stock Ubuntu installation anyway, Evolution, Rhythmbox, Ubuntu One, bluetooth stuff, etc... If I turn off the option to treat recommends as dependencies, it indicates 114 MB will be freed (swapping the regular foomatic-db stuff for the compressed db apparently).

So I guess the main difference as relevant to a single desktop/netbook ISO would be the amount of support in the KDE/Gnome stuff as provided by the upstream for actually providing a single environment that is adaptable to both. As far as fitting everything in a single ISO, it looks like that could be done.

Later, Seeker

---

### Post by CoreyB. on 2010-10-07
> **FuturePilot said:**
> Ugh, that looks like a mess. An easier way would be to use the 64bit Minimal ISO and select the netbook interface when prompted.

It's not a mess, all you have to do is install the normal 64-bit Ubuntu then copy and paste the four commands into the terminal, reboot and done.

---

### Post by CoreyB. on 2010-10-08
> **FuturePilot said:**
> Ugh, that looks like a mess. An easier way would be to use the 64bit Minimal ISO and select the netbook interface when prompted.

I cleaned it up a bit, so it doesn't look so daunting.

What do you guys think?

---

