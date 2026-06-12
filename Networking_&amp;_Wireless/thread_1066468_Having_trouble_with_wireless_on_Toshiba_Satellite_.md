---
title: "Having trouble with wireless on Toshiba Satellite A60 with Atheros AR5001X+"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by nick_a94 on 2009-02-10
I'm sort of new to linux and a couple days ago i found this computer lying around my house that nobody uses anymore, so i decided to try out Ubuntu on it. I am currently running Intrepid Ibex and the one thing I noticed after installing it is that the wireless wasn't working. So I did a little research and found out about a program called ndiswrapper and how it may solve my problem. When I tried using it though it said that i had to get some .inf file from the wireless driver to set it up. The problem is that i dont know how to get this file at all. If someone could walk me through it that would be great.

System Specs: 
Toshiba Satellite A60 
Intel Celeron 2.80 GHz
Atheros AR5001X+ Wireless Network Adapter

---

### Post by lisati on 2009-02-10
The [Toshiba web site]("http://toshiba.com") probably has a suitable driver file available on its website - it has downloads available for both my laptops (both Toshiba). The only catch I'm aware of is that you might have to extract the files using Windows.

---

### Post by nick_a94 on 2009-02-10
I have another computer that is currently running vista. Could i just download it there and transfer it over. O and what am i exactly looking for, is it just the AR5001X+ driver or something more specific.

---

### Post by lisati on 2009-02-10
It has been a while since I've downloaded drivers from Toshiba (I've normally used the recovery DVD that came with my first laptop, and the recovery partition that came with the second). 

If the driver you want comes as a ZIP file, then Ubuntu should be able to handle unpacking it without the need for going to Vista (or XP or whatever). 

I'm not sure of the best procedure to recommend for an ".EXE" file (which some of the Toshiba downloads are) - these are designed for Windows and don't normally run on *nix without help. If you're lucky they'll be a self-extracting archive that *ubuntu's "unzip" command will be able to cope with.

Anyone else with any thoughts?

---

