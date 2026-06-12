---
title: "Network card working on 10.04 32bit but not working on 10.04 64bit!"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by CyberAngel on 2011-07-25
I have a very weird problem!!!
I had an Ubuntu Server 32 bit installation and everything was working fine.
Now that I installed Ubuntu Server 64bit on a new drive in the same machine, the ethernet card is not working!! This is insane cause when I put the hard disk with the 32bit installation back and booting from it, the ethernet card is working without any problems but in the 64bits installation it is not shown at all using "ifconfig -a"

lspci output:
> 02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)

How can I check which module is being loaded in the 32bits installation to try to load it manually in the 64 bits installation?

---

### Post by wildmanne39 on 2011-07-25
Hi, that is because the driver for that ethernet card has to be dowload and compiled.

I believe this card wants the module atl1c. I'd download the tarball for compat-wireless. [http://wireless.kernel.org/en/users/...ng_the_tarball](http://wireless.kernel.org/en/users/...ng_the_tarball)

Install linux-headers and build-essential: I think they're on the CD or DVD. Extract the package and do:
```
cd Desktop/compat
```
Press the Tab key so the rest fills in.
```
./scripts/driver-select atl1c
make
sudo make install
sudo modprobe atl1c
```

To install the linux-headers and build-essential you can use a livecd.
Open Synaptic Package Manager
go to Settings>Repositories select/click the CD on in the box
Then search in the Synaptic search box for the packages below
install the build-essential and linux-headers-generic

---

### Post by CyberAngel on 2011-07-25
> **wildmanne39 said:**
> Hi, that is because the driver for that ethernet card has to be dowload and compiled.

I believe this card wants the module atl1c. I'd download the tarball for compat-wireless. [http://wireless.kernel.org/en/users/...ng_the_tarball](http://wireless.kernel.org/en/users/...ng_the_tarball)

Install linux-headers and build-essential: I think they're on the CD or DVD. Extract the package and do:
```
cd Desktop/compat
```
Press the Tab key so the rest fills in.
```
./scripts/driver-select atl1c
make
sudo make install
sudo modprobe atl1c
```

To install the linux-headers and build-essential you can use a livecd.
Open Synaptic Package Manager
go to Settings>Repositories select/click the CD on in the box
Then search in the Synaptic search box for the packages below
install the build-essential and linux-headers-generic


Thank you for the info!!
Didn't need to compile anything!
The package "linux-backports-modules-compat-wireless-2.6.38-2.6.32-33-server" which I had already installed in the 32 bits installation did the trick!

I thought that this was only containing wireless drivers though :/

---

### Post by wildmanne39 on 2011-07-25
Hi, no it contains the the driver you needed for your ehternet also.

I am glad you got it working.

---

