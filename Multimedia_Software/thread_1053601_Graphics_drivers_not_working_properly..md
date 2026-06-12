---
title: "Graphics drivers not working properly."
date: 2009-01-28
forum: Multimedia Software
---

### Post by Omcon on 2009-01-28
Well, my computer specs are:

AMD Athlon XP 2000+
768 megs RAM
Two 80 GB HDD's
Ubuntu 8.04
Nvidia Integrated Graphics GeForce2 MX (I think.)
I can't figure out a way to actually find out what my graphics hardware is, so if anyone can help me out with that, too. I would be so grateful! :)


Anyhoo, whenever I enable the Nvidia hardware drivers, and reboot, all I get is a black screen with the Nvidia logo and a cursor. And nothing else. I've let it sit and load for like 5 minutes, and nothing. So then I have to reboot in recovery mode, and do Xfix. So I was curious if anyone could help. Much appreciated!

I have tried pretty much every driver package I can get my hands on. Through synaptic, I have tried the nvidia legacy package, the nividia glx package, even the envy driver downloader program thing.


Omcon

---

### Post by overdrank on 2009-01-28
Hi and welcome, You may use this command ```
lspci
``` in the terminal to identify your hardware. The terminal is located under applications, accessories.
If you have a integrated graphics I would start with bios to see how much memory is being shared with the graphics. This can hinder performance.

---

### Post by Omcon on 2009-01-31
This is what it gave me back when I put in that command.


```
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
05:07.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 04)
```

So I would assume that my actual GPU is the VGA compatible controller, right? Anybody know how I can get the correct drivers for that?

---

### Post by overdrank on 2009-01-31
Hi and when you enable the drivers can use use the keys ctrl, alt, F1 and reach the command line?
If so you may try and then use this command ```
sudo dpkg-reconfigure xserver-xorg
``` then can use the keys ctrl, alt, F7 and hopefully this will return you to the desktop.

---

### Post by Omcon on 2009-01-31
Alright, so whe I use the nvidia-glx-envy package, and restart, that's when I get the giant nVidia logo. And no cursor. When I just enable the drivers through the system > administration > hardware drivers, it removes the envy packages and installs the nvidia-glx package. So when I restart with the nvidia-glx package, I see the ubuntu boot screen, then at the login screen, I see the loading cursor, then the pointer. Then nothing. Black screen. Even the light in my optical mouse goes out, and I can't move it around. And none of the lights on my keyboard are on. Ctrl+Alt+F1 doesn't do anything.

Help? Haha.

Omcon

---

### Post by Omcon on 2009-02-01
Alright so, when I use the 71.86.04 version of the nvidia driver through envy, I get the nvidia logo, and a login screen. And it works fine. BUT! I can't change the screen resolution or enable 3D effects, which was the whole point of me trying to fix it. -_- Any ideas?

---

### Post by Omcon on 2009-02-02
*bump*

---

### Post by redroad55 on 2009-02-02
Take a look here ..[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")post back with results and or questions ..Best to you

---

### Post by Omcon on 2009-02-03
Alright so this is what I've got so far.

```
omcon@omcon-desktop:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0xa3)   64.1MHz
        h: width  1024 start 1080 end 1184 total 1344 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz

```

And when I put in the ```
xrandr --output defualt --mode 1024x768
```

It says that it cannot find that mode. I went and made a new mode line and every thing. Any chance that I might've screwed something up? There's probably a good chance of that. Heh. But, where can I find a walk-through for this? I'm having a little bit of trouble. :) Thanks for your help so far, I really appreciate it.

Omcon

---

### Post by redroad55 on 2009-02-03
If you have not already go into synaptic and find nvidia settings  check it and apply then go to applications > system > administration > > then find the new nvidia app and see if you can change there .. Some of the things you are trying to do may require that you log out and log back in for them to take effect ..I'm done for the night will be back about 10:00 est .. Post back results and or Questions .. Best to you

---

### Post by GSI on 2009-02-03
If you are using nVidia GeForce 2 try this : 

Originaly posted by northern lights

Presumably you're on Intrepid. Have you installed all available updates?
Intrepid wouldn't recognize the GeForce 2 MX on my backup workstation either in early October. Manual driver install changed nothing either. Now it does flawlessly.

Please run
Code:

sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-glx-96

Reboot. Check again in "System > Administration > Hardware Drivers" as well as "System > Administration > NVIDIA X Server Settings".

that helped me :)

---

### Post by Omcon on 2009-02-03
> **GSI said:**
> 
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-glx-96


Alright did that, and it ran until the point when it was downloading the nvidia-glx-96 package. Said it couldn't find it. I appreciate the help, though! :)

---

### Post by Omcon on 2009-02-03
Alright, redroad, I went and installed the nvidia settings package. Tried to run it, and then got this message:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Then I went to the terminal, and ran "nvidia-xconfig" and got this back:

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.



So what now? I'm trying the envy driver that worked for me again. The 71 version. Then I am going to reinstall the nvidia-settings package and see where that gets me.

---

### Post by redroad55 on 2009-02-03
In terminal>  /etc/X11
This will tell you if in fact the directory "Is"
Post back and will go from there..Best to you

---

### Post by Omcon on 2009-02-04
Well, it appears that /etc/X11 is a directory. I dunno what to do now. Haha. All this makes me feel dumb. Anyhoo thanks for all the help so far, guys. :)

---

### Post by redroad55 on 2009-02-04
So now :
      > sudo nvidia-xconfig 
post back..Best to you

---

