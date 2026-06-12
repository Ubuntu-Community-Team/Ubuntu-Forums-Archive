---
title: "[SOLVED] Updated Ubuntu and blew out Nvidia drivers"
date: 2008-06-04
forum: Multimedia Software
---

### Post by Loki*PI on 2008-06-04
Have an Nvidia GeForce 8500 GT, running Hardy with the new release of Nvidia drivers: NVIDIA-Linux-x86-173.14.05-pkg1. 

After much pain I had the video working nicely with 12xx X 10xx resolution. Today I updated Hardy with Update Mgr. Called for a reboot. Came up in trouble shooting mode, low resolution.  Tried reinstalled drivers, had troubles, no TTY so couldn't shut down gdm. yada yada.  Back now with drivers installed but the only resolution I am able to get is 640x480 or lower.

Also Nvidia does not show up in Hardware Drivers, never has.

Suggestions to get back to a workable resolution? 

Is this going to happen with every update?

Thanks

---

### Post by glennzo on 2008-06-04
I will happen any time there is a kernel update.

---

### Post by Loki*PI on 2008-06-04
Is that because of xorg modifications or because it is a third party driver?

Thanks

---

### Post by glennzo on 2008-06-04
I believe that when you get a kernel update that often times there is a version mismatch between the kernel version and the video driver version. If you can boot back into the older kernel for a minute or two you may find that all is well there in terms of video.

---

### Post by Spleenie on 2008-06-04
I just did an upgrade and rebooted, I logged back in and could not play any 3d games :(

I had a look at the xorg.conf file and sure enough, it was a generic pos version. Somehow the upgrade had backed up my old xorg.conf file with a datestamp and replaced it (without notice) with something screwy. Replacing my old xorg.conf fixed the problem.

S.

---

### Post by Loki*PI on 2008-06-04
I was able to install the Nvidia drivers again and now have normal resolution.  Here is the procedure I followed, this is not mine, I got it from EXCiD3. 

1) Download the driver for your Nvidia Card from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
4.a) Add "nvidia" without quotes to the list.
4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
-------------------------------------------------------------------------------------------------------
If you used Envy to attempt a previous nvidia install please run this command now before you go on:

sudo dpkg -P envy

-------------------------------------------------------------------------------------------------------
If you have some old Ubuntu repository attempts installed please run this command before you go on:

sudo apt-get remove --purge nvidia*

-------------------------------------------------------------------------------------------------------
If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

sudo nvidia-installer --uninstall

-------------------------------------------------------------------------------------------------------
################################################## ##################################
##................................................ ................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................ ................................##
################################################## ##################################

CTRL-ALT-F1
8.a) Okay were in Command Line only now, we have a little left to do in here.
8.b)login:
8.c)Password:

9) sudo /etc/init.d/gdm stop
9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
11.a) Answer to the affirmative for all questions.
11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
11.c) If you somehow answered incorrectly on the last question in the installer then:
c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
Then use nvidia-settings to configure your screen by hitting Alt-F2 (or opening terminal and running this:
Code:

gksudo nvidia-settings

I had to do both the pruge nvidia and the uninstall to clean things up.  Video seems to be fine now, until the next the update.

---

