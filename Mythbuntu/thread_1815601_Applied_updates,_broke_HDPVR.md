---
title: "Applied updates, broke HDPVR"
date: 2011-07-31
forum: Mythbuntu
---

### Post by ceenvee703 on 2011-07-31
This happened the last time I applied updates, but for some reason I went insane this morning and applied updates again. Sure enough, after I rebooted, my Mythbuntu 10.04 system didn't recognize that my HD-PVR was there.

I went to the mythtv wiki page on the HD-PVR and followed their instructions for recompiling the driver. In the "make" step, though, I get the following error:

```
make -C /lib/modules/2.6.35-30-generic/build SUBDIRS=/home/mydir/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-30-generic'
  CC [M]  /home/mydir/media_build/v4l/hdpvr-core.o
/home/mydir/media_build/v4l/hdpvr-core.c:20: fatal error: linux/atomic.h: No such file or directory
compilation terminated.
make[3]: *** [/home/mydir/media_build/v4l/hdpvr-core.o] Error 1
make[2]: *** [_module_/home/mydir/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mydir/media_build/v4l'
make: *** [all] Error 2

```

I tried searching for "atomic.h" errors and HDPVR but didn't turn anything up.

What do I need to do to recompile and install the drivers? Or barring that, is it just easier to somehow upgrade to the latest Mythbuntu running on 11.04? Does that have enough built-in support so that HD-PVR drivers don't break each time I do a system update?

Very VERY frustrated right now. Thanks.

---

### Post by superm1 on 2011-07-31
What you are missing is the associated headers package that goes with that kernel.  There are two headers packages.  You need both.

linux-headers-2.6.35-30-generic
linux-headers-2.6.35-30


You should consider installing the module using DKMS instead too, then it would upgrade for you when the kernel upgrades.

---

### Post by ceenvee703 on 2011-08-01
Thanks for the reply. I already seem to have those installed:

```
sudo apt-get install linux-headers-2.6.35-30-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.35-30-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get install linux-headers-2.6.35-30

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.35-30 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I just double-checked and I hit the same error when I try to make the driver.

EDIT: this message I get when I do the "make stagingconfig" step seems relevant in retrospect, but I'm not sure what else I can do to solve it:

```


Preparing to compile for kernel version 2.6.35

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

```

---

### Post by superm1 on 2011-08-01
Ah, so if the issue is when it's trying to refresh the kernel config, follow exactly what it's telling you.  The kernel config that matches those headers is stored in /boot.  You can copy it into place here.

---

### Post by ceenvee703 on 2011-08-01
Thanks again for the help. I'll try that tonight. 

Just to confirm, I should use /boot as the substitute for <your kernel dir>?

---

### Post by superm1 on 2011-08-01
Well wait a minute.

You're on 2.6.35 on 10.04?  Are you running an updated kernel from maverick or something?

What about the kernel built in doesn't work? That newer device ID?  If you're already on a newer kernel, how about just grabbing the natty one and running that?

Would save you a bunch of trouble I'd think.

---

### Post by ceenvee703 on 2011-08-01
Sorry, my mistake, I'm on 10.10. I could upgrade to 11.04 if path forward is easier.

---

### Post by superm1 on 2011-08-01
> **ceenvee703 said:**
> Sorry, my mistake, I'm on 10.10. I could upgrade to 11.04 if path forward is easier.

Well if you've got no other reason to stay on 10.10, I think it's the path of least resistance.

Up to you, if you want to keep rebuilding the HDPVR driver manually or use the one built into 11.04 which should work fine.

---

### Post by uteck on 2011-08-02
Do you have any other video capture cards installed in the box?
I have 10.10 and when I reboot it loses the HDPVR and I have to go into Mythtv-setup and change the video device.  I tried to set it always use video0, but it seems to alternate between that and video1 when it reboots, so I try not to reboot that often.  I need to remove the analog cards since they will not be usefull when the cable converts to all digital, that should fix the problem for me.

---

### Post by ian dobson on 2011-08-02
> **uteck said:**
> Do you have any other video capture cards installed in the box?
I have 10.10 and when I reboot it loses the HDPVR and I have to go into Mythtv-setup and change the video device.  I tried to set it always use video0, but it seems to alternate between that and video1 when it reboots, so I try not to reboot that often.  I need to remove the analog cards since they will not be usefull when the cable converts to all digital, that should fix the problem for me.

That sound alot like a race condition, the kernel loads the modules in what ever order it finds the hardware, so sometimes your HDPVR comes up as video0 othertimes as video1.

Search through the forums for a udev/video0 thread. Theres a python script that creates symbolic links for video0 and video1 that always point to the same device (/dev/hdpvr -> /dev/videoX).

Here's a link [http://ubuntuforums.org/showthread.php?t=1618370&highlight=udev+video](http://ubuntuforums.org/showthread.php?t=1618370&highlight=udev+video)

Regards
Ian Dobson

---

### Post by ceenvee703 on 2011-08-02
No other video cards -- I pulled the last of them when I went with the HD-PVR. I did have that video0/video1 problem when I was running multiple cards, though.

Ultimately, superm1 called it -- I upgraded to 11.04 last night and the HD-PVR drivers included with it worked, no compiling necessary. I did have to run mythtv-setup one time to get the HD-PVR recognized again, but other than that it looks like I'm back in business.

Thanks very much for your help!

---

### Post by aircarver on 2011-08-06
I have an 11.04 new install, and everything works, including the new model HD PVR, lirc for ir remote and ir blasting for DISH set top box.

I'd recommend going that way.

(It even survived the latest bunch of updates .....  >: )

---

