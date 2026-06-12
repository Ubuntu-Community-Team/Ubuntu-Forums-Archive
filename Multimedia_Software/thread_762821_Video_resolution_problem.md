---
title: "Video resolution problem"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Jaywalker2309 on 2008-04-22
I've been running the beta with no problems at all on my nVidia 5700. Was running at a proper resolution.

As am using this just to learn Linux etc, i did a clean install from the new RC client. And i've simply not been able to get the resolution above 640x480 since. I've enabled the hardware driver etc, and i've got X server to try and change the settings, but i cannot find the place where i tell ubuntu what the monitor actually IS.

It used to be there in the Applications drop down, but its gone :( I was SO hoping to get it all working without having to ask but looks like i've failed :(

Can anyone help point me in the right direction where i can configure the monitor settings, preferably without having to use text editor and xorg.inf ;)

---

### Post by overdrank on 2008-04-22
> **Jaywalker2309 said:**
> I've been running the beta with no problems at all on my nVidia 5700. Was running at a proper resolution.

As am using this just to learn Linux etc, i did a clean install from the new RC client. And i've simply not been able to get the resolution above 640x480 since. I've enabled the hardware driver etc, and i've got X server to try and change the settings, but i cannot find the place where i tell ubuntu what the monitor actually IS.

It used to be there in the Applications drop down, but its gone :( I was SO hoping to get it all working without having to ask but looks like i've failed :(

Can anyone help point me in the right direction where i can configure the monitor settings, preferably without having to use text editor and xorg.inf ;)

HI and I believe you are speaking of screens and graphics, it is now under applications, other and you may have to edit you menus to add it. Also you may try and add the nvidia settings from synaptic manager. Then use the command ```
gksudo nvidia-settings 
``` to adjust your resolution.

---

### Post by webaake on 2008-04-22
Same problem here with HH rc version and latest Nvidia drivers via envyng - only 640x480. Even in nvidia-settings there is only 640x480 and 320x240 to choose from.

If it helped I could easily edit the xorg-conf file but it doesn't seem to help.

My card is 7600GS which used to work just fine in 1280x768 and above on Feisty.

Furthermore, when trying to edit settings within nvidia-settings, the window jumps around, making buttons almost unuseable!! Demaximaizing it works kind of...

---

### Post by overdrank on 2008-04-22
> **webaake said:**
> Same problem here with HH rc version and latest Nvidia drivers via envyng - only 640x480. Even in nvidia-settings there is only 640x480 and 320x240 to choose from.

If it helped I could easily edit the xorg-conf file but it doesn't seem to help.

My card is 7600GS which used to work just fine in 1280x768 and above on Feisty.

Furthermore, when trying to edit settings within nvidia-settings, the window jumps around, making buttons almost unuseable!! Demaximaizing it works kind of...

Oh that brings back memories. :)  I had that happen on my sons system and had to revert to a older driver with his 7300. Have you tried to reconfigure you xorg  ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` It has helped in the past.

---

### Post by webaake on 2008-04-23
Yes, tried it twice.

But some progress was made using the new graphics and screen preference 'applet' in HH. It actually wrote somethings into xorg.conf and I could boot, but no real improvements in resolution.

For the moment I'm trying out different  'modelines' in xorg.conf.

---

### Post by Jaywalker2309 on 2008-04-23
> **overdrank said:**
> HI and I believe you are speaking of screens and graphics, it is now under applications, other and you may have to edit you menus to add it. Also you may try and add the nvidia settings from synaptic manager. Then use the command ```
gksudo nvidia-settings 
``` to adjust your resolution.

Thats the one.. now i've added the program to my menus, i've set the screen to be something other then plug and pray and i have RESOLUTION :)

Huge thanks..

---

