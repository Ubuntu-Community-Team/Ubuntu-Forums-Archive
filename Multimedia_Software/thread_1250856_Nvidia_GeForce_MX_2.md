---
title: "Nvidia GeForce MX 2"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Omcon on 2009-08-27
Does anyone know if there is a graphics driver that works? If so, tell me what it is, and I will wipe this HD of Windows. :) I'd love to know if there is. Thanks a bunch. Oh, and an unrelated question: Does anyone know if Counter Strike Source can be run under WINE/Cedega?

---

### Post by cascade9 on 2009-08-27
Yes, theres a driver that works- 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Counterstike works wasl well-

[http://appdb.winehq.org/appview.php?iAppId=871](http://appdb.winehq.org/appview.php?iAppId=871)

---

### Post by Omcon on 2009-08-27
Thanks for the info, man. I just hope they work. Last time I tried installing the legacy drivers, none of them worked. Could I install these while running a live session, just to try them out?

---

### Post by inobe on 2009-08-27
your card is listed under legacy, select legacy under the first drop down.

edit; NOTICED YOUR EDIT


you can install inside windows, pop in the disk and use the wubi installer.

see if you can get drivers working that way' if that doesn't work simply uninstall ubuntu in add and remove programs.

---

### Post by Omcon on 2009-08-27
> **inobe said:**
> your card is listed under legacy, select legacy under the first drop down.

Yeah, I figured that out and edited my post. Thanks anyways! :D

---

### Post by inobe on 2009-08-27
i edited too :lol:

---

### Post by Omcon on 2009-08-27
> **inobe said:**
> your card is listed under legacy, select legacy under the first drop down.

edit; NOTICED YOUR EDIT


you can install inside windows, pop in the disk and use the wubi installer.

see if you can get drivers working that way' if that doesn't work simply uninstall ubuntu in add and remove programs.

Ok, not quite sure what you mean there. I meant just running it off the CD. To see if the graphics drivers would work, could I run CS:S off my Windows HD under WINE in a live session? Cause that's the only reason I'm still hanging on to windows. And my pirated version got noticed my MS today. haha. I'm getting the "This copy of Windows did not pass genuine Windows validation." notifications. Heh.

And I'm downloading the Ubuntu 9.04 .iso as we speak, so if this works, I'm getting this wagon train a-rollin! I am so tired of Windows. The only reason I'm using it is because lsat time I tried, I couldn't find a legacy driver that would work on my box, and also for CS:S. haha.

---

### Post by inobe on 2009-08-27
it installs ubuntu inside windows so if you don't like it' you can uninstall it.

[http://www.youtube.com/watch?v=n5x9iJWXbUY](http://www.youtube.com/watch?v=n5x9iJWXbUY)

---

### Post by Omcon on 2009-08-27
Ok, thanks a bunch for that. Is there a way to make the wubi installer work with the .iso I just downloaded, or does it have to download the torrent every time?



EDIT: Just re-read your original post. So I can just pop in the disk I burn, and it will install it from the disk? Sweet action. Thanks again man. :)

---

### Post by inobe on 2009-08-27
if you have the untuntu iso install isomaster and mount the iso as a virtual cd or burn it to a cd.

---

### Post by Omcon on 2009-08-27
OK, so got xubuntu installed cause I had a CD already lying around, and I like Xfce better than Gnome or KDE. So, got it installed through wubi, and now I'm having trouble getting the drivers to work. I enable the drivers through Applications > System > Hardware Drivers, and restart. What I get is like half the login screen. The top half is black. And when I hover over the text box for the username, the cursor changes and everything, but when I type, nothing shows up. I have to restart in recovery mode and do Xfix to get things back to normal. I've had this problem before, and have posted here about it before. This is actually like the third time. Haha. So! I'm going to go back to those posts, and follow their advice, and see if that works, If not, I'll be back here, asking for help.

---

### Post by gradinaruvasile on 2009-08-27
If u install it the first time i think the default ubuntu (gnome) would be better. It has more features that make life easier - like the integrated network support and such.

Anyways u need the following driver if u have nvidia mx :

[http://www.nvidia.com/object/linux_display_ia32_96.43.13.html](http://www.nvidia.com/object/linux_display_ia32_96.43.13.html)

Installation:

1. D/l the driver, to the desktop. Disable the restricted drivers if u enabled it.
2. Type in a terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

3. Reboot, select recovery startup mode, then root prompt.
4. Cd to the drivers directory and run the installer (terminal/command line commands - enter after each line):

cd ~/Desktop
chmod +x NVIDIA-Linux-x86-96.43.13.pkg1.run
./NVIDIA-Linux-x86-96.43.13.pkg1.run

- It will complain about runlevel 1, its not a problem. Select not to download the kernel module, and accept to set up your xorg.conf automatically.

5. When finished installing reboot (in the command line):

reboot

6. Normal boot, hopefully will work...

---

### Post by Omcon on 2009-08-27
Ok, so here's what I get when I do what you've said. Disabled the graphics drivers, and rebooted, went to recovery mode, and root prompt.

I type in:
cd~/Desktop

And I get this:
No such directory.

Help?

OH! I almost forgot. I went back to my other posts, and took their advice. It seemed to work. The login screen was partially black, but I was able to log in. Then on the main screen, the wallpaper started to load, but went all wonky on me. And I rebooted in recovery mode, and did xfix. Then I come back, and the top and bottom panels are gone. Luckily i can still access everything through the right-click menu. Any tips on how to get them back?

And if it's that big of a deal, I can always download gnome through synaptic, right?



Ok, doing fresh install through wubi of Ubuntu. I'm going to try everything again. We'll see how it works.

---

### Post by Omcon on 2009-08-28
Ok, so when I activate the drivers, and restart, I get to the login screen and everything is fine. Then, sometimes it will load into Ubuntu. But when it does load, the desktop will look like this picture I've attatched. I have the panels set to auto hide, but they kinda show up. Sometimes I'll see the cursor on a black screen. The light in my mouse comes on when I move it, but the cursor doesn't move. And nothing happens when I let it sit for a while. Ctrl+Alt+F1 does nothing. I have to do a hard shutdown, and reboot in recovery mode, and do Xfix.

Any ideas? I've tried everything that's in this thread so far, with no results. I'm stumped. :( Help?

---

### Post by gradinaruvasile on 2009-08-28
> **Omcon said:**
> Ok, so here's what I get when I do what you've said. Disabled the graphics drivers, and rebooted, went to recovery mode, and root prompt.

I type in:
cd~/Desktop

And I get this:
No such directory.


Its

```
cd ~/Desktop
```

There is a space between "cd" and the rest

---

### Post by Omcon on 2009-08-28
Ok so, did all that. I couldn't make cd ~/desktop work. But, I was able to make it work by typing in: ```
cd /home/dave/Desktop
``` and doing it from there. Installed the drivers, and had no problems. Rebooted, and then when the login screen should have come up, it looked as though I would have hit Ctrl+Alt+F1 to get to the text-based login thing. (I don't know what to call it. haha) And then the screen flashes a few times, then goes black. And nothing works, or happens. Ctrl+Alt+F1 does nothing, and I have to do a hard shutdown. Any thoughts?

---

### Post by Omcon on 2009-09-03
*bump*

---

### Post by Omcon on 2009-09-05
No one has any ideas or suggestions? It would be greatly appreciated. :)

---

