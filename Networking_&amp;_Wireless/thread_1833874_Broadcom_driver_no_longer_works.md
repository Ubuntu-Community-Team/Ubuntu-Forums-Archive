---
title: "Broadcom driver no longer works"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by NoBugs! on 2011-08-26
I tried the Ubuntu 2.6.38 kernel in the Lucid repository, and the broadcom wifi driver didn't work. After switching to the old kernel, I still have problems, after installing-reinstalling some packages I can go to hardware drivers and click "Activate" broadcom driver, it says 

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

The log ends with:
```

2011-08-26 14:14:13,829 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:14:13,860 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:14:13,916 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:14:44,979 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:14:47,352 DEBUG: Installing package: bcmwl-kernel-source
2011-08-26 14:14:49,667 WARNING: modinfo for module wl failed: ERROR: modinfo: could not open /lib/modules/2.6.32-33-generic/updates/dkms/wl.ko: No such file or directory

2011-08-26 14:14:49,669 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-08-26 14:14:49,731 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:20:11,867 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:20:11,936 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:20:11,995 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:21:53,278 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-26 14:21:59,052 DEBUG: Installing package: bcmwl-kernel-source
2011-08-26 14:21:59,940 WARNING: modinfo for module wl failed: ERROR: modinfo: could not open /lib/modules/2.6.32-33-generic/updates/dkms/wl.ko: No such file or directory

2011-08-26 14:21:59,940 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-08-26 14:22:00,015 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

---

### Post by wildmanne39 on 2011-08-26
Hi, please run these commands and post the results here:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
lsmod | grep b43
```
Thank you

---

### Post by NoBugs! on 2011-08-26
lshw shows the card:

```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0

```

```
$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

pan0      no wireless extensions.

vboxnet0  no wireless extensions.

```

"lsmod | grep b43" gives no output.

---

### Post by wildmanne39 on 2011-08-26
Hi, please post the results of:
```
lsmod
```
```
lspci -nn | grep 0280
```
```
dmesg | grep wlan0
```
```
sudo lshw -C network
```
please include all the information, please do not edit.
Thank you

---

### Post by praseodym on 2011-08-26
Did you install the kernel-headers, too? Is that the "backported"-Kernel or one from the mainline-kernel-archive?

If the first, then reinstall all components when booted into that kernel:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-generic-lts-backport-natty linux-headers-$(uname -r) dkms patch fakeroot bcmwl-kernel-source
```

If the latter install both header-files of that kernel from that archive.

---

### Post by northd_tech on 2011-08-26
> **NoBugs! said:**
> lshw shows the card:

```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
"lsmod | grep b43" gives no output.
I'm fairly sure that a Broadcom 4328 should be using the "proprietary STA" driver that should be available under System > Administration > Hardware Drivers.

Does the "Broadcom STA wireless driver" show as "Activated and currently in use" if you have a cable connection (the easiest/fastest way to fix this IMHO).

If you can't get it activated for some reason or if you cannot get a cabled ethernet connection, let's see the output of the following terminal commands:

[CODE]
lspci -vvnn | grep 14e4
lsmod | grep wl
dmesg | grep wl

```FWIW, I'm using a Broadcom [4321AG]"4328" to wirelessly post this using the Broadcom STA driver.  

If you prefer to try compiling from Broadcom's proprietary sourcecode, that should be found here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by wildmanne39 on 2011-08-26
Hi, because he updated to the new kernel it probably gave it the same issue 11.04 has and that is that the sta drivers do not work for that kernel in 11.04.

---

### Post by northd_tech on 2011-08-26
If this is an 11.xx specific problem, then I'd try compiling from the Broadcom source (that's how I did it from Ubuntu 8.xx up through and including 10.xx when the STA won't activate for whatever reason).  Of course that will require the **build-essential** (and applicable kernel **linux-headers-2.6-.**xxxx) packages to be installed first for each and every kernel that needs to be 'wireless.'  The installer script was pretty good at "barking" about whatever was missing though, as I recall.  Of course, sourcecode compilation is probably THE LEAST "user-friendly" way to fix it, and possibly one of the slower ways too.

Here's an Ubuntuforums staff member who appears to have a Broadcom 4312 running under 11.10 with the proprietary "STA" driver (which uses the "wl" driver module), though:

[http://ubuntuforums.org/showpost.php?p=11190286&postcount=3](http://ubuntuforums.org/showpost.php?p=11190286&postcount=3)

---

### Post by northd_tech on 2011-08-26
> **NoBugs! said:**
> I tried the Ubuntu 2.6.38 kernel in the Lucid repository, and the broadcom wifi driver didn't work. After switching to the old kernel, I still have problems, [COLOR=Red]after installing-reinstalling some packages[/COLOR] I can go to hardware drivers and click "Activate" broadcom driver, it says 

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

The log ends with:
2011-08-26 14:21:59,052 DEBUG: Installing package: bcmwl-kernel-source
2011-08-26 14:21:59,940 WARNING: modinfo for module wl failed: **ERROR: modinfo: could not open /lib/modules/2.6.32-33-generic/updates/dkms/wl.ko: No such file or directory**

2011-08-26 14:21:59,940 **WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver**
2011-08-26 14:22:00,015 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

Can you go into Synaptic package manager and post what packages are installed when you enter "b43" in the Quick Search bar?

Also the same when you enter "broadcom" in the same Quick Search bar of Synaptic Package Mgr (it might be easier to take a couple of screenshots and post those here).

For some reason, your "wl" module is not inserting under that 2.6.32-33 kernel from what I read in the **bolded** part- I suspect you might have "wl" blacklisted somewhere under [COLOR=Blue]/etc/modprobe.d/

[COLOR=Black]EDIT:  This pinned thread might also be worth reading:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

and this Broadcom Ubuntu documentation page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers")

EDIT2:  I just noticed that this thread was tagged "lucid"- is it really Lucid Lynx 10.04?   (Because that should work perfectly for a Broadcom 4328 just like mine under Lucid Lynx 10.04.3 LTS /n /l with the "STA" driver). Can you post the results of the following commands also?

[/COLOR][/COLOR]```
cat /etc/issue

cat /etc/lsb-release
```

---

### Post by NoBugs! on 2011-09-01
Searching for "b43" I only see b43-fwcutter. 
Searching for "broadcom" packages, I found:
bcmwl-kernel-source
b5700-source
broadcom-sta-common
broadcom-sta-source
b43-fwcutter
bcmwl-modaliases

Yes, this is Ubuntu 10.04.3 LTS, as shown in lsb-release.

---

### Post by wildmanne39 on 2011-09-01
Hi, try this please:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source bcmwl-modaliases
```
Then run
```
sudo apt-get --purge autoremove
```
Then restart your computer and run
```
sudo apt-get install b43-fwcutter
```
when it is done unplug your wired connection and restart your computer if it still does not work please post the results of
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by NoBugs! on 2011-09-01
I found the answer [here]("http://ubuntuforums.org/showthread.php?t=1693904"). I installed linux-headers-generic-lts-backport-natty and linux-image-generic-lts-backport-natty, and the [newer bcmwl-kernel-source]("http://packages.ubuntu.com/natty/bcmwl-kernel-source").

After restart, Broadcom STA Driver shows up as enabled and it works!

---

### Post by wildmanne39 on 2011-09-02
Hi, glad you got it working.

---

