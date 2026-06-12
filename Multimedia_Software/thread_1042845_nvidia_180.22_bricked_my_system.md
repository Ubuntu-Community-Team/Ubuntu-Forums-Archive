---
title: "nvidia 180.22 bricked my system"
date: 2009-01-18
forum: Multimedia Software
---

### Post by rv65 on 2009-01-18
I'm running ubuntu 8.10 x86_64 and I tried to install the 180.22 and I tried to do all the things to install it and now it goes to a low graphics mode. I tried to fix the xorg.conf and it's still messed up. I tried to fix and nothing is working. Any suggestions.

---

### Post by Montblanc_Kupo on 2009-01-18
You might take a look through this thread:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I had the same thing happen when I first installed 180.22... what I ended up doing was dropping to the terminal, stopping the gdm server, and running the .sh script with the "uninstall" option... rebooted... dropped to the terminal again... stopped gdm... redid the install... rebooted afterwards... and it worked. Make sure that all the dependancies and prerequisites are there... there's a list on nvidia's site where you download it that talks about it:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

I thought it screwed up My install at first too... but I was able to get it installed and back up and running. Good luck.

Also... make sure you're using the correct version... there are separate drivers for 32bit and 64bit:

[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)

[http://www.nvidia.com/object/linux_display_amd64_180.22.html](http://www.nvidia.com/object/linux_display_amd64_180.22.html)

---

### Post by rv65 on 2009-01-18
Still tried to install by that method and it's still having problems.

---

### Post by rv65 on 2009-01-18
No nvidia control panel but 1680x1050 which is nice. I have a GeForce 8800 GTS. I don't run SLI.

---

### Post by zeronothing on 2009-01-18
What I had to do to get it to works is uninstall everything nvidia before hand. if you had anything installed related to versions 177 or 173 uninstall it using synaptic. I had some left over packages still installed which messed up the 180.22 install.

---

### Post by rv65 on 2009-01-18
no nvidia files are installed. Just that 180.22 that messed up my system. Still can't get it to work right. I hope I can get this fixed soon.

---

### Post by zeronothing on 2009-01-18
what is exactly your problem. it didnt actually render my system unbootable, but it crapped up my graphics settings. see if you can uninstall it by issuing the command:

sudo nvidia-uninstall


after you issue the command you might have to reconfigure the Xorg config file. where are you stuck at with your system? it will not boot? it will boot but your stuck in commandline mode? let me know

---

### Post by hikaricore on 2009-01-18
Are you sure you removed every nvidia* package before trying to install the binary?
Not doing so can make a mess.

Also always run an uninstall before installing a new driver version.

---

### Post by Insane_Homer on 2009-01-18
My experiences so far have been with the 32-bi edition.

I had trouble with the 180.18 messing up X config and reverted back to the 180.16 which have been stable as hell.

Personally I'd revert back to your lastest but best working option.

180.16 have been stable and glitch free for me for over a month now.

180.xx are afterall Beta drivers

you getting them from here?
[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.22/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.22/)

> Chapter 3. Selecting and Downloading the NVIDIA Packages for Your System

NVIDIA drivers can be downloaded from the NVIDIA website ([http://www.nvidia.com](http://www.nvidia.com)).

The NVIDIA driver follows a Unified Architecture Model in which a single graphics driver is used for all supported NVIDIA GPU products (see Appendix A, Supported NVIDIA GPU Products for a list of supported GPUs). The burden of selecting the correct driver is removed from the user, and the graphics driver is downloaded as a single file named

    NVIDIA-Linux-x86_64-180.22-pkg1.run

***The package suffix (-pkg#) is used to distinguish between packages containing the same driver, but with different precompiled kernel interfaces. The file with the highest package number is suitable for most installations.***

Support for "legacy" GPUs has been removed from the unified driver. These legacy GPUs will continue to be maintained through special legacy GPU driver releases. See Appendix A, Supported NVIDIA GPU Products for a list of legacy GPUs.

The downloaded file is a self-extracting installer, and you may place it anywhere on your system.

---

### Post by sofasurfer on 2009-01-18
```

Also... make sure you're using the correct version... there are separate drivers for 32bit and 64bit:

```

I am running Intrepid 32 bit on an AMD 64 bit CPU. So to make sure I know what I am doing, do I want 32 bit or 64 bit Nvidia driver? The driver bit should match the OS bit, not the CPU bit?

EDIT::
Come to think of it, when I ran Ubuntu 8.04 I ran 32 bit but I don't see on the Ubuntu download page any mention of whether Intrepid is 32 or 64 bit. I thought I had 32 bit but now I am not sure.

EDIT::
I just found this...

~$ uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 15 11:03:58 UTC 2009 i686 GNU/Linux

So is this 32 or 64?

---

### Post by Montblanc_Kupo on 2009-01-18
> **sofasurfer said:**
> ```

Also... make sure you're using the correct version... there are separate drivers for 32bit and 64bit:

```

I am running Intrepid 32 bit on an AMD 64 bit CPU. So to make sure I know what I am doing, do I want 32 bit or 64 bit Nvidia driver? The driver bit should match the OS bit, not the CPU bit?

It's designed for the architecture of the OS, doesn't care what chip you have heh. Most software will just give you an error about it... but it's hard to say if a driver package would or not... especially with the black magic voodoo mumbo jumbo that's required to install 3rd party drivers into linux hehe.

---

### Post by hikaricore on 2009-01-18
> **sofasurfer said:**
> ```

Also... make sure you're using the correct version... there are separate drivers for 32bit and 64bit:

```

I am running Intrepid 32 bit on an AMD 64 bit CPU. So to make sure I know what I am doing, do I want 32 bit or 64 bit Nvidia driver? The driver bit should match the OS bit, not the CPU bit?

EDIT::
Come to think of it, when I ran Ubuntu 8.04 I ran 32 bit but I don't see on the Ubuntu download page any mention of whether Intrepid is 32 or 64 bit. I thought I had 32 bit but now I am not sure.

EDIT::
I just found this...

~$ uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 15 11:03:58 UTC 2009 i686 GNU/Linux

So is this 32 or 64?

That's 32 bit and you'll need to install 32 bit drivers on it.

---

### Post by rv65 on 2009-01-19
No nVidia Control panel :(. Whats wrong? It shows an nvidia splash screen when it boots up but no control panel in gnome. The Ubuntu drivers have the control panel. Is it not listing it in Gnome.

---

### Post by rv65 on 2009-01-19
Actually I did get it to work. Now I have to add the nvidia-settings to gnome so I can have it located there for easy access.

---

### Post by SeePU on 2009-01-20
Can someone give me the Ubuntu-specific direct link for installing the latest Nvidia driver (180.xx), please?

I've done it in Debian and wanted to try it in K/Ubuntu.

---

### Post by thugpoet22 on 2009-01-20
i had the same problem and we a few nights of tweaking and reading this forum i figured it out. Everything that has to do with Nvidia has to be uninstalled and you should completely uninstall it. Assuming that you have the correct package downloaded.

ctrl alt F1 

sign in user name and password

sudo killall gdm     if you are using Gnome    for kde im not sure

then cd to where the package is located and 

and install it sudo "package name" and pay close attention and read everything.

i hope that helps.

---

