---
title: "HIDPoint on 10.04"
date: 2010-05-18
forum: Multimedia Software
---

### Post by frogbrains on 2010-05-18
Hello.

Bought a lovely new Logitech MX3200 keyboard recently, didn't expect to be able to use all the media keys on it.  I was surprised, then, when I discovered HIDPoint, some software for configuring the hotkeys on many Logitech keyboards, and more surprised when I saw that mine was on the supported devices list.  Anyway, HIDPoint is only available for up to Ubuntu 9.10, and refuses to install properly in 10.04.

Here is the output when I try to run the installer:
```
adam@adam-laptop:~$ sudo ./hidpoint1-0.bin
Verifying archive integrity... All good.
Uncompressing HIDPoint1.0 (Beta) Build 100310 Setup....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................



Welcome to the HIDPoint Installation.
Please wait while the installer extracts the files to a temporary folder.

HIDPoint Installer has successfully extracted the installation
files to : /tmp/selfgz2554
The installer needs to have admin priviliges to copy files
to /usr/bin and load the driver.
Please run the hidpoint1-0.bin file using the sudo command.
  (ignore if you ran hidpoint1-0.bin file using the sudo command)


sudo ./hidpoint1-0.bin


Running the hidpoint-1.0 using the sudo command will not require you to enter
the admin password.
If your have any questions about the install please visit
our website http://www.hidpoint.com


Do you wish to continue with the Installation? [Y/n] and hit enter y
Creating symbolic links for libpng
ls: cannot access /usr/lib/libpng12.so*: No such file or directory
Gathering System information and generating a log
Launching HIDPoint Installer
./hidpointsetup: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```

I can't find libpng.so.3 in Synaptic, so what should I do to get this program to install?

---

### Post by hjrosasq on 2010-05-31
Is just the link of the library, just type 

sudo ln -s /lib/libpng12.so.0 /usr/lib/

And it's done!

---

### Post by Tirish Anau on 2011-02-03
Same here fix offered didn't seem to work.... any other suggestions?

---

### Post by supremazy on 2011-06-04
Hi there, i found the solution.

Before you install hidpoint you must install the libpng12 and libpng3 packages.Try these commands

For xubuntu

```
apt-get install libpng12-0
```

```
apt-get install libpng3
```

For ubuntu

```
apt-get install libpng12
```

```
apt-get install libpng3
```

and try the hidpoint install.

---

