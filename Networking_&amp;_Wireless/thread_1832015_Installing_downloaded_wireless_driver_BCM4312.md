---
title: "Installing downloaded wireless driver BCM4312"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by phacer on 2011-08-24
I just installed Ubuntu 11.04 on my Dell Mini 10v and for some reason I just realized that my wired network connection is not working for some reason. And not in windows either. But my wireless works in windows. So I have downloaded the latest Broadcom STA wireless drivers for linux and have tried to follow [this]("http://ubuntuforums.org/showthread.php?t=896713") tutorial to install it. But when I get to:

make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
I can't get it to work. It says:

make: Entering directory '/usr/src/linux-header-2.6.38-8-generic' 
scripts/Makefile.build:44: /usr/src/linux-header-2.6.38-8-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target '/usr/src/linux-header-2.6.38-8-generic/pwd/Makefile'. Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory '/usr/src/linux-header-2.6.38-8-generic'

I'm new to linux so any help would be appreciated. And as mentioned above I have no internet connection at all right now. 

Regards
André

---

### Post by westie457 on 2011-08-24
> **phacer said:**
> I just installed Ubuntu 11.04 on my Dell Mini 10v and for some reason I just realized that my wired network connection is not working for some reason. And not in windows either. But my wireless works in windows. So I have downloaded the latest Broadcom STA wireless drivers for linux and have tried to follow [this]("http://ubuntuforums.org/showthread.php?t=896713") tutorial to install it. But when I get to:

make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
I can't get it to work. It says:

make: Entering directory '/usr/src/linux-header-2.6.38-8-generic' 
scripts/Makefile.build:44: /usr/src/linux-header-2.6.38-8-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target '/usr/src/linux-header-2.6.38-8-generic/pwd/Makefile'. Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory '/usr/src/linux-header-2.6.38-8-generic'

I'm new to linux so any help would be appreciated. And as mentioned above I have no internet connection at all right now. 

Regards
André

Hi, that will not work mainly because it is the wrong driver.

Take a look [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"). This will guide you to the correct driver for your wireless card.

If it confuses you come back here for more guidance.

Also you will need a working wired connection to do this.

---

### Post by praseodym on 2011-08-24
Hello,

if you dont have any internet connection you can install the Broadcom-STA-driver from the installation-CD/DVD. Just install the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source** by double-clicking or add the CD as a repository and install the packages via the synaptic package manager. After that you should be able to activate the driver via "Additional Drivers"

---

### Post by phacer on 2011-08-24
Yeap, that is confusing. 

Started following the STA - No Internet Access

I guess I have to access the usb I installed ubuntu from. But how do I do that from the terminal?

---

### Post by praseodym on 2011-08-24
You can also download the packages for 32 or 64 bit from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by phacer on 2011-08-24
> **praseodym said:**
> Hello,

if you dont have any internet connection you can install the Broadcom-STA-driver from the installation-CD/DVD. Just install the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source** by double-clicking or add the CD as a repository and install the packages via the synaptic package manager. After that you should be able to activate the driver via "Additional Drivers"

Where do I find patch, fakeroot and bcmwl-kernel-soruce on the usb?

---

### Post by westie457 on 2011-08-24
> **phacer said:**
> Yeap, that is confusing. 

Started following the STA - No Internet Access

I guess I have to access the usb I installed ubuntu from. But how do I do that from the terminal?

No need to access the usb from the terminal. Do it from the normal desktop.and use nautilus to navigate your way to the required files that are on the usb. Double clicking them will open up the Software Centre to install them. You will need to provide your password.
Once you have a wired connection working to get wireless you will need to install the correct driver for your card. The STA driver is definitely the wrong one to run wireless.

---

### Post by praseodym on 2011-08-24
BCM4312 with chipset 14e4:4315  can work from Kernel 2.6.38 with the native b43 driver, no guarantee for that. See: [http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices)

---

### Post by phacer on 2011-08-24
Thanks for your help and quick answers guys!

Wireless is now working! Normal wired connection still not working! But I think it's a hardware problem.

---

### Post by westie457 on 2011-08-24
> **phacer said:**
> Thanks for your help and quick answers guys!

Wireless is now working! Normal wired connection still not working! But I think it's a hardware problem.

It probably is a hardware issue for the wired connection. So there will be no harm at all if you install the 'b43-fwcutter' package either from the usb or the repositories.

Quick way from the repos is to open a terminal and type in ```
sudo apt-get install b43-fwcutter
```

It might kick your wired connection into life.

---

### Post by praseodym on 2011-08-24
Can you show the following outputs for your wired card:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /var/lib/NetworkManager/NetworkManager.state
```

---

