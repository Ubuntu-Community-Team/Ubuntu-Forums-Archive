---
title: "xorg.conf identifier line needed for ATI"
date: 2009-01-16
forum: Multimedia Software
---

### Post by michaelalonzo on 2009-01-16
I am following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) 
and came to the point where I had to edit my xorg.conf file and add a few more lines which are:

Section "Device"
	[...]
	Driver		"fglrx"
	[...]
EndSection

I deleted the identifier portion of it by accident and saved the file. Now everytime I type:
sudo aticonfig --initial -f 

I get:
Parse error on line 38 of section Device in file /etc/X11/xorg.conf
	This section must have an Identifier line.

I try to reinstall the whole ATI driver in the terminal and the xorg.conf file is still the way I saved it as. 

I need to knwo what the identifier line is

thanks in advance

---

### Post by michaelalonzo on 2009-01-16
I added 
Identifier "Configured Video Device" 

and that seem to have solved it

---

