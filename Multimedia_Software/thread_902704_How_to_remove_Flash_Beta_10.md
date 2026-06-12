---
title: "How to remove Flash Beta 10 ?"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Browser_ice on 2008-08-27
Because of problems stated in my other [thread]("http://ubuntuforums.org/showthread.php?t=902669"), I want to remove Flash Beta 10. However, trying to look for the package name to remove, I cannot find a single one with the workd Flash in it.

How do I remove the Flash 10 Beta ?


> 
# dpkg -l | grep -i flash
# dpkg -l | grep -i adobe
ii  acroread                                   8.1.2.su1-0.0medibuntu0.8.04.1                       Adobe Reader - binary files - Medibuntu pack
ii  acroread-escript                           8.1.2.su1-0.0medibuntu0.8.04.1                       Adobe Reader - EScript plug-in - Medibuntu p
ii  acroread-plugins                           8.1.2.su1-0.0medibuntu0.8.04.1                       Adobe Reader - extra plug-ins - Medibuntu pa
ii  mozilla-acroread                           8.1.2.su1-0.0medibuntu0.8.04.1                       Adobe Reader - mozilla/konqueror plugin - Me


---

### Post by gandaran on 2008-08-28
how did you install it? by running the adobe flash installer? if that is correct then you have to delete the **libflashplayer.so** file, look for it in your hidden home .mozilla/plugins folder, if you ran the installer as root then it's installed in /usr/lib/mozilla/plugins, if you used any other method to install it could be somewhere else in the file system.

---

### Post by Browser_ice on 2008-08-28
> **gandaran said:**
> how did you install it? by running the adobe flash installer? if that is correct then you have to delete the **libflashplayer.so** file, look for it in your hidden home .mozilla/plugins folder, if you ran the installer as root then it's installed in /usr/lib/mozilla/plugins, if you used any other method to install it could be somewhere else in the file system.

I used the [procedure ]("http://ubuntuforums.org/showthread.php?t=766683")found in the sticky threads, in troubleshooting section.


[SIZE="1"]> UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY


Note: You can safely install the Ubuntu package (flashplugin-nonfree) over the top of this manual installation method at a later date, I've tested it several times. The method used below will install the plugin into the same directory the Ubuntu package does, with the same symlinks, and can be overwritten cleanly.

Install the Flash Player plugin manually by downloading the Tar archive of Adobe Flash Player v10 RC (recommended), Adobe Flash Player v10, beta 1, or Adobe Flash Player v9, the current stable/release version. Next, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then execute the following command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so[/SIZE]

---

### Post by gandaran on 2008-08-28
> sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/

well, if you used this command, then delete the /usr/lib/flashplugin-nonfree folder, no other way to remove it, (root permission need for that) use **sudo nautilus**.
if you want to play/try the various flash versions, use the hidden home .mozilla/plugins folder. its easier to install to this folder, you just extract the tar package and drag the libflashplayer.so file to the plugins folder, this is only for firefox use, for other browsers you either install in usr/lib/mozilla/plugins or the other browser plugins folder

---

