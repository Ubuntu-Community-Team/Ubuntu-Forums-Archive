---
title: "Graphics Help nVidia 8800 GTX on Precise 32bit"
date: 2012-05-21
forum: Multimedia Software
---

### Post by mythx on 2012-05-21
This is a pretty common problem that I can usually fix after a couple hours of fidgiting.  I seem to be having a tougher go at it this time though.

Like the title says, I'm running 12.04 32bit with nVidia 8800GTX graphics adapter.  A recent update that included updated packages for nvidia-current went without a hitch, until after reboot when only one monitor came up.  I did what I often have had to do in the past, and rip out the nVidia drivers and reinstall them via the Additional Drivers app.  That's no longer working.  I'm getting an error that refers me to the jockey.log file.  I'm not sure how to read the file, so I'm hoping someone here can help.

Below is the tail end of the install (when I first saw errors). The last 2 lines a couple minutes later are from an attempt to install again right after the error.  It seems some of the nvidia modules are installing, but the error comes at the end.

```

2012-05-21 20:27:33,951 DEBUG: install progress bamfdaemon 100.000000
2012-05-21 20:27:34,032 DEBUG: install progress initramfs-tools 100.000000
2012-05-21 20:27:53,769 DEBUG: Selecting previously unselected package nvidia-current.
(Reading database ... 221221 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_295.53-0ubuntu1~precise~xup1_i386.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_295.53-0ubuntu1~precise~xup1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (295.53-0ubuntu1~precise~xup1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Loading new nvidia-current-295.53 DKMS files...
Building for 3.0.0-12-generic and 3.2.0-24-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-24-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod..........

DKMS: install completed.
Setting up nvidia-settings (295.53-0ubuntu1~precise~xup1) ...
update-alternatives: warning: alternative /usr/lib/nvidia-settings-updates/ld.so.conf (part of link group nvidia_settings_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/nvidia_settings_conf is dangling, it will be updated with best choice.
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic

2012-05-21 20:27:54,503 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-21 20:27:54,504 WARNING: /sys/module/nvidia_current/drivers does not exist, cannot rebind nvidia_current driver
2012-05-21 20:30:47,742 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-21 20:30:47,744 WARNING: /sys/module/nvidia_current/drivers does not exist, cannot rebind nvidia_current driver

```

Anyway, thanks in advance for the help

Jason

---

### Post by overdrank on 2012-05-21
Moved to Multimedia & Video

---

### Post by mythx on 2012-05-21
> **overdrank said:**
> Moved to Multimedia & Video

Sorry, saw that after I posted.....

---

### Post by Nutria on 2012-05-21
> Setting up nvidia-current (295.53-0ubuntu1~precise~xup1) ...

Where did you get the package from?  It doesn't look like the stock version.

```
$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by mythx on 2012-05-21
> **Nutria said:**
> Where did you get the package from?  It doesn't look like the stock version.

```
$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
```

This was installed via the Additional Drivers utility.  Earlier I had attempted to install nvidia-current_295.40-0ubuntu1_i386.deb, but I believe I uninstalled that prior to attempting the most recent install.

Thanks

---

### Post by Nutria on 2012-05-21
> **mythx said:**
> This was installed via the Additional Drivers utility.

Hmmm.  GUIs are so black-box.

Please open a terminal window and run ```
apt-cache policy nvidia-current
```

Anyway, is the real problem that TwinView isn't activating your 2nd monitor?

---

### Post by mythx on 2012-05-22
> **Nutria said:**
> Hmmm.  GUIs are so black-box.

Please open a terminal window and run ```
apt-cache policy nvidia-current
```

Anyway, is the real problem that TwinView isn't activating your 2nd monitor?

Here's what I get.  Thanks for the response:

```
nvidia-current:
  Installed: 295.53-0ubuntu1~precise~xup1
  Candidate: 295.53-0ubuntu1~precise~xup1
  Version table:
 *** 295.53-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages

```

---

### Post by Nutria on 2012-05-22
> **mythx said:**
> Here's what I get.  Thanks for the response:

```
nvidia-current:
  Installed: 295.53-0ubuntu1~precise~xup1
  Candidate: 295.53-0ubuntu1~precise~xup1
  Version table:
 *** 295.53-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages

```

Since you've never had this kind of failure before, maybe, and I emphasize **maybe**, there's a bug in the package?

---

### Post by mythx on 2012-05-22
> **Nutria said:**
> Since you've never had this kind of failure before, maybe, and I emphasize **maybe**, there's a bug in the package?

I will entertain that.  I find the video drivers to be the most complicated aspect of Linux....how can I remove the NVIDIA stuff and install just what's minimally needed?  By minimally, id still like to play OpenGL games and stuff.

Thanks

---

### Post by Nutria on 2012-05-22
> **mythx said:**
> I will entertain that.  I find the video drivers to be the most complicated aspect of Linux....how can I remove the NVIDIA stuff and install just what's minimally needed?  By minimally, id still like to play OpenGL games and stuff.

To remove the nvidia binary, probably all that's needed is to install xserver-xorg-video-nouveau and nouveau-firmware then reboot.

OpenGL performance will stink, though.  You need the nvidia driver.

Using the nvidia driver has never been an issue for me.  Do I remember you mentioning a second monitor?

Maybe you could drop back to 295.40-0ubuntu1 from "restricted" and then open a thread on making TwinView work hassle-free.

---

### Post by mythx on 2012-05-22
> **Nutria said:**
> To remove the nvidia binary, probably all that's needed is to install xserver-xorg-video-nouveau and nouveau-firmware then reboot.

OpenGL performance will stink, though.  You need the nvidia driver.

Using the nvidia driver has never been an issue for me.  Do I remember you mentioning a second monitor?

Maybe you could drop back to 295.40-0ubuntu1 from "restricted" and then open a thread on making TwinView work hassle-free.

Yeah, I have a second monitor, though I don't think making it work is the problem.  When I install any of the nVidia drivers, I have problems, then when I launch the utility to configure the nVidia driver for X, it tells me the nVidia driver isn't loaded and I need to run nvidia-xconfig.  Running nvidia-xconfig seems to work alright, but it doesn't change anything.

Is 295.40-0ubuntu1 the ideal driver to use for the 8800GTX?

Anyway, thanks again for the help.  

Jason

---

### Post by Nutria on 2012-05-22
> **mythx said:**
> Yeah, I have a second monitor, though I don't think making it work is the problem.  When I install any of the nVidia drivers, I have problems, then when I launch the utility to configure the nVidia driver for X, it tells me the nVidia driver isn't loaded and I need to run nvidia-xconfig.  Running nvidia-xconfig seems to work alright, but it doesn't change anything.

Then how do you use the computer for those hours?   Using the 800x600 vesa driver?

Also, how long have you been having this problem?  IOW, when did it start?

> Is 295.40-0ubuntu1 the ideal driver to use for the 8800GTX?

It's the most tested version.

---

