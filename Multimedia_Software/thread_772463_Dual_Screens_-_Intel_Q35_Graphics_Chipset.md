---
title: "Dual Screens - Intel Q35 Graphics Chipset?"
date: 2008-04-28
forum: Multimedia Software
---

### Post by YTTK on 2008-04-28
I have just installed Ubuntu 8.04(Hardy Heron) on an Intel DQ35JO motherboard which has dual monitor support using the Q35 chipset. Both monitors (1440X900) are detected and are working in clone mode  using vesa driver. My question is has anyone used the latest driver from intel (2.30 I believe) and if so how do you install. I have tried to switch to existing intel drivers no luck. My main goal is to have both displays working independently. Or do I just need to wait for updates to make this work?

Thanks

---

### Post by YTTK on 2008-04-28
I Think my starting problem is the video drive by default is vesa and I have tried to change it to intel using the command
gksudo displayconfig-gtk
but no luck. So I dont know what to do next to correctly install a working intel driver.
Help anyone!

---

### Post by YTTK on 2008-04-28
I finally put enough pieces together from the bug reports to make this work.

1. Ubuntu by default - correctly configured my screens dual 1440 X 900 but in clone mode. when I ran gksudo displayconfig-gtk it showed I was using VESA driver and the screen settings were correct on one but not the second(even though both where working fine in clone mode). I assumed this meant I had a driver issue problem first - wrong!. If it works don't fix it.

2. using the link [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) I figured out I needed to add in my xorg.conf file under Section "Screen" I added
	SubSection "Display"

                Virtual                 2880 2880

        EndSubSection
3. shutdown or restart
4. run xrandr --output TMDS-1 --right-of VGA
Everything works great of course step 4 needs to be run at every boot and eventually I will figure out how to add this to my xorg.conf.
This was much easer than I thought and we need and updated sticky for those that are just starting. (like me)

---

### Post by unclben on 2008-05-04
> **YTTK said:**
> 2. using the link [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) I figured out I needed to add in my xorg.conf file under Section "Screen" I added
	SubSection "Display"

                Virtual                 2880 2880

        EndSubSectionI tried to do this with my 965G chipset and it borked X. I wonder what we did differently?

X correctly detects the native res and refresh rate for both of my monitors and screen cloning works fine, but I can't get an expanded desktop to work for the life of me. Everything I've tried completely FUBARs my display(s).

---

### Post by YTTK on 2008-05-20
This is my xorg.conf maybe this will help

[ATTACH]70931[/ATTACH]

---

