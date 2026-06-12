---
title: "DFP native resolution incorrectly detected"
date: 2009-08-02
forum: Multimedia Software
---

### Post by spenceee on 2009-08-02
G'day everyone.
 
I've just grabbed Ubuntu 9.04 (desktop) off the mirror and installed it. I upgraded it to the latest kernel available from the default sources and I have an issue with my X resolution.
 
I've got an Nvidia 8600GT and a ViewSonic DFP 22", it's native resolution is 1680x1050@60Hz.
 
I've installed the Nvidia 180 GLX drivers from the software sources and these locked the resolution down to 640x480, as the detected native resolution of the screen (incorrect). 
 
I attempted each of the previous Nvidia drivers (173, 93, 76) that were available and these all had the same issue. I also attempted the nvidia based installation from the nvidia website with the same issue.
 
If I don't use the nvidia driver, the native VESA driver uses 800x600 which is at least usable as a gnome resolution.
 
I have tried placing a line in the xorg.conf to override nvidia-native to 1650 x 1080 however this still ended up using 640 x 480.
 
Is this a known bug, is there something I can revert to? Or can you guys help me with an xorg.conf to force the screen resolution up to the correct native res of the panel?
 
Cheers for your help.

---

### Post by spenceee on 2009-08-02
Can I add that the nvidia hardware accelleration in X was noticable, along with the effects when menus opened etc.  So I would like to keep the nvidia accelleration but forcibly override the detected resolution.

---

### Post by spenceee on 2009-08-03
bump :confused:

---

### Post by xc3RnbFO8P on 2009-08-03
Did you check System> Preferences> Display, choose NO and change the resolution

---

### Post by tajreed on 2009-08-03
I have the same problem and tried the above solution with no luck. It shows the res. as in the Nvidia dialog.

---

### Post by spenceee on 2009-08-04
I've seen a few people with the problem, but it's not common, so it probably wont be fixed :'(.
 
Can anyone help me override Nvidia and force in a resolution?  Or fix the issue with the EDID data being incorrectly read?

---

### Post by Musashi 360 on 2009-08-20
Hi I seem to have had the same problem as you did, To begin with I'm just a linux noob, I knew nothing about terminal commands... spoiled by osx's ease-of use. So I decided to try out linux on an old hp pavillion pc, everything in the installation went quite well, not a hickup. I was amazed! Then I saw a pop-up showing me drivers for my nvidia gfx card (geForce 5200 256 mb) so i went ahead to install them and reboot the system after the install, I only had two options in the nvida-settings tool for resolution :640x480 and 320x240... But my monitos is able to handle 1360x768 px. I searched the net and tried a great number of solutions (most of them said I had to manually add the resolution to my xorg.config) but none worked.

Out of curiosity (I was about to uninstall ubuntu he he), I changed the vertical refresh and horizontal sync values for my monitor (the ones that were detected automatically) and this seemed to do the trick, now I have a complete list of available resolutions in the nvidia settings tool and in the ubuntu-incuded tool aswell. Ill explain how I did this in the hopes it helps other users like me :).

First you need to start the nvidia-settings tool as super user from the terminal:
```
gksudo nvidia-settings
```Go to "X server display configuration", then click on the "Save to X Configuration File" button. Then you mus de-select the "merge with existing file" checkbox and finally click "save"

Now open a terminal and type:
```
sudo nano /etc/X11/xorg.conf
```That should open the xorg configuration file in the same terminal window you are in. Now scroll down to the "monitor" section, this section looked like this in mine:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection
```Change the horizsync and vertrefresh values to:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection
```NOTE: This are the vaues my display can handle, it is better if you get the exact values for your display, I asume no responsability if you fry your monitor doing this.

Finally, hold the "Control" button +  the "X" button and save the changes. Reboot your computer, and open your nvidia-settings tool again and happily select the resolution your monitos supports from the list. 

Hope this helps. Cheers!:popcorn:

---

