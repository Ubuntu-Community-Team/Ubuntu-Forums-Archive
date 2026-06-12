---
title: "Mythbuntu Boot Problem"
date: 2011-02-07
forum: Mythbuntu
---

### Post by Sum Guy on 2011-02-07
I've recently installed Mythbuntu on a new system and I'm having trouble getting it to boot consistently. Most of the time it boots fine, but occasionally it'll drop into tty1. Switching to tty7 indicates that the system stopped loading while "Checking battery state...". Note that the system is a desktop unit, so it only has a motherboard battery.

The system is using the v4l-DVB drivers with a supported TV card (DTV-2000DS), although the drivers are those from the Mercurial driver source because I was unable to remove the FiredTV module from the newer Git driver source. In addition, it's using the proprietary NVIDIA drivers.

---

### Post by Sum Guy on 2011-02-09
I've recently come across more problems to deal with. First, one I forgot to mention before, the system occasionally fails to power down as well, dropping me into the recovery menu. A lot of the time I shut down from the command line, but I make sure to use the -P flag, and this doesn't appear to matter anyway because it failed shutting down from inside xfce as well.

The other problem is the sudoers file. I decided to finally configure ACPI shutdown, and started with the sudoers file. However, sudo visudo insists that there is a syntax error one line above the new entry. I thought this was weird, this line being a comment explaining the addition, but removing this line, and the blank line separating it from the previous entry because this also got a syntax complaint, visudo continued to complain about the syntax of the line above, the line granting administrator privileges to admins. Even if the syntax I used was wrong, why would visudo conplain about the line above (it complained about the new entry when I had the wrong syntax, and merely changed lines when it was right).

Thanks for the help.

---

### Post by Sum Guy on 2011-02-12
The system recently had a catastrophic failure related to disk space (I think), and I had to reinstall. Now, the system is using the Ubuntu non-free drivers offered in the third-party driver manager. Unfortunately, the system is exhibiting more problems than before. Now, Watch TV doesn't work, showing the loading screen and then returning to the menu. I've already changed playback modes, and it's not returning to the login screen like the normal problem associated with this option. In addition, a manual recording worked, including playback, indicating that all the required software and hardware is working.
[http://ubuntuforums.org/showthread.php?t=1683134](http://ubuntuforums.org/showthread.php?t=1683134)
Of the previous problems, at least the boot into tty1 still stands in the new install.

EDIT: The new install won't tune any channels now, including with the command line scanner I used before. I had another try at getting the v4l-DVB drivers, but when I tried to get the kernel-source for some reason the command only looked in the repository for xbmc (I added it to get xbmc). Note that I used the standard method to add this repository to the package manager (the method explained on xbmc's website). The driver instructions are below:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

As it stands I need the kernel source to use ncurses, to remove the firedtv module. If someone could tell me what I need to put in instead of <some dir with media -git tree> I could probably remove it manually, and just use the kernel-headers, plus I'm not sure ncurses would work with the build script.

Any help would be appreciated, as I've been spending months trying to get this running, and every time I have some success something goes mysteriously wrong and I have to start again.

---

### Post by Sum Guy on 2011-02-13
I've switched to the slightly older Mercurial tree (which I was avoiding earlier due to stability concerns, although I used it before when it was the only option) and my tuners are back online. I also got LiveTV working - I accidentally set it to record to a read only vfat drive, rather than the rw drive I'm using for the purpose. I'm now back to the original power problems, and preventing another catastrophic failure.

I would still appreciate input on the power problems.

Thanks

---

### Post by nickrout on 2011-02-13
You ask many questiona but you give us no information on your system, your hardware, your software versions or what your logs tell you.

---

