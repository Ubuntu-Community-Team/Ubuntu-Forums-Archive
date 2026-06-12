---
title: "NVIDIA and OpenGL Problems"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by tman elite on 2007-09-06
This is actually a set of questions:

First, I have the "NVIDIA Accelerated Graphics Driver" in the Restricted Device Manager.  Under Status it says "In Use" but under Enabled the check box is empty.  Is this an error, or can a driver be In Use without being enabled?

Secondly, does the driver not support OpenGL?  It seems like OpenGL does not work with the driver.  For example, SuperTux (which has optional OpenGL) works fine when OpenGL isn't selected, but as soon as I select to use OpenGL, the window closes.  The terminal output is this:

> Error: I could not set up video for 640x480 mode.
The Simple DirectMedia error that occured was:
Couldn't find matching GLX visual
Does anyone know what's wrong?

---

### Post by cubeist on 2007-09-07
I am not sure about the first question, what happens when you click 
enable?  Mine says it is in use and the enabled box is checked.  Perhaps it is not recognizing the driver when you boot.  You could reinstall it.

As to the opengl issues, I know my monitor does not like 640 x 480 but will run games ok at 800 x 600.  Anyway, to check the opengl status and specs of your card open a terminal and type "nvidia-settings"  this will open a gui app that displays all the information and settings for your graphic card... I would advise caution on what settings you change in there because you could really mess up your display!!

---

### Post by tman elite on 2007-09-07
The GUI opened, but I'm not sure what any of it does.  Also, while the GUI is running the following was displayed in the terminal:
> ~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

When I try to run SuperTuxKart, which uses OpenGL, the terminal displays:
> Data files will be fetched from: '/usr/share/games/supertuxkart/'
PW: GLX extension not available on display ':0.0'?!?

I think there's something wrong with either my driver or nvidia settings that I don't know how to fix.



When I check the "enable" box in Restricted Drivers, it says I need a system restart, but when I restart the system, X no longer works.  I have to use
"sudo dpkg-reconfigure -phigh xserver-xorg'
to get X working again and then reboot the computer.  Then everything is the exact same as when it started.  The driver still says "In Use" but is not "enabled."

However, I think it's working because my FPS for a lot of games is much higher than when I didn't have the Nvidia Driver installed.

---

### Post by hessiess on 2007-09-07
can you post the system specifications please.

---

### Post by tman elite on 2007-09-07
I reinstalled NVidia, now everything works, but it still seems like OpenGL isn't compatible.  When I select the OpenGL option for SuperTux, it runs, but the window is mostly black, and the part that isn't is mostly a big blue rectangle.  It doesn't show what it's supposed to.  SuperTuxKart runs now, but everything is black up until the point where you pick your kart (then everything returns to normal)  

Does anyone know why OpenGL doesn't seem to work with the driver?

---

### Post by tman elite on 2007-09-07
The checkbox under "Enabled" is now checked.

---

### Post by statistic on 2007-10-12
sorry to revive a month dead topic, but the problem was never really resolved and I'm having the same issue. Same output from nvidia-settings and supertux won't run. 
specs:
compaq presario v6030ca
1024 ram, 1.8 Ghz processor
nvidia geforce go 6150

I'm using feisty, and am very confused. I've tried everything to get the drivers to run properly, but as the other user said, I'm getting good frame rates and movies run great but when opengl needs to run it eats it's self. Starcraft runs fine through wine even though it did report that it was not going to use openGL.

Any insight into the matter would be great, because I know I will eventually need open GL for something.

Thanks.

---

### Post by LauraSakura on 2007-10-29
> I'm using feisty, and am very confused. I've tried everything to get the drivers to run properly, but as the other user said, I'm getting good frame rates and movies run great but when opengl needs to run it eats it's self. Starcraft runs fine through wine even though it did report that it was not going to use openGL.

I'm having the exact same problem on gutsy. nvidia and everything says its fine... but any opengl game i start.. I get only a black screen.

---

