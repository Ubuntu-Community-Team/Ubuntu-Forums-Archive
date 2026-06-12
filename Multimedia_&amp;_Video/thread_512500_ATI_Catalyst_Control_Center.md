---
title: "ATI Catalyst Control Center"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by redhat24 on 2007-07-29
I have Feisty (Kubuntu), ATI x700, latest driver.

I was following the following guide - Method 1, Ubuntu Way:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

Everything worked fine i guess, because fglrxinfo shows the correct values (vendor: ATI, not MESA).

But i would like to have an ATI Catalyst Control Center (CCC). How can I have it? I need it because i would like to connect my PC to TV.

Thanks!

ps.: I've read in an other thread, that CCC is in Accessories by default, but i didn't find it ;)

- Bálint Kriván -

---

### Post by Daveth on 2007-07-29
from recollection of a few years back when I supported ATI products, their control centre is a windows .exe application, is it not?  You could try running it under wine.

---

### Post by redhat24 on 2007-07-29
i'm sure that there should be a Linux implementation of CCC ;)

---

### Post by Daveth on 2007-07-29
um, you may be right

[http://www.phoronix.com/forums/showthread.php?t=926](http://www.phoronix.com/forums/showthread.php?t=926)

and

[http://digg.com/linux_unix/AMD_Catalyst_Control_Center_For_Linux_Released](http://digg.com/linux_unix/AMD_Catalyst_Control_Center_For_Linux_Released)

---

### Post by redhat24 on 2007-08-01
I'm still looking for the solution

---

### Post by holodad on 2007-08-25
Install Ati Catalyst CC from ati driver binary, i run it with this command
DISPLAY=:0 amdcccle
If you use XGL session, this will work but however, i'am trying to get this work without running DISPLAY=:0.....

---

### Post by ericstoesser on 2008-03-10
> **holodad said:**
> Install Ati Catalyst CC from ati driver binary, i run it with this command
DISPLAY=:0 amdcccle
If you use XGL session, this will work but however, i'am trying to get this work without running DISPLAY=:0.....

WOW i got it finally, i couldn't access it through the menu, but i could from the command line

---

