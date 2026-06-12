---
title: "Restricted Drivers Manager and GeForce 8600"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by WATERBOYsh on 2007-07-17
I just upgraded my computer, and I got a GeForce 8600GT. When I open the Restricted Drivers Manager, a pop-up claims "Your hardware does not need any restricted drivers."

I had wanted to do it this way because (and correct me if this has changed, its been a long time) if you manually install the drivers from NVidia's web site, then anytime there is a patch to the kernel pushed out through synaptic and the kernel changes, you have to reinstall the nvidia driver to the new kernel. I'm pretty sure that the Restricted Drivers Manager will do this for you. I just remember trying out Linux a couple years ago, installed the drivers from NVidia's site, and then a couple months later when a kernel security update was pushed out, I installed it, not knowing what would happen. Then when I tried to boot, the screen would go black and boot me into a terminal saying that the loading of X failed. I'm not a linux expert and I wouldn't know how to fix my computer if that happened again. That was what caused me to go back to Windows before, and I don't want it to cause it again.

---

### Post by dabl on 2007-07-17
I THINK, but cannot state with 100% certainty, that your GeF 8600 requires the 100.14.11 driver, but the nvidia-glx-new package (the one that Restricted Drivers uses) is only -9755.  If I'm right about this, then you will need to install the proprietary driver yourself.  Best way for Linux noobs to do that is to use the Envy script installer, obtainable here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want to download the file "envy_0.9.6-0ubuntu1_all.deb", about 2/3 of the way down the page, and follow his instructions to install it as a package on your Ubuntu system.

Then it will appear in your System menu and you can run it from there. If you install it successfully, but have any problem running it as a GUI app, you can open a console and enter ```
sudo envy -t
``` and it will run just fine in text mode.  :)

---

### Post by nouse66 on 2007-07-17
yeah, dabl is basically right. support for the 8600 series was added in a newer driver than what ubuntu has in the repos:
[http://www.nvidia.com/object/linux_display_ia32_100.14.03.html](http://www.nvidia.com/object/linux_display_ia32_100.14.03.html)

---

