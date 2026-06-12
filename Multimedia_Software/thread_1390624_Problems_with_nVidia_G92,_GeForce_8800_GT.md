---
title: "Problems with nVidia G92, GeForce 8800 GT"
date: 2010-01-25
forum: Multimedia Software
---

### Post by salttalk on 2010-01-25
I already posted this message on another thread but I'd like to start a new thread with it now, and add a few more details.

My son and I are having trouble getting the graphics card to work properly in his computer. 

The resolution is good, but the graphics card is not fully functioning. He works on animation and graphics of several kinds, and the graphics programs cannot run without a fully functioning graphics card.

The computer will not run Blender and other graphics programs. Nor will it even allow for the "normal" "Visual Effects" in the "Appearance Preferences." (It comes up with the error: "Desktop effects could not be enabled," after it tries to find the driver.)

The system is:

[COLOR="Blue"]**Graphics Card:** nVidia G92, GeForce 8800 GT
**System:** Ubuntu 9.10 Karmic, 2.6.31-17-generic, 4.4.1 (x86_64-linux-gnu)
**Processor:** AMD Athlon 64 X2 Dual Core 4200+ (3 Gigs RAM)[/COLOR]

We know the graphics card works because it works in Windows. (We set up the computer to boot off of either of two hard drives -- either in Windows XP or Ubuntu 9.10, karmic.)

Neither my son nor I understand much of the terminology on your forums, although I have been using Ubuntu for some years and have read quite a bit. (I also have the "Beginning Ubuntu Linux" book.) I love Ubuntu, but sometimes I just cannot figure out how to get some things running.

We have tried many different ways of installing the drivers and setting up the xorg.conf file. We have followed the instructions on this and other threads. We also installed NVIDIA-Linux-x86-64-190.53-pkg2.run, as well as 173 and 185.

The screen will only work at a proper resolution when we set the "Driver" to "nv" in the xorg.conf file. The screen goes completely blank and dead if we set the "Driver" to "nvidia." Then we need to reboot in safe mode and edit the xorg.conf file with VIM.

When we set the driver to "nv," the Xorg log shows only this one error:

[COLOR="Blue"](EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)[/COLOR]

But when we set the driver to "nvidia," the Xorg log gave the following errors before the screen went dead:

[COLOR="Blue"](EE) Jan 20 16:04:32 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jan 20 16:04:32 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jan 20 16:04:32 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/COLOR]

I don't understand this because, with the "nvidia" setting, it says it successfully loads the driver:

