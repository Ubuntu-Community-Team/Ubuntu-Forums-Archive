---
title: "Nvidia/Compiz problem"
date: 2009-06-21
forum: Multimedia Software
---

### Post by platosearwax on 2009-06-21
Just recently installed Ubuntu 9.04 (though I have been running OpenSUSE 11.0 for the last year so I am not exactly new to linux).  Things seem to work great, though there was some problem with the install, ie I had to use the alternate install CD and also manually install the Nvidia drivers before I could even get a GUI (not even basic graphics at boot would work).  

Anyway, I have a GeForce 6200 with 256MB and am running version 185.18.14 of the Nvidia driver.  Here are my problems:

When effects are enabled, I lose color on the title bar of all windows.  And when I open terminal it comes up completely trasparent (ie I see what is behind it) and unusable.  System Information is also unusable as it flickers and is halfway trasparent.  

When effects are disabled, all those things are fine but I have no video capabilities whatsoever.  Attempt to run any kind of video and my system hard locks and I have to shut it off manually.  

Anyone have any ideas?  I can provide any other information you need.  I have probably messed some stuff up since I have been messing around with settings trying to get things to work.  

Thanks in advance.

---

### Post by Arup on 2009-06-21
Install compiz fusion icon and enable loose binding and indirect rendering, see if this issue goes away.

---

### Post by platosearwax on 2009-06-21
> **Arup said:**
> Install compiz fusion icon and enable loose binding and indirect rendering, see if this issue goes away.

Done and no, nothing changed.  I did get color on the title bar of the window I had open but it went away if I closed it and opened again.

EDIT: Actually, I get some title bar color, but it seems to be random.  Some windows do and others don't.  This really isn't a big deal but, you know, it is in an obsessive why doesn't this work kind of way!

---

### Post by platosearwax on 2009-06-24
Not that anyone is following this but me, but no actual solution yet, but enough workarounds to make it livable.  

If I use Emerald as the window decorator it seems to solve the title bar color problem.  I still have some totally unusable (ie the windows open seemingly empty but are transparent so you can't see anything.  If I move them it looks like I am moving a chunk of the desktop) programs but I installed a new terminal which was the most important.  

I'm not even sure if this is a known bug or something specific to my system (I had a difficult time ever getting a GUI when I installed Ubuntu and had to install the proprietary Nvidia drivers from the start).  Just thought I would put this out there in case anyone is searching or something.

---

### Post by platosearwax on 2010-04-19
Again replying mostly to myself, and long after the original posts on this.  But I felt like I should update this for search purposes.  

With the latest Nvidia driver, 195.36.15, almost all of my graphics problems are solved.  System monitor is still a bit flickery, but I have a regular terminal and all the other menu artifacts and window decoration problems are gone.  As are minor things like the drop down search history in Firefox which would never work with effects enabled and right click context menus which were spotty at best.

Plus I now have screenlets!  Seriously, this really rocks now.

---

