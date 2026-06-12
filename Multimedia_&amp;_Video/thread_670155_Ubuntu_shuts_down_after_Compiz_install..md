---
title: "Ubuntu shuts down after Compiz install."
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by Absinthe Minded on 2008-01-17
Hi all,

I recently spent ages getting Compiz to work so that I could use all the nice display features, such as the cube, etc.

All working lovely, but it seems that since the install, the PC kind of turns itself off. The tower is still running and the screen is still on - it's just blank. I've disabled the power saving settings, but that doesn't help.

Has anybody else had this problem, or do any of you know what it might be?

Cheers,
Nick.

---

### Post by namnam on 2008-01-17
In the steps you took to get it running, did you by any chance install new display drivers?

---

### Post by Absinthe Minded on 2008-01-17
> **namnam said:**
> In the steps you took to get it running, did you by any chance install new display drivers?Well, I was originally running onboard video and threw an ATI card in instead as I didn't think the onboard would be up to it.

I had lots of trouble with driver install, etc (for the new card), so I gave up and threw it out! On returning to the onboard graphics, I installed the restricted drivers (but they were running the card before the Compiz install).

Cheers,
Nick.

P.S. Thanks for trying to help me out!

---

### Post by namnam on 2008-01-17
You say the screen is blank, but if you somehow can get to the terminal by either pressing CTRL+ALT+F1 or by logging in remotely then you could try setting up a new xorg.conf by:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

The "-phigh" is so that the system tries to figure out good default settings. Otherwise you'll get loads of questions.

I hope that helps!

---

### Post by Absinthe Minded on 2008-01-17
> **namnam said:**
> You say the screen is blank, but if you somehow can get to the terminal by either pressing CTRL+ALT+F1 or by logging in remotely then you could try setting up a new xorg.conf by:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

The "-phigh" is so that the system tries to figure out good default settings. Otherwise you'll get loads of questions.

I hope that helps!I can try that when I get home. It won't be a problem to get to the terminal - the shutdown problem only seems to arise when I'm out of the room! I've just remembered that sometimes when I return to the room, the login screen is up.

Thanks again for helping out - I'll let you know how I get on.

Cheers,
Nick.

---

### Post by Absinthe Minded on 2008-01-17
OK, just tried it and here's what I get:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080117215008
nick@nick-linux:~$ 
```

I forgot to tell you that I edited the code below, I'm pretty sure that was in the xorg.conf - all I did was change the '0' for composite, to '1'. That's what eventually got Compiz to work.

```
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

So, maybe that's what the customised configuration warning is all about, Should I ignore the warning and continue (and, if so - how do I continue?)

Sorry for such noob-ness.

Cheers,
Nick.

---

