---
title: "Install Ausus USB-N13 on Ubuntu with custom kernel"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by lucaghera on 2013-03-13
Hi all,

I would like to install the Asus USB-N13 wi-fi adapter on an industrial PC with a custom kernel.

The adapter usually works without problems and configurations on standard Ubuntu distro.

Can you help me in configuring the adapter on this pc?

Please find some useful info below.

Thanks in advance,
Luca

```
root@rh2c:~# uname -a
Linux rh2c 2.6.34.5-pal-m3d-rt #3 SMP Thu Aug 2 14:36:05 CEST 2012 i686 GNU/Linux
```
```
root@rh2c:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
```
```
root@rh2c:~# lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by praseodym on 2013-03-13
Install the driver with dkms according to this:

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=0b05%3A1784#Installation-ueber-DKMS](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=0b05%3A1784#Installation-ueber-DKMS)

P.S.: 10.04 is only supported until April!

---

### Post by lucaghera on 2013-03-13
Thanks,

however 

```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```

fails due to the custom kernel with the following error:

```
E: Couldn't find package linux-headers-2.6.34.5-pal-m3d-rt
```

Consequently also 

```
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
```

fails:

```
sudo dkms build -m Ralink_5370sta -v 2.5.0.3

Error! Your kernel headers for kernel 2.6.34.5-pal-m3d-rt cannot be found at
/lib/modules/2.6.34.5-pal-m3d-rt/build or /lib/modules/2.6.34.5-pal-m3d-rt/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.34.5-pal-m3d-rt package.
```

---

### Post by praseodym on 2013-03-13
Obviously, you are using a mainline kernel (realtime?!). Where did you get it from? The kernel headers should be there, too.

---

### Post by lucaghera on 2013-03-13
Yes,
it is a xenomai patched kernel. It was installed on the PC, however the headers are not there :-(

---

### Post by praseodym on 2013-03-13
What about:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```

---

### Post by lucaghera on 2013-03-13
I edited the previous post. Btw the command ```


sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```

fails with

```
E: Couldn't find package linux-headers-2.6.34.5-pal-m3d-rt
```

---

### Post by praseodym on 2013-03-13
Do you need this kernel urgently? If not, install the regular one:
```

sudo apt-get install linux-generic linux-headers-generic
```
Boot into this one and install the driver.

---

### Post by lucaghera on 2013-03-13
Yes, I need a real time kernel because the pc is controlling a machine.

---

