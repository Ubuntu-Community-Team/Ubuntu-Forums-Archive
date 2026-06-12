---
title: "NVIDIA geforce MX 440 VGA"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by amila_aina on 2006-08-05
I'm new to ubuntu.I plugged a NVIDIA geforce MX 440 AGP8x card & installed ubuntu dapper.It was completed successfully.Bt Whan it bot gives some Xorg configuration error.Doesnt go to the desktop,too.Any help PLS..............

---

### Post by tseliot on 2006-08-05
What do you mean when you say that you plugged an Nvidia card?

Do you have an integrated card too?

---

### Post by amila_aina on 2006-08-08
Yep.I have Intel Integrated card

---

### Post by amila_aina on 2006-08-08
Ubuntu installed successfully on it.But When it boots up it freezes the point where hardwre configuration happens.

---

### Post by tseliot on 2006-08-08
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by amila_aina on 2006-08-09
thanks for the halp.I tried both method 1 & 2 but still the pc get stucked when loading hardware drivers...Any alternative pls?

---

### Post by tseliot on 2006-08-09
> **amila_aina said:**
> thanks for the halp.I tried both method 1 & 2 but still the pc get stucked when loading hardware drivers...Any alternative pls?

Did you follow the guide which link I posted before?

You might follow that guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

and then try point 7 of the problems Section of this other guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

and please don't mix method 1 with method 2

---

### Post by amila_aina on 2006-08-12
That worked.Bravooo.Thank you very much......

Now when i try to run application using WINE,it says that 
"Cannot open Dispaly.Failed to initialize the window".

same thing happends when running 3ddesktop too.Any sugetions please!

---

### Post by tseliot on 2006-08-12
> **amila_aina said:**
> That worked.Bravooo.Thank you very much......

Now when i try to run application using WINE,it says that 
"Cannot open Dispaly.Failed to initialize the window".

same thing happends when running 3ddesktop too.Any sugetions please!

Post the output of this command:
```
glxinfo | grep direct
```

---

### Post by amila_aina on 2006-08-12
> Post the output of this command:
Code:

glxinfo | grep direct



Here is the output
"Error: unable to open the display(null)"

---

### Post by tseliot on 2006-08-12
> **amila_aina said:**
> Here is the output
"Error: unable to open the display(null)"

The driver might not be installed properly.

Try my envy script and say no when it asks you to automatically set up the xserver for you:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

