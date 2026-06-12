---
title: "Nvidia driver issues 12.04 nvidia 7800 gtx"
date: 2013-01-10
forum: Multimedia Software
---

### Post by alexr1090 on 2013-01-10
Before I start I'd like to apologize for double posting this here--> [URL="http://askubuntu.com/questions/239450/nvidia-7800-gtx-drivers-not-working-for-12-04"]http://askubuntu.com/questions/239450/nvidia-7800-gtx-drivers-not-working-for-12-04
[/URL]


I mistakenly thought that askubuntu.com was a part of ubuntuforums. Any way I figured I would re-post it here because this is where I originally intended to post it. Any way on to the issue. . .



I bought a used nvidia 7800 gtx card and plugged it in to the  motherboard and then plugged the monitor into the the vga portion of a  dvi to vga converter located in the back of the card. I booted up and  got a 640x480 resolution. I then attempted to install the nvidia 304.37  driver. I now know that this driver has been updated to 304.64. Anyway, I  installed the 304.37 driver, restarted the computer, the screen went  white and black then dropped me to a command prompt. 

  I have since uninstalled that driver, reinstalled 304.60, 304.64, and  attempted a couple of others -- all of which were unsuccessful. The  furthest I have been able to get thus far is the 'ubuntu' picture  showing when the operating system is loading. 

  I have googled this for a while now and some other things I've tried are sudo apt-get install nvidia-current nvidia-settings, sudo apt-get install nvidia-current-updates, sudo apt-get install nvidia-experimental-304,  searching the kernel log file for hints (I read it could be an issue  with nouveau but found nothing in the log files about noveau). I did  find in the log files this: 

       NVRM: Your system is not currently configured to drive a VGA console
NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
NVRM: requires the use of a text-mode VGA console. Use of other console      
NVRM: drivers including, but not limited to, vesafb, may result in      
NVRM: corruption and stability problems, and is not supported.   

So me not being able to boot into the gui only happens when the  monitor is plugged into the card. I'm able to boot into the gui (lightdm  I believe?) when I have the monitor plugged into the on-board graphics  though *** however, I'm only able to get 640x480 resolution now and that is the only resolution available to me ***. 

  My main concern is getting the video card to display the gui, after  that I'll work on the resolution problem. Unless the resolution not  displaying all the possible values IS the problem. But I don't know what  the problem is, which is why I came here. So anyone who might know  anything about this feel free to post some things to try. I'm pretty new  to linux and ubuntu so don't rule out me not getting something obvious.

---

### Post by alexr1090 on 2013-01-10
So I've also tried this:[http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml](http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml)

And I've tried installing the nouveau-firmware. I also tried editing the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
``` line in grub (in /etc/default) to turn off acpi and of course then compiled grub using ```
sudo update-grub
``` and none of these attempts have worked. 

Oh and I also uninstalled everything nvidia drivers touch and reinstalled them all according to this page ( sorry can't find the page atm ). 

More stuff I've tried:
```
sudo nvidia-xconfig
```
```
sudo nvidia-xconfig --dac-8bit
```
```
sudo nvidia-xconfig --no-dac-8bit
```

Now the part I find a little weird is this. When I use the previous kernel version (3.2.0-34) I DO get a gui. However, lol this is a bit funny because of how it's not working but it boots using 800x600 resolution, and that's the only resolution available to me. Also it thinks my computer is a laptop for some reason. Also the mouse randomly disappears at times. Well back to Google for me. Any ideas?

---

### Post by BicyclerBoy on 2013-01-11
If you download/install the direct-from-nVidia way you need the kernel header packages & (other 32 bit stuff on 64bit machine if need 32bit opengl support).

There is a kernel headers meta-package that always points to a matching headers package.
Only the most recent nVidia installer package has solved the "re-compile with every kernel update" problem.

The nVidia driver needs blacklists for default kernel nouveau & other framebuffer drivers..
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/commonproblems.html)
(search blacklist)

All the install methods are meant to do the blacklisting thing but this does not always seem to work..

Buried deep in the nVidia driver install there is a "blacklist".conf file..

You should be fine with *buntu distro nVidia "additional drivers".
You don't have a new model like GT680..

The std distro nVidia driver will automatically rebuild with every kernel update.

---

### Post by dannyboy79 on 2013-01-11
u said the card is used, are you sure the card is even any good?

like the poster above me, you need to make sure the nouveau driver is black listed as it often times conflicts with the nvidia binaries. Is it a AGP, PCI, or PCIe card?

---

### Post by alexr1090 on 2013-01-11
So I decided to reinstall the kernel (before I had gotten these responses)... which it acutally installed the pae version. . . I suppose due to a memory upgrade. Anyway after the kernel installation I ran into a bit of a problem with my wireless card not working on it (but it worked on previous kernels) so I copied the Makefile from my previous installation under '/usr/src/linux-headers-3.2.0-35-generic/drivers/net' and voila! I have internet.


> **BicyclerBoy said:**
> If you download/install the direct-from-nVidia way you need the kernel header packages & (other 32 bit stuff on 64bit machine if need 32bit opengl support).

There is a kernel headers meta-package that always points to a matching headers package.
Only the most recent nVidia installer package has solved the "re-compile with every kernel update" problem.

The nVidia driver needs blacklists for default kernel nouveau & other framebuffer drivers..
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/commonproblems.html)
(search blacklist)

All the install methods are meant to do the blacklisting thing but this does not always seem to work..

Buried deep in the nVidia driver install there is a "blacklist".conf file..

You should be fine with *buntu distro nVidia "additional drivers".
You don't have a new model like GT680..

The std distro nVidia driver will automatically rebuild with every kernel update.
Right. After I installed the new kernel my first move was to install it using the install additional drivers in the gui. So I've done that... and good news is I was able to boot into the gui. Bad news is my resolution was a measly 800x600 with no other options. Also when I would go to system settings > Display - My monitor was coming up as a laptop for some unknown reason. Also I checked the nvidia-graphics-drivers.conf file in /etc/modprobe.d and nouveau was indeed blacklisted there.

some time passed...

So I totally got rid of nvidia on my machine. . . Booted up and for some reason everything appears to be working correctly. Really not sure about this. I'm going to leave my computer on for a while and see if it continues to display correctly. If it doesn't I'm afraid that there's a problem with this card.

> **dannyboy79 said:**
> u said the card is used, are you sure the card is even any good?

like the poster above me, you need to make sure the nouveau driver is black listed as it often times conflicts with the nvidia binaries. Is it a AGP, PCI, or PCIe card?

I was fairly certain the card was good. My logic being that if it's bad it wouldn't be able to display anything. Correct me if my logic is off though. My feeling was that it was a problem with some display setting.

However, my thoughts have changed now that I have it working. There were some errors during boot yet it seems to be working alright now that I got rid of everything nvidia. But if that would solve it, it should have worked right out of the box. So at this point I'm beginning to think that the card could be bad.

 It's a PCIe card.

---

### Post by alexr1090 on 2013-01-12
So it's been running using nouveau now with the only bug being that the ubuntu boot screen looks like a zebra. I can live with that/find a fix anyway. So it's looking good guys. I've got the cube going on making the gui nice and sexy. Thanks for the replies!

edit: on the error I was getting. . . The only thing I can figure is that I had a problem with the original kernel.  Solution for this exact particular case was reinstalling the kernel.

---

### Post by BicyclerBoy on 2013-01-13
The gnome desktop display tool never worked with nVidia X server driver.
You have to use "nvidia-settings".

I think the later drivers resolved the xrandr/Display tool problem.

---

