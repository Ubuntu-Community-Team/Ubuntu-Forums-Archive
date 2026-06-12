---
title: "AZiO AWU212N Wireless USB Adapter problem"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by taylorbarclay on 2010-07-09
***UPDATE:  This has been solved.  I followed the instructions that jamesbond07 posted [HERE (CLICK ME)]("http://ubuntuforums.org/showthread.php?t=1468429&highlight=Realtek+RTL8191SU&page=2") and used his attached file and all is working with my USB Adapter now.  ***

System & Wireless Information as per posting a Wireless issue ticket:

**1 ) Machine Brand and Model (PC/Laptop)**:

Dell XPS 200

The rest of the support ticket appears to be worthless as it lists nothing about wireless, because I'm attempting to use a USB adapter.  If something is needed more from the ticket let me know and I'll port it over.

- - -

Alright, this post is for installing the Realtek RTL8191SU chipset for using my AZiO AWU212N Wireless USB Adapter.

I was lead to these sources after the poster in this thread suggested I look for the chipset:  [http://ubuntuforums.org/showthread.php?p=9570821](http://ubuntuforums.org/showthread.php?p=9570821)

and

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9557203](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9557203)

It doesn't appear that those posters were able to solve their issues either..

Those two threads led me to the download from Realtek, but I cannot for the life of me follow the included read me for compiling the driver.  I believe I understand how to uncompress the tar.gz file, but once it gets to the "make" the Terminal says no makefile found.  

I need a walkthrough of this, and possibly and English translation of the installation instruction.

I'm attaching the read me for the most recent driver install, and the power point file that comes with it to install is here on Google Docs:  [http://docs.google.com/present/edit?id=0AQa7s1hRoWfoZGhrbmQ4YjdfM2ZiZ2JzamZ4&hl=en](http://docs.google.com/present/edit?id=0AQa7s1hRoWfoZGhrbmQ4YjdfM2ZiZ2JzamZ4&hl=en).  I even added the tar.gz file for the driver.

Someone?

EDIT:  After digging through the build log for the 2.6.34 Ubuntu kernel I found this: 
RealTek RTL8192SU Wireless LAN NIC driver (RTL8192SU) [M/n/y/?] m

Does that help me at all?  I obviously don't have the 8192SU, I have the 8191SU.

---

### Post by VeeDubb on 2010-07-10
Do you know which chipset that adapter uses?  As you can see already, it's actually a Realtech.  There's only a few manufacturers of WiFi chipsets, so most brands are just re-brands, sometimes with different plastic casings, sometimes just a different retail package.

---

### Post by taylorbarclay on 2010-07-10
According to the manual the chipset is:  Realtek RTL8191SU

I'm now looking for help based on that chipset to see what can be done, but I'm still stuck with nothing.

Just by the way, I reinstalled 10.04 completely fresh last night so I'm now with a blank slate of an OS.

---

### Post by taylorbarclay on 2010-07-10
Solved.

---

