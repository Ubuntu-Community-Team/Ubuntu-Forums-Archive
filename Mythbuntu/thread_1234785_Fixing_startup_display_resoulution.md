---
title: "Fixing startup display resoulution"
date: 2009-08-08
forum: Mythbuntu
---

### Post by tonycollinet on 2009-08-08
OK - I've got 9.04 running fine, setup on a monitor.

I'm now trying to get it to run on my TV - a panasonic 42 inch, using the VGA Input.

The problem is that mythbuntu always boots into a resolution of 1152x864 - which the TV won't display

I can change this (using VNC) to 1360x768, which the TV displays fine, but next time I boot, it reverts back to 1152x864.

Same happens if I select 1024x768.

How can I fix the resolution to something the tv will show.

Thanks



I am running on a compaq PC off the built in graphics. lspci -v gives:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
	Subsystem: Compaq Computer Corporation Device 00b9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at fc400000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>
	Kernel modules: intelfb

---

### Post by movieman on 2009-08-08
There's a bug in xfce where it doesn't set the resolution correctly when you log in; I had the same problem, where it would always switch to 1360x768 when I want it to run at 720x400. I believe it's fixed in 4.6.1 and we're running 4.6.0.

I initially put an appropriate xrandr line into an autostart script so it switched on login, but it might be better to put that into the session startup script in /usr/share/mythbuntu so it's available to all users. In my case it's:

xrandr --output VGA --mode 720x400 --rate 70

but you'd need to figure out the right parameters for your system.

---

### Post by tonycollinet on 2009-08-09
MM - thanks for the tip:

After some more reading around - I solved this by adding the following to the "Screen" section of xorg.conf

		DefaultDepth	24
		SubSection	"Display"
			Depth	24
			Modes   "1360x768"
		EndSubSection


I now want to set a 50Hz output frequency, to avoid judder with UK Pal live TV (And recordings?) I'll see if I can work that out for myself.

OK - Answered that one now. By using the modeline generator (link below) I seem to be able to create pretty much any mode I need. BUT my TV can't display 50Hz on VGA - so I'll need to get a graphics card with TV OUT.

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)


PS - How do I add a "solved" to the subject line?

---

### Post by NTolerance on 2009-08-09
> **tonycollinet said:**
> MM - thanks for the tip:

After some more reading around - I solved this by adding the following to the "Screen" section of xorg.conf

		DefaultDepth	24
		SubSection	"Display"
			Depth	24
			Modes   "1360x768"
		EndSubSection


I now want to set a 50Hz output frequency, to avoid judder with UK Pal live TV (And recordings?) I'll see if I can work that out for myself.

OK - Answered that one now. By using the modeline generator (link below) I seem to be able to create pretty much any mode I need. BUT my TV can't display 50Hz on VGA - so I'll need to get a graphics card with TV OUT.

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)


PS - How do I add a "solved" to the subject line?

Be careful with a TV-out video card.  There may be precious few that can output a HD signal and they'd need to have a component output.  Most, if not all, videocards only have S-Video output which cannot do HD resolution.  I assume your current video card is integrated and doesn't have a DVI port?  You may want to look into simply upgrading your video card and using a DVI-HDMI cable.  No guarantees, but it's worth looking into.

---

