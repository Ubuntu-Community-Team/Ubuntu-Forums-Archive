---
title: "[SOLVED] Cannot connect to Creative Zen X-Fi mp3 player"
date: 2008-08-20
forum: Multimedia Software
---

### Post by lavinog on 2008-08-20
I just bought a Creative Zen X-Fi 8mb portable media player.
I cannot seem to connect it with ubuntu.
It works on one of my winXP machines, but I would like to get it to connect to Ubuntu.
I have tried:
```

~$ lsusb
Bus 007 Device 019: ID 041e:4162 Creative Technology, Ltd 

~$ mtp-detect
libmtp version: 0.2.6.1

Attempting to connect device(s)
Detect: No Devices have been found


~$ mkdir zen
~$ mtpfs zen
~$ cd zen
bash: cd: zen: Transport endpoint is not connected

```

This device is pretty new, and I am sure support for it will improve. In the meantime has anyone had any success with it?

---

### Post by lavinog on 2008-08-20
I solved my own issue.
I added the following to **/etc/udev/rules.d/45-libmtp7.rules**
```

# Creative ZEN X-Fi 8GB
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

```
Then rebooted and now i can mount my zen

---

### Post by wpiter on 2008-08-22
Hi, I'm to having troubles with the Zen X-Fi (16 GB version)

I used your fix, direct copy paste, since the ID is the same.

However when i rebooted, and once again
```

wouter@wouter-laptop:~$ lsusb
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 041e:4162 Creative Technology, Ltd
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
wouter@wouter-laptop:~$ mtp-detect
libmtp version: 0.2.6.1

Attempting to connect device(s)
Detect: No Devices have been found
wouter@wouter-laptop:~$ mkdir zen
mkdir: cannot create directory `zen': File exists
wouter@wouter-laptop:~$ mtpfs zen
fuse: bad mount point `zen': Transport endpoint is not connected
wouter@wouter-laptop:~$ cd zen
bash: cd: zen: Transport endpoint is not connected
wouter@wouter-laptop:~$
```

how do i proceed from here, how do i mount the bloody thing. It is giving me a headache and making me wish i got a cowon D2

---

### Post by lavinog on 2008-08-22
> **wpiter said:**
> Hi, I'm to having troubles with the Zen X-Fi (16 GB version)

I used your fix, direct copy paste, since the ID is the same.

However when i rebooted, and once again


how do i proceed from here, how do i mount the bloody thing. It is giving me a headache and making me wish i got a cowon D2

It worked on my 64 bit machine, but later when I tried it on my 32-bit machine I got a similar issue.

I submitted the bug to libmtp development.

There is a newer version of libmtp, I am going to try that and see if it improves it.

---

### Post by lavinog on 2008-08-22
I think I see the issue:
/etc/udev/rules.d/45-libmtp7.rules has two sections: libmtp_usb_rules and libmtp_usb_device_rules

on my 64-bit machine I added the line in the device_rules section and on the others I added a line in the usb_rules section.

make sure you add a line in both sections. 

```

LABEL="libmtp_usb_rules"
# Creative ZEN X-Fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

```

```

LABEL="libmtp_usb_device_rules"
# Creative ZEN X-Fi
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

```

You may need to edit /etc/udev/libmtp.rules also to have this line:
```

LABEL="libmtp_rules"

# Creative Zen X-Fi
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

```

After that you should reboot and test with mtp-detect and mtpfs.

As of right now mtpfs is giving me a **fuse: failed to open /dev/fuse: Permission denied** message on my 32 bit machines...I need to see why it worked on my 64bit machine or see if updating libmtp helps.

---

### Post by wpiter on 2008-08-25
mtpfs is working like a charm at the moment, so I'm able to copy pasta files to my zen x-fi. This is how it is done:

[http://www.anythingbutipod.com/forum/showthread.php?t=32817](http://www.anythingbutipod.com/forum/showthread.php?t=32817)

simply create a mount point for your device in /media/MyZen
mount your Zen
transfer your files
unmount your Zen

easy as cake

---

### Post by lavinog on 2008-08-25
> **wpiter said:**
> so I'm able to copy pasta files to my zen x-fi.

pasta files?

That is pretty much what I was doing, I didn't try the -o allow_other option, but it works on my main machine just fine...I'll try the allow_other thing tomorrow on my 32bit machine.

---

### Post by wpiter on 2008-08-25
drag 'n drop / dragon drop
copy paste / copy pasta

[IMG]http://http://www.zorg.ch/files/17/250px-Copy-Pasta.jpg[/IMG]

---

### Post by b3n87 on 2008-09-22
Hi guys, just thought I'd add my two cents.

To get a friends Zen working I plugged it in with the USB cable, it then started charging but nothing else happened. So i started up Rhythmbox with the MTP plugin enabled and the Zen mounted through Rhythmbox and I started transferring files. This was all done without installing a libmtp file or anything like that. 

Hope this helps

---

### Post by labinnsw on 2010-11-13
> **lavinog said:**
> You may need to edit /etc/udev/libmtp.rules also to have this line:
```

LABEL="libmtp_rules"

# Creative Zen X-Fi
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

```

After that you should reboot and test with mtp-detect and mtpfs.

Since "/etc/udev/libmtp.rules" does not exist and nothing else is working. I will try to create it. What's the worst that can happen?; it doesn't work? Well I will take the risk because it might work.

---

### Post by lavinog on 2010-11-13
> **labinnsw said:**
> Since "/etc/udev/libmtp.rules" does not exist and nothing else is working. I will try to create it. What's the worst that can happen?; it doesn't work? Well I will take the risk because it might work.

A lot has changed since then.
What version of ubuntu are you using?

---

### Post by labinnsw on 2010-11-14
Thanks for responding

I am using Lucid. I did create the rule but after reading the readme in /etc/udev/rules.d, I moved it to /lib/udev/rules.d. Either way, it made no difference. I should also mention that my Zen is a Style 300 4GB. (with product ID 2016, which I changed accordingly.)

_**Edited to add new information**_
I reread the README and made some changes. I have attached the new rules which are now saved in etc/udev/rules.d.

Still I get this.
```
labinnsw@UbuntuLTS-desktop:~$ mtp-detect
libmtp version: 1.0.1

Listing raw device(s)
   No raw devices found.
labinnsw@UbuntuLTS-desktop:~$ 

```

It is recognized as a Flash drive, I want it to be recognized as a PDE device.

---

### Post by labinnsw on 2011-02-13
[Problem solved.]("http://ubuntuforums.org/showthread.php?p=10181043#post10181043") Well not really, an acceptable workaround was found.

---

