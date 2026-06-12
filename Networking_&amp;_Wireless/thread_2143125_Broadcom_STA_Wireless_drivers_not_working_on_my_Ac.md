---
title: "Broadcom STA Wireless drivers not working on my Acer Aspire 5755G, Ubuntu 12.04 LTS"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by Nerph on 2013-05-07
Hello,

I realize there is a similar, if not nearly identical topic to this one, but I've posted there and while I got 1 reply, it seems it is no longer being watched, so I decided to make my own thread.

I've recently installed Ubuntu 12.04 LTS via wubi in Windows 7, the installation was successful and I can boot into Ubuntu, however I can not get the wireless drivers to install, below I shall list what I've already been asked to do and have tried, but hasn't fixed the issue.

Firstly, in the other topic, it was asked to do this command in the terminal:

```
lspci -nn | grep 0280
```

I did this, and this is the outcome:

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
```

It was then advised to do these commands:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```
and then
```
sudo modprobe wl
```

After trying this, I got the following errors:

[COLOR=#000000]Code:[/COLOR]

```
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
```

and 

```
FATAL: Module wl not found.
```

I was then advised to do this:

```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

but after doing the 2nd command (the `uname -r` one) I got this error, and then the same errors as previously stated:

```
Reinstallation of linux-headers-3.5.0-23-generic is not possible, it cannot be downloaded.
```

So I was wondering, is there anything else I can do, or am I going to have to just accept that I wont be able to get my wireless to work?

---

### Post by Nerph on 2013-05-11
Sorry to "bump" my own thread, but it seems other peoples help requests are actively being helped and I've not had a reply for 3 days, so I was just wondering if my thread had been missed.

---

### Post by chili555 on 2013-05-11
I wonder if this helps: [http://packages.ubuntu.com/precise-updates/linux-headers-3.5.0-23-generic](http://packages.ubuntu.com/precise-updates/linux-headers-3.5.0-23-generic)

Be sure to get the 32- or 64-bit package as appropriate:```
arch
```Once you have the package downloaded to your Desktop, open a terminal and do:```
sudo dpkg -i Desktop/linux-headers-*.deb
```Then try again:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by Nerph on 2013-05-11
when installing the downloaded .deb file, using the "sudo dpkg -i <filename>" command, I just get the same error as I've been getting before:

```

ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.

```

I'm guessing this means my laptop doesn't support the required files needed to get my wireless to work or? I'm confused.

---

### Post by chili555 on 2013-05-11
> I'm guessing this means my laptop doesn't support the required files needed to get my wireless to work or? I'm confused. Not quite yet. It ain't over until Chili says it's over! Let's do some deeper diagnostics:```
lsb_release -a
uname -a 
ls /boot | grep vml
```Thanks.

---

### Post by Nerph on 2013-05-11
Ok, here comes the info:

```
lsb_release -a
```

gave this output:

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
```

-

```
uname -a
```

gave this output:

```
Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

-

```
ls /boot | grep vml
```

gave this output:

```
vmlinuz-3.2.0-23-generic
vmlinuz-3.5.0-23-generic
vmlinuz-3.5.0-23-generic.efi.signed
```

---

### Post by chili555 on 2013-05-11
Looks pretty solid. Let's see:```
cat  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log 
```Can you get a temporary wired ethernet connection so you can update and get the latest kernel version?

---

### Post by Nerph on 2013-05-11
Result of running "cat  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log":

```

DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.5.0-23-generic (x86_64)
Sat May 11 17:29:22 CEST 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'

```

I am currently using a wired ethernet connection to reply to you, so I can definitely stay connected and update to the latest kernel version, just let me know what to do!

---

### Post by chili555 on 2013-05-11
Please try:```
sudo apt-get update && sudo apt-get -y upgrade
```You should get, as one of the upgrades, a newer kernel version, also known as linux-image. Reboot and then try again:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by Nerph on 2013-05-11
Success! I didn't see anything called linux-image while the update was running in terminal, but it was moving so fast I probably missed it. Once it was done, I rebooted, did the "sudo apt-get install --reinstall bcmwl-kernel-source" command and my wifi light suddenly turned on! Did "sudo modprobe wl" as well, not sure what that does but my wifi stayed on, and I am now posting this reply via wifi!

Thank you so much for your patience and brilliant support!

---

### Post by chili555 on 2013-05-11
I'm glad it's working! Have fun!

---

