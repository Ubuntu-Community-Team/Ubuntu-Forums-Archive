---
title: "[SOLVED] NVidia Pink Screen Bug"
date: 2007-12-11
forum: Mythbuntu
---

### Post by threedogs on 2007-12-11
First post and I'm trying to get everything right. I installed Mythbuntu Gutsy and I'm getting the Pink Screen of Death that I learned here was an NVidia driver bug. Some say reverting to an earlier driver might fix the problem. Below is a thread I found telling me how to do this, but it doesnt seem to work for me. Maybe step 5 is the problem? I think Mythbuntu uses XFCE not KDM or GDM. I've been searching how to stop XFCE with no luck. I would sure like some help!

url://ubuntuforums.org/showthread.php?p=3911959

1. Remove your current nvidia driver
aptitude remove nvidia-glx-new
2. download the nvidia driver
3. logoff of your session
4. switch to a different console ctrl-alt-f1
5. login and quit X
sudo /etc/init.d/(k|g)kdm stop
6. run the nvidia installer
sudo sh /path/to/NVIDIA-Linux-x86-100.14.11-pkg1.run
7. answer a few questions and you should be set.
8. either reboot or restart X
sudo /etc/init.d/(k|g)kdm stop
9. voila

---

### Post by superm1 on 2007-12-11
Before trying out that driver, i'd say you might want to try the packaged variant instead

nvidia-glx-new is the newer one
nvidia-glx is the older one


So instead, try to 

```
apt-get install nvidia-glx
```

And then reboot.

If that doesn't work, remove nvidia-glx and then stop gdm (mythbuntu uses gdm)

```
sudo /etc/init.d/gdm stop
```

---

### Post by threedogs on 2007-12-11
I did as you suggested and tried to load the old driver using apt-get. I thought it loaded, but where can I look to make sure? When I run the Mythbuntu Control Center it tells me the Nvidia restricted driver is not in use. When I click to use it, it tells me to insert the disk to load GLX-new (so I aborted).

---

### Post by superm1 on 2007-12-11
> **threedogs said:**
> I did as you suggested and tried to load the old driver using apt-get. I thought it loaded, but where can I look to make sure? When I run the Mythbuntu Control Center it tells me the Nvidia restricted driver is not in use. When I click to use it, it tells me to insert the disk to load GLX-new (so I aborted).
Well if it installed, reboot and try it (ignore what mcc is telling you).  If it didn't, then remove and use the manual method.

---

### Post by threedogs on 2007-12-12
I'm feeling real stupid, but I cant seem to follow the simple instructions in my first post. Here is what is happening...
- I mouse to the upper left "applications, quit"
- I select "log out"
- A graphical screen appears telling me I will log back in in 30 secs
- I hit "ctrl, alt, F1" , get the command prompt and log in
- About now the 30secs are up and I'm back in the graphical environment and MythTv is restarting

Do all you guys have degrees in computer science? Do I need to trade my PC in for an abacus?

---

### Post by threedogs on 2007-12-12
I finally got out of the X environment by pounding on the keyboard until the application crashed that kept restarting MythTV like a trick birthday candle. While attempting to install the older NVidia driver I got the following error.

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

So I'm missing a development tool? Maybe Is this telling me it's trying to rebuild the kernel and I don't have the proper build environment? Surely there would have been some mention of this in the instructions I'm trying to follow. I can only conclude that I'm doing something wrong, but don't know what.

---

### Post by superm1 on 2007-12-12
> **threedogs said:**
> I finally got out of the X environment by pounding on the keyboard until the application crashed that kept restarting MythTV like a trick birthday candle. While attempting to install the older NVidia driver I got the following error.

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?]("ftp://download.nvidia.com%29?") (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").

So I'm missing a development tool? Maybe Is this telling me it's trying to rebuild the kernel and I don't have the proper build environment? Surely there would have been some mention of this in the instructions I'm trying to follow. I can only conclude that I'm doing something wrong, but don't know what.

You need to install build-essential to use the module.

---

### Post by threedogs on 2007-12-12
Thanks SuperM1. You've been very patient and helpful. Im glad to know I was sort-of on the right track. I just put in an ATI9600 to replace my GeForce 6200. Dont know what effect that will have on video quality but it sure beats a pink screen! Hopefully this will stop my computer from locking up so that I can fix my three other problems...
1. LIRC control of a satellite box
2. SPDIF passthru from my D865PERL
3. Suspend/Wake so I dont have to run 24/7

I've actually been able to get LIRC working, and I've been able to get sound working, but not at the same time. I hope I can get a working installation in 2007.  Otherwise MCE2005 goes back in Jan 1!

---

### Post by threedogs on 2007-12-13
SuperM

Well, this has never happened before but with the ATI card I got everything working from a clean install in about an hour, including LIRC, SPDIF audio and suspend! Not knowing what to do with my time I grabbed another hard drive and am trying to get my NVIDIA 6200 working with the intent of documenting it for others who have the same problem.  I did the following after a clean install of Mythbuntu 7.10.

1. download the Nvidia driver to the desktop
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)
2. open synaptic, install "build-essential", close synaptic 
3. open a terminal
4. aptitude remove nvidia-glx-new (remove current driver)
5. uname -r (find the kernel version: mine is 2.6.22-14-generic)
6. sudo apt-get install linux-source-2.6.22 (puts kernel source in /usr/src)
7. cd /usr/src
8. sudo tar -xjvf linux-source-2.6.22.tar.bz2 (unpacks many, many files!)
9. sudo ln -s linux-source-2.6.22 linux
10. close the terminal
11. logoff the session (ctrl-alt-backspace)
12. switch to a different console (ctrl-alt-f1) and login
13. sudo /etc/init.d/gdm stop (to quit X)
14. cd Desktop 
15. sudo sh /path/to/NVIDIA-Linux-x86-100.14.11-pkg1.run (run nvidia installer)
16. answer a few questions and you should be set.
17. reboot

