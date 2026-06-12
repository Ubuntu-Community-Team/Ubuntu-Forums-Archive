---
title: "Screen Resolution"
date: 2008-05-26
forum: Multimedia Software
---

### Post by andrecamp on 2008-05-26
Hi,

I am new to Ubuntu, however, I pretty much have only one problem. 
The highest I can get the screen resolution to go by using the screen resolution selection from System/Preferences is 800X600. What can I do to get it to go higher? Like when I ran windows it was 1280×1024 or something like that.

Please help and if possible make it easy cause I am noob to Ubuntu and all this coding stuff.

Thanks. :)

---

### Post by Drakkor on 2008-05-26
Have you gone to System>Administration>Hardware Drivers to see if you can get either ATI or Nvidia  restricted drivers ?

---

### Post by chiefci on 2008-05-26
Hello.
try this, install sudo apt-get install displayconfig-gtk.
You can now selcet your monitor and resolution.
When this not take effect you must change xorg,conf

Chief

---

### Post by Chainz on 2008-05-26
Same with me! :(

No restricted drivers for my system, displayconfig-gtk is already in the newest version...
There were no problems with previous versions of Ubuntu. Who da hell took this useful option for setting resolutions and drivers and so on? :confused:

If Ubuntu is going that way... I'll look for some better distros.

---

### Post by crazdawgs90 on 2008-05-26
My screen works fine at 1400x1050 (laptop screen). I am using a laptop in a docking station hooked up to a Samsung monitor (1280x1024). The monitor setting is 1280x1024, but Ubuntu seems to use the laptop screen settings of 1400x1050 and the extra pixels are not visible on the screen. 

Yesterday, the problem was I couldn't see the right side of the screen. I tried to adjust the horizontal size through my monitor menus, it didn't work. Today, I installed updates and now I can see the right side of the screen, but the left is cut off and the resolution is on the correct setting so far as I can tell. I am currently using Ubuntu 8.04. Any advice let me know. 

For you, though, if the drivers are working I would suggest going to System-> Preferences->Screen Resolution and select Detect Displays. If you are like me and using a laptop with a monitor, then try dragging the laptop screen down and your monitor screen should appear below. Select the monitor screen option and it should highlight in orange, then adjust the pixel settings, if desired, and select apply and if it works say save settings. If not then I don't know. Good luck!

---

### Post by andrecamp on 2008-05-27
I went to System-Administration-Hardware Drivers
Then I saw my NVidea Graphics card which was enable and to the right of it, it said not in use. :S

Edit: Nevermind. Ubuntu updated the drivers and now my screen is 1024x768 but thats the max.
My screen with windows was 1152x864 and it was able to go all the way up to 1280x1024 its aiight now.

---

