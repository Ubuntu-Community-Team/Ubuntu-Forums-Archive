---
title: "HELP: Installing Inkscape &amp; libpng &amp; zlib"
date: 2008-12-12
forum: Multimedia Software
---

### Post by Paulzy on 2008-12-12
I want to install **Inkscape**. Everyone has it installed. But I can't. configure says I don't have right **libpng 1.2** version. I have **1.2.15**,  I downloaded **libpng-1.2.33**. But libpng's **configure** it wants **zlib**! But the Synaptic Package Manger says I have **zlib1g 1:1.2.3.3** installed.

COME ON!!

Why is installing software in linux so blast compilcated?! I want **Inkscape**. I've installed programs via the command line before, but this thing won't budge.... Are there blast straight forward binary installs for Ubuntu Linux. COME ON!

OK....question: How do I install Inkscape 0.45 on Ubuntu? Does anyone have Inkscape installed? Can you tell me how you got it intstalled? I have Ubuntu 8.04.1 (Hardy LTS), kernel 2.6.24.22-45, GNOME 2.22.3

sigh..
:confused:

Paulzy

---

### Post by Paulzy on 2008-12-12
Ok I installed libpng alright. Now it gives me this:

> configure: error: libgc (the Boehm Conservative Collector) 6.4+, is needed to compile inkscape -- [http://www.hpl.hp.com/personal/Hans_Boehm/gc](http://www.hpl.hp.com/personal/Hans_Boehm/gc)


sigh...i'm getting annoyed. i love linux, but this is the 21st century. **All** these tools should be included. :confused:

---

### Post by Paulzy on 2008-12-12
sigh...
Installed inkscape 0.46, ran sh configure; it wanted libpng
Installed libpng 1.2.33
Ran sh configure for inkscape, now it wants gc greater then 6.4
Installed gc 6.8
Ran sh configure for inkscape, now it wants freetype-configure.

Why is there NO listing of dependicies with this program? Why can;t be distributed fully compiled? eerrrrgggggg

---

### Post by Paulzy on 2008-12-12
Okay got FreeType from here: [http://www.linuxfromscratch.org/blfs/view/stable/general/freetype2.html](http://www.linuxfromscratch.org/blfs/view/stable/general/freetype2.html)

But the sloppy writing doesn't tell you how to install it. AND when i unpack it and read the INSTAL.UNIX file it says to run configure. But there is NO configure script...***go figure!***

I'm going to bed!

---

