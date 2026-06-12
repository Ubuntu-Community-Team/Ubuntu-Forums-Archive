---
title: "Switching from proprietary Nvidia driver to Nouveau"
date: 2010-12-17
forum: Multimedia Software
---

### Post by Aat on 2010-12-17
I'm using ubuntu 10.10 with the proprietary Nvidia-driver for my graphics card.
I'd like to switch to the open source Nouveau driver. What is the best way to go about this?

Thanks in advance.

---

### Post by CheetoBandito on 2010-12-17
Read:

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

Troubleshoot:
[http://www.google.com/search?q=ubuntu+Nouveau&hl=en&safe=active&client=firefox-a&hs=69L&rls=org.mozilla:en-US:official&prmd=ivnsfd&tbs=dsc:1&tbo=u&sa=X&ei=27oLTYu7GoSdlgfL0PmhDA&ved=0CDYQmAcwAg](http://www.google.com/search?q=ubuntu+Nouveau&hl=en&safe=active&client=firefox-a&hs=69L&rls=org.mozilla:en-US:official&prmd=ivnsfd&tbs=dsc:1&tbo=u&sa=X&ei=27oLTYu7GoSdlgfL0PmhDA&ved=0CDYQmAcwAg)

---

### Post by BicyclerBoy on 2010-12-17
Normally it is a real struggle to get the nvidia driver to load in preference to nouveau.
(editing files blacklisting stuff etc)

I would first find these system files & check..search for keywords like blacklisting nouveau driver.
There is plenty of info relating to nvidia & nouveau & *buntu 10.04.
 
Assuming nvidia driver is in package manager (synaptic): 
So it should as a simple as removing nvidia driver & installing nouveau..

If the driver has been installed direct from nvidia install shell script (with X server not running) then you need to read the nvidia installer help file about how to un-install.

It is not that difficult but you need to know how to:
    stop X server from starting (or stop it)
    find the install script (name path etc)
    run shell script in the terminal login (no GUI)
    restart X server
    fix xorg.conf maybe

There is always the install CD as rescue/last resort..

---

### Post by gradinaruvasile on 2010-12-17
You will regret it.

---

### Post by Yellow Pasque on 2010-12-17
Boot to recovery console and choose prompt with network connection.
First, back up your xorg.conf and remove the nearly useless 'nv' driver if installed:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get remove --purge xserver-xorg-video-nv
```
Then, if you installed the driver from the Ubuntu repo (or through the Hardware Driver dialog):
```
sudo apt-get remove --purge nvidia-current nvidia-current-dev nvidia-settings
```
If you downloaded your driver directly from nvidia's site:
```
sudo nvidia-settings --uninstall
``` 
Now, install nouveau and reinstall some other packages to make sure nvidia didn't leave proprietary cruft behind:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-nouveau
```

Before rebooting, make sure nouveau isn't blacklisted:
```
cd /etc/modprobe.d/
ls
```

> You will regret it.
Even if he/she does, it is fairly simple to switch back. Nouveau works fairly well with older cards and 3D acceleration and video decode accel for newer cards is rapidly being reverse-engineered.

---

### Post by efflandt on 2010-12-17
Normally if you simply went to **Additional Drivers** and selected "activate" for nvidia drivers from there (even if you used x-swat repository for most recent drivers), it is simply a matter of going back to **Additional Drivers**, selecting "remove", and reboot.

It is more difficult if you went through the difficulty of installing nvidia drivers from nvidia.com.  I have never done that.

Once you are back to the default nouveau driver, you may want to try Quick search of "experimental" in Synaptic and try **libgl1-mesa-dri-experimental** to see how that works for 3D.

---

### Post by Aat on 2010-12-18
Thanks for all the replies, much appreciated.
My main concern is if the nvidia-driver doesn't leave stuff behind.
Is there a way to tell one is definitely running nouveau?

---

### Post by Elfy on 2010-12-18
Have a look in the xorg log in the Log Viewer, System Admin menu.

---

### Post by Aat on 2010-12-19
Again, many thanks. Apparently, Ubuntu 10.10 is smart enough to install nouveau, when the proprietary driver is disabled. It's running now, according to the log-file. And faster too, I'd say. Even 3D is working!

---

### Post by murphycc on 2011-08-23
Aat,

So did you end up doing what Temujin suggested, and did that sequence work?

I am in a similar situation. Using 10.10 and did not realize all this time I had been using the default Nouveau driver (I have Geforce 6100). I used Google Earth and it was really slow. I then realized I wasn't using the Nvidia proprietary 3d driver, so I installed that.

Google Earth was much faster, but I was getting occasional 'flickering' on my screen (flashing of white lines depending on what action I was doing on screen). I tried a few different Nvidia driver versions, but all of them had the flickering issue.

So I want to go back to Nouveau driver because that worked. I probably just had the 2d driver installed, but I would be willing to try the 3d version.

I found some info on this forum about installing 3d version of Nouveau driver, and it sounds quite complex. Doesn't seem like it should be.

Anyhow, I was just wondering if Temujin's instructions worked and/or what else you had to do to install Nouveau again. Also, did you install the 3d version and if so, how?

Thanks,
Chris

---

### Post by Aat on 2011-08-23
Chris,

It was even easier than that. I followed the advice of efflandt and just de-installed the proprietary driver. In the procedure, nouveau was automatically installed. After a reboot to check that everything was ok, I also installed libgl1-mesa-dri-experimental, which gave me 3d-support.

I hope this works for your card too. If not, please post again.

---

### Post by JustGlowing on 2011-10-17
> **Aat said:**
> Again, many thanks. Apparently, Ubuntu 10.10 is smart enough to install nouveau, when the proprietary driver is disabled. It's running now, according to the log-file. And faster too, I'd say. Even 3D is working!

Actually, I deactivated the proprietary driver and the graphic environment stopped to work. I had to re-enable the proprietary driver from command line!

---

