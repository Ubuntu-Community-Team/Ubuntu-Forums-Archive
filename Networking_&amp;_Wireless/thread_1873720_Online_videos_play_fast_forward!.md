---
title: "Online videos play fast forward!"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Friwise on 2011-11-01
Hello!
I am running Ubuntu 11.10 from the first day that it appeared.
I had some issues but I have solved all of them with the help of forums.
What happened now is that all the videos that I watch online (youtube, dailymotion etc), for unknown reason, behave like if I had chosen to be fast forward.
I cannot really watch any video because it is too fast.

Do you have any idea how to solve it and what might have caused it?

Thanks in advance

---

### Post by tybrownintn on 2011-11-02
I would love an answer to this.  I tried in chrome and also firefox.  I also installed adobe flash which uninstalled the ubuntu flash installer.  Nothing changed.  I have googled this and find the question asked many times but never answered.  Not running 64 bit.  

Suggestions?

---

### Post by tybrownintn on 2011-11-03
Went back over to Linux Mint 11, which is based on 10.04.  It is doing the same thing.  Never had the problem before so some update has done it and I assume it is a Flash issue and not Ubuntu issue.  Still, surely others are having this problem?

---

### Post by tybrownintn on 2011-11-03
Apparently this is not even just a linux problem. Report of issue on XP.  Problem is that the solution there is to update the video driver. I am using gnome 3 shell which does not work with the proprietary ati drivers.  Guess I have to choose between the two, flash or gnome 3 shell.

---

### Post by tybrownintn on 2011-11-03
Using the proprietary driver seems to have fixed the issue with Ubuntu though I was already using it with Mint so not sure what is going on.  For now, I can watch videos but I cannot use Gnome Shell...maybe they will give some ATI love later.

---

### Post by Perfect Storm on 2011-11-04
You could try this: [http://www.shainmiley.com/wordpress/?p=986](http://www.shainmiley.com/wordpress/?p=986)

---

### Post by tybrownintn on 2011-11-04
I think I will try again when the new driver comes out.   That was a great tutorial though.

---

### Post by Friwise on 2011-11-06
One day after the problem disappeared... I still don't know what was going on!

---

### Post by camelthemammel on 2011-12-10
I had the same problem and my audio was also gone. Going to sound settings > output  and switching from "Manhattan HDMI Audio" to "Internal audio" solved the audio problem and the online movies were back to normal speed.

---

### Post by harrir on 2011-12-20
> **camelthemammel said:**
> I had the same problem and my audio was also gone. Going to sound settings > output  and switching from "Manhattan HDMI Audio" to "Internal audio" solved the audio problem and the online movies were back to normal speed.

Thank you, camelthemammel! I have had this problem several time in different distros and never understood what was wrong or how to fix it. That worked. I can't believe it was that simple! Thanks!

---

### Post by harrir on 2012-01-18
> **camelthemammel said:**
> I had the same problem and my audio was also gone. Going to sound settings > output  and switching from "Manhattan HDMI Audio" to "Internal audio" solved the audio problem and the online movies were back to normal speed.

This worked great in ubuntu with the gnome/unity settings, but I'm trying xubuntu now and it does not have the sound settings > output control. Anyone have any ideas on how to fix it in xubuntu?

---

### Post by antimofeew on 2012-05-28
There is the same option in Xubuntu (XFCE). You can access it clicking the sound icon in the notification area.

---

### Post by elbakly on 2012-11-04
I have the same problem videos runs fast forward and sounds fast

my video runs normally as long as vlc was opened i dont know why

do you all have vlc installed too i'm using ubuntu 12.04 upgraded from 11 not neatly installed

---

### Post by thistrain on 2013-01-28
This can be solved by editing grub as shown in this bug fix.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)




=== Workaround 1 ===
 Edit /etc/default/grub and change this line:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 to this line
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"
 Now run "sudo update-grub", then reboot your computer.


This is for ATI radeon type audio cards.

---

### Post by martbuang on 2013-02-04
Just had the same problem with Ubuntu 12.10 64 bit. After install video played fine with Flash in Firefox and with MoviePlayer, but the next day video played very fast and with no sound for both. After reading this thread checked Sound in System settings and found Output was set to HDMI/DisplayPort, changing it back to Analouge Output which fixed the problem. It was my fault for not checking after I'd had a look at the Sound setting earlier! ](*,)

---

### Post by rosshadden on 2013-11-18
> **camelthemammel said:**
> I had the same problem and my audio was also gone. Going to sound settings > output  and switching from "Manhattan HDMI Audio" to "Internal audio" solved the audio problem and the online movies were back to normal speed.

After hours troubleshooting, searching, and attempting fixes, this ended up being my solution as well.  Thank you, and I HATE FLASH.

---

