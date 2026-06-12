---
title: "Refresh rate..."
date: 2008-08-27
forum: Multimedia Software
---

### Post by Jaeric on 2008-08-27
Hello all.  I am having issues with my refresh rate that is keeping me from playing certain games.  The resolution settings do not allow over a 52Hz refresh rate.  My monitor is rated 30-60kHZ and 56-75Hz.  I am running Linux Mint Elyssa and Ubuntu Hardy with the same issue.  Any help would be greatly appreciated.  Thanks!

---

### Post by overdrank on 2008-08-27
> **Jaeric said:**
> Hello all.  I am having issues with my refresh rate that is keeping me from playing certain games.  The resolution settings do not allow over a 52Hz refresh rate.  My monitor is rated 30-60kHZ and 56-75Hz.  I am running Linux Mint Elyssa and Ubuntu Hardy with the same issue.  Any help would be greatly appreciated.  Thanks!

Hi and welcome, What is the model of the graphics card? You can use the command ```
lspci 
```in the terminal and look for VGA.

---

### Post by Jaeric on 2008-08-27
> **overdrank said:**
> Hi and welcome, What is the model of the graphics card? You can use the command ```
lspci 
```in the terminal and look for VGA.

Thanks for the welcome and the quick reply!  I am away from my PC, but at lunch I will get the info.  Any other info that you might need?

---

### Post by tuxxy on 2008-08-27
What video card are you using ?

---

### Post by Jaeric on 2008-08-27
> **overdrank said:**
> Hi and welcome, What is the model of the graphics card? You can use the command ```
lspci 
```in the terminal and look for VGA.

ok, here is the info on my graphics card: 01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

I am using the latest drivers supplied by Envy

Also, my monitor is an HP Pavilion f50

---

### Post by Jaeric on 2008-08-27
*Bump*

---

### Post by Jaeric on 2008-08-27
> **tuxxy said:**
> What video card are you using ?


ok, here is the info on my graphics card: 01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

I am using the latest drivers supplied by Envy

Also, my monitor is an HP Pavilion f50

---

### Post by Jaeric on 2008-08-27
Ok, I solved the problem by browsing the forums a bit more.

It was a simple matter of editing the xorg.conf file.  I added the  line
Option "DynamicTwinView" "false" under the device section and rebooted the graphics.  I now have the proper refresh settings to choose from instead of the default silliness that is the other settings.  Now to see if this fixed my ability to play games...

---

### Post by overdrank on 2008-08-27
> **Jaeric said:**
> Ok, I solved the problem by browsing the forums a bit more.

It was a simple matter of editing the xorg.conf file.  I added the  line
Option "DynamicTwinView" "false" under the device section and rebooted the graphics.  I now have the proper refresh settings to choose from instead of the default silliness that is the other settings.  Now to see if this fixed my ability to play games...

Hi and sorry for being late, needed sleep. :)
Have you tried using the nvidia-settings? If they are not installed you can use synaptic manager and then use the command ```
gksu nvidia-settings
```

---

