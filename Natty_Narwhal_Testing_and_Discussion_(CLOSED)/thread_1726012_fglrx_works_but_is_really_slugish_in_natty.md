---
title: "fglrx works but is really slugish in natty?"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by AndersAA on 2011-04-10
Just tried natty, and fglrx installed fine. See no errors in dmesg or in /var/log. Xorg starts up, fglrx_info shows ati everywhere.

But, it's really really slugish. It's slower than the open source driver is (and that feels noticably slow as well). Is this known/any workarounds?

---

### Post by andrek on 2011-04-10
Disable sync to vblank in compizconfig settings manager (OpenGL section). You might also want to go to Composite -> untick Detect Refresh Rate and move the Refresh Rate slider up to 200.

---

### Post by AndersAA on 2011-04-10
Tried that, still slow unfortunatly :/, doesn't seem to have made a change at all.

---

### Post by ranch hand on 2011-04-10
I will try that too in Nawty.

Checked this thread because I have the same problem in my Debian install.  No compiz on here but fglrx is a little better than the FOSS drivers (a first for me).  But it is laggy.

I think it has to have something to do with 2.6.38 kernel.  Probably an update or 2 will fix it.

---

### Post by AndersAA on 2011-04-12
I just tried glxgears. I get around 28k frames when using unity. And around 35k without. However, in unity, it looks like I'm getting around 3fps.

Scrolling in google chrome is perfectly smooth, however, dragging the window around is lagging really bad.

---

### Post by rajeev1204 on 2011-04-12
There is an issue with the vsync in fglrx and in compiz.It is recommended to disable both and see if it helps.

A new driver should fix it this month i hope.

---

### Post by ranch hand on 2011-04-12
I haven't done anything to my nawty install and do not think I will.

Here on Debian testing the problem seems to have cleared up as of late yesterday.  I do not use compiz (never liked it) so I have no idea if that would be effected by the fglrx updates I got or not.

---

### Post by AndersAA on 2011-04-13
Tried disabling vsync in opengl options in config.
In aticonfig
and turned off detect refresh rate and set it to 60.

Still have the exact same problem :/

---

### Post by laleshii on 2011-04-26
Had the same problem. Worked when disabled Vsync and detect refresh rate ( and set to 200).

But still having problems with 3D . When I run glxgears I get about 1700fps ( I don't know if that is good performance for my 5650 HD card ) but the gears just stall .

---

### Post by screaminj3sus on 2011-04-26
I had this problem (dragging windows was really laggy, everything else was fine) turning off sync to vblank in compiz worked for me though, I was able to leave vsync (tear free desktop) enabled too. My card is an hd2600.

---

### Post by Netich on 2011-04-27
vblank in compiz has also worked for me (slugish window movement).

Anyway, i remember tearing when moving windows in maverick, so i guess it is a new option that doesnt work too well.

Btw, natty has been the release with less fglrx-ati related problems.

---

