---
title: "No video"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by cmptrbuff on 2008-02-24
Hello. I am new to this forum and fairly new to linux.  Last night I installed Ubuntu, and have been playing around with the operating system, and installing programs and drivers . I installed the ati proprietary driver and everything was working good, until I started messing around in the system folder, and video settings.  I apparently selected the wrong video driver and now I cannot see anything on the screen.  The system told me to restart the computer, which I did, but now I have no video, but sound is working.  I cannot see anything, so as to fix the problem.  I do not have enough experience in Linux to work around this problem.  Can anyone tell me how to reset the video?  Would I need to input some sort of command line reset?  Thank you for your help ](*,)

---

### Post by overdrank on 2008-02-24
> **cmptrbuff said:**
> Hello. I am new to this forum and fairly new to linux.  Last night I installed Ubuntu, and have been playing around with the operating system, and installing programs and drivers . I installed the ati proprietary driver and everything was working good, until I started messing around in the system folder, and video settings.  I apparently selected the wrong video driver and now I cannot see anything on the screen.  The system told me to restart the computer, which I did, but now I have no video, but sound is working.  I cannot see anything, so as to fix the problem.  I do not have enough experience in Linux to work around this problem.  Can anyone tell me how to reset the video?  Would I need to input some sort of command line reset?  Thank you for your help ](*,)

Hi and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by cmptrbuff on 2008-02-24
Thanks for the info.....i will reboot and try this and respond back whether it worked or not

---

### Post by cmptrbuff on 2008-02-24
I followed the instructions, but its telling me "package 'xserver-org' is not installed and no info is available

---

### Post by overdrank on 2008-02-24
> **cmptrbuff said:**
> I followed the instructions, but its telling me "package 'xserver-org' is not installed and no info is available

Hi and it is xserver-xorg.

---

### Post by cmptrbuff on 2008-02-24
It looks like everything is working now.  Thanks for noticing my typo error.  I am now in the workspace.  Looks like i need to learn some of these command line commands.  I've been reading that learning these command line skills are a power way of getting around Linux.  Thanks for your help...I'll have to write down this fix, just in case it happens again.

---

### Post by overdrank on 2008-02-24
> **cmptrbuff said:**
> It looks like everything is working now.  Thanks for noticing my typo error.  I am now in the workspace.  Looks like i need to learn some of these command line commands.  I've been reading that learning these command line skills are a power way of getting around Linux.  Thanks for your help...I'll have to write down this fix, just in case it happens again.

Great and good luck!

---

