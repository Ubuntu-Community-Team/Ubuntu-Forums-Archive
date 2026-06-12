---
title: "Intel Centrino 6300 N working in 11.10, not in 10.10"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by lostinsauce on 2011-10-28
I have a Lenovo T410 running Windows 7, Ubuntu 11.10, and Blackbuntu (Ubuntu 10.10).  In both Windows 1 and Ubuntu my wireless card works fine and I am able to connect.  In Blackbuntu, I'm completely unable to bring up the wireless card (centrino 6300 N).  Some background:

lshw -C network on 11.10 gives me what I would expect, but on 10.10 it shows the wireless network as "UNCLAIMED".  I am unable to see any iwlagn info in dmesg, nor am i able to bring it up.  lsmod shows only cfg80211 referencing mac80211, neither sees iwlagn.

ifconfig only shows lo and eth0, despite my attempts to create a wlan0 in the etc/network/interfaces file.  I also created an instance for wlan0 in the /etc/udev/rules.d/70-persistent-net.rules file.

Finally, i tried the compat-wireless fix that seemed to work well on these forums and the install errored out.

Note:  I've ensured that the proper firmware is in /lib/firmware.  My problem is that wlan0 is not being created>>the driver is just not being applied to the wireless card.

All help is much appreciated...any ideas?

---

### Post by praseodym on 2011-10-28
How did you install compat-wireless, do you have a link? Firmware is also updated? You can use the Oneiric package for the firmware:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Search for "linux-firmware"

---

### Post by collisionystm on 2011-10-28
> Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly.

Welcome to the open source site hosting Intel's wireless projects for Linux. Here you will find information about the Linux-based wireless drivers for Intel adapters.

This site hosts the open source iwlwifi project for use with the following hardware (support for different hardware depends on kernel version used):

the minimum version is indicated below

Intel® Centrino® Wireless-N 100 (2.6.37)
Intel® Centrino® Wireless-N 130 (2.6.37)
Intel® Centrino® Advanced-N 6230 (2.6.36)
Intel® Centrino® Wireless-N 1030 (2.6.36)
Intel® Centrino® Advanced-N 6205 (2.6.35)
Intel® Centrino® Wireless-N + WiMAX 6150 (2.6.30)
Intel® Centrino® Advanced-N + WiMAX 6250 (2.6.30)
Intel® Centrino® Ultimate-N 6300 (2.6.30)
Intel® Centrino® Advanced-N 6200 (2.6.30)
Intel® Centrino® Wireless-N 1000 (2.6.30)
Intel® Wireless WiFi 5150AGN (2.6.29)
Intel® Wireless WiFi 5100AGN, 5300AGN, and 5350AGN (2.6.27)
Intel® Wireless WiFi Link 4965AGN (2.6.24)
Intel® PRO/Wireless 3945ABG Network Connection adapter (2.6.24)


