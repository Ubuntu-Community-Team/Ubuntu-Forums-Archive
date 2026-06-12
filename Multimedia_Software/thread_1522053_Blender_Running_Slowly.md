---
title: "Blender Running Slowly"
date: 2010-07-01
forum: Multimedia Software
---

### Post by skaarr on 2010-07-01
I hope this is the right forum for this.
I downloaded Blender today to try my hand at making some 3D graphics. I have used it in the past on a windows machine and it ran smoothly. This time I have downloaded it onto a computer with similar specs but it runs very slowly. The program is laggy and slow to respond to both keyboard and mouse input. When I checked the system monitor it said that I am using 50% of my cpu and 1/6th of my memory running both Blender and Firefox(to write this post). The machine is running no hotter than usual and the fans do not seem to be being stressed at all.

Does anyone know what could be causing the program to run so slowly?
Thanks in advance.

---

### Post by power ohn on 2010-08-10
> **skaarr said:**
> I hope this is the right forum for this.
I downloaded Blender today to try my hand at making some 3D graphics. I have used it in the past on a windows machine and it ran smoothly. This time I have downloaded it onto a computer with similar specs but it runs very slowly. The program is laggy and slow to respond to both keyboard and mouse input. When I checked the system monitor it said that I am using 50% of my cpu and 1/6th of my memory running both Blender and Firefox(to write this post). The machine is running no hotter than usual and the fans do not seem to be being stressed at all.

Does anyone know what could be causing the program to run so slowly?
Thanks in advance.

I've got the same issue, it is especially apparent when opening a menu (any of them)

---

### Post by power ohn on 2010-08-13
> **power ohn said:**
> I've got the same issue, it is especially apparent when opening a menu (any of them)

It was a driver problem. Im running an ATI radeon HD 4350 512MB card. the only solution (for an ATI system) is to to the ATI site download the appropriate drive (google "ati drivers") and run the following shell command: 
      ~$ sudo sh ./whatever_driver_name_it_is.run
That worked for me, actually a bit faster on linux now that i've got the correct driver.

---

