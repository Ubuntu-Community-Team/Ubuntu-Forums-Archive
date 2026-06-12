---
title: "X doesn't like my VGA!"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by suhaib on 2006-08-30
Hey there,

I'm pretty new to Ubuntu and Linux as a whole I guess (been using Debian at uni for a year, just recently started using Ubuntu at home and work!).  I've used the search function and unfortanatley I haven't found a resolution to my problem.

I'm at work and we had to change the graphics card for a particular machine.  After that, the x failed to run.  I followed the instructions in the sticky about the recent Ubuntu updates, assuming that it may be a problem with the version (which was out of date anyway).

The problem however persists.  The card in the machine is a Trident Microsystems 3DImage 9750.  Can anyone help me with this problem?

Thank You, all help is much appreciated.

I apologise in advance if this same problem has been answered many times and/or is easy to resolve.

---

### Post by tseliot on 2006-08-30
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.
Type:
```
reboot
```

The Xserver should work fine. If it doesn't, try using "vga" instead of "vesa"

---

### Post by suhaib on 2006-08-30
Thanks, I tried this a few times but got the same error message every time.

> xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.conf .20060830115048
find: cannot get current directory: Permission denied
dexconf: error: cannot generate configuration file;
xserver-xorg/config/device/driver not set.  Aborting  Reconfigure the X server with "dpkg-reconfigure xserver-xorg" to correct this problem.
xserver-xorg persistant warning: error while preparing new Xorg X server configuration file in /etx/x11/xorg.conf.dpkg.new; not attempting to update existing configuration

Is the problem to do with the permissions of the xorg.conf file?  I selected "yes" when it asked if I wanted to write to it or not.  I also tried selecting "no".

---

### Post by tseliot on 2006-08-30
> **suhaib said:**
> Thanks, I tried this a few times but got the same error message every time.



Is the problem to do with the permissions of the xorg.conf file?  I selected "yes" when it asked if I wanted to write to it or not.  I also tried selecting "no".

Did you boot in Recovery mode before typing that command?

---

### Post by suhaib on 2006-08-30
Yeah, I did.  It was second on the selection.

---

### Post by tseliot on 2006-08-30
Try this:
```
apt-get update
```

```
apt-get install -f

```
```
dpkg-reconfigure -phigh xserver-xorg
```

```
dpkg-reconfigure xserver-xorg
```

and select the "trident" driver instead of "vesa"

---

### Post by suhaib on 2006-08-30
Still receiving similar errors.  Permission denied.  Currently I'm trying to change the permissions of the /etc/x11/xorg.conf file, or shouldn't this be needed?

Also, is there anyway of booting into a safe video mode?

---

### Post by tseliot on 2006-08-30
> **suhaib said:**
> Still receiving similar errors.  Permission denied.  Currently I'm trying to change the permissions of the /etc/x11/xorg.conf file, or shouldn't this be needed?

Also, is there anyway of booting into a safe video mode?
The problem is that when you boot in Recovery mode you are root (and therefore you have the permission).

Safe mode is available only on the livecd (and it sets the driver to "vesa")

---

### Post by suhaib on 2006-08-30
Thanks for your help.  The GUI is BACK!

In recovery mode, i typed the command "su -" followed by the admin/root password.  I then tried the installation again selecting trident (previously I wasn't even able to choose) and received no error messages although the GUI was still down.  So I tried again, selecting Vesa for the second (or third) attempt.  My GUI has returned!

I'm not sure if the list of commands you typed earlier in post #6 were necessary though.  I tried them the first time round (when selecting trident), but in the attempt that corrected the problem, i typed dpkg-reconfigure xserver-xorg with out the other commands that preceded it and now everything is fine.  What exactly did the other commands do?

Thanks again!

---

### Post by tseliot on 2006-08-30
> **suhaib said:**
> Thanks for your help.  The GUI is BACK!

In recovery mode, i typed the command "su -" followed by my password.  I then tried the installation again selecting trident (previously I wasn't even able to choose) and received no error messages although the GUI was still down.  So I tried again, selecting Vesa for the second (or third) attempt.  My GUI has returned!

I'm not sure if the list of commands you typed earlier where necessary though.  I tried them the first time round (when selecting trident), but in the attempt that corrected the problem, i typed dpkg-reconfigure xserver-xorg and now everything is fine.  What exactly did the other commands do?

Thanks again!
```
apt-get install -f
```
fixes broken packages

```
dpkg-reconfigure -phigh xserver-xorg
```
updates your xorg.conf (it generates a new one)

---

### Post by suhaib on 2006-08-30
Ahh ok.  Thank you very much for all your help and the time spent in doing so.

Take care, probably see you around here more often.

---

### Post by jd65pl on 2006-09-01
I am having a similar problem but I dont have the "vesa" option only

neomagic
siliconmotion
voodoo

are options

please help!

---

### Post by jd65pl on 2006-09-01
To answer myself I downloaded the vesa driver

---

