---
title: "config help needed to run driver installer, or advice on what I'm doing wrong"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by Mock Force on 2010-11-17
Important information:
Comp - dell Inspiron e1705
OS - Win 7/ Ubuntu 8.04 w/ Kernel 2.6.22.19
Wireless Card - intel/pro Broadcom Wireless 3945ABG

Hey I'm trying to get my wirless card working with Ubuntu ver. 8.04 kernel 2.6.22.19(I'm need this particular version for research I'm doing) and I have figured the problem is a driver issue.

I started off using this [guide]("http://ubuntuforums.org/showthread.php?t=112526") to install the ndiswrapper, and tried to install the driver which was provided from dell(I use an Inspiron e1705 dual booted with Win 7), which didn't work. and then I downloaded the driver designed especially for my card(intel/pro Wireless 3945ABG)from [intellinux]("http://www.intellinuxwireless.org/?n=Downloads"). So I figured the .inf and .sys files would be explicitly provided but they weren't and instead the [readme]("http://www.intellinuxwireless.org/tar.php?p=iwlwifi&f=README.iwlwifi-3945-ucode&a=iwlwifi-3945-ucode-15.32.2.9.tgz") says I need to use the firmware bootloader, which requires udev and hotplug be configured, but gives no instructions on how to configure these things or what changes need to be made.

Either I'm on the right track to getting the driver installer working and the problem fixed, I just need the driver .inf and .sys files and to follow the tutorial guide aforementioned, or I'm going in the wrong direction.

I really need help, I posted once before in the hardware/laptops section of the forum and got a response that didn't work.

---

### Post by chili555 on 2010-11-17
> I have figured the problem is a driver issue.How so?

The Intel 3945ABG works out of the box in 8.04 and doesn't need ndiswrapper. If it's not working for you, something else is wrong. Please post:```
lsmod | grep dell
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by Mock Force on 2010-11-17
the commands you told me to execute did nothing and rfkill wasn't even a recognized command. What are these supposed to show?

scott@scott-laptop:~$ lsmod | grep dell
scott@scott-laptop:~$ rfkill list all
bash: rfkill: command not found
scott@scott-laptop:~$ dmesg | grep iwl
scott@scott-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  273124  10 
af_packet              24968  2 
i915                   25984  2 
drm                    84116  3 i915
binfmt_misc            12936  1 
rfcomm                 42392  2 
l2cap                  26368  13 rfcomm
ppdev                  10500  0 
acpi_cpufreq           10824  1 
cpufreq_powersave       2944  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8328  0 
video                  17544  0 
sbs                    19592  0 
battery                11012  0 
dock                   10760  0 
button                  8976  0 
container               5632  0 
iptable_filter          4096  0 
ip_tables              14180  1 iptable_filter
x_tables               16516  1 ip_tables
ac                      6276  0 
ndiswrapper           193436  0 
sbp2                   24072  0 
parport_pc             36772  0 
lp                     12708  0 
parport                37960  3 ppdev,parport_pc,lp
iTCO_wdt               12068  0 
hci_usb                18332  2 
joydev                 11456  0 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
iTCO_vendor_support     5124  1 iTCO_wdt
serio_raw               8324  0 
sdhci                  18828  0 
shpchp                 34836  0 
mmc_core               28548  1 sdhci
psmouse                40208  0 
pcspkr                  4352  0 
intel_agp              25620  1 
pci_hotplug            32960  1 shpchp
agpgart                35272  3 drm,intel_agp
evdev                  11392  5 
ext3                  134920  1 
jbd                    59944  1 ext3
mbcache                 9860  1 ext3
sg                     36892  0 
sr_mod                 17956  0 
cdrom                  38048  1 sr_mod
sd_mod                 30848  3 
ata_generic             8836  0 
ohci1394               36400  0 
ieee1394               96696  2 sbp2,ohci1394
b44                    28300  0 
mii                     6656  1 b44
ehci_hcd               35980  0 
ata_piix               16004  2 
libata                128240  2 ata_generic,ata_piix
scsi_mod              147212  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26896  0 
usbcore               137860  5 ndiswrapper,hci_usb,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32008  2 acpi_cpufreq,thermal
fan                     5892  0 
fuse                   47124  3 

as to why I believe it's a driver issue, I was under the impression that driver information was contained within the Kernel, the Intellinux site said the kernels older than 2.6.24 don't come with the wireless driver software.

---

### Post by chili555 on 2010-11-17
> kernels older than 2.6.24 don't come with the wireless driver software.It sure did when I ran 8.04.

When a command returns nothing it either means 'command executed and no errors to report' or if it's a diagnostic tool, it means 'nothing to report.' rfkill is a somewhat new tool; I don't still have the 2.6.24 kernel on my machine, so I was guessing a bit there.

Your lsmod indicates that ndiswrapper is already installed. What does this tell us?```
ndiswrapper -l 
```That's an l for list.

The module used to be known as ipw3945; let's check that:```
sudo modprobe ipw3945
dmesg | grep 3945
```While you do that, I am going to look for a live CD for 8.04. If I can, I will load it up and we'll work this through together.> that driver information was contained within the KernelCorrect.

---

### Post by chili555 on 2010-11-17
The best I could do is 8.10. What a blast from the past! As of then, the module was named iwl3945.> $ locate 3945.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.koI don't recall when the module changed from ipw3945 to iwl3945, so, try both.

---

### Post by Mock Force on 2010-11-17
here's the output

scott@scott-laptop:~$ ndiswrapper -l
scott@scott-laptop:~$ sudo modprobe ipw3945
[sudo] password for scott: 
FATAL: Module ipw3945 not found.
scott@scott-laptop:~$ dmesg | grep 3945

thanks for your help on this by the way.

---

### Post by Mock Force on 2010-11-17
scott@scott-laptop:~$ sudo modprobe iwl3945
FATAL: Module iwl3945 not found.

also not found.

---

### Post by chili555 on 2010-11-17
Please post:```
 ls /lib/modules/`uname -r`/kernel/drivers/net/wireless

