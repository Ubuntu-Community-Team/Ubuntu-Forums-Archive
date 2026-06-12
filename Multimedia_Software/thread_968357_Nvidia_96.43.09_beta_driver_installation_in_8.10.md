---
title: "Nvidia 96.43.09 beta driver installation in 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by GourdCaptain on 2008-11-02
I have a computer with a GeForce 4 MX GPU (integrated into the motherboard) and as is well known, the proprietary NVIDIA drivers don't work with the current version of Xorg and the kernel. NVIDIA recently released beta drivers that supposedly do (and do, from reports on other forums) but the maintainer of the Ubuntu package of these drivers at [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107") recommended that you wait until an Ubuntu version was released or nasty things could happen. 

This package maintainer recently posted at [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/43]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/43")a set of modified versions of these drivers for Ubuntu use, and I was wondering how to install them. There's no included readme file, but at the above post he says I would have to remove them from the Jockey Blacklist, which isn't something I know how to do. So how do I install these drivers (or is there an automated debian package somewhere I can install?

P.S. I already know about having to add the line Option "AddARGBGLXVisuals" "True" to my xorg.conf to get these to work correctly.

---

### Post by solitaire on 2008-11-02
Not tried Alberto's fix yet. I got the Nvidia drivers working.

Do you have a desktop or Laptop?

my GeForce4 is on a laptop and the Nvidia drivers default output to a CRT display instead of my LCD screen.

of you have a laptop then add the following after the AddARGBGLXVisuals" line:```

Option "UseDisplayDevice" "DFP"
```.

---

### Post by GourdCaptain on 2008-11-02
> **solitaire said:**
> Not tried Alberto's fix yet. I got the Nvidia drivers working.

Do you have a desktop or Laptop?

my GeForce4 is on a laptop and the Nvidia drivers default output to a CRT display instead of my LCD screen.

of you have a laptop then add the following after the AddARGBGLXVisuals" line:```

Option "UseDisplayDevice" "DFP"
```.

I've got a desktop with a CRT monitor, on which I want 1024x768 resolution (hence why I don't like the NV drivers. I'm currently using VESA, which stinks in the efficiency department.)

---

### Post by GourdCaptain on 2008-11-02
Well, I can now install the drivers if I can get xorg to stop running. Unfortunately, no matter how I kill it, It respawns and begins running again. Ctrl-alt-backspace from the login screen results in an infinite loop of "The greeter seems to be crashing" errors. Hitting ctrl-alt-1 to go to terminal and killing xorg with a command - it restarts. Booting into a root shell at recovery mode doesn't work as I need Internet access from my wireless to install the drivers, and in the process of running the "telinit 3" command, xorg starts and becomes unkillable again. This is rather... annoying to say the least. Any tips to kill xorg permanently (and no, I have not tried silver bullets or destroying the head)

---

### Post by nicrizzo on 2008-11-03
Press ctrl+alt+f1, login into your system and type (without quotes):
"sudo /etc/init.d/gdm stop"

install the driver then:

"sudo /etc/init.d/gdm start"
(use kdm instead of gdm if you are using kde)
   nic

---

