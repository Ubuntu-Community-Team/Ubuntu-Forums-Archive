---
title: "How to make the TNT2 run with Composite WM"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by jbtito03 on 2006-12-16
Hello everyone

**I am startig this thread with the goal to make the riva TNT2 card work with XGL/AIGLX and Beryl/Compiz.**

For the start if anyone has problems with the 3d function of the card here is a how to:

First install the nvidia-legacy drivers via synaptic with the kernel commons:
(Taken from [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"))

[I]Packages may be installed by right-clicking on the package and selecting Mark for Installation.

   1. Click the Search button and search for "linux-restricted-modules". You must have restricted      modules enabled.

   2.  Find the appropriate module for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8. Selecting one will also install nvidia-kernel-common. (Note: you have to select the restricted modules first because the nvidia-glx package automatically installs the i386 one - and if you have a generic kernel image, the X will not work.)

   3. Click the Search button and search for "nvidia".

   4. You will install either nvidia-glx-legacy or nvidia-glx. If your graphics card is at the end of [WWW] this list of cards (marked as "legacy"), you will need to install nvidia-glx-legacy. Otherwise, install nvidia-glx.
   
   5. If you are going to compile 3D applications, install nvidia-glx-dev.

   6. If you are running Hoary Hedgehog or Breezy Badger, then install nvidia-settings and nvidia-xconfig. DO NOT install either package in Ubuntu 6.06 LTS because it will remove nvidia-glx. These programs are now provided in nvidia-glx.

   7. Click the Apply button to install the new packages.

   8. Once Synaptic has finished applying your changes, exit the application.

   9. Select the Applications menu at the top of the screen, then Accessories, then Terminal.

  10. In the terminal window, type the following:
          * sudo nvidia-glx-config enable

If you are running Edgy, type the following instead:
          * sudo nvidia-xconfig

   11.  Close all your applications, then press Ctrl-Alt-Backspace to restart the X server. If you see an NVIDIA splashscreen after hitting Ctrl-Alt-Backspace, your drivers are properly installed.


After all this is done check out your xorg,conf file:

#sudo pico /etc/X11/xorg.conf

and add:

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection
[/I]
Now... that should do it for 3D support.

**BUT - as the composite window managers need composite extension i am looking for either a way to get the composite extension working or someone with the TNT2 card that has composite enabled and beryl/compiz woking. I read also some forum threads that got the TNT2 working out of the box without disabling the composite extension.**

On some pages it says that compiz/beryl run even on a TNT1 card and so they should run on a TNT2. 

Please all you users and dev. have your go :D

Cheers...

JB

---

### Post by energiya on 2006-12-25
> **jbtito03 said:**
> 
#sudo pico /etc/X11/xorg.conf

and add:

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection

Now... that should do it for 3D support.

**BUT - as the composite window managers need composite extension i am looking for either a way to get the composite extension working or someone with the TNT2 card that has composite enabled and beryl/compiz woking. I read also some forum threads that got the TNT2 working out of the box without disabling the composite extension.**


managed to get 3D working, but Beryl was asking for composite, so I added
> Option         "AllowGLXWithComposite" "1"
to my "Device" section in /etc/X11/xorg.conf and removed
> 
Section "Extensions" 
        Option  "Composite" "Disable"
EndSection 
when starting beryl-manager, it worked (did it?). I get this:
> 
** (beryl-manager:4498): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

but I don't know if it's XFCE4 (I'm using XUbuntu 6.10) of something else ](*,)

---

### Post by jbtito03 on 2006-12-25
Hi... 

That is exactly the problem i am facing. As far as i know (did a lot of research) it is a problem with the nvidia-legacy drivers. Composite extension is only experimental. With the newer drivers it wont work on the legacy GPUs.

Ehat card did you say u are running?


Cheers

JB

---

### Post by energiya on 2006-12-26
> **jbtito03 said:**
> 
**I am startig this thread with the goal to make the riva TNT2 card work with XGL/AIGLX and Beryl/Compiz.**


I have a Riva TNT2 M64 Pro. Tried to compile non-legacy drivers but didn't work (as expected). I'm just curious how did the Gentoo guys managed to get it working :-k 

...and... sorry about my english

---

### Post by jbtito03 on 2006-12-27
Yeah.. me too. I really dunno where the problem lies - is it the driver or the kernel? really dunno :D

---

### Post by energiya on 2006-12-30
Managed to install Ubuntu 6.10 and I get the same error, so I'm officialy done with it. Anyway, found this [link]("http://doc.gwos.org/index.php/Desktop_EyeCandy") and managed to get some nice shadows (don't need something else).

---

### Post by Didius on 2007-01-02
I have the same problem to, how can i get beryl to work (with composite on) when composite should be off to get 3D.

I hope there is an answer somewhere, i have been searching for it the last day's and haven't found anything usefull.

---

### Post by energiya on 2007-01-03
I added
> Option "AllowGLXWithComposite" "1"
to my "Device" section in /etc/X11/xorg.conf and removed
> Section "Extensions"
Option "Composite" "Disable"
EndSection
now, when starting Beryl I get a message that many more get (I think is a bug).
> beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
Look [here]("http://www.ubuntuforums.org/showthread.php?t=315869&page=2").

---

### Post by jbtito03 on 2007-01-04
Well... after a lot of research i have found out that we have to wait until the free NV drivers will be enabled for 3D and compositing...

That will bi somewhere at the end of 2007 or beginning of 2008 and even then there is no guarantee.

Anyway... i found a MX440 Geforce 4 with 64 ram and it runs perfectly :D 

Any other info yould be usefull...


Cheers

Jb

---