```We'll find it...or build it.

Those tickmarks are on the same key with ~.

---

### Post by Mock Force on 2010-11-17
scott@scott-laptop:~$ ls /lib/modules/`uname -r`/kernel/drivers/net/wireless
airo_cs.ko   atmel_pci.ko  ipw2200.ko     prism54         wavelan.ko
airo.ko      bcm43xx       libertas       ray_cs.ko       wl3501_cs.ko
arlan.ko     hermes.ko     netwave_cs.ko  spectrum_cs.ko  zd1201.ko
atmel_cs.ko  hostap        orinoco_cs.ko  strip.ko        zd1211rw
atmel.ko     ipw2100.ko    orinoco.ko     wavelan_cs.ko

---

### Post by chili555 on 2010-11-17
Man! That's a mighty slim folder.

In System > Administration > Synaptic, do you see a package called linux-backports-modules-generic? I believe it contains an updated (or, evidently a new) iwl3945. If so, please install it and then do:```
sudo modprobe iwl3945
```

---

### Post by Mock Force on 2010-11-17
I found multiple iterations of the folders similar to the one you described, all of which had another descriptor in the package name. the way they were layed out was something like what I have below

linux-backports-modules-2.6.24..(here was a number between 16 and 28)-generic
linux-backports-modules-hardy-generic

should I install the one with hardy or one of the others?

---

### Post by chili555 on 2010-11-17
> linux-backports-modules-hardy-genericIt will pull in the one(s) you need. Afterwards, try:```
sudo modprobe iwl3945
```

---

### Post by Mock Force on 2010-11-17
I installed the version with hardy like you said and now the version of backports currently installed is 2.6.24.28.30 according to the synaptic, 

scott@scott-laptop:~$ sudo modprobe iwl3945
[sudo] password for scott: 
FATAL: Module iwl3945 not found.
scott@scott-laptop:~$ sudo modprobe ipw3945
FATAL: Module ipw3945 not found.

this is the output after installing the backport.

---

### Post by chili555 on 2010-11-17
Is there a package in there, linux-backports-modules-2.6.24-28-generic?

[http://packages.ubuntu.com/hardy-updates/i386/linux-backports-modules-2.6.24-28-generic/filelist](http://packages.ubuntu.com/hardy-updates/i386/linux-backports-modules-2.6.24-28-generic/filelist)

> --- snip ---
/lib/modules/2.6.24-28-generic/updates/ipw2100.ko
/lib/modules/2.6.24-28-generic/updates/ipw2200.ko
**/lib/modules/2.6.24-28-generic/updates/iwl3945.ko**
/lib/modules/2.6.24-28-generic/updates/iwl4965.ko
/lib/modules/2.6.24-28-generic/updates/iwlcore.ko
/lib/modules/2.6.24-28-generic/updates/lbm-iwl-cfg80211.ko
/lib/modules/2.6.24-28-generic/updates/lbm-iwl-mac80211.ko
etc., etc.
I don't understand. I will google...

---

### Post by Mock Force on 2010-11-17
yes it installed when I selected "linux-backports-modules-hardy-generic" to be installed. this is what I see in the synaptic now

[IMG]http://www.facebook.com/photo.php?fbid=456270622514&set=a.456270582514.242938.516582514#%21/photo.php?pid=5339093&id=516582514[/IMG]

sorry about the quality of the pic, and that it's from fb.

---

### Post by Mock Force on 2010-11-17
[http://www.facebook.com/photo.php?fbid=456270622514&set=a.456270582514.242938.516582514#!/photo.php?pid=5339093&id=516582514](http://www.facebook.com/photo.php?fbid=456270622514&set=a.456270582514.242938.516582514#!/photo.php?pid=5339093&id=516582514)

here the link to the photo I was refering to

---

### Post by Mock Force on 2010-11-17
here another thing that may be interesting or of importance

scott@scott-laptop:~$ locate iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-28-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko

I believe the iwl3945.ko is the driver file needed to use Wifi, it actually is located within the kernel version I just installed. Perhaps I need to uninstall the other generic package I see present in my system?

---

### Post by chili555 on 2010-11-17
What is your running kernel version (he asked, smelling a rat)?```
uname -r
```I wonder if your kernel is NOT 2.6.24-28-generic. I wonder if it is -server or -somethingelse. I would have thought that installing linux-backports-modules-hardy-generic  would have figured that all out for us.

PS- I love your FB profile!

---

### Post by Mock Force on 2010-11-18
I already know my kernel isn't 2.6.24-28. I put my kernel version in my first post because I figured that was important.

scott@scott-laptop:~$ uname -r
2.6.22.19

I'm using this version because a program I'm going to be using for research requires this version be run in order to operate properly.

When I boot up my computer I'm able to use the old kernel version still and my wifi works on that version. I only recently tried the old kernel boot up.

---

### Post by chili555 on 2010-11-18
I don't understand how the backports modules got installed for 2.6.24-xx. I suppose you have more kernels installed than just 2.6.22-19. I don't understand why, when you installed linux-backports-modules-hardy-generic it didn't install the backports modules for 2.6.22-19.> When I boot up my computer I'm able to use the old kernel version still and my wifi works on that version. I only recently tried the old kernel boot up.This part I *really* don't understand. Do you mean that you have a kernel installed even *older* than 2.6.22-19 in which the wireless works???

As I said, as far as I can remember, iwl3945 is included in 8.04 and the associated backports modules. I'd suggest you open Synaptic and mark the linux-image-2.6.22-19 for re-installation and search for and install  the exactly matching linux-backports-modules.

Incidentally, I searched here for linux-image 2.6.22 and found none.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Mock Force on 2010-11-18
> **chili555 said:**
> Do you mean that you have a kernel installed even *older* than 2.6.22-19 in which the wireless works???

Sorry, poor choice of words there, when I initially installed Ubuntu on my computer I was using Ubuntu 8.04.01 with Kernel 2.6.24.xx and then I installed the older Kernel. When I start up my computer the grub gives me three options for which kernel I want to use, 2.6.22.19, 2.6.24.28, and a third which I never use. When I run the Kernel version 2.6.24.28 the wirless works fine, when I run the kernel version 2.6.22.19 the wireless doesn't work.

and there is no linux kernel-image-2.6.22.19 in the synaptic for me to reinstall.

---

### Post by chili555 on 2010-11-18
My next best suggestion is to build it from scratch. It really doesn't look too hard:  [http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

Normally, building from a tarball requires the packages *build-essential* and linux-headers matching your running kernel. Where did you get 2.5.22-19 if not from Ubuntu? I don't suppose you have the headers. How about the source?

If we cannot get those, ndiswrapper using the .inf and .sys may, in fact, be the only practical solution.

Is this by chance a dual-boot with Windows, where the correct .inf and .sys are hiding?

---

### Post by Mock Force on 2010-11-18
I'll try the intellinux solution later tonight if I have time, thanks again for your help. I'll post something tomorrow about my status. 

[http://www.kernel.org/pub/linux/kernel/v2.6](http://www.kernel.org/pub/linux/kernel/v2.6) you can find the .tar here, I used an instruction set given to me by my supervisor to install the kernel.

Also I am dual booting windows but what are you asking about the correct .inf and .sys file? what do you mean they're hiding inside my windows partition?

---

### Post by chili555 on 2010-11-18
> I'll try the intellinux solution later tonight if I have time, thanks again for your help. I'll post something tomorrow about my status.
While booted into the 2.6.22-19 kernel, be sure to install *build-essential* through Synaptic before you start.> what do you mean they're hiding inside my windows partition? I mean just that. If the Intel 3945ABG is working in Windows, then you already have the .inf and .sys files needed for ndiswrapper. You just need to search your Windows install for them and transfer them and install ndiswrapper. More on what to search for in a few moments.

Use either the Intellinux method *OR* ndiswrapper; not both.

Edit: The .inf is named w39n51.inf. I suspect the .sys is similarly named.

Edit2: I imagine your supervisor has a sly grin; this is fun stuff, eh?

---

