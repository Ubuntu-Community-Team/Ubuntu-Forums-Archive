---
title: "Automounting and sharing filesystems at boot"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by DrDevice on 2009-01-12
Greetings and salutations Ubuntu users!  The good doctor coming to you for a dose of advice on a small but important problem I am having.

I run a dual-boot Heron/XP machine, which Grub has kindly set to have boot off the latest Linux kernel I have installed.  Which is what I want.  Downside:  If for any reason I reboot and walk away, or the comp reboots when I'm away, it does not mount or share my drives on my network.  Just sits there on the login screen.

What I *think* I'm looking for is a script that runs at boot, before login, that runs as root and simply mounts and shares filesystems with the share names and permissions I choose.

What I need is confirmation that this method is possible, with a couple pointers to get me started.  Else a better method to do the same thing would be groovy.

Thanks for your dedication, gang!

---

### Post by superprash2003 on 2009-01-12
hope this helps [http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/](http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/)

---

