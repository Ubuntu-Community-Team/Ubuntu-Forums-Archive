---
title: "Problem installing NVIDIA driver package!"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by Richard.F on 2007-12-18
So I download a NVIDIA driver package from their website for my card.
It tells me you have to install it without running the X server. So I did this:
To enter a terminal:
```
CTRL+ALT+F1
```
Logged in.
Exitted the X server:
```
sudo /etc/init.5/gdm stop
```
Ran the driver package
```
sudo sh /path/file.run
```
Now, this happened:
```
No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site (ftp://download.nvidia.com)?
```
I clicked yes and then this:
```
No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.
```
I clicked yes and then this:
```
gcc-version-check failed:

Could not compile gcc-version-check.c. Please be sure you have your distribution's libc development package installed and that 'cc' is a valid C compiler name.

If you know what you are doing an want to ignore the gcc version check, Select "No" to continue installation. Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart the installation. Abort now?
```
I clicked no and this then this:
```
ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package.
```
Then:
```
ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

I really need help with this guys!

---

### Post by Whiffle on 2007-12-18
I think you need to 

```

sudo apt-get install build-essential

```

---

### Post by talon95 on 2007-12-18
Maybe you need to do step #2 in Method #2,

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2)

---

### Post by Richard.F on 2007-12-18
I tried both of your messages but this came up:
```
ERROR: Unable to determine the version of the kernel sources located in '/lib/modules/2.6.22-14-generic/build'. Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' RPM installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option.
```

---

### Post by skompier on 2007-12-19
Why not install Envy and let it do everything for you?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Richard.F on 2007-12-19
I'll try that.

---

