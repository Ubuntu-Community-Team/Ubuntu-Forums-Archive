---
title: "More NVIDIA 3D problems"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by shendric on 2006-06-26
Hi all,

I've been talking about this with guys in Gaming Central, and they suggested I bring this over here.  I'm trying to run some 3D games, with my NVIDIA GeFORCE GO 6600, and I keep getting the following error, for example, from glxgears:

Xlib: extension "GLX" missing on display ":0.0".

Just to see what might help, here are the relevant sections of my xorg.conf:

```

Section "Module" 
# Load "GLcore" 
Load "i2c" 
Load "bitmap" 
Load "ddc" 
# Load "dri" 
Load "extmod" 
Load "freetype" 
Load "glx" 
Load "int10" 
Load "type1" 
Load "vbe" 
EndSection

```

```

Section "Device"
        Identifier      "NVIDIA"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"                 "1"
#       Option          "TwinView"
#       Option          "TwinViewOrientation"   "DFP-0 RightOf CRT-0"
#       Option          "MetaModes"             "1680x1050, 1024x768; NULL, 1024x768; 1680x1050, NULL; 1680x1050 +0+0, 1024x768 +1024+0"
#       Option          "MetaModes"             "1024x768, 1680x1050; NULL, 1680x1050; 1024x768, NULL; 1024x768 +0+0, 1680x1050 +1024+0"
EndSection

```

I'm running Breezy, and any help I could get in this would be appreciated.  I attempted a dpkg-reconfigure of the X server, but it didn't help.

Sean

---

### Post by gborzi on 2006-06-26
You should check the /var/log/Xorg.0.log file for errors, which are denoted by an (EE) at the start. Maybe the error is due to the fact that the file /usr/X11R6/lib/modules/extensions/libglx.so is missing or is wrong. In order to have the GLX extension the libglx.so file must be a link to a file named libglx.so.1.0.xxxx, where xxxx is the nvidia driver version. On my system, where I use the prepackaged drivers, xxxx=7667. Have you used the prepackaged drivers ?

---

### Post by shendric on 2006-06-26
[QUOTE=gborzi]Have you used the prepackaged drivers ?[/QUOTE]

I'm checking the other information now, but I'm using the drivers installed from Synaptic.

Sean

---

### Post by shendric on 2006-06-26
Ok, the log shows that it failed to load /usr/X11R6/modules/extensions/libglx.so and I looked to see if it was there, and it is, along with the following:

libglx.so.1.0.8756
libglx.so.1.0.7667

And libglx.so is a link to libglx.so.1.0.7667.

Sean

---

### Post by gborzi on 2006-06-26
Perhaps you tried to install the latest nvidia drivers (8756) with the NVIDIA installer and it changed some files of the nvidia default package (7667). I suggest you to uninstall the latest nvidia drivers (with sudo sh ./NVIDIA... --uninstall) and check the nvidia-glx, nvidia-kernel-common, linux-restricted-modules-`uname -r`, linux-restricted-modules-common and nvidia-settings and reinstall the broken one(s). You can check them with debsums, e.g. > debsums -a nvidia-glx etc.
Reinstall with > sudo apt-get install --resinstall nvidia-glx and so on. Also, before un/installing anything stop gdm (or kdm) and remove the nvidia module from the kernel, i.e. > sudo modprobe -r nvidia if it's loaded.

---

### Post by shendric on 2006-06-26
[QUOTE=gborzi]Perhaps you tried to install the latest nvidia drivers (8756) with the NVIDIA installer and it changed some files of the nvidia default package (7667). I suggest you to uninstall the latest nvidia drivers (with sudo sh ./NVIDIA... --uninstall) and check the nvidia-glx, nvidia-kernel-common, linux-restricted-modules-`uname -r`, linux-restricted-modules-common and nvidia-settings and reinstall the broken one(s). You can check them with debsums, e.g.  etc.
Reinstall with  and so on. Also, before un/installing anything stop gdm (or kdm) and remove the nvidia module from the kernel, i.e.  if it's loaded.[/QUOTE]

Ok, let me see if I get what you're suggesting in the right order:

