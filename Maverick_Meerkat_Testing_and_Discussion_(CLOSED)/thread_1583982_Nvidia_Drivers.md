---
title: "Nvidia Drivers"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Peter7K on 2010-09-28
Hello all.  I just went through a small ordeal attempting to install the latest nvidia beta driver.  It ended up affecting the permissions on my gdm.conf and I had to purge/reinstall my gdm.  However, I'm having some trouble getting back to the default proprietary nvidia driver.

Normally when one installs Ubuntu, they are offered various driver options, which are not installed already with Ubuntu (usually proprietary or not, etc).  Normally I can enable compisiting and desktop effects with the first proprietary nvidia driver that it offers me to install.  However, I can't seem to find the correct driver, or perhaps that driver is not functioning properly as it did when I first installed Maverick.  I believed "nvidia-current" to be the driver, but it does not allow me advanced desktop effects or compositing.  Is this/is this not the main proprietary nvidia driver?  If not, what is the normal driver I need so I can enable desktop effects?  If it is the default driver, why aren't my desktop effects working?  Thanks.

Update: 
Now on booting up I get this error:
```
 Failed to acquire org.gnome.DisplayManager: Connection ":1.14" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the config file"

```
I've tried dpkg-reconfigure gdm and apt-get purge gdm apt-get install gdm but no such luck, it still continues to deny me use of gdm, I have to use the recovery kernel :/

I actually had this issue right after installing the beta nvidia driver, but it seemed as if I had fixed it after removing the nvidia driver.  Now reinstalling the driver from the "Additional Drivers" application, this error has started up again.  Very obnoxious!  It seems I need a way of updating the gdm.conf file so I can access it, I've searched a bit online and all I've found is people saying they just reinstalled the OS...

---

### Post by VMC on 2010-09-28
From a terminal what's the output of this:

```
apt-cache policy nvidia-current
```

---

### Post by Peter7K on 2010-09-28
Installed: 256.53-0ubuntu3
  Candidate: 256.53-0ubuntu3
  Version table:
 *** 256.53-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted i386 Packages
        100 /var/lib/dpkg/status
     195.36.24-0ubuntu1~10.04 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted i386 Packages


Now on booting up I get this error:
```
 Failed to acquire org.gnome.DisplayManager: Connection ":1.14" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the config file"

```
I've tried dpkg-reconfigure gdm and apt-get purge gdm apt-get install gdm but no such luck, it still continues to deny me use of gdm, I have to use the recovery kernel :/

I actually had this issue right after installing the beta nvidia driver, but it seemed as if I had fixed it after removing the nvidia driver.  Now reinstalling the driver from the "Additional Drivers" application, this error has started up again.  Very obnoxious!  It seems I need a way of updating the gdm.conf file so I can access it, I've searched a bit online and all I've found is people saying they just reinstalled the OS... :-({|=

---

### Post by cariboo on 2010-09-28
> **Peter7K said:**
> Installed: 256.53-0ubuntu3
  Candidate: 256.53-0ubuntu3
  Version table:
 *** 256.53-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted i386 Packages
        100 /var/lib/dpkg/status
     195.36.24-0ubuntu1~10.04 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted i386 Packages


Now on booting up I get this error:
```
 Failed to acquire org.gnome.DisplayManager: Connection ":1.14" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the config file"

```
I've tried dpkg-reconfigure gdm and apt-get purge gdm apt-get install gdm but no such luck, it still continues to deny me use of gdm, I have to use the recovery kernel :/

I actually had this issue right after installing the beta nvidia driver, but it seemed as if I had fixed it after removing the nvidia driver.  Now reinstalling the driver from the "Additional Drivers" application, this error has started up again.  Very obnoxious!  It seems I need a way of updating the gdm.conf file so I can access it, I've searched a bit online and all I've found is people saying they just reinstalled the OS... :-({|=

You have the 195 drivers from Lucid installed too, remove those and see what happens.

---

### Post by Peter7K on 2010-09-28
> **cariboo907 said:**
> You have the 195 drivers from Lucid installed too, remove those and see what happens.

How do I go about doing that?  I tried uninstalling and reinstalling, the Lucid driver is still there.

---

### Post by cariboo on 2010-09-28
Do they show up in synaptic?

---

### Post by Peter7K on 2010-09-28
Well "nvidia-current" shows up in synaptic.  I'm not really sure how I can have both lucid and maverick versions installed.  I can force the version in synaptic down to lucid but that would remove my Xorg and all of the things it depends on, etc.

---

### Post by mc4man on 2010-09-28
> Version table:
*** 256.53-0ubuntu3 0
500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted i386 Packages
100 /var/lib/dpkg/status
195.36.24-0ubuntu1~10.04 0
500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted i386 Packages

You don't have the 195 installed, it probable that it's (lucid-updates/restricted) still in your sources.list and or /var/lib/apt/lists -  that's why it's showing up in the 'version table:'

Ex. 
easy to recreate here
> doug@doug-desktop1:~$ apt-cache policy  nvidia-current
nvidia-current:
  Installed: 260.19.06-0ubuntu1~xup3
  Candidate: 260.19.06-0ubuntu1~xup3
  Version table:
 *** 260.19.06-0ubuntu1~xup3 0
        100 /var/lib/dpkg/status
     256.53-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted i386 Packages
     195.36.15-0ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted i386 Packages

---

### Post by sdowney717 on 2010-09-28
I downloaded the latest beta .run file and used that.
Boot to console
goto directory
run it as 
./namefile.run

let it do everything, you might get a symbolic link error, let it update the xorg config

sudo reboot

[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)

---

### Post by Peter7K on 2010-09-28
> **sdowney717 said:**
> I downloaded the latest beta .run file and used that.
Boot to console
goto directory
run it as 
./namefile.run

let it do everything, you might get a symbolic link error, let it update the xorg config

sudo reboot

[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)

This is precisely what I did that caused the problem to my gdm.conf in the first place, I'll try it again though :/

EDIT: Hallelujah, it worked this time!

Weird, I did the exact same procedure as last time.. ah well.  Thanks for the help. *Solved*

---

