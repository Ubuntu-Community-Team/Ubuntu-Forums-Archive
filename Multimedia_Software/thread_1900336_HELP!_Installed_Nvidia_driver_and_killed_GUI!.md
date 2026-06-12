---
title: "HELP! Installed Nvidia driver and killed GUI!"
date: 2011-12-26
forum: Multimedia Software
---

### Post by hungryghost on 2011-12-26
Hi,about a week ago I installed 10.10 as a dual boot with XP on my laptop.This came after my previous attempts to install 11.10 came to a sticky end when I tried to install Nvidia drivers. It asked for a reboot and then the screen died and wouldnt respond (or so I thought at the time)


      Now I've foolishly done the same thing again! I'm kicking myself. Last night I was exploring the 'appearance' settings, and tried to switch from 'No visual effects' to 'Normal'. It told me I needed to install proprietry Nvidia drivers. I followed the prompts and downloaded and installed them, and restarted as it asked me. (even though I had slight misgivings I thought that the last install just had had problems; this one seemed fine)

     After the restart, it went through grub menu, brief purple screen, then laptop screen switched off! But luckily, I had the TV connected as a second monitor, and so Ubuntu booted up normally on that screen.

      This is where I made my big mistake. Instead of accepting that the Nvidia drivers were causing problems and removing them while I still had chance, I tried to get laptop screen to activate. 

     Went to System>Preferences>Monitors. It told me that this option was not supported and to try the drivers own preferences, which then appeared.

     It was a similar window, with a display showing the relative positions of the two screens. Sure enough, the laptop was marked 'disabled'. I clicked it to enable.
I was told: to complete this change you need to save the (somethingsomething)xorg? file and restart. There was a button marked save. I did this and rebooted.

    This time when the computer got past the GRUB menu, a purple screen with "UBUNTU 10.10" in worryingly blocky letteres appeared. then we went to a text login screen. Instead of the GUI all I can get is a $ prompt.

    I have googled this problem and there seem to be a fair few people who have experienced the same thing. Can't find a solution yet though.

    I found a (SOLVED) thread where someone had same problem. Followed their advice and typed-    sudo nano  /etc/X11/xorg.conf

   and altered the driver from "Nvidia" to "Nv" in the driver section, in the hope this would restore old drivers.
   
    I did the same thing to xorg.conf.backup.

    Nothing.


     Please can someone help me to get my desktop back! I was enjoying exploring ubuntu, now I'm stuck back in Windows XP. 

    It seems like my installation is all still there and working; just lacking its GUI. I don't want to go through rigmarole of wiping reformatting and reinstalling. (not even sure if this would work...I tried it with 11.10 and problem was still there...thats why I tried 10.10 in first place.)

     Please can someone help....thank you.

---

### Post by hungryghost on 2011-12-26
ok. Used recovery console to boot in failsafe graphics mode; and restored default.It now lets me boot up into desktop. Only remaining problem is System/Preferences/monitors still tries to take me to Nvidia menu, and I can't get TV to display from computer. How can I completely remove Nvidia driver.

---

### Post by hungryghost on 2011-12-26
OK thanks for looking, I have removed the offending driver; think I'll  live without it!

---