stop gdm (how?)
sudo modprobe -r nvidia
Uninstall the latest drivers (I'm not sure how to go about that)
Check(?) the packages nvidia-glx,nvidia-kernel-common,linux-restricted-modules-'uname -r', linux-restricted-modules-common and nvidia-settings
reinstall the above packages.

Sorry to be so dense, but this gets into areas I'm not as proficient with, and I want to make sure I don't mess anything up.

Sean

---

### Post by tseliot on 2006-06-26
Try my script (use the "install" function), it should solve the mismatch:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by shendric on 2006-06-26
[QUOTE=tseliot]Try my script (use the "install" function), it should solve the mismatch:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")[/QUOTE]

I would, but I have a wireless card, and it may need the restricted modules, so I'd rather not chance it.

Sean

---

### Post by gborzi on 2006-06-26
[QUOTE=shendric]Ok, let me see if I get what you're suggesting in the right order:

stop gdm (how?)[/QUOTE]
With this command: > sudo /etc/init.d/gdm stop this should kill Xorg, check that it is really stopped (sometimes it can freeze), using > pgrep Xorg if this command gives a number Xorg is still "alive" and you have to kill it with > sudo pkill -9 Xorgif pgrep says nothing, Xorg is killed.

[QUOTE=shendric]sudo modprobe -r nvidia[/QUOTE]
ok, in case it complains the module is not loaded, don't care.
[QUOTE=shendric]
Uninstall the latest drivers (I'm not sure how to go about that)[/QUOTE]
Well, this depends on how the libglx.so.1.0.8756 ended up in /usr/X11R6/lib/modules/extensions/ . If it was due to an attempt to use the NVIDIA-Linux-x86-1.0-8756-pkg1.run file provided by NVIDIA, use this same file to issue the command > sh ./NVIDIA-Linux-x86-1.0-8756-pkg1.run --uninstall
If this is not the case, I need to know how the libglx.so.1.0.8756 was installed in your system in order to help. If you don't know, don't do this step and hope for the best.
[QUOTE=shendric]
Check(?) the packages nvidia-glx, nvidia-kernel-common, linux-restricted-modules-'uname -r', linux-restricted-modules-common and nvidia-settings[/QUOTE]
In case debsums is not installed, install it with > sudo apt-get install debsums and use it simply by typing > debsums -a <package name>
[QUOTE=shendric]
reinstall the above packages.[/QUOTE]
You need only to reinstall the broken ones.

[QUOTE=shendric]
Sorry to be so dense, but this gets into areas I'm not as proficient with, and I want to make sure I don't mess anything up.

Sean[/QUOTE]
Don't worry, it's better to be safe than sorry !

---

### Post by shendric on 2006-06-26
[QUOTE=gborzi]
Well, this depends on how the libglx.so.1.0.8756 ended up in /usr/X11R6/lib/modules/extensions/ . If it was due to an attempt to use the NVIDIA-Linux-x86-1.0-8756-pkg1.run file provided by NVIDIA, use this same file to issue the command 
If this is not the case, I need to know how the libglx.so.1.0.8756 was installed in your system in order to help. If you don't know, don't do this step and hope for the best.
[/QUOTE]

I installed the latest drivers recently using Synaptic.  I haven't installed them from the NVIDIA site.

Sean

---

### Post by shendric on 2006-06-26
Ok, I may have gotten some ideas on this.  It appears that the 8756 drivers were installed by the manufacturer of the laptop using the NVIDIA drivers from the site, as I found the NVIDIA-Linux-x86-1.0-8756-pkg1.run file on the machine.  So, when I tried to install the latest nvidia drivers from Synaptic, I was installing the 7667 ones, rather than the newest ones from NVIDIA.

Should I just uninstall the Synaptic packages and re run the NVIDIA .run file?

Sean

---

### Post by gborzi on 2006-06-26
[QUOTE=shendric]Ok, I may have gotten some ideas on this.  It appears that the 8756 drivers were installed by the manufacturer of the laptop using the NVIDIA drivers from the site, as I found the NVIDIA-Linux-x86-1.0-8756-pkg1.run file on the machine.  So, when I tried to install the latest nvidia drivers from Synaptic, I was installing the 7667 ones, rather than the newest ones from NVIDIA.

Should I just uninstall the Synaptic packages and re run the NVIDIA .run file?

Sean[/QUOTE]
Yes, this can work. I suppose that the prepackaged drivers didn't worked because the nvidia kernel module was that installed by the manufacturer (i.e. 8756) whereas the libraries were those installed with synaptic (i.e. 7667). However, you can also try to find the nvidia.ko module installed by the manufacturer (this should be somewhere under /lib/modules/`uname -r`/kernel), delete it and run > sudo depmod -a and use the prepackaged drivers.

---

### Post by shendric on 2006-06-26
Woohoo!

I uninstalled the drivers I installed from Synaptic and reinstalled the drivers using the NVIDIA package, and it seems to be running fine, now.

Sean

---

