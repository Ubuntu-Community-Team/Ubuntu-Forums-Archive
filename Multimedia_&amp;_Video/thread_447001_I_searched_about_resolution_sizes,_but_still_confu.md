---
title: "I searched about resolution sizes, but still confused"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by PLmatt91 on 2007-05-17
I am new to using Ubuntu and I gotta say, this is extremely hard for me to understand, yet use.  I used this [http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04) to help me out but I don't tihnk half of the stuff work on it.  I don't know why.  

Now I have a LCD monitor capable of going to 1400x1050 resolution, but I"m currently stuck on 1280x1024.  How can I change this? Thanks for all the help,

-Matt.

---

### Post by Dekunuts on 2007-05-17
this can usually be fixed quite easily.
first you need to find out what the hsync and vsync ranges for you monitor are (brand site, manual,...).
Then enter these at the correct place in the config file. 
access the config file by typing

sudo gedit /etc/X11/xorg.conf

the section you need to edit looks like this.

Section "Monitor"
	Identifier	"B_106055"
	Option		"DPMS"
	HorizSync	30-94
	VertRefresh	50-75
EndSection

also make sure that the 1400x1050 

	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

is in there

i can't remember if you need to reboot but restarting x has to happen i think, so just reboot after saving the file and having edited it correctly.

---

