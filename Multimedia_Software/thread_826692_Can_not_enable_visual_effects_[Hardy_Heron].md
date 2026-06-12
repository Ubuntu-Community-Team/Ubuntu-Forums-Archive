---
title: "Can not enable visual effects [Hardy Heron]"
date: 2008-06-12
forum: Multimedia Software
---

### Post by blueocean89 on 2008-06-12
Few days ago I disabled the visual effects to increase the performance and save the energy(?) and now I can not enable it anymore! It says: "Desktop effects could not be enabled" !?!? What could I do now to get it back?! or How can I "reset" it all ? ... sorry, Im new to Ubuntu!
My laptop:
Acer 4720 Intel Graphics Media Accelator X3100

Thanks in advance,

---

### Post by itix on 2008-06-13
If you go to the terminal (apps => aacessories => terminal) and type [COLOR="Green"]*compiz --replace*[/COLOR], what does it say??

---

### Post by Aryding on 2008-06-16
I'm having this problem with my 9600GT, I had visual effects enabled and on restart lost them.

Here's what I get when I enter compiz --replace into the terminal

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: present. 
Checking for FBConfig: Error: glXCreateContext failed
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by yno037 on 2008-06-22
I Have a similar problem. I've had visual effects enabled ever since the release of Hardy Heron. I run Ubuntu off of an external drive. I plug the hard drive at work because Windows was having trouble. It worked, but it asked me to install an nVidia restricted driver. When I tried to run ubuntu back to my laptop the display was messed up (it was running 800X600 but I got that fixed). But I cant get the visual effects fixed. or AWN... this is the output of compiz --replace :

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/home/XXX/.themes/OS-X Leopard/gtk-2.0/gtkrc:206: Unable to locate image file in pixmap_path: "Lines/line-v.png"
/home/XXX/.themes/OS-X Leopard/gtk-2.0/gtkrc:209: Background image options specified without filename

My laptop is an Aspire 5610z

---

### Post by RROY on 2008-06-22
I did this and it fixed my problem with Compiz not starting.

Run the following in a terminal (Applications -> Accessories -> Terminal)

```
sudo apt-get install compizconfig-settings-manager
```

I then restarted, and I could enable Visual Effects through:

System -> Preferences -> Appearance -> Visual Effects

I could also edit the individual Compiz settings through:

System -> Preferences -> Advanced Desktop Effects Settings

---

### Post by stwert on 2008-07-05
I'm new to Ubuntu as well, and I'm not sure if my visual effects were ever enabled, but it says they can't be enabled.
Apparently compizconfig-settings-manager is already the newest version, or already installed, but I still can't get anywhere. 
compiz --replace gives:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Thanks for your help.

---

### Post by TVC15 on 2008-07-06
Hello all,

Same problem here! 
"desktop effects could not be enabled", although I have the latest restricted drivers up and running.

My card is Nvidia 7800GS 512MB AGP.  Ubuntu 8.04

All help and tips are welcome.


Thanks,

Johan

---

### Post by overdrank on 2008-07-06
> **TVC15 said:**
> Hello all,

Same problem here! 
"desktop effects could not be enabled", although I have the latest restricted drivers up and running.

My card is Nvidia 7800GS 512MB AGP.  Ubuntu 8.04

All help and tips are welcome.


Thanks,

Johan
Hi and a good place to start is here at the FAQ's
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by stwert on 2008-07-07
So I think I got it working on my own. I just went System > Administration > Hardware Drivers  and Enabled the device driver that was unselected. I don't know that much about proprietary drivers, but I guess Ubuntu didn't want to enable it automatically cause it's not really open source or supported.

---

