---
title: "Nvidia - seem to be nearly there"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by kreyszig on 2007-02-25
Hi,

I'm installing nvidia's own linux drivers (9746) for my 8800GTS and thought I had everything set up nicely (finally)- I run through nvidias script - it builds the kernel interface, I don't run the config utility during the install (after trial and error this seems to work the best) and I can startx nicely. However when I reboot x won't start, and I get the message:

..the Nvidia kernel module has the version 1.0-7184 but this X module has the version 1.0-9746...

then no screens found etc. 
The only way I can get X to start is by re-running the installation script. 
Does this mean that somehow the installation script is not updating the "nvidia kernel module" somehow? I'm pretty stuck so any advice would be greatfully recieved - as long as it does not involve using a different driver - I *have* to use the official nvidia version. 

Thanks in advance, please help!

---

### Post by taurus on 2007-02-25
Did you by any chance install an older nVidia driver for your graphic card before you install the latest version by hand?

---

### Post by kerry_s on 2007-02-25
I would say you probably want to uninstall all the nvidia stuff installed in synaptic, that means the ubuntu restricted kernel and the nvidia-glx driver.

---

### Post by kreyszig on 2007-02-25
re earlier model driver: well I suppose I did - I'm using feisty which wasn't installing via the alternate install disc, so I had to use the desktop version. That wouldn't recognise the 8800 so I had to use a 6800 to do the basic install. I guess that probably set up some other drivers for me. 

kerry_s - can you tell me how I can do this via command line? 

Regards, and thanks for the quick responses

---

### Post by taurus on 2007-02-25
Try something like

```
sudo aptitude update
sudo aptitude --purge remove nvidia-glx
```
Reboot and see if you can install the latest version by hand now.

---

### Post by kreyszig on 2007-02-25
Thanks- I tried that and I get the same issues - any other suggestions?
Edit: I removed the restricted kernel and hey presto - all is sweet! Thanks for your help!

---

### Post by Alpha_Maverick on 2007-03-13
how does one remove the restricted kernel? I am having a similar problem

---

### Post by Hub-1 on 2007-03-13
> **Alpha_Maverick said:**
> how does one remove the restricted kernel? I am having a similar problem

You have to disable Ubuntu's own drivers to avoid conflict.
To do this, edit /etc/default/linux-restricted-modules-common:

```
gksudo gedit /etc/default/linux-restricted-modules-common
```

Modify the line **DISABLED_MODULES=""** to the following:
```
DISABLED_MODULES="nv"
```

If you previosly installed ubuntu's "nvidia-glx" delete these drivers and the init script:

```
sudo apt-get --purge remove nvidia-glx nvidia-settings
sudo rm /etc/init.d/nvidia-glx
```

Then reinstall the driver.

---

### Post by simonn on 2007-03-13
During startup, if the linux restricted modules package is installed, the dir /lib/modules/[kernel version]/volatile/ has a tmpfs ([http://en.wikipedia.org/wiki/Tmpfs](http://en.wikipedia.org/wiki/Tmpfs)) mounted to it and the restricted modules are copied to it from /lib/linux-restricted-modules/[kernel version].

I have no idea why this is done.

When you install the nvidia drivers from the nvidia web site manually, it installs them to lib/modules/[kernel version]/volatile/ as well. However, as this is a tmpfs they are lost on reboot.

---

