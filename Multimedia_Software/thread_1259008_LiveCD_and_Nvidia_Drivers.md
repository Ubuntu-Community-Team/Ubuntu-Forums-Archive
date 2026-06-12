---
title: "LiveCD and Nvidia Drivers"
date: 2009-09-05
forum: Multimedia Software
---

### Post by ParkerH19 on 2009-09-05
So I'm trying out the Ubuntu live cd and love it, I got all my internet drivers working now, so it's time for some pretty desktop effects to try. I downloaded the nvidia drivers and installed them, and when you restart, they're gone and so is the internet. I suspect it's because I have the Live CD running and it doesn't save anything. Is there any way that I can get the nvidia drivers working on the Live CD? Thanks!

---

### Post by starcraft.man on 2009-09-05
> **ParkerH19 said:**
> So I'm trying out the Ubuntu live cd and love it, I got all my internet drivers working now, so it's time for some pretty desktop effects to try. I downloaded the nvidia drivers and installed them, and when you restart, they're gone and so is the internet. I suspect it's because I have the Live CD running and it doesn't save anything. Is there any way that I can get the nvidia drivers working on the Live CD? Thanks!

You plan on working from a liveCD on a permanent basis? Like always on? Are ya sure? The live CD really only meant for testing and diagnostic repair. As ya like though. 

As to installing nvidia driver, ya, you can do it without rebooting. The reason it's all gone after rebooting your liveCD is that live caches to RAM, reboot = RAM flush. That's gonna happen every time ya shut off or reboot, so unless ya plan to keep it perpetually on liveCD I suggest ya install to an HDD, a default install of Ubuntu takes no more than 5 GB, excluding media files on home (unlike say Windows which balloons up real fast past 10GB with updates and office installed).

To install nvidia driver manually (what needed) follow this short easy guide, its by terminal.

```
1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

	-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
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
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

```

I removed some unneeded steps, guide is from someone else, copied it down when I was still fresh :).

---

### Post by ParkerH19 on 2009-09-06
Thank you so much for taking the time to help me! But...I think I'm going to just try using Wubi. Do you know if Wubi is compatible with Vista and Jaunty? Thank you!

---

