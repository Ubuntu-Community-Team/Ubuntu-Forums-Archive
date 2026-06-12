---
title: "Getting Dual Monitors Working on ATI Radeon X800 XL"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by jremerson on 2007-10-12
I have read a number of the Dual Monitor Posts and cannot seem to get this working.

Below is all of the information that I can think to provide, if something else is needed please let me know:

Please note I have both monitors connected and the 2nd is showing up as a clone of the 1st. in Screens and Graphics it shows as disabled.

I am running Gutsy.

```
 lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)

```

One of the things that I tried was this:

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

When I got to here:

```
sudo aticonfig --initial
```


The error that was received was:

```
sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

```


I have received this error a number of times when trying various methods. I have tried taking my backup copy and renaming it to xorg.conf however this does not seem to fix the problem.

Any help at this point is greatly appreciated. 

Thanks,
Jim

---

### Post by u1tra on 2007-11-13
Installed for the first time yesterday, and having the same issues as you.  I was heading down a different path to you though, and think I have the answer to your problem.

I'm betting your xorg.conf file isn't present of isn't setup correct.  You can view/edit it in your terminal..
```
gksudo gedit /etc/X11/xorg.conf
```

You can set one up for a single screen using:
```
sudo dpkg-reconfigure xserver-xorg
```

After I done that, and got the first screen working, I used your approach, downloaded the ATi driver from their site, and installed using their instructions.  After the GUI install finished, I open terminal and used:

```
aticonfig --initial
aticonfig --initial=dual-head --screen-layout=right
```

Now I have 2 windows and can move between them.  But now I don't have any wobbly windows :( So hoefully I can work on fixing that.. it's too cool to loose.

Hope I've helped you out!
Ultra

---

