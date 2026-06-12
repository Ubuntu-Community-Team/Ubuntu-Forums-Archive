---
title: "Nvidia driver 260.19.16"
date: 2010-10-30
forum: Multimedia Software
---

### Post by claven123 on 2010-10-30
[http://ubuntuforums.org/showthread.php?t=906865&page=16](http://ubuntuforums.org/showthread.php?t=906865&page=16)
 
I've been working on my issue for some time, thanks to all those who have helped me.  
 
I now have both monitor working and noticed my drivers are not current.  I have the older ones installed.  The 260.19.06 one.  I installed via the suggested restricted driver utility in ubuntu 10.10.
 
I don't have full use of the graphics and would like to install the latest driver. 
 
Question:
1. Do I uninstall  nouvea and nv drivers (still installed)
2. Do I uninstall the current nvidia driver, then do a manual install of the latest driver from nvidia?
 
 
 
Thanks,

---

### Post by P4man on 2010-10-30
The drivers you have, are the ones that have been tested with ubuntu 10.10, not the ones nvidia released a few days ago. If it aint broken, dont fix it. At some point those drivers will be updated as part of the update process, unless you have a compelling reason to install them by hand, my advice is: dont. Especially if you need to ask how.

But if you insist, just download the package from nvidia website, make it executable and run it. You shouldnt have to "uninstall" anything.

---

### Post by claven123 on 2010-10-30
I know how to install them, I just needed clarification on what to do with the old drivers. I'm not 100% happy with what I have.  I can live with it, but it's not correct.  It just works.  

Anyway thanks for the advice.

---

### Post by tommcd on 2010-10-31
You should remove the nvidia driver from the Ubuntu repos before installing the driver from nvidia.com.
You also need the **build-essential** package, as well as the linux-headers for your kernel.
This guide is a bit out of date, but it is a good reference:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
Also make sure you blacklist nouveau. See this from Ubuntu-Geek:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

### Post by Scott O'Nanski on 2011-01-11
> **P4man said:**
> The drivers you have, are the ones that have been tested with ubuntu 10.10, not the ones nvidia released a few days ago. If it aint broken, dont fix it. At some point those drivers will be updated as part of the update process, unless you have a compelling reason to install them by hand, my advice is: dont. Especially if you need to ask how.

But if you insist, just download the package from nvidia website, make it executable and run it. You shouldn't have to "uninstall" anything.

Absolutely TERRIBLE advice! Bad! Now go lay down... :D

The drivers from Nvidia's website are NOT compatible with the nouveau driver - the nouveau driver should either be remove, or blacklisted, or else your system will hang at boot.

To the OP;

Read the installation 'how-to' onj the Nvidia website - that's how I learned to install them.

[quote="nvidia website"]
Before you Begin

Before you begin the installation, exit the X server and terminate all OpenGL applications (note that it is possible that some OpenGL applications persist even after the X server has stopped). You should also set the default run level on your system such that it will boot to a VGA console, and not directly to X. Doing so will make it easier to recover if there is a problem during the installation process. See Appendix I, Tips for New Linux Users for details.

If you're installing on a system that is set up to use the Nouveau driver, then you should first disable it before attempting to install the NVIDIA driver. See Q & A 8.1, “Interaction with the Nouveau Driver” for details.[/quote]

The instructions go onto say...

[quote="nvidia website]

	

How do I prevent Nouveau from loading and performing a kernel modeset?
	

A simple way to prevent Nouveau from loading and performing a kernel modeset is to add configuration directives for the module loader to a file in /etc/modprobe.d/. These configuration directives can technically be added to any file in /etc/modprobe.d/, but many of the existing files in that directory are provided and maintained by your distributor, which may from time to time provide updated configuration files which could conflict with your changes. Therefore, it is recommended to create a new file, for example, /etc/modprobe.d/disable-nouveau.conf, rather than editing one of the existing files, such as the popular /etc/modprobe.d/blacklist.conf. Note that some module loaders will only look for configuration directives in files whose names end with .conf, so if you are creating a new file, make sure its name ends with .conf.

Whether you choose to create a new file or edit an existing one, the following two lines will need to be added:

blacklist nouveau
options nouveau modeset=0

The first line will prevent Nouveau's kernel module from loading automatically at boot. It will not prevent manual loading of the module, and it will not prevent the X server from loading the kernel module; see "How do I prevent the X server from loading Nouveau?" below. The second line will prevent Nouveau from doing a kernel modeset. Without the kernel modeset, it is possible to unload Nouveau's kernel module, in the event that it is accidentally or intentionally loaded.

You will need to reboot your system after adding these configuration directives in order for them to take effect.[/quote]

Maybe it's just placebo, but I always I find I get better performance out of the newest drivers (generally speaking).

---

### Post by efflandt on 2011-01-11
There is no need to mess around trying to remove and/or blacklist nouveau and manually install drivers that may need to be reinstalled whenever you get a kernel update, which will be missing modules for your manually installed video drivers.

If you need newer nvidia drivers than are in your Ubuntu version, and you are running Lucid or Maverick, it is much easier to simply use x-swat ppa repos to get the most recent nvidia driver packages that cooperate with Ubuntu.  Simply:
[FONT=monospace]
[/FONT]```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```If you are using an earlier nvidia version from the repos, first use Additional Drivers (Hardware Drivers in Lucid) to "remove" nvidia.   Then "activate" nvidia, reboot.  It is that simple, and they will still work after kernel updates.

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

