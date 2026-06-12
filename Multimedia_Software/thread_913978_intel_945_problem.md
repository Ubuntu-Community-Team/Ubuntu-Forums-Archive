---
title: "intel 945 problem"
date: 2008-09-08
forum: Multimedia Software
---

### Post by rafa23189 on 2008-09-08
Hi:
I have a P4 631 with a intel945gcpe and 1gb of ram (667), 
"lsmod" indicates I have an intel 915 chipset, how do I change that?
Flight gear runs really slow, is my pc wrong conifured? or my hardware does not support it? 
Cheers
Rafa

---

### Post by Whiffle on 2008-09-08
Open up a terminal and run:


glxinfo | grep direct


If it says Yes, then your drivers are correctly installed.  There are a couple of tweaks we can add though that will speed things up a bit.

---

### Post by rafa23189 on 2008-09-08
It said Yes, so I should get a new pc:(

---

### Post by Whiffle on 2008-09-08
Yeah Intal 915 isn't the most powerful.  I have it on my laptop... 

But, we can help it a little.  Do:
```

gksudo gedit /etc/X11/xorg.conf

```

and scroll down to the section labeled "Device".  It should have a line called "Driver", which has "intel" to the right of it.  Add the following couple of lines, if they're not already there:

```

Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"

```


Log out, and log back in, and hopefully things will be a little snappier.

---

### Post by rafa23189 on 2008-09-09
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"


Mine is a 945 not a 810, 810 is much older:(

---

### Post by Whiffle on 2008-09-09
Thats normal, the i810 driver covers a bunch of the different intel cards.  Which version of ubuntu are you using?

---

### Post by rafa23189 on 2008-09-10
8.04.1

---

### Post by Yellow Pasque on 2008-09-10
> "lsmod" indicates I have an intel 915 chipset
How does it do that? What does lspci show?

---

### Post by rafa23189 on 2008-09-10
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
You were right

---

