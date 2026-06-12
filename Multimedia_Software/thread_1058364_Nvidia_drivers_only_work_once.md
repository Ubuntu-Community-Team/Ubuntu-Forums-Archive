---
title: "Nvidia drivers only work once"
date: 2009-02-02
forum: Multimedia Software
---

### Post by jrbootsma on 2009-02-02
Okay, so I'm running Ubuntu 64-bit 8.10 on a new laptop after my old one broke. It uses an Nvidia 9600M GT card so I decided to use the proprietary drivers. I get this same problem with both the pre-compiled 177 drivers and the self-built 180 drivers from Nvidia's site. 

Basically the first time I run Ubuntu with the gdm enabled the drivers work exactly how they're supposed to, but next time I boot, the x-server tries to start up 3-5 times then tells me my hardware and display could not be properly detected. At this point my screen has a band of corrupted colors across the top and the screen is offset to the right and 'wraps' i.e. i move the cursor past the right edge of the screen at it appears on the right. 

Going into the trouble shooting section the only error I find is:
GLX failed to initialize. Compatible NVIDIA x driver not found.

So i change my xorg.conf file driver setting back to nv and I'm back to non-accelerated graphics.

checking dmesg gives no errors.

To reproduce this bug I don't even have to re-install the drivers. If I change my xorg.conf file back to nvidia without the gdm running the drivers work again, but only for one boot. If I edit the xorg.file while the x-server and gdm is running it will crash the first time as well.

This leads me to believe the problem is somewhere in the shutdown procedures of the x-server or gdm. If anyone could give me some insight into this it would be greatly appreciated.

If you need to look at any specific log files let me know and I will post them.

---

### Post by redroad55 on 2009-02-02
take a look here. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by jrbootsma on 2009-02-02
I've already taken a look at that, and the drivers won't show up in the Hardware Drivers any more anyway. I've tried different ways of installing different drivers, but the only way that somewhat works is manual installation of drivers from the Nvidia site, or using the Synaptics package manager.

---

### Post by skompier on 2009-02-02
I feel your pain. I had the exact same problem when I installed a new 9800GT. I have it working now with no problems, but I can't remember exactly what I did. I do remember reading a post about having to identify some PCI bus info and adding this to xorg.conf in a device section. I rebooted and everything worked. I'll see if I can find the post again but I searched high and low and tried everything. Dumb luck shined on me.

Here's the post that I was referring to. I was following these instructions and then when I rebooted, all was working. This is not to say that this will work for you. I tried EVERYTHING, including going to 8.04 from 8.10. Good luck.

[http://ubuntuforums.org/showthread.php?t=1035873&highlight=9600](http://ubuntuforums.org/showthread.php?t=1035873&highlight=9600)

---

### Post by blue13130 on 2009-02-02
Hi take a look at my post in another thread about help with Nvidia drivers:
[http://ubuntuforums.org/showpost.php?p=6549293&postcount=6](http://ubuntuforums.org/showpost.php?p=6549293&postcount=6)

I use the latest Nvidia drivers from the website and have got them working with Ubuntu 8.04.2 32bit and 8.10 64bit using the method I described in the mentioned post.  The important part is to remove all current nvidia packages on your machine.  For some reason there is a conflict when having the linux-restricted-modules* packages.  I have not had any problems on my machines after removing those packages.  If you do you can reinstall them later.

---

### Post by skompier on 2009-02-02
> **blue13130 said:**
> Hi take a look at my post in another thread about help with Nvidia drivers:
[http://ubuntuforums.org/showpost.php?p=6549293&postcount=6](http://ubuntuforums.org/showpost.php?p=6549293&postcount=6)
  For some reason there is a conflict when having the linux-restricted-modules* packages.  I have not had any problems on my machines after removing those packages.  If you do you can reinstall them later.

I also did this and this may have fixed my problem also. I tried so many things I have no idea what the magic combination was.

---

### Post by redroad55 on 2009-02-02
this may help you isolate the problem..
To disable gdm from running during boot, disable the rc service like this: 
>  sudo update-rc.d gdm stop 2 3 4 5 .
Note :- Please note that there is a dot at the end. This is essential.
Then to re-enable it later,
> sudo update-rc.d gdm start 30 2 3 4 5 . stop 01 0 1 6 .
This will run X in complete isolation from gdm.
GDM has startup scripts that are executed when X is initiated.In GDM, these are in /etc/gdm/     
 
Give it a try if you want and post back

---

### Post by jrbootsma on 2009-02-03
Okay, so I tried adding the BusID line to my xorg.conf file, but the same thing still happened, and I've already completely removed the linux-restricted modules package. However GLX will still crash on the second boot after the drivers are activited (which really bugs cause for some reason they work the first time...). 

I tried the update-rc command but the console said "System startup links for /etc/init.d/gdm already exist."

As a side note I'm thinking of just switching to a different distro anyways, as I'm learning how to program in opengl (hence the need for the proprietary drivers) so if anyone knows of a distro well suited to this I'd appreciate it if you let me know.

---

### Post by blue13130 on 2009-02-04
> **jrbootsma said:**
> Okay, so I tried adding the BusID line to my xorg.conf file, but the same thing still happened, and I've already completely removed the linux-restricted modules package. However GLX will still crash on the second boot after the drivers are activited (which really bugs cause for some reason they work the first time...). 

I tried the update-rc command but the console said "System startup links for /etc/init.d/gdm already exist."

As a side note I'm thinking of just switching to a different distro anyways, as I'm learning how to program in opengl (hence the need for the proprietary drivers) so if anyone knows of a distro well suited to this I'd appreciate it if you let me know.

As a final attempt, remove all nvidia packages and remove your xorg.conf file.  Then reinstall the Nvidia driver that you downloaded and see if that makes a difference.

---

