---
title: "nvidia graphics driver failed after upgrading to 2.6.28-16 server kernel"
date: 2009-10-23
forum: Multimedia Software
---

### Post by pythonscript on 2009-10-23
After upgrading to 2.6.28-16, server variant, my nVidia graphics driver stopped working. Because Hardware Drivers doesn't supply a driver that's compatible with the server kernel, I've always had to download the latest driver from nVidia's website and use that, which I did this time as well. However, when the x-server tries to start on boot, I get an error that the nVidia driver failed to start. Here's what I've done so far. 

In a virtual terminal, I killed all the graphical/x processes, then:

```
sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
```which completes just fine and asks me to restart. Then I get the error... this process has *always *worked for me before, so I can't figure out the problem now. Does nVidia maybe not have a driver out for this kernel yet? Any ideas how to fix this? Thanks!

EDIT:  Also, I intend to keep using the server kernel, for various reasons, on my laptop, so switching to the generic kernel simply isn't an option. My laptop's specs are in my signature.

---

### Post by ds32497 on 2009-10-23
Mine did the same thing. After upgrading the kernel to 2.6.28-16-server from 2.6.28-15 my ati driver stopped working. I've been able to go into recovery mode and uninstall the fglrx drivers and then use the xorg.conf.failsafe file to get back to semi-functionality. I've tried to make sure that all the kernel header and source files ae installed, which they did not appear to be as part of the upgrade, and then reinstall the ati fglrx drivers. Same thing. I've gone through the process booting into recovery mode and uninstalling to get basic functionality back but this is not good. From the original post this do not appear to be confined to just nvidia or ati but affects both.

HP dv2 laptop
AMD Neo processor
4 Gig of memory
Ubuntu 9.04
AMD Radeon HD 3400

---

### Post by pythonscript on 2009-10-25
Is this going to be a problem under Karmic, too? I just had this problem occur again on Jaunty when I booted today, so I tried booting with the 2.6.28*-15* server kernel, as well as the generic kernel, and neither of them worked! I can't get to any graphical interface at all... which is making life hard. Any ideas, besides just reinstalling my entire system? I can't think of anything else right now!

---

### Post by pengcar on 2009-10-25
It's so weird!
I got the same problem with my PC at home. After update to 2.6.28-16, the display driver stop working. I checked the log and found that it's seems the graphic card can't obtain a IRQ resource.
Below is the configuration of my home PC:
CPU: AMD barton 2500+
MB: Nvidia nforece2
Display card: FX5700

But today I update PC of my office, it works OK. It's a DELL Optilplex 755.

---

### Post by tomtom12 on 2009-10-29
Yes, same here. First tried to upgrade from 9.04 to 9.1 using alternate cd and my 5 yr old laptop would never start again; just flashing on some terminal screen during boot!! I had to complete format / new install. During that  I saw [fail] in Terminal output during install, when it tried to install   Nvidia. Further install went ok, but now no advanced desktop and no Nvidia drivers anywhere((( 
Should UBUNTU recommend people with Nvidia cards to WAIT upgrade till this issue is gone???

---

### Post by pythonscript on 2009-10-29
I upgraded to 9.1 with a fresh install, and when I just use the generic kernel, the nvidia drivers from Hardware Drivers work great. I haven't tried moving to the 2.6.31-14 server kernel yet; I'm waiting until Karmic gets a few more stability updates before I really tinker with my system.

---

### Post by Turtle.net on 2009-10-30
The problem persist with Karmic ... and now Hardware Drivers cannot detect and/or suggest any driver ....
What a pain :(

---

### Post by pythonscript on 2009-10-30
> **Turtle.net said:**
> The problem persist with Karmic ... and now Hardware Drivers cannot detect and/or suggest any driver ....
What a pain :(

Are you using the generic kernel or the server kernel? I switched back to the generic kernel (out of frustration) when I did a fresh install of karmic, and Hardware Drivers worked great for me. I don't think HD has ever been able to get graphics drivers that are compatible with the server kernel; at least, it wouldn't in jaunty.

---

### Post by Turtle.net on 2009-10-30
No I have the generic driver installed

---

### Post by pythonscript on 2009-10-30
> **Turtle.net said:**
> No I have the generic driver installed

Generic *driver*, or generic *kernel*? If it's the latter and you're video isn't functioning properly, then I'm not sure what the problem is with your drivers; Hardware Drivers pulled them just fine for me. What kind of video card do you have? 

```
lspci | grep VGA
```

If it's the former, then you should load the proprietary drivers from Hardware Drivers.

---

### Post by Turtle.net on 2009-10-30
```
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] 9rev a1)
```I solved my problem by desinstalling all the nvidia related drivers and applications (nvidia-settings) and I installed the latest driver (190) from nVidia website.

Now, the problem is [solved]("http://ubuntuforums.org/showpost.php?p=8198932&postcount=10").

It seems to be an incompatibility between Karmic's kernel and the official 185 driver ...

---

### Post by Turtle.net on 2009-10-30
And again, hardware drivers doesn't give anything ...

---

