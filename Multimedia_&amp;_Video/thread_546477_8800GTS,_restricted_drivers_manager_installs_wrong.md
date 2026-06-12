---
title: "8800GTS, restricted drivers manager installs wrong package"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by jodansmif on 2007-09-08
I have an NVIDIA 8800 GTS... my problem is that with the default nv driver, my desktop is way off center (it is centered correctly when I boot XP). One suggestion to fix this problem is to install the binary drivers (which I wanted to do eventually anyway). The recommended method of turning them on in Restricted Drivers Management led to the install of nvidia-glx (the 96xx series) when my card needs nvidia-glx-new (the 97xx series) according to the NVIDIA website.  The 96xx drivers borked up my xorg.conf and I ended up reinstalling Ubuntu.

How do install the correct drivers in this situation? My browsing has led to two suggestions: use apt-get (whatever that is) or some script set called Envy (no thanks, given what I've heard about Automatix). 

Also, when the appropriate drivers are installed, how should I go about recentering my desktop in my monitor... GUI preferred but I can manage CLI stuff if well directed. Finally, if I screw up again, how can I restore the default nv drivers without reinstalling Ubuntu?

Many thanks!

---

### Post by goatflyer on 2007-09-09
sudo apt-get is a standard command-line way to get software from the official repositories. (sudo aptitude is another).  You may already know synaptic and add/remove as the standard gui ways.

envy is a non-official way of installing proprietary drivers for nvidia and ati cards onto ubuntu systems.  You will not find the proprietary nvidia driver in the official ubuntu repositories.

I used envy myself with great success after struggling and then giving up trying to install the official 0nvidia drivers as described on the nvidia site.  The Ubuntu drivers did not work at all with my 7600GS AGP card.

You may have better luck than I did following the nvidia site instructions, here they are:
 [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

Otherwise, envy is here.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy downloads the ubuntu kernel header files for the version of kernel you are using, downloads the correct driver from nvidia, compiles everything and installs it and updates your xorg files.

The only drawback I've found with my setup is after an automatic ubuntu update in which the kernel version changes, my gui fails to load because my (now old) nvidia driver was not compiled for the new kernel.  When that happens, I just run "envy -t" to use envy's command line menu and hit "install new nvidia driver" again.  The problem is then solved until the next kernel update.

Good luck, whatever you decide to try.

---

### Post by Straylit Me on 2007-09-09
Use Envy. It wont take 10 minutes.

Go to the link he ^ provided. Download install the .deb and Choose Applications>System Tools>Envy
From there just choose "Install nvidia driver" and watch it work its magic.

---

