---
title: "Problem With GLX and NVIDIA"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by dingansich on 2007-04-17
After getting the Nvidia drivers installed, and my system running with a reasonable screen rez, the NVIDIA X Server Settings pannel is still reporting:

The OpenGL extension 'GLX' is not supported by
the X server or there was a problem retrieving
GLX information from the X server.

Some hunting around in the forums led me to pop open my xorg.conf file to add:

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

to it, but it was already there.  So I rebooted figuring maybe this hadn't taken for some reason, but no go.  My xorg.conf file looks ok as far as I know, and I'm still getting the error.

I took a look in my Xorg.0.log and found this:

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000038gl
(EE) Failed to load /usr/lib/xorg/modules/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

and then later:

(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

Ok ... I'm a little new at this, and wrestling with the NVIDIA driver was a pain.  How do I know if the GLX module loaded is the NVIDIA GLX module?  (Looking in /usr/lib/xorg/modules I see to modules that look to be nvidia related, but neither indicate an association with GLX.)

I'm running an Athlon 64 3200+ system, 1 GB of RAM, NVIDIA 6600 GT w. 128 MB RAM on Edgy.  Any help is appreciated.

---

### Post by Inigo Montoya on 2007-04-17
The kernel module that needs to be loaded to use the nvidia driver is called nvidia. You can check if its loaded by typing the following command in a console window
```
lsmod | grep nvidia

```
The output should be something like this
```
nvidia               4714708  22
agpgart                33456  2 nvidia,amd64_agp
i2c_core               22288  3 i2c_ec,nvidia,i2c_viapro
```
The first line tells you that the kernel module nvidia is loaded and used.
If that should not be the case you can try to load the kernel module by typing
```
sudo modprobe nvidia
```
If that returns no output the module is loaded correctly. Restart your Xorg (there is an option in the dropdown menu of the login screen) to see if it works.
If it doesn't work please post the returned error message and in addition the newest entries in your /var/log/messages log file.

greetings
im

---

### Post by dingansich on 2007-04-17
Thanx for the fast reply!  Ok, so I threw "lsmod | grep nvidia" into a console, and this is what I got:

```

nvidia               7774104  16 
i2c_core               29312  3 i2c_ec,nvidia,i2c_nforce2
```

So I'm missing that second "agpgart" entry.  Is that something critical?

Anyhow, I ran the modprobe anyway to see what would happen, and I got no errors.  It returned me to a prompt without spitting anything out.  I checked /var/log/messages, and there's nothing in there (just a -- MARK -- entry for about 4 minutes before I ran the modprobe).

Thanx again for the quick reply.

---

### Post by Inigo Montoya on 2007-04-17
There seems to be no problem kernel module wise. That's good.
Your Xorg log says
```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000038gl
(EE) Failed to load /usr/lib/xorg/modules/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
```
On my installation libgl.so is placed in /usr/lib/xorg/modules/extensions/.
So you should look up where yours is with:
```
find /usr/ -iname libglx.so
```
If libglx.so is placed in /usr/lib/xorg/modules/extensions/ you could change your xorg.conf by adding
```
ModulePath "/usr/lib/xorg/modules/extensions/"
```
to the Files section.
:-k
Guess the above wont work. Sorry.
How did you install your nvidia driver? Did you get the ubuntu package or did you install "on your own"?
What's your setup anyway (k/x/ubuntu version, video card, monito(s) asf.)?

---

### Post by dingansich on 2007-04-17
I'm running Edgy (Ubuntu 6.10).  My video card is an NVIDIA GeForce 6600 GT (128 MB RAM), and my monitor is a DELL 2005FPW (LCD Wide-screen).

I installed the NVIDIA driver by grabbing it from the NVIDIA website and manually installing it.  The one provided through the Ubuntu repositories doesn't seem to work with Edgy (it throws some kind of kernel version mismatch error if I remember correctly).  Anyhow, the manual install was a pain, but it looks like I may have to go through it again.

Thanx again for the help.

---

### Post by dingansich on 2007-04-17
FIXED!

I reinstalled the NVIDIA driver (the one provided from their website: NVIDIA-Linux-x86_64-1.0-9755-pkg2).  I didn't bother to uninstall the existing driver (which was ostensibly the same anyway - seeing as how I had already installed this driver once before), but the installer handled that anyway.

I did a default installation, allowing the installer to prompt me through the process without changing anything (other than specifying that I wanted the nvidia-xconfig utility run when asked).  And now my GLX Information panel shows a properly configured video card!

Honestly, I don't know what the problem was, but I guess, if you encounter something like this, try reinstalling the driver.

Thanx for all the help Inigo (I swear I did not kill your father :D )!

---

### Post by Radamand on 2007-04-20
Just wanted to add my thanks as well.  I was having the same problem after upgrading to Feisty, I reinstalled my NVIDIA drivers and viola!

Thanks!

---

### Post by skynexus on 2007-04-21
Recently upgraded to Feisty and had the same problem (as described by post #1). The original Nvidia driver was installed prior to the upgrade. I am fairly confident this problem occurs when upgrading to Feisty while having the original driver already installed (for example, I found two different versions of libglx in /usr/lib/xorg/modules).

Tried re-installing the original Nvidia driver and it complained about missing kernel sources. Rather than trying to figure out what to install, I decided to remove the original Nvidia driver and reinstall nvidia-glx:

```
(press Ctrl-Alt-F1)
sudo /etc/init.d/gdm stop
sudo apt-get remove nvidia-glx
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run --uninstall
sudo apt-get install nvidia-glx
sudo /etc/init.d/gdm start
```

This worked for me.

I have installed Feisty from scratch and it is marvelous, including installation of restricted drivers with Nvidia. Unfortunaly, I suspect those upgrading from Edgy with the original driver might experience this problem with the GLX extension.

---

### Post by skynexus on 2007-04-21
I would just like to comment on my previous post. Re-installing nvidia-glx was problematic. Specifically, apt-get failed to remove the package, and this turned out to be a problem with compiz that resulted in a white screen when switching on Desktop Effects (other OpenGL applications seemed to work fine). The error message was as follows:

```
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
```

To solve the problem, I manually removed the offending file that seemed to confuse apt-get. Then, I could re-install nvidia-glx, and that solved the problem with compiz. The whole procedure was:

```
sudo /etc/init.d/gdm stop
sudo rm -f /usr/lib/libGL.so.1.2
sudo apt-get remove nvidia-glx
sudo apt-get install nvidia-glx
sudo /etc/init.d/gdm start
```

Just for the record, before that, I tried installing the original Nvidia drivers again (the ones you download from the Nvidia site), now using the latest version, but had the same problem as before (no linux sources found).

Well, I hope this helps.

---

### Post by gigahz on 2007-08-12
> **dingansich said:**
> Some hunting around in the forums led me to pop open my xorg.conf file to add:

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

**[COLOR="Red"]This helped me, too.[/COLOR]** Ubuntu 7.04 kernel 2.6.20-16-generic with a 10de:0028 "nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)".

At some point, I ran the nvidia supplied "NVIDIA-Linux-x86-1.0-7185-pkg1.run" but I'm not sure whether that's the one in use right now. 

This is what seems to be installed; Restricted Drivers Manager tells me it's green, enabled and in use...

```
arno@arno-desk:~$ dpkg -l |grep nvidia
ii  nvidia-glx                                 1.0.9631+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-legacy                          1.0.7184+2.6.20.5-16.29                NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
```


the following was in my xorg log, after saying that nvidia driver loaded OK:

```
(EE) GLX is not supported with the Composite extension
```

So I figured the Composite extension made trouble here. Wow, didn't know my card had one...

I added the quoted lines to the end of /etc/X11/xorg.conf and hit CtrlAltBksp,

---voilà ! glxinfo showed good things and glxgears a framerate of about 500 :)

---

