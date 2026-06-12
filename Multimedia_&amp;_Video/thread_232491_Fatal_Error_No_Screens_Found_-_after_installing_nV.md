---
title: "Fatal Error: No Screens Found - after installing nVidia drivers"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by nightfire117 on 2006-08-08
Ackkkk another problem for the n00b Linux user here (aka Nightfire117). 

You see... I have attempted to install the nVidia video drivers for my GeForce FX 5200 onto my Ubuntu Dapper system. Now, it won't boot into X and says:

Fatal error: No screens found

or something like that, and X won't start. Ugh, this is terribly frustrating. I used an "unofficial" installation method to get the drivers from the Synaptic package manager (and I also installed the AMD K7 kernel, I think... but it shouldn't make a difference... seeing as I've had this problem before when I tried to install the nVidia drivers). Uhm I don't know what to do, and I don't want to reformat AGAIN after having this problem before.... I'd be willing to if it'll work for sure and someone will give me a 100% guarantee of how to exit X so I can use the nVidia installer and have it working. Will it...? I need it to work... hehe. 

Thing is, I don't know much about Linux at ALL. So, I don't know how to post any log files or config files or whatnot here. So I don't know what to do. At all. I'm such a noob, but hey, weren't we all? That's no excuse. Any help would be much appreciated....

~Nightfire

---

### Post by computergroove on 2006-08-09
OK, First you should be ablt to boot to a login console even if X wont start. Login and type 
> sudo cp /etc/X11/xorg.conf_backup(***what ever your backup filename is***) /etc/X11/xorg.conf

You can easily find out what your backup filename is by typing the above command (sudo cp /etc/X11/xorg.conf and hit tab a few times). Hitting tab a few times should dislay a file name on the screen which you need to replace the (***what ever your backup filename is***) section above with. If this is done successfully you can type > sudo reboot and you should boot back into Gnome. Install the Nvidia drivers by using the synaptic package manager and marking the nvidia drivers for installation. When they are downloaded go to applications > terminal and type
> sudo gedit /etc/X11/xorg.conf
Find a "device" section that has your video card named under it you will see a driver version of "nv". Change the "nv" to "nvidia" and save the file and hit ctrl alt backspace. Your computer will boot you off the desktop and log you back into Gnome. If you see the Nvidia splash screen and it boots into Gnome then you are all set.

---

### Post by nightfire117 on 2006-08-09
Thanks for the reply m8. I'll check back here after I've done that and let you know how I've screwed it up even more - just kidding, thanks for your help, I'll try that out. :-D

~Nightfire

[EDIT]: Thanks, restoring the file worked good and I'm running X again. However... I guess I'll put off those nVidia drivers until some other time. Thanks for your help! :D

~Nightfire

---

