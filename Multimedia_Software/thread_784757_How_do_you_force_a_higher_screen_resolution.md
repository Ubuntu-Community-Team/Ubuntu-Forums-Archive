---
title: "How do you force a higher screen resolution"
date: 2008-05-06
forum: Multimedia Software
---

### Post by MattyMcSwain on 2008-05-06
I am new to Linux and just installed Ubuntu.  I got the nvidia driver working on Envy, however on the screen resolution preference, it won't allow me to set the resolution above 1024x768.  How do I force it to a higher resolution that this computer can easily handle in Windows?

---

### Post by Cornova on 2008-05-06
Open the terminal and type 'sudo displayconfig-gtk' and see if you can select the type of monitor you have, then put in the resolution you want.

---

### Post by roddersg on 2008-05-06
I have the same problem with a Nvidia GEForce6100.  I can increase the resolution above 800x600.

Tried the following:
envy-gtk to load the new drivers
nvidia-xconfig / nvidia-settings
displayconfig-gtk

I am able to get to the screen which shows the selection of the card/display, make changes and save the configuration in a file. But when I restart X/Gnome it reverts back to the 800x600

Any advice?

---

### Post by roddersg on 2008-05-06
I have the same problem with a Nvidia GEForce6100.  I can increase the resolution above 800x600.

Tried the following:
envy-gtk to load the new drivers
nvidia-xconfig / nvidia-settings
gksudo displayconfig-gtk

I am able to get to the screen which shows the selection of the card/display, make changes and save the configuration in a file. But when I restart X/Gnome it reverts back to the 800x600

**Update**
gksudo displayconfig-gtk
then do a **logout**.  Do not simply shut down X (Ctrl-Alt-Backspace).  The settings are now loaded and when you login again, the resolutions are changed to a higher set.
I believe it is in the detection of the display screen that is causing this problem as once the display is set then the graphics mode work out ok.

The problem I now have is I cannot enable the Appearance>Visual Effects.  I used to be able to do that when I first installed the Desktop version.  Now, in order to take advantage of my RAM, I have the server version with ubuntu-desktop installed as a feature.

Also the startup login screen (gdm) does show properly as the display seems bigger than my screen.

---

