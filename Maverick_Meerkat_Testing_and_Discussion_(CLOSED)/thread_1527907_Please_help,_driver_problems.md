---
title: "Please help, driver problems"
date: 2010-07-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by loganfynne on 2010-07-09
I recently got a new computer, (Dell Inspiron 1440). I installed Ubuntu 10.10 in a dual boot system with Windows 7. At first I had a few problems with GRUB, and a few other things. I got through those problems, and then broke a few things, and broke both installations while trying to restore my backup data to it from my old computer. At first Ubuntu wouldn't even boot, but I fixed that problem. Now, when I boot I get an error message, 
"Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) open /dev/fb0: No such file or directory
(EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
(EE) intel(0): Failed to become DRM master.
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) intel(0): /dev/agpgart is either not available, or no memory is available
(EE) intel(0): Failed to initialize kernel memory manager
(EE) intel(0): AGP GART support is either not available or cannot be used.
(EE) intel(0): AGP GART support is either not available or cannot be used.
(EE) intel(0): Couldn't allocate video memory"

I press Enter (Mouse doesn't work).
Then I get a menu asking for actions, and if I choose run Ubuntu in low-graphics mode, it gets me to the login screen, but the login screen doesn't show any users.
If I choose reconfigure graphics, I get put into a loop, and no matter what I choose it just shows the reconfigure graphics menu again.
If I choose troubleshoot the error, it will let me do anything but edit the configuration file (The only thing that would actually help).

When I go the console, I have tried 

```
sudo dpkg-reconfigure xserver-xorg
```
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```
sudo dpkg-reconfigure xserver-xorg -plow
```

With no output at all. (I've tried this multiple times.)

Then I uninstalled xserver-xorg

```
sudo apt-get remove xserver-xorg --purge
```

Then I went to a Live CD and uninstalled xserver-xorg from the Live CD, reinstalled (To get the .deb files), and copied them to /var/cache/apt/archives on my Ubuntu partition. I then rebooted and went to the console again and ran

```
sudo dpkg -i /var/cache/apt/archives/*
```

Then I tried booting regularly (to no avail). I believe the problem to be in missing /dev files. Any way I can fix Ubuntu to boot with the drivers for my computer?

---

### Post by Mark Phelps on 2010-07-10
From your post count, it looks like you're a novice regarding Ubuntu. If that's the case, then why on earth would you be messing around with an ALPHA version of an OS?

If you really want to experiment with Ubuntu, choose a fully-developed version, like 10.04.

---

### Post by loganfynne on 2010-07-10
That happens not to be the case.

And now, after more messing around, I'm just getting a kernel panic. Here's the error message.
/sbin/init No file or folder found.
Kernel Panic

(/sbin/init is there. I've checked, it has permissions to execute and owner is root.)

I am now in the process of getting back to where I was.

---

### Post by lisati on 2010-07-10
Moved to Maverick Meerkat Testing and Discussion

---

