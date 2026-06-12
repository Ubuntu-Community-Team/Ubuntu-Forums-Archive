---
title: "No splash screen on boot-up (Gutsy Gibbon)"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by krussell on 2007-11-06
Hello :-)
I am not sure where to put this thread, it is related to boot-up splash screen.
My monitor is Samsung with highest resolution of 1024x768 @ 55 Hz.
While using the live-cd to boot, the nice Ubuntu splash screen shows fine.
BUT, when installed on the harddisk, this boot-up-splash shows something that my monitor cannot display, so instead of the splash i see blank screen and a message telling that the refresh rate is out of limit. 
I edited /boot/grub/menu.lst and put "vga=791" (this worked with Ubuntu 6.1, 6.0 !). 
I am absolutely at a loss, when booting from cd the ubuntu splash shows, but after installing in the harddisk all i see is blank screen.
Need some help on it.

---

### Post by aamod on 2007-11-06
Try waiting for some time assume the amount of time it would take until you get login screen. May be you'll get login screen.

---

### Post by dspdude2000 on 2007-11-06
I have this same problem on my laptop.  I also have maximum resolution of 1024x768.  The boot-up splash screen must be compiled into the kernel?  The kernel would have to be changed to fix this?  The log in screen comes up fine after X starts.

---

### Post by eye208 on 2007-11-06
This is easy to fix. Enter

sudoedit /etc/usplash.conf

into a terminal. Change the xres and yres values to 1024 and 768 respectively. Press Ctrl-O to save the file and Ctrl-X to exit the editor. Then enter

sudo dpkg-reconfigure -phigh usplash

Now the splash screen will use 1024x768 resolution.

---

### Post by krussell on 2007-11-06
Hello :-)
Thanks eye208.
My linux machine is not with me at the moment, i will try the solution you gave.
However, i have a feeling that it'll work.
Thanks again

---

### Post by krklabunde on 2007-11-06
I just entered these commands and it ruined my computer.  Here is the problem:
I just installed Ubuntu last night on a new slave hard drive.  Windows XP is on the master drive.
All worked fine except the splash screen as described here, and the fact that my keyboard didn't work (logitech wireless) during the screen where I select the OS to boot from.  However, the keyboard works fine before this point (in the bios).  No big deal since Ubuntu defaulted as the OS in 10 seconds.  Once Ubuntu is running, the keyboard and mouse work fine.  I will need to fix this soon since I can't select Ubuntu troubleshooting mode or Windows to boot without the keyboard being recognized.
Now that I fixed the splash screen with the commands provided in this post, I get the following error right after Ubuntu begins to load:
[INDENT]Starting up ...   [   23.991011] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/INDENT]
This never happened until the moment I rebooted after enter the commands for the splash screen.
I have no idea how to fix this.

---

### Post by eye208 on 2007-11-06
Changes made to /etc/usplash.conf will not be applied until the initramfs image has been updated. This is done when the usplash package is reconfigured.

How this could break your boot sequence is beyond me. It might have been a bug in initramfs-tools just waiting to be triggered. It would have happened anyway after the next kernel update. I entered the same command in Gutsy only a few days ago, and it worked fine, so I don't know what went wrong in your case. However, this should not happen, so it might be a good idea to file a bug report in Launchpad.

---

### Post by Gremlinzzz on 2007-11-06
install startup manager its in synaptic

---

### Post by dspdude2000 on 2007-11-06
This worked perfectly, eye208.  Thanks!

---

### Post by pmontini on 2007-11-10
The update to my usplash.conf file worked perfect!  Thanks!

(Better than Startup-Manager.  I used it on my laptop and it seems to have changed they way my computer boots.  I get 800x600 usplash and GDM)

---

