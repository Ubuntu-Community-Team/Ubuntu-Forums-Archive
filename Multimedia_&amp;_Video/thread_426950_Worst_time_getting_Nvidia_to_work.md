---
title: "Worst time getting Nvidia to work"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by jason@surferz.net on 2007-04-29
Hello all :)

I am a computer technician by trade; I fix spyware and virus's on MS Windows systems all day every day.  I switched to linux on my home machine for no other reason than wanting to get rid of Windows XP.  I primarily use my machine at home for email, photo editing, internet, etc... and Ubuntu has proven to me to be outstanding in doing what I want to do.  Ubuntu (or linux in general) being free is just a GREAT bonus.  I've been detered from linux distro's in the past mainly for compatibility reasons, but the more I use it the more I realize that everything I need is readily available.  Not to mention where I live broadband is almost impossible, until my company made wireless broadband available, which makes the concept of "free" software much more appealing....now I can actually get it.  And Ubuntu is just so easy to migrate to from Windows...I Love It!!!

The only drawback so far....sometimes I just want to play some games...usually FPS or driving stuff...I've found a handful of good games for linux and got them to run (sort of).  My biggest problem and the reason for this post is this....

I have an nvidia 5700 AGP card.....

I CAN NOT FOR THE LIFE OF ME get this thing to install properly.

I've tried nvidia's driver.....X crashes.

I've tried using Envy to install the drivers...X crashes.

I've tried uninstalling EVERYTHING to do with nvidia, glx, old kernel sources, and reinstall the driver.....X crashes.


I can't seem to get 3D to work properly.

I have 6.10 installed, and I used to have an ATI 9700 card that after some tweaking I got to work.

I have reinstalled 6.10 with the nvidia card several times and NEVER been able to get it to work.  Directions from Wiki, Nvidia, or Envy never seem to get things working.  If i replace the driver in the xorg.conf file with the nv driver, it works, but no 3D support.

HELP!!!!!!!!!!!!!!!!!!!!!!

---

### Post by raffytaffy on 2007-04-29
when you state " i tried nvidia driver" do you mean the one from synaptic manager ( apt-get) ? "nvidia-glx" i think its called. ? or are you talking about the one from their website...NVIDIA-Linux.... installer.?

---

### Post by jason@surferz.net on 2007-04-29
both...:(  no luck either way, xorg crashes every time......thought it might be the card but it works under xp just fine

---

### Post by raffytaffy on 2007-04-29
can you tell me which driver you are trying to install "the version" of it...is it 9755 by any chance?

---

### Post by jason@surferz.net on 2007-04-29
tried that and the 7XXX (cant remember exactly) legacy driver

---

### Post by raffytaffy on 2007-04-29
i would suggest you try the 9631 driver
```
 wget ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run
``` 
into your home folder. and before you attempt install try this
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1

sudo gedit /etc/X11/xorg.conf

Add the lines which begin with the word "Option" in this section of the file
```
Section "Device" Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]" Driver "nvidia" BusID "PCI:1:0:0" Option "NvAGP" "0" Option "RenderAccel" "Off" Option "IgnoreDisplayDevices" "DFP,TV" Option "NoRenderExtension" "Off" Option "AllowGLXWithComposite" "Off" EndSection
```

before install make sure you have the needed packages IE: kernel source, headers etc etc.

then restart xserver.  - if you get error you can -> sudo cp /etc/X11/xorg.conf_backup1 /etc/X11/xorg.conf to restore previous file.

now go into console ctrl=alt=f1 ...log in
turn off xserver ->  sudo /etc/init.d/gdm stop
run the installer -> sh NVIDIA_linux.....
and hope it works.

---

### Post by jason@surferz.net on 2007-04-29
a 6200 turbocache is a pci-ex card...mine is agp...no problem there as far as the conf file goes?

---

