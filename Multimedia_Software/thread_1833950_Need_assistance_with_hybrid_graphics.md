---
title: "Need assistance with hybrid graphics"
date: 2011-08-26
forum: Multimedia Software
---

### Post by ad8bc on 2011-08-26
A few months ago my Lenovo U460 laptop started overheating and abrubtly shutting down when it was set to use the discrete video card (Nvidia).  This happened both in Windows 7 and Ubuntu.  It worked fine when set to use the onboard Intel graphics chip.  Unfortunately, I couldn't figure out how to switch it to the onboard mode in Ubuntu (that was version 10).
 

 Yesterday a tech came out and replaced my motherboard and video card.  Nvidia graphics work much better both in Windows 7 and Ubuntu (now v11).  But still, if I play a video long enough in Ubuntu it will overheat and shut down.  I would like to now try to switch it over to the onboard Intel graphics.
 

 I am somewhat new with Linux but I gave it the ol' college try.
 

 I reviewed this page ([https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)).  Step one was execute this command: grep -i switcheroo /boot/config-2.6.*  and the result was
 /boot/config-2.6.35-22-generic:CONFIG_VGA_SWITCHEROO=y 
 /boot/config-2.6.38-10-generic:CONFIG_VGA_SWITCHEROO=y 
 

 I assume the “y” means yes, the kernal is compiled to the correct version.
 

 However, when I execute the second step (ls -l /sys/kernel/debug/vgaswitcheroo/switch) I get the following:  
 ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory 
 This happens whether I use “sudo” or su -l or even a root login.
 

 So...  noting that the aforementioned webstite mentioned the “modeset=1” kernal option must be set, I found this site ([http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)), I followed the directions and the line was replaced with “GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"” and I did an “update-grub”.
 

 Here's the weird thing.  Then I was able to execute the commands in the first webpage to activate and switch the adapters.  The commands executed but nothing happened.  No screen flicker or nothing.  I ran the command and pretended that it worked, just in case, and ran a long youtube video and it shut down after a few minutes.
 

 Since then, I have not been able to run the switch commands (sudo, su -l, or root).  I once again get the “No such file or directory”.
 

 Any thoughts?

---

