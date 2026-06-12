---
title: "Ubuntu Feisty with GeForce 8800 GTS"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by alisic on 2007-06-09
Hey!
I have a new comp and I installed Feisty on it. The installation went fine, the X server started and I successfully logged into my account. But the resolution was 1024x768 because the proper NVIDIA drivers hadn't been installed yet. So I chose to enable the restricted drivers. It said it enabled them and prompted me for a reboot. Once I rebooted, X server wouldn't start. The error message was quite lengthy, but the gist of it was: fatal error, no screen found. 

Now without X, I also have no internet connectivity (don't know why, my wireless NIC worked when I was in X before trying to enable the restricted drivers). I googled the problem and searched the forums here, but no solution really worked. I tried doing dpkg-reconfigure xserver-xorg and selecting the vesa to get basic X stuff running, but it didn't work, still 'no screen found'. I also tried dpkg-reconfiguring xserver-xorg by selecting the nvidia option, but to no avail. I even tried going to the live CD, downloading the .deb for a previous version of X server (1.0.0.2 I think) and installing that, but to no avail (I later saw that I was doing that on guides someone posted from 2006 I think, so that might have been a mistake).

Does anyone know what's going on here? I've exhausted my resources, really, so I turn to you good people and thank you in advance for any help or tips. By the way, if it helps, it's the 32-bit version of Feisty, the card is an XFX GeForce 8800 GTS, I have one CRT and one LCD running on it, but I can configure TwinView later.

I'm pretty much still a noob, and keep in mind that I don't have internet connectivity without X, so I can't apt-get stuff while in the console, I have to boot up into the live CD, wget .deb packages (probably) and put them on my home folder in the HD installation.

Thanks!

---

### Post by alisic on 2007-06-09
Just a little update, if this maybe helps.
I tried formatting the current Feisty partition and installing again. But this time instead of just checking the restricted drivers that popped up in the tray, I did
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```
But the same thing happened and I still got the no screens found error.

Then, I tried installing Feisty again and this time updating the nvidia drivers via automatix2. It updated, I rebooted and as expected, X crashed, but this time with a different error message. And now I didn't even get into the command prompt, it was just a dark screen, I could type stuff and it was displayed on the screen, but that's about it.

Here's the error log from the latest failure [http://netvibes.box.net/ping/download/68125947/7qik7dvkcijebie3hf5na86n64](http://netvibes.box.net/ping/download/68125947/7qik7dvkcijebie3hf5na86n64)

---

### Post by wererabbit on 2007-06-09
Ok, I have a similar setup as you, just upgraded to the EVGA 8800GTS card.  I've got it mostly working.  

Here is how I got the Feisty install to work:

1. Install onto my computer from CD
2. Run Automatix2 and install mostly everything.
3. reboot
4. Go to Alberto Milone's website and run Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))
5. reboot - Envy will have installed the nvidia drivers that work for our cards.
6. You will have to edit your xorg.conf file by hand to add the custom resolutions for your desktop - pretty easy to do - instructions on this all over the place.
7. At this point, you should be good to go.  Anything from here is icing on the cake.

Icing:
8. You'll probably want to install Beryl and Emerald from the Synaptic Package Manager.
9. This may or may not work right off, and will probably be a real pain the patoot.  Just fiddle with it and do searches on the site for problems you encounter.  Google searches are nice too.

I think that is pretty much it. Good luck! :D

---

### Post by heldal on 2007-06-11
> **alisic said:**
>  By the way, if it helps, it's the 32-bit version of Feisty, the card is an XFX GeForce 8800 GTS, I have one CRT and one LCD running on it, but I can configure TwinView later.


The nvidia-glx-new package is missing a file that is required to make the 8800 GPUs work. See eg: [http://ubuntuforums.org/showthread.php?p=2797667#post2797667](http://ubuntuforums.org/showthread.php?p=2797667#post2797667)

> 
I'm pretty much still a noob, and keep in mind that I don't have internet connectivity without X, so I can't apt-get stuff while in the console, I have to boot up into the live CD, wget .deb packages (probably) and put them on my home folder in the HD installation.


Without network the best you can do is to grab a copy of the driver package from Nvidia's site and put it on a CD you can take with you. That gives you the option of either use the nvidia-glx-new package in feisty and extract only the missing from nvidia's package or use nvidia's package instead. Automatix and other alternative tools for installation usually require network connectivity.

---

### Post by ZeusABJ on 2007-07-11
One question for you guys. Wererabbit your method does work and I can get the nvidia driver for my 8800 card installed using Envy. The problem is it seems to make Ubuntu very unstable and I'm plagued with performance issues. Frame rates are slow and I seem to have a lot of artifacts when I resize Windows. What makes this more frustrating is I've tried other distros but I don't seem to have these glitchy performance issues and resizing and moving windows seems much smoother. I don't understand what I'm doing wring here and this is just becoming really frustrating. Any suggestions?

---

