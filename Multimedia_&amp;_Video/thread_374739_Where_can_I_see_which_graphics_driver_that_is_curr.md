---
title: "Where can I see which graphics driver that is currently in use?"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by pfred on 2007-03-02
I just have a teeny weeny question that seems quite simple, but as a ubuntu noob I cannot seem to work it out. I have been mucking around with different drivers for my nvidia geforce 6600GT, uninstalling and installing using Envy and also synaptics. I still don't really get the difference between "Legacy", glx and so on. My question is though:
Is there anywhere I can look and see which driver I currently have installed? Like device manager in windows. I tried the ubuntu device manager but i can't seem to find any info on the driver name and version.

I have had problems with my keyboard and mouse freezing, and by reading the forum I worked out it might be the nvidia drivers so I'm still mucking around with the drivers.

Fred

---

### Post by po0f on 2007-03-02
pfred,

Login on a virtual console (Ctrl-Alt-F1), and stop X: `sudo /etc/init.d/gdm stop`.  Now, switch to another console (Alt-F2) and type the following command: `sudo tail -fn0 /var/log/messages`.  Switch back to the first console (Alt-F1) and remove and reload the nvidia driver: `sudo modprobe -r nvidia && sudo modprobe nvidia`.  Switch back to the second console and look at the output, it should tell you which driver version was loaded.

Or, you could just install the version in the repos and know what version you are using.  ;)  With a 6600GT, you *don't* need to use the legacy drivers.  To install the latest version for your version of Ubuntu:

```
$ sudo apt-get update
$ sudo apt-get install nvidia-glx
```

---

### Post by aidanr on 2007-03-03
or just run nvidia-settings

---

### Post by po0f on 2007-03-03
aidanr,

Your answer was a lot easier than mine; I didn't realize nvidia-settings was still installed with the driver.  :D

---

### Post by pfred on 2007-03-04
Thanks guys,
I suppose the solution is not as easy as in windows... Anyway, nvidia-config confirms that I have version 1.0-9631, which is the second newest driver from the nvidia website. However, to work this out I had to go to the nvidia website and compare version numbers and then compare the version number under the nvidia-glx entry in synaptics to rule out that I installed the Ubuntu driver. So there is no easy graphical interface way, where you in a few clicks can get the info whether the driver installed is a legacy, Ubuntu or Nvidia driver?

The reason I wasn't sure which driver I had is that I tried a lot of different ones to try and get a stable system that doesn't freeze up on me all the time. This one seems to be fine, since I havent had a freeze yet.

---

