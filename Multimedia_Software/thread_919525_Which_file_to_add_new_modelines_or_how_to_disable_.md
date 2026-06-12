---
title: "Which file to add new modelines or how to disable `bulletproof-X'"
date: 2008-09-14
forum: Multimedia Software
---

### Post by chrysemys on 2008-09-14
Hi, I am setting up a system with kubuntu for a friend of mine and am experiencing some annoying problems which I am unable to fix on my beloved commandline.

I need to find the place where I can add a customised modeline so the system will not forget or overwrite it. After 10 years of Debian/GNU Linux tweaking experience I wopuld expect this to be comfortably located in a plain ASCII file somewhere, but I cannot find this anywhere.

The reason why:
In order to get some game running with ATI-fglrx drivers I need to set kdm to use a virtual desktop which is 64-pixels wider than my actual desktop (1984x1200 on a 1920x1200 screen: Iiyama ProLite E2403WS) This is a worklaround for a bug in the fglrx-driver garbling up the screen.
I edited the xorg.conf file and added the line 
Virtual  1984  1200
in the  SubSection "Display" of the applied `Section "Screen"': This does not give me the required virtual desktop at startup, but enables me to set it to the right size with the graphical tool (as a commandline addict I find this a bit cumbersome, but alas..) at this point my cerfully constucted xorg.conf apparently gets overwritten bluntly with the erroneous 1920x1200 modeline which I already fixed before.
After the next reboot the server indeed fails to start up with the modeline and the `bulletproof x' monstrosity starts up and reduces the screen resolution further because I cannot select the proper monitor to get the working modeline.

To me solutions appears to be:
* Either add the correct modeline permanently to the database with all other monitor definitions, but I am unable to locate the file with these definitions.

* Or find out how I can permanently store the information extracted by displayconfig-gtk from the Iiyama .inf file on my system: it seems to be forgetting this.

* Disable the bulletproof X feature: someone wrote this can be don in the /etc/gdm/gdm.conf, but since this file is absent on the Kubuntu system I do not know where else I should do this.

* wait six weeks and hope my monitor definitions are included in Ibex

*On the long term: install a future version of Fglrx where the initial bug is fixed.

Its quite a long story, but I hope someone can create some clarity.

---

### Post by EvanCarroll on 2008-11-09
I just wanted to revitalize this posting with a bump. This is totally crazy. Putting modelines in xorg.conf doesn't disable the DDC. How do I disable the DDC, "NoDCC" is not working for me. I have a 1080p television hooked up through hdmi. It doesn't like the 800x600 resolution that every libsdl app wants to put it in when hey go full screen..

---

