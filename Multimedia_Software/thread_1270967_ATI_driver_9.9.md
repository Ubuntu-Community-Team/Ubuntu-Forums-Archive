---
title: "ATI driver 9.9"
date: 2009-09-20
forum: Multimedia Software
---

### Post by gsxruk on 2009-09-20
Hi all,

I just recently purchased a new PC and have installed Ubuntu 9.04 x86_64 on it this morning.  The PC has an ATI 4890 graphics card and when the FGLRX driver was enabled I got the "AMD unsupported hardware" graphic in the lower right hand corner.

After some reading it looked like there was no immediate fix, so I have tried installing the ATI driver 9.9 from AMD direct.  This has installed with no problems and seems to be working fine.

However, I remember on another Linux distro I used in the past, that when a proprietary driver is used, it creates problems when a new kernel is installed through updates.

My question is, will this still be the case here, and if so, what should I do in that event?

Thanks.

---

### Post by HavocXphere on 2009-09-20
No, shouldn't be a problem.

I've been through a few kernel updates (also running the drivers off the AMD site) & this is the first I hear about that.

---

### Post by gsxruk on 2009-09-20
Ok thanks.  I'll leave it as is and see what happens next time there's an update.

Cheers.

---

### Post by markbuntu on 2009-09-20
You will only have that problem if you have more than one driver installed, which you might have since you enabled the driver from the repository and then installed the driver from the ati site. You can use synaptic package manager to remove the fglrx driver from the repo and then reinstall the other driver if you have problems.

---

### Post by gradinaruvasile on 2009-09-20
> **gsxruk said:**
> Hi all,

I just recently purchased a new PC and have installed Ubuntu 9.04 x86_64 on it this morning.  The PC has an ATI 4890 graphics card and when the FGLRX driver was enabled I got the "AMD unsupported hardware" graphic in the lower right hand corner.

After some reading it looked like there was no immediate fix, so I have tried installing the ATI driver 9.9 from AMD direct.  This has installed with no problems and seems to be working fine.

However, I remember on another Linux distro I used in the past, that when a proprietary driver is used, it creates problems when a new kernel is installed through updates.

My question is, will this still be the case here, and if so, what should I do in that event?

Thanks.

Reinstall ur driver. Boot into recovery mode, select xfix and u should have a working X (the graphical interface). Remove the driver, then reinstall it.

The problem is created by the drivers kernel module (the module that connects the driver to the hardware) which has to exist for the running kernel (system core) AND match the kernel version. The default ubuntu drivers and those from the official repos have the kernel module pre compiled for every kernel version released and thus no need for other actions. 
   OTOH the drivers downloaded from ati/nvidia are used on different linux distributions/kernel versions, some of them not released at the time the driver is released. So they have a mechanism included in their install scripts that compiles the kernel module. So if a new kernel is installed, u have to recompile the kernel module, meaning uninstalling/reinstalling the driver.

---

### Post by gsxruk on 2009-09-23
I've wrecked everything now.

I was not too happy with how the graphics were performing.  I'm not sure whether it was configuration, but every now and again parts of the screen would turn black.  It's a little difficult to explain, but lets say I'm browsing in Firefox, the bottom half of the screen may just turn a block of black all of a sudden and then disappear when the screen is refreshed.

Anyway, I thought I would uninstall the drivers and start again.  After uninstalling the driver, I restarted the system and the screen is just a blurr now.  Can't see anything to log in.

Can somebody guide me into bringing this back to life please?

---

### Post by Melcar on 2009-09-23
- Log into a fail-safe terminal

- Rebuild X:

```
sudo dpkg-reconfigure xserver-xorg
```

- Open up your xorg.conf for editing:

```
sudo gedit /etc/X11/xorg.conf
```

- Look for the Device section and add the following option:

```
Driver  "ati"
```

- Save the file and close it

- Reboot

You should now have a functioning display on your next login.  Once logged in you can go ahead and install the proprietary driver (the one you got from the AMD website) with the following steps;

- Open a terminal and cd into the location where you have the driver:

```
 cd /[location of driver]
```

- Run the installer:

```
 sudo sh ati*.run
```

- Let it finish and once back in the terminal do the following:

```
cd
sudo aticonfig --initial
```

- Reboot your machine

You should now have a working driver.  Note that every time the kernel receives updates you are going to have to re-install the driver.

---

### Post by humphreybc on 2009-09-23
This post may be of help:

[http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)

---

### Post by gsxruk on 2009-09-24
Thanks all, very helpful posts.

---

