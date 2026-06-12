---
title: "ATI Driver Hell"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by penguins! on 2007-06-01
I have a Radeon X1900XTX and I haven't been able to get 3D acceleration working since the Feisty release :(  That was quite a while ago.

I've followed every tutorial I can find, tried installing the driver via the repositories and manually. Nothing works. 
The driver seems to install fine but fglrx still talks about Mesa.

I just installed version 8.37.6 of the driver but the problem remains.

Found the following in my xorg log that might be relevant:

```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7c5a000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

So it seems to be using kernel module 8.34.8 which clearly doesn't work with driver 8.37.6.

I've tried rebuilding the new module, loading it, unloading it, nothing.
The odd thing is that an ati module in any shape or form never seems to load. I added "fgrlx" to modules also.

Any ideas?  Where would I find this older module and how do I get rid of it?

Any help greatly appreciated. Thanks!

---

### Post by hobbes_ba on 2007-06-02
I'm having the same problem. it keeps showing

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module

i even reinstaled my ubuntu.


Anyone?

---

### Post by penguins! on 2007-06-02
OK so I have a messy solution but it eventually worked for me.

First back up your /etc/X11/xorg.conf file because you'll most likely break X dozens of times doing this :p

Remove all traces of fglrx from your system

```
sudo apt-get remove fglrx*
```

The problem seems to be that ubuntu's pre-packaged drivers were causing mayhem on my system after the feisty upgrade so I removed lots of stuff associated with the linux-restricted-modules packages. It never allowed me to install the proprietary drivers in the first place so it was of little use to me.

```
sudo apt-get remove linux-restricted-modules-common
```

Now download and install the 8.37.6 ATI driver per instructions here:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.37.6_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.37.6_Driver_Manually")

Reboot. Fglrxinfo will probably indicate that acceleration isn't working and you'll still find the same message in your xorg log.

I managed to get the drivers working by manually loading the correct kernel module. Try the following:

```

sudo rmmod fglrx
sudo insmod /lib/modules/2.6.20-16-generic(or whatever your kernel version is)/misc/fglrx.ko
modprobe fglrx

```

After restarting X with Ctrl+Alt+Backspace (*not* rebooting the system), 3D acceleration was working for me.

Now the problem is that this was necessary after every reboot. I tried looking for the 8.34.8 module everywhere but couldn't find it. So I still haven't a clue what really causes this.

I tried a number of things to make the changes stick and a combination of the following eventually worked:

Open
```
sudo gedit /etc/default/linux-restricted-modules-common
```

Add the line
```
DISABLED_MODULES="fglrx"
```

My xorg log was still complaining about "instructions" in lrm-video. I did the following:
Open
```
sudo gedit /etc/modprobe.d/lrm-video
```

There should be a line that looks something like this:
```
install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```.

You want to comment that out so it looks like this:

```
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
```.

I rebooted at this point and 3D acceleration was working. The above process took the best part of a day however :(

Let me know if this works for you. If you don't have any luck I'll see if I can identify any other changes I made to the system.

Hope it helps :)

---

### Post by hobbes_ba on 2007-06-02
Dont' work for me.

Now i have a different log message on /var/log/Xorg.0.log[

EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

lsmod | grep fgrlx gives me nothing.

loading manually fglrx nothing seems to happen.

i got stuck right there.

The 'funny' part is that my ubuntu feisty is brand new.

Any ideas?

---

### Post by Gimpy_Rob on 2007-06-17
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

Same problem exactly.  I've followed many instructions to try to get it to work, but getting frustrated.  I believe I'm running newest version of everything.  Downloaded from ATI, etc.

Radeon 9800 Pro if it matters.

Anything else I should post to help diagnose problem?

---

### Post by NetherBen on 2007-07-11
--

---

### Post by Tuckwoor on 2007-07-12
Same problem here :(

[http://ubuntuforums.org/showthread.php?t=485886]("http://ubuntuforums.org/showthread.php?t=485886")

---

### Post by Bablefish on 2007-07-12
I have the same problem, but I got around this to a Yes limited degree by using Evny.

---

### Post by Tuckwoor on 2007-07-12
I got stuck with the mesa 3d problem when I used envy.

---