[http://intellinuxwireless.org/](http://intellinuxwireless.org/)


open a terminal and type

```
uname -a
```

what is your kernel version?

If its greater than 2.6.24

type

```
sudo modprobe iwlagn
```

Wait a minute or 2. See if you have wireless.

---

### Post by lostinsauce on 2011-10-28
My kernel is 2.6.39.  From root, modprobe iwlagn comes back with FATAL: Module iwlagn not found.

I'm not sure how I can install this, I cant run any update because I dont have the wireless, nor a wired connection.  If there is a .deb or .bz2 available somewhere, I can get it from my 11.10 partition then jump over to 10.10 and tar it.

Speaking of which, I am trying the firmware oneiric update right now, will need to hop over.

Thanks much for the help!

---

### Post by lostinsauce on 2011-10-28
Ok, post lunch and nothing new to report.  I upgraded the firmware using the oneiric package and it made no difference.  
 
Any ideas on how I can install iwlagn or bring it up?  Below are some of the *important* outputs I've gleaned.  Let me know if you think anything else might be useful:
 
 
[EMAIL="joshogan@joshogan-ThinkPad-T410~$"]joshogan@joshogan-ThinkPad-T410~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0d:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

[EMAIL="joshogan@joshogan-ThinkPad-T410~$"]joshogan@joshogan-ThinkPad-T410~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:63:c7:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2400000-f2420000 
eth0:avahi Link encap:Ethernet  HWaddr f0:de:f1:63:c7:cb  
          inet addr:169.254.11.253  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:f2400000-f2420000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4096 (4.0 KB)  TX bytes:4096 (4.0 KB)

[EMAIL="joshogan@joshogan-ThinkPad-T410~$"]joshogan@joshogan-ThinkPad-T410~$[/EMAIL] lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: [EMAIL="pci@0000:00:19.0"]pci@0000:00:19.0[/EMAIL]
       logical name: eth0
       version: 06
       serial: f0:de:f1:63:c7:cb
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.12-1 latency=0 multicast=yes port=twisted pair
       resources: irq:41 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       version: 35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f2000000-f2001fff

---

### Post by garvinrick4 on 2011-10-28
Do these 2 lines of code show your iwlagn driver present. Is a kernel driver.
```
locate iwlagn
```
```
lsmod | grep iwl
```

---

### Post by garvinrick4 on 2011-10-28
You can install a 3.0 kernel and up like oneiric if you choose.
They are already built in .deb and all you have to do is download and I can show
you simply how to install. Need to know if you have used 32 or 64 bit operating system.

---

### Post by lostinsauce on 2011-10-28
Lsmod returns nothing with iwlagn, but the locate tool returns hits in:

etc/modprobe.d/intel-5300-iwlagn-disablelln.conf
Lib/modules/2.6.39-3-bb03/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko.ignore
usr/src/Linux-headers-2.6.39-3-bb03/include/config/iwlagn.h

Sorry for the slow replies...I'm trying to reply on my iPad so I can leave the OS up...

---

### Post by lostinsauce on 2011-10-28
I'm down to try a new kernel...pretty sure the problem is my current kernel not picking up the driver anyway...

I have a 64 bit kernel.

---

### Post by garvinrick4 on 2011-10-28
> **lostinsauce said:**
> I'm down to try a new kernel...pretty sure the problem is my current kernel not picking up the driver anyway...

I have a 64 bit kernel.
Ok will write it up for you and be in next post:

---

### Post by garvinrick4 on 2011-10-28
We are going to download a kernel from this site and install it and we need to upgrade
your module-init-tools
First the module-init-tools:
Lower left of page download the "amd-64.deb" to[COLOR=Red] DESKTOP[/COLOR] or drag and drop to Desktop:
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500)
Then:
```
cd Desktop
``````
ls
``````

sudo dpkg -i (copy and paste to here for output of ls command)
``` There is a space after "-i"
[COLOR=Red]Done with that now Drag and drop all the module-init-tools to Downloads from Desktop:
[/COLOR] 
Now we will Download three items to Desktop from this site.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.1-oneiric/")
The all.deb, 
the headers 64 bit,  
the image 64 bit.

Download all three to [COLOR=Red]Desktop[/COLOR] or drag and drop there:
Now this one piece of code will install all three make sure the 3 are the only .debs on Desktop, can see with ls command:
```
Cd Desktop
``````
ls
``````
sudo dpkg -i *.deb
```Done reboot into new kernel 3.0.1
Hopefully iwlagn kernel driver works in your 10.10 (does for mine so this is in practice not theory) I have a machine with iwlagn driver.

---

### Post by lostinsauce on 2011-10-28
Crap i think i might have screwed it up.  The first time through I ran the three .debs with the module-init-tools deb still in the Desktop.  Rebooted and saw that nothing changed, caught the error, then sent the module-init-tools deb to downloads and tried again, but no luck.  Do i have to undo something done the first time?  Note that grub only gives me the option for the 2.6.39 kernel, and uname -a gives me the same thing.

---

### Post by garvinrick4 on 2011-10-28
> **lostinsauce said:**
> Lsmod returns nothing with iwlagn, but the locate tool returns hits in:

[COLOR=Red]etc/modprobe.d/intel-5300-iwlagn-disablelln.conf[/COLOR]
Lib/modules/2.6.39-3-[COLOR=Red]bb03[/COLOR]/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko.[COLOR=Red]ignore[/COLOR]
usr/src/Linux-headers-2.6.39-3-bb03/include/config/iwlagn.h

Sorry for the slow replies...I'm trying to reply on my iPad so I can leave the OS up...
You had N disabled, make sure router not set to "N" only.
[COLOR=Red]ignore [/COLOR]speaks for itself
Blackbuntu never messed with it myself. 

working system below:
```
rick@rick-sda15:~$ locate iwlagn
/lib/modules/3.0.0-11-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/3.1.0-1-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/usr/src/linux-headers-3.0.0-11-generic/include/config/iwlagn.h
/usr/src/linux-headers-3.0.0-12-generic/include/config/iwlagn.h
/usr/src/linux-headers-3.1.0-1-generic/include/config/iwlagn.h


```
```
rick@rick-sda15:~$ lsmod | grep iwl
iwlagn                318792  0 
mac80211              481634  1 iwlagn
cfg80211              204147  2 iwlagn,mac80211 
```

---

