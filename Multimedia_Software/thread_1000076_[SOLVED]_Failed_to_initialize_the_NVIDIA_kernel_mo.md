---
title: "[SOLVED] Failed to initialize the NVIDIA kernel module"
date: 2008-12-02
forum: Multimedia Software
---

### Post by Usufruct on 2008-12-02
Hi folks,

With the (relatively) recent update from linux kernel 2.6.27-7 to 2.6.27-9, Ubuntu fails on boot to load the nVidia kernel module.  It says something like:

```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! 
Please snsure that you have an NVIDIA device in the system and that the 
NVIDIA device files have been created properly.
```

I am running the nVidia beta driver 180.06, which I suspect might have something to do with the issue.  It boots and runs fine if I go back to the 2.6.27-7 kernel.

Can anybody point me in the right direction?

---

### Post by Usufruct on 2008-12-02
I suppose this could possibly be helpful, it's the device sections of my xorg.conf:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 350M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 350M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

```

---

### Post by element_G on 2008-12-02
all you need to do is reinstall the NVIDIA drivers for the new kernel (this has to be done everytime a new kernel is installed) I assume you know how to do this but don't hesitate to ask.

---

### Post by mlapaglia on 2008-12-02
Just re-run the installer file the original way you did it, clicking yes to all the defaults. the module will be re-compiled, and a quick sudo /etc/init.d/gdm start will have you back in gnome.

---

### Post by Usufruct on 2008-12-03
Thank you both, this solved my issue!

---

### Post by atexannamedbob on 2008-12-07
> **element_G said:**
> all you need to do is reinstall the NVIDIA drivers for the new kernel (this has to be done everytime a new kernel is installed) I assume you know how to do this but don't hesitate to ask.

I just installed intrepid and have been having this problem and its driving me crazy!!
Hey I am having the same problem but I am not sure how to fix it meaning,
reinstall the NVIDIA drivers for the new kernel, I am really new to ubuntu so sorry if this is obvious. I tried using the hardware drivers tab to reinstall the drivers from 177-173 then back to 177 but no luck.

---

### Post by atexannamedbob on 2008-12-07
Just re-run the installer file the original way you did it, clicking yes to all the defaults. the module will be re-compiled, and a quick sudo /etc/init.d/gdm start will have you back in gnome.

I also am not sure what the installer files are?

---

### Post by Gregz on 2008-12-08
The command [/etc/init.d/gdm stop] or start will not work for me.

says no directory every time.

---

### Post by element_G on 2008-12-08
> **Gregz said:**
> The command [/etc/init.d/gdm stop] or start will not work for me.

says no directory every time.

Which *buntu are you running?

Xubuntu & Ubuntu use gdm
Kubuntu uses kdm

---

### Post by Gregz on 2008-12-08
I thought  it was Ubuntu with gnome but how can I check to be sure??

Just tried both neither will work, about too reload this whole thing and if that don't work back to sucky windows for me... I don't have the time to mess with this for days....

Really don't want to reload

---

### Post by element_G on 2008-12-08
**Gregz :**
 
just to be sure, you're running the following command right? Without the [square brackets]
 
```
 
sudo /etc/init.d/gdm stop

```
 
**atexannamedbob**
> **atexannamedbob said:**
> Just re-run the installer file the original way you did it, clicking yes to all the defaults. the module will be re-compiled, and a quick sudo /etc/init.d/gdm start will have you back in gnome.
 
I also am not sure what the installer files are?
 
The best way to install the nvidia drivers is detailed in the following thread:
[http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia)
you will have to download the drivers from NVIDIA's website: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
 
note: this method will require you to reinstall the drivers everytime a new kernel is installed (which is what the OP was asking about)

---

### Post by Gregz on 2008-12-08
I did without brackets. I found one command that does work { sudo service gdm stop}. I have downloaded and tried to install 180.08  and 177.82 neither will install. Keeps telling me no kernel source.

---

### Post by element_G on 2008-12-08
That's strange that you have to use that command for gdm...
 
this command needs to be ran before you run the NVIDIA installer, it should take care of any dependencies
 
```
 
sudo apt-get install linux-headers-$(uname -r) \ build-essential pkg-config xorg-dev
 

```

---

### Post by Gregz on 2008-12-08
> **element_G said:**
> That's strange that you have to use that command for gdm...
 
this command needs to be ran before you run the NVIDIA installer, it should take care of any dependencies
 
```
 
sudo apt-get install linux-headers-$(uname -r) \ build-essential pkg-config xorg-dev
 

```


Do I type it in just like that or change uname ????

---

### Post by Gregz on 2008-12-08
I have tried to run it two ways:


james@Catfish:~$ sudo apt-get install linux-headers-$(uname -r) \ build-essential pkg-config xorg-dev
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package  build-essential
james@Catfish:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot xserver-xorg-video-ati toshset acpid laptop-mode-tools dkms
  libscrollkeeper0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@Catfish:~$ sudo apt-get install linux-headers-$(uname -r) \ build-essential pkg-config xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package  build-essential


About to give up here:cry:

---

### Post by element_G on 2008-12-08
yes, you leave in the uname -r (this is actually a command that you can run in the terminal, it tells you the currently running kernel version)
 
From your apt output it says you have the build-essential package already but just to be sure run these two commands seperately 
 
 
```
 
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install build-essential pkg-config xorg-dev

```

---

### Post by Gregz on 2008-12-08
YYYYEEEESSSSS Thank you Thank You !!!!


Changing my headers did it. went right in. I don't really know if me trying different things and it fixed multiple things or what. But its up and running. Have to admit kinda scared to reboot  lol

---

### Post by element_G on 2008-12-08
> **Gregz said:**
> YYYYEEEESSSSS Thank you Thank You !!!!


Changing my headers did it. went right in. I don't really know if me trying different things and it fixed multiple things or what. But its up and running. Have to admit kinda scared to reboot  lol

glad to hear of your success, don't give up on ubuntu just try out compiz-fusion /desktop effects. you won't go back ;)

---

### Post by tasmaniasedado on 2009-03-08
LOL
i have an acer 4520
installed ubuntu 8.10 with no updates
wifi wasnt working
got it to work but then video drivers went off
installed the new drivers and then runned the two lines posted up here, restarted and everything was almost ok, screen was buggy, changed resolution then back the the correct resolution and now its all working wonderfull

---

### Post by sinedanat on 2010-03-06
Hi!

How I solved this problem and installed nvidia driver:
See post #12 in [http://ubuntuforums.org/showpost.php?p=8925725](http://ubuntuforums.org/showpost.php?p=8925725)

---

### Post by IanW on 2010-06-01
I found another way around this - see [bug #556736]("https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/556736?comments=all") reply #6.

---

