---
title: "Can I reinstall ALL networking aspects of Ubuntu??"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by inspired on 2009-09-13
Hi folks,
I have an issue with networking suddenly not working. Basically I have lost domain resolution on all networks I connect to. I connect to a router, can ping IPs on the internet, but can't ping or access any site by domain name (only by IP). It's all explained over here: [http://ubuntuforums.org/showthread.php?t=1263995](http://ubuntuforums.org/showthread.php?t=1263995)

I am wondering if I can simply reinstall ALL networking related stuff in Ubuntu?
In windows XP if I had an odd networking issue arise out of the blue that I could not fix, I could always resort to just uninstalling the TCP/IP stack, and all other aspects of Networking on XP. I could then reinstall them and voila... problem fixed.

I'd like to do the same on Ubuntu. I don't wish to reinstall Ubuntu has I had a system with extensive customization, applications installed, etc., and I don't wish to try and set all that up again. That's way I moved to Linux... to get away from the annual reinstall of XP I used to do.

Regards,

Jonathan

PS. I am posting this question in its own post because I am simply seeking info on how to reinstall Ubuntu networking system... not for support on my issue... that can be handled on the other thread if there are suggestions.

---

### Post by falconindy on 2009-09-14
Seems like you're bringing a shotgun to a squirrel hunt...

Linux isn't Windows. Reinstalling subsystems like this isn't something you should ever really need to do. Besides, the core of any subsystem in Linux is the kernel module and the associated driver. Anything else involved is a program that monitors or maintains aspects of your connections. In the end, these programs are really just overglorified GUIs for editing text files. If the device works but you're not getting the desired results, chances are its your config. It's less likely, but it's also possible that its your driver.

---

### Post by inspired on 2009-09-14
> **falconindy said:**
> Seems like you're bringing a shotgun to a squirrel hunt...

Linux isn't Windows. Reinstalling subsystems like this isn't something you should ever really need to do. Besides, the core of any subsystem in Linux is the kernel module and the associated driver. Anything else involved is a program that monitors or maintains aspects of your connections. In the end, these programs are really just overglorified GUIs for editing text files. If the device works but you're not getting the desired results, chances are its your config. It's less likely, but it's also possible that its your driver.
Thanks for explaining.

As far as I know, that is basically what's reinstalled on XP when I would remove networking and TCP/IP. The underlying driver for the network adapter, and the TCP/IP stack along with all its configuration settings.
I've found no pertinant information on how to sort out the configuration of my now broken networking subsystem, which is why I wanted to simply reinstall that from scratch... hoping that the default configuration would work, just as it always use to. I have no idea what changed my configuration, nor what changes where made, nor how to identify those changes, thus no idea how to reverse them. Therefore it seemed to me that the next best approach is just to wipe if clean and start from scratch. Various people have suggested a reinstall of the OS in order to fix this issue or ones similar to it. That to me seemed unacceptable... very much the shotgun approach you describe... something I don't wish to do. At least, not if I can just reinstall a clean configuration of the networking subsystem.

Have you got any tips on how to go about cleaning out the networking configuration and refreshing it? Also, how to reinstall a driver (including whatever configuration files it utilises).

With thanks,
Jonathan

---

