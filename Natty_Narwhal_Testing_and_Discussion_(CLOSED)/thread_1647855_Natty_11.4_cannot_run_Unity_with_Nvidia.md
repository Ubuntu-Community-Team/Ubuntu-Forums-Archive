---
title: "Natty 11.4 cannot run Unity with Nvidia"
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by toogooda on 2010-12-18
I was recently shocked by the decision to change to unity in 11.4, but as a Ubuntu supporter I wanted to give it a go before I make up my mind.
I decided to download the Alpha 1 release not to evaluate as it is too early but because I wanted to see how it look on my large full HD screen. and other than on youtube where the resolution is terrible I have never actually seen it.

I downloaded the Iso and chucked it in virtualbox only to find that virtualbox does not have the 3d support to get Unity running and has no intention at this stage to offer it. So the largest Linux distro can not be used virtually what the F% no one else shocked by this?

OK so look at the docos to see how you are supposed to test it and see that you do it via USB, so I created a usb startup disk and like every other version of Nvidia I have used on the laptop I don't get 3d effects until it has installed the Nvidia driver. So I accept the normal offered Nvidia drivers only to find it fails

```
SystemError: Failed to fetch  http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.21-0ubuntu1_amd64.deb  404  Not Found
```

So I still can't even see Unity, when I follow that path it seems it is looking for the wrong file as the closest one there is .....Oubuntu2... not 1 as above.

Has anyone with a Nvidia card actually got unity running without a full system install?

---

### Post by Jay Car on 2010-12-18
Maybe visit the Natty Narwhal Testing and Discussion thread to get more help...it's here: [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Lots of excellent information on that forum.  I know it helped me a LOT today...though my Natty installation is still pretty broken tonight.  Tomorrow should be better...or maybe next week. 

:)

---

### Post by tekkidd on 2010-12-18
Ok first of all, you are trying to install nVidia drivers from the repos which is a bad idea. Here is how to do it manually: 

All these commands are from the console (CTRL+ALT+F1)

1)Assuming the computer has internet access do: ```
wget http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run
``` for 32bit and ```
http://us.download.nvidia.com/XFree86/Linux-x86_64/260.19.29/NVIDIA-Linux-x86_64-260.19.29.run
```
for 64 bit

2)Now shut down the desktop with ```
sudo service gdm stop
``` or ```
sudo /etc/init.d/gdm stop
```

3) Now add an executable permission with ```
chmod +x NVIDIA-Linux-x86-260.19.29.run
``` for 32bit and ```
NVIDIA-Linux-x86_64-260.19.29.run
``` for 64 bit

4) Now execute with ```
./Linux-x86-260.19.29.run
``` for 32 bit and ```
Linux-x86_64-260.19.29.run
``` for 64 bit

5) Now just follow the directions to install the driver

6) When done press CTRL+ALT+DEL to restart.

Hope this helped 
Visit my blog @ tekkidd.tumblr.com

---

### Post by dcstar on 2010-12-18
> **Jay Car said:**
> Maybe visit the Natty Narwhal Testing and Discussion thread to get more help...it's here: [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Lots of excellent information on that forum.  I know it helped me a LOT today...though my Natty installation is still pretty broken tonight.  Tomorrow should be better...or maybe next week. 

:)

Users of pre-release versions must **post all issues in the relevant development forum**. **The normal forums are for released versions only** and people who use a pre-release version are told in the conditions of use to only post in the development forum.

---

### Post by uRock on 2010-12-18
> **dcstar said:**
> Users of pre-release versions must **post all issues in the relevant development forum**. **The normal forums are for released versions only** and people who use a pre-release version are told in the conditions of use to only post in the development forum.
+1 This release has more than 4 months to go before release date.

---

### Post by efflandt on 2010-12-18
The problem trying to use nvidia drivers on an iso (even on USB) is that everything is fixed during boot, so I don't even think tekkidd's method would work because nouveau would still load during boot, and then nvidia cannot load.  Although, for regular installations I have never had any video problems with nvidia drivers from the repos, formerly using a GT 220 since Maverick beta, and currently using a GT 430 that is so new that the kernel does not know what model it is yet (in lspci).

Another issue with the iso is that a persistent data "file" (casper-rw) has not been working in Natty.  But I partially partitioned USB as part FAT32, part ext2, then after using Startup Disk Creator (in Maverick) to make a current Natty USB with minimal 128 MB persistence, deleted casper-rw file and labeled the ext2 partition as casper-rw.  That seemed to work, because after rebooting Firefox remembered my history.

Some people supposedly had success installing **libgl1-mesa-dri-experimental** on the iso (you have to enable other repos to see that), and logging out and back into X.  But even with working persistent data and that package and **sudo restart gdm** or reboot, I cannot get "Try Ubuntu" to try Unity even though **glxgears** works and **glxinfo** includes:

```
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
...
(maybe due to software rasterizer?)
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9
OpenGL shading language version string: 1.20
```As mentioned, Natty development is in its early stages.  So if you want to see what it looks like, do a regular install to USB flash or hard drive, or other hard drive.  But do not expect it to be flawless yet.

---

### Post by Merk42 on 2010-12-18
> **toogooda said:**
> I downloaded the Iso and chucked it in virtualbox only to find that virtualbox does not have the 3d support to get Unity running and has no intention at this stage to offer it. So the largest Linux distro can not be used virtually what the F% no one else shocked by this?
The largest distro can not be used virtually **at this time**. 3D Support in Virtualbox **always** breaks during alphas/betas, regardless of Unity, and Virtualbox doesn't support alpha/betas. 3D, and therefore Unity, will work once 11.04 is released.

