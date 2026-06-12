---
title: "WORKING! Gusty + NVIDIA 8800GT dual screens"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by louminati on 2008-03-19
Below I describe how I got my **NVIDIA 8800GT dual screens** working properly on **Ubuntu Gusty Gibbons** generic 32 bit kernel/Gnome.  After hours of surfing and tweaking it finally works!

My system is a Dell XPS 420 with Intel Core2 Q6600 and a 512MB NVIDIA GeForce 8800GT graphics adapter.  I am running two 19" LCDs at 1280x1024.

The live CD forced low graphics mode.  Same with the full install.  Envy would not work correctly for me.  I could get a pretty clean looking desktop with the generic VESA graphics card driver, and generic LCD monitor drivers using the correct resolution, but I really wanted to experiment with the Open GL desktop effects and the super-fun compiz cube.  So I went on the hunt for the correct NVIDIA drivers.

**The following procedure finally got the NVIDIA driver loaded correctly:**

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=726480[/COLOR]]("http://ubuntuforums.org/showthread.php?t=726480")

In case of any link problems, the thread title is "[SOLVED] NVIDIA 8800GT graphic card installation problem."

This is apparently somewhere on the NVIDIA site but I found it on the thread above:

> Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

> * development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed

I skipped these steps above and started below.

> * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist
I had the nvidia-kernel file but not the glx.

> If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. 
**This above step was key I believe.  It can be done from System, Administration, Synaptic Package manager for those who are new like me.**

> Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv nvidia_new"

I also did the above step even though it may have been redundant.

> Additionally, delete the following file if it exists:

/lib/linux-restricted-modules/.nvidia_new_installed
I did not have this file.

**Now you've set the stage to install the correct drivers.  Go to the NVIDIA website and pull down the latest driver.**  As of this posting the exact file was NVIDIA-Linux-x86-169.12-pkg1.run
Link [[COLOR="Blue"]here[/COLOR]]("http://www.nvidia.com/object/linux_display_ia32_169.12.html")

Stop X from a terminal with:

```
sudo /etc/init.d/gdm stop
```

Run the NVIDIA driver package with:

```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

You will get an error about the kernel, just keep marching and the package will work through it.  Choose the option for it to modify for xorg.conf file for you.

Start X back up with:

```
sudo /etc/init.d/gdm start
```

You should see a brief NVIDIA splash and BAM you're there!

My setup includes dual screens which needed to be set up using “Twinview” and not “separate X screen.”  I first used the “separate X screen” option but this resulted in some strange behavior...such as the fact that I couldn't start a separate Firefox session on the second screen, menu bars would often disappear, and the menu items were very slow (1 – 1.5 second delays on click.)  Twinview, once set up properly, immediately eliminated all these issues.

Access this NVIDIA setup with:

```
sudo nvidia-settings
```

**Sudo from terminal is important since running the NVIDIA X Server Settings from Applications, System Tools does NOT seem to write changes to the xorg.conf file.**

If you get any strange behavior, restart X and reboot.  I had an issue at first where only half of my desktop was displayed with Twinview (and it wasn't the half with all the useful desktop items.)  I had to escape to the terminal with ALT-CTRL-F1 and vi my xorg.conf file to change the “twinview” param back to zero, and then restart X and ensure both displays were enabled properly.  You can probably avoid this headache by ensuring both displays are configured properly and enabled before flicking the twinview switch from the NVIDIA settings gui.

After completing the above I was able to install compiz and get the cube working great.  Both screens rotate the same cube but I can move windows from one screen to the other and run multiple apps wherever I choose.  It's behaving exactly like I'd expect it to now.

I hope this post will spare someone else the many hours of frustration I had as a brand new Ubuntu user.

Many **thanks to “bobetko”** and others in the community for posting the info on the forum here that finally helped me get the driver installed correctly.  Also **thanks to NVIDIA** for writing great linux drivers!

Cheers and rock on!

:guitar:

-Lou

---

### Post by cunliffe on 2008-03-20
I followed a similar guide but yours is much more complete. Thanks for making this.

I had one problem. 

Symptom: wireless internet dies after rebooting (but 8800GT works great!)

When I clicked on the restricted driver manager it said something like:

> You need to install the following package: linux-restricted-modules-2.6.22-14-generic

Why it happens: my wireless apparently uses a restricted module (Atheros Hardware Access Layer). When you remove linux-restricted-modules you break it.

Also I have also seen people recommend you uninstall nvidia-kernel-common. Both of these uninstalled my linux-restricted-modules because my restricted modules depend on nvidia-kernel-common.

Fix: I booted up off the ubuntu CD (which had internet) and did this:

 sudo apt-get --download-only --reinstall install linux-restricted-modules-2.6.22-14-generic
 sudo apt-get --download-only --reinstall install nvidia-kernel-common

That got the files, then I moved them to the harddisk ( /var/cache/apt/archive/ ), then rebooted off the harddisk, then installed them like this:

 sudo apt-get install --no-download nvidia-kernel-common
 sudo apt-get install --no-download linux-restricted-modules-2.6.22-14-generic

Both my video and my internet are now working now. Perhaps there are easier ways; I'm very new at this. I hope this helps someone.

---

