---
title: "Photo printing with Gimp 2.6 on Intrepid Ibex and failing"
date: 2009-03-14
forum: Multimedia Software
---

### Post by robfindlay on 2009-03-14
I am trying to figure out how to "setup" GIMP's printing options to do photo prints. 

As it is right now when I go to print inside gimp I have *exactly* the same printing options as in every other program. 

It just seems to default no matter what to a letter-size print even if I go under what properties I do have and indicate it's a 4x6 photo sheet.  The online resources I have and the Beginning GIMP book i bought show a much wider set of available print options--I just don't seem to have them! 

Here is my setup: 
Intrepid Ibex
Gimp 2.6.3.1 
Gutenprint version 5.2.0~rc1 from package cups-driver-gutenprint.  
On an HP C-4280

HELP!

-Rob

P.S. My printer seemed to auto-detect just fine and prints 8x11 just fine, so.......HELP!  :-)

---

### Post by robfindlay on 2009-03-15
> **robfindlay said:**
> I am trying to figure out how to "setup" GIMP's printing options to do photo prints. 

As it is right now when I go to print inside gimp I have *exactly* the same printing options as in every other program. 

It just seems to default no matter what to a letter-size print even if I go under what properties I do have and indicate it's a 4x6 photo sheet.  The online resources I have and the Beginning GIMP book i bought show a much wider set of available print options--I just don't seem to have them! 

Here is my setup: 
Intrepid Ibex
Gimp 2.6.3.1 
Gutenprint version 5.2.0~rc1 from package cups-driver-gutenprint.  
On an HP C-4280

HELP!

-Rob

P.S. My printer seemed to auto-detect just fine and prints 8x11 just fine, so.......HELP!  :-)

Bump!....anybody?

---

### Post by robfindlay on 2009-03-15
> **robfindlay said:**
> I am trying to figure out how to "setup" GIMP's printing options to do photo prints. 

As it is right now when I go to print inside gimp I have *exactly* the same printing options as in every other program. 

It just seems to default no matter what to a letter-size print even if I go under what properties I do have and indicate it's a 4x6 photo sheet.  The online resources I have and the Beginning GIMP book i bought show a much wider set of available print options--I just don't seem to have them! 

Here is my setup: 
Intrepid Ibex
Gimp 2.6.3.1 
Gutenprint version 5.2.0~rc1 from package cups-driver-gutenprint.  
On an HP C-4280

HELP!

-Rob

P.S. My printer seemed to auto-detect just fine and prints 8x11 just fine, so.......HELP!  :-)

There's gotta be someone who can throw me a bone on this one??

---

### Post by RedRat on 2009-03-15
Well I have a similar problem with printing emails in Thunderbird. Whenever they print, they always print in the horizontal or landscape mode even though I set it to portrait. All my other applications I can choose portrait or landscape without problems.

Sounds like both of us are having a problem with communicating with either the printer or CUPS/Gutenprint. If anyone out there has some ideas, I too would love to hear them.

---

### Post by robfindlay on 2009-03-16
> **robfindlay said:**
> I am trying to figure out how to "setup" GIMP's printing options to do photo prints. 

As it is right now when I go to print inside gimp I have *exactly* the same printing options as in every other program. 

It just seems to default no matter what to a letter-size print even if I go under what properties I do have and indicate it's a 4x6 photo sheet.  The online resources I have and the Beginning GIMP book i bought show a much wider set of available print options--I just don't seem to have them! 

Here is my setup: 
Intrepid Ibex
Gimp 2.6.3.1 
Gutenprint version 5.2.0~rc1 from package cups-driver-gutenprint.  
On an HP C-4280

HELP!

-Rob

P.S. My printer seemed to auto-detect just fine and prints 8x11 just fine, so.......HELP!  :-)

Installed the gutenprint module for gimp and loaded the c4200 ppd file.

Fixed.

---

