---
title: "Ubuntu 8.0.4 with Nvidia Quadro NVS 285 (2 screens)"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Fortisunto on 2008-05-08
Hello

I am new to Linux - and i have found the install of 8.0.4 very easy and no problems with detecting hardware etc. In general i am really seeing the benefits of using Linux, and enjoying it, but....

I am having extreme diffculty trying to get 2 screens working together with my Nvidia Quadro NVS 285.

I have done the following, please let me know if i have done anything wrong.

1.Downloaded the correct nvidia 32 drivers from here.....
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)
2.Stopped the xserver (went to command line)
3. Tried to run the nvidia installer - said that i needed certain lib files etc. So i ran the unbuntu package manager to add all libs available.
4.This time the Nvidia installer did get past the 1st stage - recompiles Kernel, all said complete fine ok although says max res can do is 800x600 on my 19"NEC screens,and asks to reboot.
5.The screens come up but only in "clone" mode in the 800x600 - although i know these screens do 1280x1024 fine in windows.

I log in and in the main GUI now i got to Applications->System tools and i see a "NVIDIA X Server Settings" - i click this and i get the surprising message...

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root and restart the X server"

I do this and it says copied to /etc/X11/xorg.conf, i reboot and it just says "ubuntu is running in low-graphics mode - your screens and graphics card can not be detected. I click continue and it has option choose driver by model - i click nvidia but my model of card is not there? I have kind of given up for now.

Sorry for my ramblings but can anyone give me some advise on maybe what i am doing wrong? Im sure i have the right driver and have followed the correct instructions. 


Any advice gladly accepted and appreciated :)

---

### Post by airbornemist6 on 2008-05-08
I would recommend uninstalling that driver and using the restricted driver and then installing nvidia-settings which will let you enable twinview and also set up your display resolutions for you.

---

### Post by Fortisunto on 2008-05-09
> **airbornemist6 said:**
> I would recommend uninstalling that driver and using the restricted driver and then installing nvidia-settings which will let you enable twinview and also set up your display resolutions for you.

Hello, thanks very much for the reply.

Please could you point me in the direction of where i can get the "restricted driver" and the "nvidia-settings" from? Im rather new to all this :(

cheers

---

### Post by dstorrez on 2008-09-13
The best way I found to resolve this issue with this card was to load and run Envy.

Go to System>Administration>Synaptic Package Manager. Search for Envy and load. Then go to Applications>System Tools>EnvyNG. Run the automatic Detection and it will load all the right drivers.

You can also load the Nvidia X Server Settings to setup all your settings. Just go to the Synaptic Package manager and search for Nvidia and you will find it. You can setup your screen resolution and position of screans. Lots of good stuff. But only problem I ran into is that when you want to same your setting .ie. Save to X Configuration File. you need to be SuperUser. just run "sudo /usr/bin/nvidia-settings" enter your password thats it. 
hope this helps.

---