### Post by lostinsauce on 2011-10-28
On the kernel topic, I know that my 11.10 install is running a x86 kernel, so do you think I should just try to install BB with the x86 .iso instead of x86_64?  I feel like there might be a problem with the newer kernel not picking up the older firmware, if it was never updated.  Could have just been a small thing they missed in the distro.

---

### Post by garvinrick4 on 2011-10-28
First see what is installed in module-init-tools.
If you do not have aptitude installed do it.
```
rick@rick-sda15:~$ aptitude show module-init-tools
Package: module-init-tools               
New: yes
State: installed
Automatically installed: no
Version: 3.16-1ubuntu1
Priority: required
Section: admin
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 442 k
Depends: libc6 (>= 2.8), upstart-job
PreDepends: dpkg (>= 1.15.7.2)
Conflicts: module-init-tools
Breaks: initramfs-tools (< 0.92bubuntu23), initramfs-tools (< 0.92bubuntu23)
Description: tools for managing Linux kernel modules
 This package contains a set of programs for loading, inserting, and removing
 kernel modules for Linux.
Homepage: http://www.kerneltools.org/

```
Run 
grep menuentry /boot/grub/grub.cfg
to see what you have as a menu entry in kernels

---

### Post by lostinsauce on 2011-10-28
Wow.  Well I feel like an idiot.

Can I just change the file name safely to drop the "ignore" portion?

I don't think that changing the router settings will work because the card is N-specific.  Also, if it brought up the card on a,b, or g wouldnt iwlagn work in that case?

oye vai

---

### Post by lostinsauce on 2011-10-28
THe module-init-tools all look correct.  I have version 3.13 but other than that everything else appears the same.  The grub lookup shows that the 3.0.1-030001-generic option IS there, but it doesnt come up when I reboot in.

---

### Post by lostinsauce on 2011-10-28
When I navigate to etc/modprobe.d, I can't even find the intel file.  It still shows up in the locate iwlagn, but doesnt appear when i run ls from that directory or when I navigate there in the gui.

---

### Post by garvinrick4 on 2011-10-28
> I don't think that changing the router settings will work because the card is N-specific. You made a file to not use the N in your card.

---

### Post by garvinrick4 on 2011-10-28
> THe module-init-tools all look correct.  I have version 3.13 but other  than that everything else appears the same.  The grub lookup shows that  the 3.0.1-030001-generic option IS there, but it doesnt come up when I  reboot in.You have another install of Ubuntu that is in control of grub then,
Boot into that install and sudo update-grub and will put new kernel in as a menuentry>
Or while in this install give it the grub:
sudo grub-install /dev/sda; sudo update-grub

You should be ok now after booting into new kernel hopefully.

---

### Post by garvinrick4 on 2011-10-28
In /etc/modprobe.d
you will find a config file you made with this name below to disable "N" in your Network card. Get rid of it, toss it out. You have something intel-5300 with iwlagn-disable in it
or a iwlagn conf file.
Or make sure router is set as mixed and not N only in 2.4 ghz so as to accept G and not just N.

> intel-5300-iwlagn-disablelln.conf

---

### Post by garvinrick4 on 2011-10-28
> **lostinsauce said:**
> Crap i think i might have screwed it up.  The first time through I ran the three .debs with the module-init-tools deb still in the Desktop.  Rebooted and saw that nothing changed, caught the error, then sent the module-init-tools deb to downloads and tried again, but no luck.  Do i have to undo something done the first time?  Note that grub only gives me the option for the 2.6.39 kernel, and uname -a gives me the same thing. If module-init-tools was still on desktop when you ran 
sudo dpkg -i *deb it just tried to reinstall it and found it did not need to was already that version so then when on to install the other 3 from kernel you were installing. 
*.deb just means install them all that are .deb in directory you are in. Easier than one
at a time but you can do them one at a time as you did the module-init-tools.

---

### Post by lostinsauce on 2011-10-28
Alright--major success!

You were spot on about the other distro holding the grub power.  Ran those commands and it booted up with the 3.0.1 kernel.  Now i see wlan0 in the iwconfig and the card seems to be running based on the lshw -C network command.  Now i'll just configure the wireless connection and cross my fingers.  Thanks so much for the help--the new kernel did the trick!

---

### Post by garvinrick4 on 2011-10-28
Allright, I hoped you learned a bit about installing .deb packages and how easy it is.
Always look for packages that are under builds or built into .deb already. Compiling from
source is a pain, can be done but why not look for built packages if you can.
IN upper right hand corner of Forums page is link to launchpad.net that is where you find
all things Ubuntu and .deb and by package name.  Join it and learn to get around on that site.

If you want .ppa's they are there or you can get a lot here with easy instructions below.
[http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)

Please mark as Solved please in upper right hand corner under Thread Tools so users with same
can benefit. Enjoy your Ubuntu_._

---