...And I get hung up on step 15 with the following error message...

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: The kernel header file '/usr/src/linux/include/linux/version.h' does not
       exist.  The most likely reason for this is that the kernel source files
       in '/usr/src/linux' have not been configured.

Sure enough, there is no version.h in that directory, though the directory does exist and does contain many files. Any ideas?

---

### Post by superm1 on 2007-12-14
> **threedogs said:**
> SuperM

Well, this has never happened before but with the ATI card I got everything working from a clean install in about an hour, including LIRC, SPDIF audio and suspend! Not knowing what to do with my time I grabbed another hard drive and am trying to get my NVIDIA 6200 working with the intent of documenting it for others who have the same problem.  I did the following after a clean install of Mythbuntu 7.10.

1. download the Nvidia driver to the desktop
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)
2. open synaptic, install "build-essential", close synaptic 
3. open a terminal
4. aptitude remove nvidia-glx-new (remove current driver)
5. uname -r (find the kernel version: mine is 2.6.22-14-generic)
6. sudo apt-get install linux-source-2.6.22 (puts kernel source in /usr/src)
7. cd /usr/src
8. sudo tar -xjvf linux-source-2.6.22.tar.bz2 (unpacks many, many files!)
9. sudo ln -s linux-source-2.6.22 linux
10. close the terminal
11. logoff the session (ctrl-alt-backspace)
12. switch to a different console (ctrl-alt-f1) and login
13. sudo /etc/init.d/gdm stop (to quit X)
14. cd Desktop 
15. sudo sh /path/to/NVIDIA-Linux-x86-100.14.11-pkg1.run (run nvidia installer)
16. answer a few questions and you should be set.
17. reboot

...And I get hung up on step 15 with the following error message...

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?]("ftp://download.nvidia.com%29?") (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: The kernel header file '/usr/src/linux/include/linux/version.h' does not
       exist.  The most likely reason for this is that the kernel source files
       in '/usr/src/linux' have not been configured.

Sure enough, there is no version.h in that directory, though the directory does exist and does contain many files. Any ideas?

This is because you are supposed to install the header files, not the source.

---

### Post by threedogs on 2007-12-14
SuperM1

Thanks. You got me going in the right direction and its working now with no pink screen. I used the following website to develop most of this checklist.

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

1. download the Nvidia driver to the desktop
[http://www.nvidia.com/object/linux_d...100.14.11.html](http://www.nvidia.com/object/linux_d...100.14.11.html)
2. open synaptic
3. mark the following for  install…
build-essential
linux-headers
pkg-config
xserver-xorg-dev
4. mark the following for removal
linux-restricted-modules
linux-restricted-modules-common
5. close synaptic 
6. open a terminal
7. aptitude remove nvidia-glx-new --purge (remove current driver)
8. sudo rm /etc/init.d/nvidia-kernel (delete this file)
9. logoff the session (ctrl-alt-backspace)
10. switch to a different console (ctrl-alt-f1) and login
11. sudo /etc/init.d/gdm stop (to quit X)
12. cd Desktop 
13. sudo sh /path/to/NVIDIA-Linux-x86-100.14.11-pkg1.run (run nvidia installer)
14. answer a few questions
15. reboot

---

### Post by rikai on 2008-02-22
sorry for reviving a bit of an old post, but for future reference, the "envy" program pretty much automates this process. it is available [here]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by SniperKIng on 2008-02-22
Its true was suffering from the pink screen when playing any video prior to listening to music (May be coincidence) i used ENVY which supports the latest drivers and i havent had the problem come back for about a week so i feel its workd.

---

