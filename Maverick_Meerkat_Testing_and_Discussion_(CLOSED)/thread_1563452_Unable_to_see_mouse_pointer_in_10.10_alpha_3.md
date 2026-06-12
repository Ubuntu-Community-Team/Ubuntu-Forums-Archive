---
title: "Unable to see mouse pointer in 10.10 alpha 3"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by skbhat03 on 2010-08-29
Dear All,

I am trying to install Xubuntu 10.10 (alpha 3) using a live cd.
The mdm check is fine.

Everything goes on fine except the mouse pointer.
I am able to use the arrow keys and tab button to navigate.

Can anyone please help to fix this problem.

Thanks & Best regards,
Subbu.

---

### Post by plucky on 2010-08-29
> **skbhat03 said:**
> Dear All,

I am trying to install Xubuntu 10.10 (alpha 3) using a live cd.
The mdm check is fine.

Everything goes on fine except the mouse pointer.
I am able to use the arrow keys and tab button to navigate.

Can anyone please help to fix this problem.

Thanks & Best regards,
Subbu.

You might get an answer in the Testing forum [Here](http://ubuntuforums.org/forumdisplay.php?f=385) or hit the "Report Abuse" button and get a moderator to move this thread to that forum.

Good luck

---

### Post by Mark Phelps on 2010-08-29
You're not supposed to post threads dealing with versions under development in this forum.  There are testing forums in the Development section for such posts.  This forum is for the released versions of Ubuntu, only.

Have asked to Mods to move this thread there.

In future, please post threads dealing with unreleased versions in those forums.

---

### Post by Iowan on 2010-08-29
Moved to Maverick Meerkat Testing and Discussion

---

### Post by skbhat03 on 2010-08-29
Sorry :(

---

### Post by ranch hand on 2010-08-29
Is this fully up to date?

One easy way to get it up to date is to boot to recovery and use the "dpkg fix broken packages" menu option.

I ran the upgrades from this morning and nothing broke and do not see any sign of major breakage here in the forum so it should be safe (testing upgrades always carry some risk of breakage).

---

### Post by cariboo on 2010-08-29
Are you by any chance trying to install it in vbox, as I have the same problem with the daily builds in vbox 3.8.2.

---

### Post by skbhat03 on 2010-08-30
Hi,
 
@cariboo907: I am not installing it in vbox.
 
@ranch hand: I will try the boot to recover option and try.
 
 
Thanks :)
Subbu

---

### Post by Tracy177 on 2010-08-30
i had the same problem u need to know that u have to install graphic drivers when you do that you reboot and you will see your mouse cursor again.

---

### Post by skbhat03 on 2010-08-30
Tried all options, give above, no use :(

---

### Post by mpaczynski on 2010-09-07
Hi 

I just installed Ubunty 10.10 during installation there was no mouse so I have to use tab and narrow buttons.
After Ubuntu is installed I can click mouse but there is no pointer. I tried to change it few times but nothing seems to working.
Can anyone provide step by step how to solve it?
I have HP laptop, previous 10.4 version was working with no problems.

Thank you in advance.

BR
Michal

---

### Post by azurehi on 2010-09-07
I have posted about this very problem a number of times and just about given up on any of the "buntus", as well as Mint.  I know to install Nvidia 96 after installation (installation is difficult without pointer)...but then I cannot get to desktop - "low graphics mode".  

My solution is to use PCLinuxOS - Nvidia is already installed and everything just works.

---

### Post by mpaczynski on 2010-09-08
I just experianced strange problem.When I change something in Appierance and reboot system I can see mouse, but after second reboot problem is again. So I go to Appierance and change something again. Reboot system. Mouse come again. Then next reboot mouse is gone.

Can anyone help and try to solve it befor 10.10 will be official released.

BR
Rafal

---

### Post by andrboot on 2010-09-12
Hi Guys;

I encountered the same problem on archlinux & on ubuntu 10.10, the solution is to confirm that you have xserver-xorg-video-fbdev installed & then remove xserver-xorg-video-intel & logout/restart for the changes to take effect.

^ If your Video Card is intel :P :)

---

