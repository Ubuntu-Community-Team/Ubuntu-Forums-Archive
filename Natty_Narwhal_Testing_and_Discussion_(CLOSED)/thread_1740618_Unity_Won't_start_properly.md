---
title: "Unity Won't start properly"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2011-04-27
I have installed 11.04 on my desktop and noticed that unity dash, launcher panel, etc wouldn't appear with unless I used the "compiz" command to manually run compiz. I've added it to "Startup Applications" and it works fine.

But I didn't need to do this with my laptop and so I'm wondering if anyone know why and if there a fix for this or is it not worth fixing.

My desktop is running an Nvidia GeForce 8600 but the driver in "Additional Drivers" is saying that it is active but not in use (see screen shot). Yet if the other driver is activated I cant get the system to boot to a GUI properly at all.

---

### Post by grahammechanical on 2011-04-27
Driver not in use does not mean that the driver is not been used. It means that you are not using 3D graphics. I am using Unity 2D on 11.04 Beta and my driver is listed as activated but not in use. On my 10.10 installation the same driver is listed as activated currently in use. I am using enhanced effects in 10.10.

Did you install the Compiz Config Settings Manager? (CCSM) Did you select the Unity 2D option to be run after log in? System Settings> Login Screen>Unlock>Select from drop down list.

Regards.

---

### Post by wgarcia on 2011-04-27
I have the same setting as Jonny87, with a nVidia Quadro FX 1700 card. In Additional Drivers it tells me "installed but not in use" for the current driver. 

But I'm running Unity, so Compiz and 3D effects, right? In any case there is no option to choose "special effects" as it was in Preferences -> Appearance in previous versions. 

My xorg.conf also shows that I'm using "nvidia", so propietary driver, and not "nouveau". 

Is this a bug? Is the "current driver" actually being used but not showing properly in "Additional Drivers"?

---

