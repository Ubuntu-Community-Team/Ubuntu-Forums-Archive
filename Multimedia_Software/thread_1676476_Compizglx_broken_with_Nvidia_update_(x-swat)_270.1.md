---
title: "Compiz/glx broken with Nvidia update (x-swat) 270.18-0ubuntu1~maverick~xup1"
date: 2011-01-27
forum: Multimedia Software
---

### Post by danzvash on 2011-01-27
GLX extension in X seems to have broken suddenly.

Running:
Maverick 64bit up-to-date
nvidia-current (x-swat ppa): 270.18-0ubuntu1~maverick~xup1
xserver-xorg-core version: 1.9.0-0ubuntu7.3

Yesterday I switched to Nouveau drivers to try and run X in realtime kernel, and then switched back to Nvidia drivers - and now Compiz is broken. Excerpt from Xorg.0.log:
```

[    21.540] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.540] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[    21.540] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[    21.540] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[    21.540] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[    21.540] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.

```

nvidia-current has updated in the process of switching drivers, to **270.18-0ubuntu1~maverick~xup1** (I have the x-swat PPA enabled).

In order to fix the GLX problem I tried rolling back to 
**260.19.29-0ubuntu1~xup~maverick3**
and also to 
**260.19.06-0ubuntu1** from the ubuntu restricted repo.

Nothing seems to make a difference. Glx is still broken:

```
root@mango:~# glxinfo 
name of display: :0.0
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x5400003
  Serial number of failed request:  31
  Current serial number in output stream:  31

```

What has happened and how can I get my GLX working again?**[B]**[/B]

---

### Post by time-trader on 2011-01-28
Same here on Lucid Lynx. Had to purge all 270.18, nvidia  and roll back to 195.36 to get it working.

---

### Post by BicyclerBoy on 2011-01-28
Backup or delete your xorg.conf file & try install nvidia driver & settings utility.

Run nvidia-settings GUI
config setup
save to xorg.conf (not really necessary for most people)
restart/reboot

post 
/var/log/Xorg.0.log
if you still have problems..

The newer ubuntu nvidia install script is meant to prevent the nouveau kernel module problem.

---

### Post by Quadunit404 on 2011-01-28
This seems to be a problem if you are using X from the X.org-Edgers PPA. NVIDIA is working on a fix for the problem last I checked the nvnews forum but did not state when the new driver will be available.

If you use X.Org Server 1.9 though your GLX is fine.

---

### Post by BicyclerBoy on 2011-01-28
Thanks for the warning.
This was mentioned in the natty forums last week.

Did not think this was going to hit 10.10 & Lucid.
(Nouveau's revenge maybe)

IIRC
The Xorg 2.0 update will break all the closed source drivers until they are re-build.
The fault is the package dependencies are wrong.

Stick with Xorg 1.9 & nvidia 260 until the smoke clears I guess.

---

### Post by murataht on 2011-03-31
Maybe I am wrong, but I have encountered a same problem, glx cannot be initialized, hence glxgear gives the error : badWindow ...

I have solved it just by directing nvidia to a correct libglx.so. I mean in my ubuntu installation, there are two libglx.so at the same directory "/usr/lib/xorg/modules/extensions" : 
1) libglx.so  --> xorg
2) libglx.so.260.19.21  --> nvidia

This caused nvidia to use the wrong glx module! 

So I have changed the xorg glx to libglx.so.xorg, and simlink a libglx.so to nvidia one. After a reboot it worked, compiz, glxgear, etc.
<code>
sudo mv libglx.so libglx.so.xorg
sudo ln -s libglx.so.260.19.21 libglx.so
sudo reboot
</code>

If you are in the situation, hope this can help you.

---

### Post by nv22nv on 2011-05-02
murataht, thanks for the hint, that solved to problem for me. 

If there's another possibile solution, I'd like to hear it. After all, the linking of the correct .so file will need to be repeated after each update of the NVIDIA driver.

Edit: Correcting myself: The nvidia installer will create the link automatically, so this won't need to be done manually after each update.

---

### Post by m.capurso on 2011-05-03
This solved the problem also for me. I made a fresh install of 10.4 on a Toshiba Satellite with NVIDIA GEFORCE4 420 GO and I had the same problems with glx.
I SOLVED it using the suggestion from MURATAHT.

---

### Post by kapitanbar on 2011-05-09
I have another driver for my Nvidia, but Murataht's solution worked OK anyways, Thank you very much!

---

### Post by mikilion on 2011-05-15
> **murataht said:**
> So I have changed the xorg glx to libglx.so.xorg, and simlink a libglx.so to nvidia one. After a reboot it worked, compiz, glxgear, etc.
```

sudo mv libglx.so libglx.so.xorg
sudo ln -s libglx.so.260.19.21 libglx.so
sudo reboot

```

This workaround don't works for me.

Architecture AMD64
nvidia-graphics-drivers 270.29-0ubuntu1~lucid~xup2 (Ubuntu X Swat stable updates)
Xorg 1:7.5+5ubuntu1
Linux 2.6.32-31-generic Ubuntu 10.04 Lucid SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

---

### Post by scottstensland on 2011-06-01
given U have an nvidia card ...  broken GXL error messages
can be fixed with a reinstall of the driver available from :

[http://developer.nvidia.com/cuda-toolkit-40/](http://developer.nvidia.com/cuda-toolkit-40/)

currently its Developer Drivers for Linux (270.41.19)

download your 32 or 64 bit 

get into a NON X terminal using Ctrl-Alt-F1

assure U remove lingering drivers. Find them using

dpkg -l | grep nvidia

these are OK (not drivers do not purge these packages) :

nvidia-cg-toolkit 
nvidia-common                   

sudo apt-get --purge remove XXXXX

see currently running X server :  ps  -eaf|grep X

kill off your X server :

sudo service gdm stop

assure its gone :  ps -eaf | grep X

install your nvidia driver 
(this is for 32 bit) :

sudo sh devdriver_4.0_linux_32_270.41.19.run

hit tab to move cursor 

say YES to backup and cut a fresh X config file

... ignore that error message ...

sudo reboot

you should be all set at this point - cheers - scott stensland

---

