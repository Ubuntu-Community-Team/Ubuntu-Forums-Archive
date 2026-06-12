---
title: "Ahhh! Video Card problems, Hardy, Geforce4Ti4600"
date: 2008-08-06
forum: Multimedia Software
---

### Post by justinreeves16 on 2008-08-06
Ok I am at my ends here, I had Feisty installed and had video drivers installed via Envy, all was ok.

Have since updated to Hardy video didnt work correctly, some how got it to work ok, loaded a lot of different drivers different ways through web help pages. Noticed no Open Gl based apps were working.

Checked Administration/Hardware Drivers said Nvidia wasnt being used.
once checked video was worse, boots up with cannot detect video, and I have to select screen and video card, but its not correct card/drivers, still only 800*600.

I uninstalled Envy(didnt work on Hardy) Installd EnvyNG
Installed Nvidia drivers, Automatic.
  
Once finished, rebooted, same problem no detection of video devices.

What the, Im new to Linux, and almost ready to boot it. This is always the only problem I have with Ubuntu is video drivers. Ahhhh!!

The card is a Leadtek Winfast A250, Or Nvidia Geforce4 Ti4600

---

### Post by wolfen69 on 2008-08-06
can you get to a command line? if you can, uninstall envyNG with
```
sudo apt-get remove --purge envyng-gtk
``` then run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then maybe you can get back to a working state and then can backup your xorg.conf file. if you have it backed up, you can always get back to a good working state easily. and then try something else. be patient.

---

### Post by justinreeves16 on 2008-08-07
Strange thing is I just turned my computer on (the next day) and now I have video res back to 1280*1024, but when I look at System/Administrator/Nvidia Xserver settings, It says the Nvidia driver isn't being used.

I tried to run houdini 3D animation software says system settings must have resolution of at least 0 by 0.
  Tried to run Billard-Gl games, error:  OpenGL GLX extension not supported by display ':0.0'

Tried to run Foobillard game, error: main:rgstereo=0Video mode set failed: Couldn't find matching GLX visual

---

### Post by justinreeves16 on 2008-08-07
Ok I tried to uninstalling Envy and all as mentioned above.
I then tried to DL the NVIDIA drivers from NVIDIA 96.43.07
EnvyNG was installing 96.43.05

Entered boot manager stopped gdm.
installed NVIDIA's drivers from prompt(ok), ran GDM, still same issue.

Anyway still didn't work, still boots up cannot detect video devices, manually configure, still only 800*600.

I also tried under Hardware Drivers checking Nvidia accelerated graphics, still same prob., Changed under Appearance Preferences, Visual Effects, Extra, checked, it installed drivers also but still same problem.  
Also the first time I messed with drivers I lost the 1280*1024 I spontaneously had when I turned the nightmare on today.

This is horrible I have been trying to just get something as simple as a device driver to work in a OS for 7+ hours with absolutely no success or even change in system. 
What blows me away is that something this simple in WIN(swear word)you could get almost anyone to get it to work, but it seems no one has given me anything forums, or web sites that has helped one bit, this is insane.

---

