---
title: "Problems concerning VGA out"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by WesV on 2008-02-22
Good Evening Ya'll,
I will preface by saying that this is the first time I have used Linux in about 6 years.  I installed Gutsy a couple days ago onto my 4 year old
 Toshiba A20-S259 Laptop
Trident CyberBlade XP2 graphics card (integrated)
 P4 2.66 
768mb ram

Install went great and the last couple days have been wonderful till I decided to screw around with it today.  I wanted to run an external monitor off the DB25 port (SVGA) in the rear so when I tried going through the "Screens" menu, I couldn't get anything to happen.  I found this bit of code:
[http://wiki.eeeuser.com/ubuntu#videolcd_and_vga]("http://wiki.eeeuser.com/ubuntu#videolcd_and_vga") and decided to try it letter for letter since the Dell monitor I was hooking up supported 1024x768 (how I had it running under XP.

It took the command just fine and when I rebooted, the Dell came on with the boot sequence and then flickered and a Dell error message came up saying it does not support the specified resolution.  I unplugged the Dell, rebooted the system, got into the Gnome and check the screens again and now it had the external listed as 800x600 (I never checked after I entered the command to see what it said.)

Once again I rebooted with Dell attached figuring I would give it one more try, same thing.  Ok I disconnect again and try to reboot and now we have trouble.  It will go through the first set of boot instructions, Show the Ubuntu loading screen and then begin the next set of instructions and it starts repeating "to much load for irq11" and a blue screen pops up saying the X program cannot load due to settings, change them and try to reboot Gnome Desktop...

So I reboot and enter into the kernal through recovery mode and get to the prompt.  When I am there it and type the command to shut off the VGA port is says "can't open display"  If I try going into the /etc/X11/xorg.conf file it says "Permission Denied"

How can I fix it without having to reinstall and start over?  If there is any other spec or command you need let me know.

Much appreciation!

WesV

---

### Post by Sam Lars on 2008-02-22
You need sudo to get to xorg.conf and other system files.  If you can tell us what's in there we should be able to help you.

---

### Post by WesV on 2008-02-23
> **Sam Lars said:**
> You need sudo to get to xorg.conf and other system files.  If you can tell us what's in there we should be able to help you.

I appreciate the help

You will have to forgive the newbie-ish of this

I am under the root prompt already, isn't that the point of sudo is to get you root access?  Anyway I tried entering sudo before xorg command I listed above and returned "command not found"  Maybe I am using it incorrectly:

root@wes-laptop:~# sudo /etc/X11/xorg.conf

Is my command screwed up or is it right and I need to try something else?



edit:

Never mind, I got in with the command:
~# vim /etc/X11/xorg.conf

Will update in a moments (BTW, no sudo needed)
Thanks
WesV

---

### Post by Sam Lars on 2008-02-23
You have to use a text editor to view that file.  sudo  just opens it as root.  If your on a terminal, try ```
sudo nano /etc/X11/xorg.conf
```
If you're in Gnome, replace nano with gedit.

---

### Post by WesV on 2008-02-23
IT IS FIXED!!!!  

I went into the xorg file as described above and couldn't see anything significant in the file but I found a command through a lot of messing around within the files and configuration packages that fixed everything!

~# dpkg-reconfigure -phigh xserver-xorg

It reconfigured my setting back to original and at the end gave me a post install warning that it had over written some custom settings (the ones I screwed up presumeablly.)  I hope my experience will help someone else out too!

Thanks
WesV

---