[COLOR="Blue"](II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.18  Wed Jul 22 16:35:50 PDT 2009
(II) Loading extension GLX[/COLOR]

I have tried the "How to Install nVidia driver" thread and just about everything else I can find. Will this nVidia card even work on Karmic?

I just reinstalled EnvyNG and ran it to install the video drivers. It didn't work and the screen went dead again. So I had to change the "Driver" in the "xorg.conf" file to "nv" again to be able to see the screen.

However, this time the "Xorg.log" seemed to give a different set of errors:

	[COLOR="Blue"](II) LoadModule: "glx"
	(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
	dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000025gl
	(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
	(II) UnloadModule: "glx"
	(EE) Failed to load module "glx" (loader failed, 7)

	...

	(**) NVIDIA(0): Enabling RENDER acceleration
	(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
	(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
	(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
	(EE) NVIDIA(0):     you continue to encounter problems, Please try
	(EE) NVIDIA(0):     reinstalling the NVIDIA driver.[/COLOR]

After it says "resource ranges after preInit" and makes a list of memory addresses, it says the following and dies:

	[COLOR="Blue"](II) NVIDIA(0): Initialized GPU GART.
	(II) NVIDIA(0): Initialized GPU GART.[/COLOR]

Thanks. Hope to hear from someone.

---

### Post by NT4usB on 2010-01-26
More on envy.
Did you first select the option to completly remove the nvidia driver first? Then, after all the old stuff is cleaned out, install?
This has worked for me in the past.

---

### Post by Dynamus on 2010-01-27
[http://lovehateubuntu.blogspot.com/2008/03/ubuntu-and-geforce-8800.html](http://lovehateubuntu.blogspot.com/2008/03/ubuntu-and-geforce-8800.html)
this might help I'm about to try it.

---

### Post by knighthaq on 2010-01-27
[http://ubuntuforums.org/showthread.php?t=990978 ]("http://ubuntuforums.org/showthread.php?t=990978")

Try this link i have a gtx 260 and used these current drivers with these instructions worked well however i did have to change permision settings manually to keep my settings the way i wanted
[]("http://ubuntuforums.org/showthread.php?t=990978")

---

### Post by salttalk on 2010-01-28
Hi. Thanks for the replies.

Well, I have gone to the Synaptic Package Manager to uninstall everything nVidia-related. I also uninstalled from the prompt (nvidia-uninstall) and I always tell the installation program to delete any files if it finds any. I have installed every way possible, without any success.

(... Although every time an nvidia program installs, it seems to install successfully, without any indication that anything went wrong, until I reboot and the screen dies.)

I did notice a couple of things on the one thread. He mentioned "Get the pkg1," and I could only download "pkg2" of both the 190.53 and 195.30 versions, 64 Bit. But I don't think that could make any difference, since there was no "pkg1" for the 64-bit.

I actually think the GeForce 8800 GT is not supported by any nVidia drivers for 64-bit machines. So I guess my son will not be using Blender 3d on linux.

I need to give up for the moment. (I have too much other work to do right now.) But I'll try again sometime soon.

But thanks again for your help.

---

### Post by IllegalCharacter on 2010-01-28
> **salttalk said:**
> I actually think the GeForce 8800 GT is not supported by any nVidia drivers for 64-bit machines.
I'm not sure what you mean, I'm using that exact card on my 64-bit box, with Karmic kernel version 2.6.31-17-generic.

I'm not sure what repos you're using, but 190 and 195 are not available for me. Try installing the nvidia-glx-185 and nvidia-settings packages, then enable the new driver from System->Administration->Hardware Drivers. It will probably ask you to reboot, don't do it! Try going to a terminal (Applications->Accessories->Terminal) and typing:
```
sudo nvidia-settings
```Click "X Server Display Configuration" and try clicking Reset and then Save to X Configuration File. It sounds to me like the settings have been tweaked and might be a bit messed up. You don't need to play with the xorg.conf file to get this card working.

---

### Post by salttalk on 2010-02-04
Hi. I just wanted to update this thread to say we have tried a number of things over the last little while, including suggestions here. Nothing has worked.

Since others have similar systems which work with the same video card, I think our card must have a glitch in it. Even though it works when we boot in Windows, it could have just enough of a glitch that it will not work in Ubuntu.

As I mentioned before, it does provide a clear picture, good resolution on the monitor. It just will not run Blender and other 3D applications. So, we can live with that. We can run Blender in Windows, although it is always preferable to run it in Ubuntu, if one can.

Again, thanks for all your help.

Greg

---

### Post by VisionaryVanGogh on 2010-02-21
Hi everyone, I have the same version of Ubuntu (Karmic) and the same video card (nVidia GeForce 8800 GT). I've been having the same problem.

I've tried a lot, and no solution seems to be working. Not having a graphics card is really difficult, because I can't use Blender and some other programs. 

I've also tried the suggestions in the thread here, and nothing has helped. I'm still getting a blank screen.

---

### Post by sx-1 on 2010-04-16
I'm new to Linux and I'm also having problems with G92 and nvidia driver. I Installed 195.36.15 from nvidia website. The drivers are installed and loaded when run as root. But not loaded when run as user. Drivers don't show up in System-Administration-Hardware Drivers wizard. But I've ran a Benchmark file downloaded from 
[http://blenderartists.org/forum/showthread.php?t=136371&highlight=quadro](http://blenderartists.org/forum/showthread.php?t=136371&highlight=quadro) 
and the results when running as root are comparable to those listed on the above page. But when run as user they are about 80% slower. I've uninstalled compiz and nothing is running in the background.  I.ve not resolved the problem, But I don't think its with x-config or the drivers. The drivers should already be loaded at runlevel 1. Well they must be if I can run them as root. Being a newbie I can only speculate that a user ini file isn't pointing to the drivers or is pointing elsewhere. As far as I know linux registers the gpu, i.e. G92 G84 etc., and not the brand/version so I don't think its a problem with 8800 or 9800 or whatever. No one has mentioned running as root and whether it makes a difference perhaps you might try as we may have the same problem.

---

### Post by IllegalCharacter on 2010-04-17
Hi sx-1, you're best just to use the drivers that come in the Ubuntu repository. You can install them by going to System->Administration->Hardware Drivers and enabling the latest Nvidia ones.

---

### Post by sx-1 on 2010-04-17
Update. when I ref., benchmarking blender I mean 2.49a. I've used 2.5 but it runs like a pig. If I turn on VBO's it crashes and won't start again because the prefs are saved to a .B25.blend file (hidden) in the home folder. If I delete the file, blender 25 will work. Everything runs well when I run as root.
viz; Grub Boot Loader/Recovery mode/drop to the root shell/ startx. Using Ubuntu drivers doesn't make much of a difference. The drivers are loaded otherwise I would get a message on start up like 'can't find drivers. Ubuntu running in low resolution mode'. Something happens between runlevel 1 (root) and runlevel 3 (usr) which causes ubuntu to stop accessing all of the drivers functions. If I log on as root and then log on as usr (Telinit 3), the system runs DKMS autoinstallation services. DKMS loads the graphics drivers but it won't load the extensions, like nvidia glx.

---

### Post by sx-1 on 2010-04-19
@saltalk. I've temporarily solved my problem by running blender from a root shell. It seems that when blender starts it invokes nvidia which tries to load nvidiactl. nvidiactrl is locked and won't run. Check this for yourself by opening a terminal and typing blender. Check the output from the terminal. Then try typing sudo blender and see if it resolves the problem. If it does you'll either have to change permissions for nvidiactl and any other files that prevent the driver extensions from running or continue to load blender from the terminal

---

### Post by gijoe50000 on 2010-04-30
I have the same problem!
I think it may have something to do with x, i went to the command line, after the error occured and ran restart x and it worked, temporally, but when i restarted it was the same thing.
 
I had the problem before and i somehow found a different program to automatically generate a new xconf file for me and it worked, but i cant remember what i done.
 
another idea might be to edit the xconf file and manually enter your display mode'
for example:
 
 --mode=1600x1200

---

### Post by gijoe50000 on 2010-04-30
when i get the "nvidia kernel module failed to load"  error on startup:...

 I go to console and type

      sudo nvidia-xconfig

(and then..)

      startx

i get a normal boot!!
 I am assuming that my xconf file is ok since it then boots normally.
anyone got any ideas?
 is it a startx problem? 
why does it load normally when i startx again? 

I dont want to do this every time i boot!!

---

### Post by pyite on 2010-08-14
I am having this same error!

I was using a 260GTX with the drivers from the NVidia site; but I went back on the wagon from WoW and switched to an 8600GT and the default drivers.

I'll bet there is something lingering from the NVidia site drivers.   Customized install procedures (including "make install") are simply satanic!!

The steps I'm going to try to fix this are:

1) Finding an uninstall procedure for the custom drivers
2) Removing anything on the filesystem containing 190.53 (the version of said drivers) and re-running ldconfig.
3) Giving up and trying the latest drivers from their site.

---

### Post by pyite on 2010-08-14
Ugh, looks like the nvidia driver replaced all of the symlinks from the original .deb; for example:

(how TF do you do fixed width fonts or something like a <pre></pre> tag?)

soam / # locate libGLcore | xargs ls -l
lrwxrwxrwx 1 root root       22 2010-04-14 21:32 /usr/lib32/libGLcore.so -> libGLcore.so.185.18.36
lrwxrwxrwx 1 root root       19 2010-03-20 21:19 /usr/lib32/libGLcore.so.1 -> libGLcore.so.190.53
-rw-r--r-- 1 root root 16118572 2009-11-10 00:14 /usr/lib32/libGLcore.so.185.18.36
-rwxr-xr-x 1 root root 17368612 2010-03-20 21:19 /usr/lib32/libGLcore.so.190.53
lrwxrwxrwx 1 root root       19 2010-04-14 21:32 /usr/lib/libGLcore.so.1 -> libGLcore.so.190.53
-rw-r--r-- 1 root root 18972488 2009-11-10 00:14 /usr/lib/libGLcore.so.185.18.36
-rwxr-xr-x 1 root root 20713400 2010-03-20 21:19 /usr/lib/libGLcore.so.190.53

So let's see how many of these I may potentially have to deal with:


soam / # locate 190.53
/root/NVIDIA-Linux-x86_64-190.53-pkg2.run
/usr/lib/libGL.so.190.53
/usr/lib/libGLcore.so.190.53
/usr/lib/libXvMCNVIDIA.so.190.53
/usr/lib/libcuda.so.190.53
/usr/lib/libnvidia-cfg.so.190.53
/usr/lib/libnvidia-tls.so.190.53
/usr/lib/libvdpau.so.190.53
/usr/lib/tls/libnvidia-tls.so.190.53
/usr/lib/vdpau/libvdpau_nvidia.so.190.53
/usr/lib/vdpau/libvdpau_trace.so.190.53
/usr/lib/xorg/modules/libnvidia-wfb.so.190.53
/usr/lib/xorg/modules/extensions/libglx.so.190.53
/usr/lib32/libGL.so.190.53
/usr/lib32/libGLcore.so.190.53
/usr/lib32/libcuda.so.190.53
/usr/lib32/libnvidia-tls.so.190.53
/usr/lib32/libvdpau.so.190.53
/usr/lib32/tls/libnvidia-tls.so.190.53
/usr/lib32/vdpau/libvdpau_nvidia.so.190.53
/usr/lib32/vdpau/libvdpau_trace.so.190.53


Yuk!  Have I mentioned that customized installs are bad news, and cause excessive re-installs?

---

### Post by pyite on 2010-08-17
OK I have a script to clean up bogus NVidia libraries.  My original symptom was this error in /var/log/Xorg.0.log:

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000025gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


[http://knm.org/recreate_debian_nvidia_symlinks.pl](http://knm.org/recreate_debian_nvidia_symlinks.pl)

When you run it, it outputs a set of commands that will clean your system if you run them as root.  So, for example, maybe run this:

Step 1: BACK UP YOUR SYSTEM unless you don't mind re-installing

Step 2:

wget [http://knm.org/recreate_debian_nvidia_symlinks.pl](http://knm.org/recreate_debian_nvidia_symlinks.pl)
chmod +x recreate_debian_nvidia_symlinks.pl
./recreate_debian_nvidia_symlinks.pl > /tmp/fix.sh
vi /tmp/fix.sh (make sure the commands look valid)
chmod /tmp/fix.sh
sudo /tmp/fix.sh

This will search for the valid glx libraries (as reported by dpkg), and then will try to re-create the appropriate symlinks.  In my case, many of them were pointing to a bogus 190.53 install that was no longer valid.

Please let me know if things work out for you (or if you have some bugs to report :D

This made X work for me (got rid of the above mentioned errors).

Good luck!
Mark

---

