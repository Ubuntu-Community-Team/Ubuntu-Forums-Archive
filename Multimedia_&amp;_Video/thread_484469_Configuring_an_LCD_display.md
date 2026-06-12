---
title: "Configuring an LCD display?"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by Erdaron on 2007-06-25
I'm having some trouble configuring my monitor to run properly with my hardware. It runs almost perfectly - except during boot when the login screen should show up, the monitor goes dark and displays the message "Input signal out of range." I can type in my username and password blind, and then everything goes back to normal.

Things that may be relevant:

```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

```

From /etc/X11/xorg.conf:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	49.0
	Vertrefresh	43.0	-	72.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection
```

```
aticonfig --query-monitor
  Connected monitors: crt1
  Enabled monitors: crt1

```

I'm using Feisty with the latest kernel. The monitor is a flat panel LCD HP Pavilion vf15

---

### Post by Gremlinzzz on 2007-06-25
if you go to system_adminastratoin-login window -security- you can enable automatic login.till you find a fix .

---

### Post by Erdaron on 2007-07-24
Thanks for the tip, Gremlinzzz. I"m currently running in the automatic login mode.

Looking around, I've found that if I remove GDM, I'll have a simple text-mode login, and then I could just run startx, and that should bring up Gnome.

Does GDM do anything else? Because I'm not really attached to a graphical login window. Especially since I can't see it anyway.

---