Thank you for at least making the effort to try Unity in Virtualbox/USB before passing judgement on it though.

---

### Post by ronacc on 2010-12-18
if your box supports booting from usb you can install it to a usb stick and boot from that, the resulting system is slow but useable, that way you can install the Nvidia drivers and anything else because it is  a"real" system not a " live cd" .iso  . note! INSTALL it to the usb stick ( and have grub install there so it don't mess with your existing boot files) , using startup-disk-creator and a persistant file with the .iso is not working for everyone right now .

---

### Post by cariboo on 2010-12-18
> Ok first of all, you are trying to install nVidia drivers from the repos which is a bad idea. Here is how to do it manually: 

I have to ask why you think installing nvidia-current from the repos is a bad idea.

---

### Post by Harry33 on 2010-12-18
> **cariboo907 said:**
> I have to ask why you think installing nvidia-current from the repos is a bad idea.

+1
I think it's just the other way round.
Installing nvidia-current from the official repos or from xorg-edgers for example is a good idea to get a recent version stable or beta, you name it.

---

### Post by ronacc on 2010-12-18
yeah except that right now jockey-gtk is broken , additional drivers fails . also nvidia-common fails to install which screws up the proprietary driver .

---

### Post by jerrylamos on 2010-12-18
Unity busted on IBM Thinkpad T40, as installed from CD Daily Build 20101218.  Purplish screen with cursor.  Entered a launchpad bug.

Using Install worked since it doesn't use a fancy desktop.  The installed natty booted to a purplish screen with cursor.  Much thrashing around with removing and installing compiz, gnome-panel &, etc. etc. to try to get enough of a panel to logout, log in with ubuntu classic desktop.  Running O.K. for an Alpha now.  Sure would like a boot option to choose ubuntu classic desktop.

Now this is with ati radeon graphics - what's that got to do with the persistent nvidia status 1 error that crops up on the T40?

Thanks, Jerry

---

### Post by ronacc on 2010-12-18
> **jerrylamos said:**
> Unity busted on IBM Thinkpad T40, as installed from CD Daily Build 20101218.  Purplish screen with cursor.  Entered a launchpad bug.

Using Install worked since it doesn't use a fancy desktop.  The installed natty booted to a purplish screen with cursor.  Much thrashing around with removing and installing compiz, gnome-panel &, etc. etc. to try to get enough of a panel to logout, log in with ubuntu classic desktop.  Running O.K. for an Alpha now.  Sure would like a boot option to choose ubuntu classic desktop.

Now this is with ati radeon graphics - what's that got to do with the persistent nvidia status 1 error that crops up on the T40?

Thanks, Jerry

I think a bum python is keeping jockey from running which keeps the restricted drivers unuseable , I get this error when I update with synaptics .```
Setting up nvidia-common (0.2.25) ...
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
dpkg: error processing nvidia-common (--configure):
 subprocess installed post-installation script returned error exit status 1

```
also a similar python error when trying to run jockey-gtk from term .maybe something like this is screwing up the ATI driver also .

---

### Post by toogooda on 2011-03-25
Alpha 3 solved this

---

### Post by Neobuntu on 2011-04-09
Funny that it's not working, in beta 1, then. DRI seems to be working, accept for anything (including KDE), other than Ubuntu Classic, with no enhancements. (and safe mode). Why? Again DRI is on!

Unity 2d partly works, but that is not what I want.

I'm not sure if I like Unity or not, as I'd need to see it working, with Nvidia (Geforce 7200). It would be nice, if the Beta worked.

The Noeve (whatever) had some errors, and I would be happy with that, if it surpassed the non-free Nvidia driver. ]

As usual, is this Nvidia's fault? Who knows? This is getting old, and it certainly will not win any of my friends, to Ubuntu. Since Ubuntu is now, 11.04. [http://www.ubuntu.com](http://www.ubuntu.com)

So, now you may go on about saying I'm a fool; for trying a Beta, and I should understand, that it's a Beta. This song, and dance is getting very old, my friends. Using a whole new interface (unity), requires sooner stability, and not the inevitable delay (likely now, *more* than the typical 3 months, after a "release").

---

### Post by MAFoElffen on 2011-04-09
Okay, so I know this thread was started under alpha1, which since beta1 there seems to be some changes on this...

On alpha1 on my test box here I was trying to use the older nvidia nv driver... which did work for me.  Since beata1, as of 2 days ago, there seems to be a new driver in the repo's that works just fine for me and possibly for others..  and beta1 auto-notified me that it was there.

Yes, on initial installs (with nvidia cards) initial boot of the sys would tell me that Unity was not avaiable to me and would fall back to Standard Ubuntu... but after the nvidia driver install and then running nvidia-xconfig, it would then come up fine for me.

---

### Post by Duncan Williams on 2011-04-10
As a linux newbie you probably think I am mad to install natty on my pc.
I used 10.1 for a few weeks (with nvidia 128mb ge5200), fell in love with ubuntu and was only having the odd problem with it booting up with the wrong resolution sometimes.

I am at a friends house in an isolated part of West Australia and my ubuntu installation died in transit.

I booted with winXP and decided to download natty instead of maveric as it is nearly due for release and I wanted to see what it was like (no distro disks with me-so I can put maveric back when I get home again)

Anyway, After installation it boots to a blank black screen, so,
Booted into recovery/use basic graphics for this session.
and,
It al works fine, except > graphics a bit substandard on video playback.

So,

I am pretty sure that my video card is not being recognised.
(nouvea error on recovery boot)

How can I resolve this............
Have posted in general/development forums...
Can someone help a newcomer to fix this problem (I don't want to go back to 10.10 or windows)

---

