---
title: "Script To Detect Attached Monitor"
date: 2008-07-20
forum: Multimedia Software
---

### Post by SuperMike on 2008-07-20
I have an Acer Extensa 4420 laptop with a VGA out jack. How can I set up my system such that when an attached monitor is connected, it detects this and uses the appropriate xorg.conf file I have for that, but when it is not connected to any separate monitor, it uses a default xorg.conf file?

I'm thinking there might be some trick with a command line X command to detect an attached monitor, and then it's just a matter of putting this in a Bash script that runs on boot.

---

### Post by SuperMike on 2008-07-21
I do know this. Some people make a startup script in their /etc/init.d folder (not an easy feat) that does an if/then check on the output from ddcprobe to see if it lists "analog signal". Well, whether I have my monitor connected or not, ddcprobe is still returning "analog signal".

But then I found I could do 'Xorg :2 -probeonly -logfile /tmp/vid.txt' and then filter on my monitor's manufacturer code (first 3 digits of it, in this case) to come back. When I did that, I found that it could probably detect when my monitor was connected or not. But when I converted this into a script, evidently it did not work because the Xorg command runs and then seems to have a problem writing /tmp/vid.txt fast enough for me to grep on it. No matter what I do, I couldn't make the script work.

---

### Post by SuperMike on 2008-07-25
I found the solution. You need to Google on how to create an /etc/init.d startup script for Ubuntu or Debian (and a recent one because this process has changed with a new bootup scheme, I think). Once you know that, you can create a script in there like 'externaltest' which looks like this:

#!/bin/bash

if /bin/dmesg | /bin/grep -i 'kernel' | /bin/grep -q xinerama; then
	/bin/cp /etc/X11/xorg.conf.ATTACHED_MONITOR_ONLY /etc/X11/xorg.conf
else
	/bin/cp /etc/X11/xorg.conf.LAPTOP-ONLY /etc/X11/xorg.conf
fi

Then, inside your /etc/X11 directory, create two separate xorg.conf files -- one for having an attached monitor, and one for standalone. That way for instance you can support Xinerama mode on one, and no Xinerama mode on the other.

Next, make a backup of your /boot/grub/menu.lst file into $HOME:

sudo cp /boot/grub/menu.lst $HOME

Next, edit /boot/grub/menu.lst. Find your two kernel boot lines -- one is regular and the other is for recovery mode. Copy those lines so that you have two sets. Now, on the second set, drop the recovery mode section because you only need one recovery mode. Next, edit the title in the second section so that it reads "Boot with attached monitor". Now, on the end of the kernel line below that title, add an option we can parse on. For instance, I added the word "xinerama" on the end of mine because this is exactly what one of my xorg.conf files will do. In your case, you can use another word, but try to make it exotic so that you don't cause the kernel to interpret it. For instance, I wouldn't call it vga or something like that because that's already an existing kernel parameter.

Next, if you didn't use "xinerama" as your kernel parameter, then go to that /etc/init.d/externaltest script and edit it such that it says this other keyword you did use.

Next, reboot and choose this. What happens is that the kernel sees that extra parameter, doesn't know what it is, and ignores it without error. Then, dmesg captures this output after boot and sees that the system was booted with that option. Then, externaltest loads and reads this and swaps out xorg.conf files accordingly.

Now, Google on how to cause your grub menu to display so that you can choose options. Otherwise, press Esc on boot when prompted so that you can display the GRUB menu. From there, choose the one for external monitor as you need to do so.

---

### Post by ag65151 on 2008-07-26
There are some fairly complex answers here. I do it more simply. Of course, if you need a different xorg.conf, then you probably need to use some of the above solutions.

For me, I switch monitors using xrandr. So I use the following:

```
#! /bin/sh

if xrandr -q |grep -q "VGA-0 connected" ; then
	xrandr --output VGA-0 --auto
	xrandr --output LVDS --off
fi 

```

Then I just run this script as a start-up app in Gnome (System -> Preferences -> Sessions -> Startup Programs tab).

You could substitute any number of xrandr calls after the if statement to set up your monitor properly. For me, turning on my VGA-0 and turning off my LVDS is enough to give me full resolution on my 19" eternal monitor.

This has to be after X has started, so if you really need to change xorg.conf, then it won't work. xrandr is supposed to be eliminating the need for messing with xorg.conf, however.

---

