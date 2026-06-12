---
title: "Error on trying to increase screen resolution"
date: 2008-10-02
forum: Multimedia Software
---

### Post by Shaddam on 2008-10-02
I just did a fresh install of Ubuntu Release 8.04.1 (Hardy) desktop version and my max resolution is 800 x 600.  I’ve installed the drivers for my oldschool 3DFX Voodoo 5500 by executing the following commands:

"sudo apt-get install libglide3"
"sudo ldconfig"

the glxgears work great.

I then tried 
"sudo dpkg-reconfigure -phigh xserver-xorg"

However, this errors out every time.  I’ve attached a screenshot of the error.  It’s SOOO annoying to have a 800 x 600 resolution.  I’ll admit that I’m an Ubuntu noob and am trying to learn all about it.  If anyone can give me some guidance as to how I can improve my resolution please let me know!

---

### Post by Shaddam on 2008-10-04
> **Shaddam said:**
> I just did a fresh install of Ubuntu Release 8.04.1 (Hardy) desktop version and my max resolution is 800 x 600.  I’ve installed the drivers for my oldschool 3DFX Voodoo 5500 by executing the following commands:

"sudo apt-get install libglide3"
"sudo ldconfig"

the glxgears work great.

I then tried 
"sudo dpkg-reconfigure -phigh xserver-xorg"

However, this errors out every time.  I’ve attached a screenshot of the error.  It’s SOOO annoying to have a 800 x 600 resolution.  I’ll admit that I’m an Ubuntu noob and am trying to learn all about it.  If anyone can give me some guidance as to how I can improve my resolution please let me know!
Can no one help me with this error?  I'd really appreciate any help :D

---

### Post by wolfen69 on 2008-10-05
```
sudo dpkg-reconfigure xserver-xorg
```(no -phigh) then restart x or reboot.

---

### Post by Shaddam on 2008-10-06
Thank you for your help wolf69!  I tried the "sudo dpkg-reconfigure xserver-xorg" and got the following error:

nathan@nathan-desktop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for nathan: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081006084046
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): No such device
nathan@nathan-desktop:~$ 

Below is an attached screenshot of the terminal window.  Any ideas on how to fix this so I can have a better resolution then 800 x 600?

Also, I've read the following posts about this and it seems I'm not the only person who hasn't gotten this question answered:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=895259](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=895259)
[http://ubuntuforums.org/showthread.php?p=5627277](http://ubuntuforums.org/showthread.php?p=5627277)

---

