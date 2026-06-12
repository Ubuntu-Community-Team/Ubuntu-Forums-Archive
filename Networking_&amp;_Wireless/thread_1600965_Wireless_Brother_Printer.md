---
title: "Wireless Brother Printer"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by linuxonbute on 2010-10-19
I have a Brother DCP585CW and have installed the drivers from Brother and it worked fine 

on Ubuntu 9.10 on both my desktop and laptop.

I have installed 10.04 on both and now the problem.

It works fine on the desktop but i get a problem on the laptop.

it is a wireless printer and I can print to it but only after I do 2 things each time I reboot 

the laptop. I have to configure it through cups ( [http://localhost:631](http://localhost:631) ) because it keeps 

getting set to being connected via USB and letter rather than A4 paper on each boot but 

the correct setting is:

```

Description:DCP585CW Location:Landing Driver:Brother DCP-585CW CUPS v1.1 (color)
Connection:lpd://192.168.1.66/binary_p1 Defaults:job-sheets=none, none media=adobe_A4_8.125x11.5139in 

```i also have to correct it via System/Administration/Printing and setting A4 and setting it to 

the default.

Has anyone any idea what is wrong?

thanks

---

### Post by linuxonbute on 2010-10-25
> **linuxonbute said:**
> I have a Brother DCP585CW and have installed the drivers from Brother and it worked fine 

on Ubuntu 9.10 on both my desktop and laptop.

I have installed 10.04 on both and now the problem.

It works fine on the desktop but i get a problem on the laptop.

it is a wireless printer and I can print to it but only after I do 2 things each time I reboot 

the laptop. I have to configure it through cups ( [http://localhost:631](http://localhost:631) ) because it keeps 

getting set to being connected via USB and letter rather than A4 paper on each boot but 

the correct setting is:

```

Description:DCP585CW Location:Landing Driver:Brother DCP-585CW CUPS v1.1 (color)
Connection:lpd://192.168.1.66/binary_p1 Defaults:job-sheets=none, none media=adobe_A4_8.125x11.5139in 

```i also have to correct it via System/Administration/Printing and setting A4 and setting it to 

the default.

Has anyone any idea what is wrong?

thanks
Well I have not been able to solve the problem as such. I have a work around which is to
add an extra printer vial cups and system/administration/printing. 
The one I actually have - my networked Brother printer - then setting this one to enabled/shared/default and it now works fine. Still cannot see why it worked without all this messing around from my desktop PC.

---

