---
title: "NVIDIA GeForce 6600 install - I require kernel header files? ;s"
date: 2008-06-04
forum: Multimedia Software
---

### Post by Cup of Squirrels on 2008-06-04
Hello,

I'm taking another shot at Linux and Ubuntu, and need some quick assistance in obtaining header files and such.

I am currently following this guide:
[http://wp.uberdose.com/2004/12/11/ubuntu-and-nvidia-geforce-6600/](http://wp.uberdose.com/2004/12/11/ubuntu-and-nvidia-geforce-6600/)


I have managed to exit my X windows session, as required by the offical NVIDIA Linux driver installation, and according to the guide during the installation a new module would be built (Whatever that is). The installation begins to prompt me about this, but is apparently unable to build it as I need the libc kernel header files, or something...

I type in "sudo apt-get install linux-headers" to list the available headers, and this shows up in the terminal:

```
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

```

Now, when I type in sudo apt-get install linux-headers-2.6.24-16-generic 2.6.24-16.30, I am told my headers are up to date, and the package "2.6.24-16.30" cannot be found. I have tried a number of combinations of these listed packages, but it is either I am up to date, or the package can not be found.

Regardless of this, the installation still demands I need to header files. I am very confused as to where to go from here, which I why I've come here to ask you for your help in what direction to take from here.

Thanks :)

---

### Post by unutbu on 2008-06-04
The guide you are using is from 2004. I wouldn't use it. /etc/X11/XF86Config is now /etc/X11/xorg.conf, for example.

There are 3 ways to install the nvidia restricted drivers: 

1) Click on System>Administration>Restricted Driver Manager in the gnome panel menu. 

2) Use Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). If you are running Hardy, I believe envy is now an official package. It will download and install the latest nvidia driver for you.

3) Compile the drivers yourself. This is the most complicated option.

---

### Post by Pjotr123 on 2008-06-04
> **unutbu said:**
> The guide you are using is from 2004. I wouldn't use it. /etc/X11/XF86Config is now /etc/X11/xorg.conf, for example.

There are 3 ways to install the nvidia restricted drivers: 

1) Click on System>Administration>Restricted Driver Manager in the gnome panel menu. 

2) Use Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). If you are running Hardy, I believe envy is now an official package. It will download and install the latest nvidia driver for you.

3) Compile the drivers yourself. This is the most complicated option.

+1

Envy is in Universe now.
@ Cup of Squirrels: you can try this simple how-to:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

---

### Post by Cup of Squirrels on 2008-06-04
Hello there,

Thanks for the help. It turns out I needed to perform "apt-get install built-essential" for the libc header files the install mentioned.

After installing the drivers, I went over to "hardware drivers" and ticked my NVIDIA card. After Ubuntu downloaded some extra package to support it, I rebooted the pc, did some settings I was prompted to do.

After that however, the X server was loaded, and the screen went horrible - jagged lines of a small selection of colours, and my monitor gave a hardware error. ctrl+alt+F1 took me back to the "text console", but even that had a few errors when it started to print text.

I will probably boot my distro up in safe mood and have a little tinker - perhaps I chose the wrong "driver type" or something during the pre-GUI prompt.

---

### Post by Pjotr123 on 2008-06-04
> **Cup of Squirrels said:**
> Hello there,

Thanks for the help. It turns out I needed to perform "apt-get install built-essential" for the libc header files the install mentioned.

After installing the drivers, I went over to "hardware drivers" and ticked my NVIDIA card. After Ubuntu downloaded some extra package to support it, I rebooted the pc, did some settings I was prompted to do.

After that however, the X server was loaded, and the screen went horrible - jagged lines of a small selection of colours, and my monitor gave a hardware error. ctrl+alt+F1 took me back to the "text console", but even that had a few errors when it started to print text.

I will probably boot my distro up in safe mood and have a little tinker - perhaps I chose the wrong "driver type" or something during the pre-GUI prompt.

You are polluting your system.  :-)

You should simply do the simple things that were advised to you. This way you make everything needlessly complicated and you will probably not succeed......

---

### Post by Cup of Squirrels on 2008-06-04
> **Pjotr123 said:**
> You are polluting your system.  :-)

You should simply do the simple things that were advised to you. This way you make everything needlessly complicated and you will probably not succeed......


Hm, I'm not sure what you mean by "polluting my system" - I'm loading up too much unneeded crap? For example, I may have conflicting graphics drivers?

I'll give the info and links posted a deeper look and see where I can go from there.

Thankyou :)

---

