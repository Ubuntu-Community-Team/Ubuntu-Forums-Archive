---
title: "benchmark testing my video?"
date: 2009-03-01
forum: Multimedia Software
---

### Post by Daremo_06 on 2009-03-01
Newly intruduced to Ubuntu and Linux in general and I had some more questions. 

I am currently running a new installation of Intrepid on a Lenovo 8808 pc, with an ATI 9200Pro card.  I am also running dual displays, and while the default drivers seem to be working, occasionally the DVI screen "jiggles" a little tiny bit.  Its almost like we are driving down the road and hit a small bump.  The VGA out screen doesnt do this at all.  I also notice that certain programs that have a very tiny font (DVDFlick for example, which I am still working on getting running, but thats another story..) show that font as a jumbled mess instead of text.

When I run glxgears, I only get 650 fps avg and I know that its not a good benchmark.  So what is?  What can I run to make sure I am correctly configured for this card?  I don't currently play alot of 3d games, I mainly play puzzle pirates, surf the web and answer emails and chat in IRC/instant messaging.  But if I do decide to get something like say Halo for example, I would like my system to be already running correctly for it to display correctly.

Also my Xorg.conf is very small and seems to be a very basic default setup.  Is this normal for an Intrepid install with this ATI card (its not supported by the fglr drivers) or should it be full of various settings and configs.  Or does Xrandr handle that?

Here is the Xorg.conf file

Here is my Xorg.conf
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2880 1024
	EndSubSection
EndSection


Thanks,

Rob

---

