---
title: "Google Earth resolution problem"
date: 2010-07-28
forum: Multimedia Software
---

### Post by MorrisseyJ on 2010-07-28
I am having what i think is some trouble with Google Earth in 10.04 (i haven't used it in 9.10, so i don't know if this is a hardware specific problem).

in Google Earth the image that i see is not smooth (as it is in windows) when i zoom in. Instead it looks as though i have the plates of the different satellite images sitting jaggedly next to one another. i also have the yellow lines that ring continents as well as other colourful lines shooting out of my screen at random points and which move as i continue to zoom. 

At the moment GE is functional as the very centre of the image is always clear. I have some problems if i am measuring a path where the yellow line (path line) gets jumbled up with all the other lines shooting out of the screen. This makes things functional but pretty ugly and sometimes very distracting. Also irritating is the fact that the amount i can see on my screen at any one time is reduced by what i have referred to as jagged satellite plates.


To make clear the effect i am describing i have attached a screen shot.

I am not sure if this is simply how GE looks on ubuntu - i have not been able to convert any of my friends to the OS - or if i have a resolution setting issue or something.

Any help would be much appreciated.

---

### Post by Athos2006 on 2011-01-02
And I have the same problem.
Ubuntu 10.04 
Google Earth
5.1.3533.1731

---

### Post by petermck on 2011-01-09
I've got exactly the same problem with GE version 6. I am using a Radeon 2100 on board GPU with the open source drivers on Maverick. I can't use the ATI proprietry drivers since these do not support this chipset on newer kernels.
I'm guessing it is a problem with the drivers, but I'm not sure yet. Is someone able to confirm this?

---

### Post by MorrisseyJ on 2011-01-10
For me:

> lspci | grep VGA returns:

> VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

Is there any other info you need?

---

### Post by MorrisseyJ on 2011-08-09
Not sure what fixed this but issue it is resolved in  Google Earth version 6.0.3.219, running Natty.

---

