---
title: "No Internet, please help - Intel 82573L LAN/Intel 3945abg"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by dookiebowser on 2011-04-23
HI guys,

I'm dead in the water right now. No internet. The tools and information to fix these issues are out there, I just need help with execution since I'm still new to linux.

My ethernet is not working. The system knows it's there but there is no eth0. I think this is due to the EEPROM issue to do with power saving and corrupting the first few bits of data. I was able to fix this in the past with this computer (HP dv6375) but cannot remember how I did it nor get it done again through research.

$ lspci -v | grep 82573L
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

$ lsmod | grep e100
e1000e                119856  0

$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:8d:60:a9  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe8d:60a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3157204 (3.1 MB)  TX bytes:468211 (468.2 KB)

This fix: [http://ubuntuforums.org/showthread.php?t=868077](http://ubuntuforums.org/showthread.php?t=868077) did not work.
[I]FATAL: Error inserting e1000 (/lib/modules/2.6.32-30-generic/kernel/drivers/net/e1000/e1000.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[/I]

Wireless is not working (properly) either. I'm suffering the Intel 3945abg slow speed issue well documented in the [Launchpad]("https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/621265") bugs, but cannot fix it. I get about .47 Mbps where it should be 6 Mbps  I've read that it was an issue dealing with the Maverick kernel, but I am now running Lucid and having the same problem (when others were able to downgrade and resolve the issue). Downstream is never above 1Mbps (normal is 6Mbps), Upstream sporadically reaches 2Mbps which is normal for my net.

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"IDI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:97:7E:68   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Please help! thanks!

---

### Post by Ropes on 2011-04-23
Can you connect to your router/network at least(probably 192.168.0.1)? 

If you can't even do that it might actually be a hardware issue.  However it seems that your eht0 isn't properly setup looking at your ifconfig.

What is your network interface setup as?
```
terminal->cat /etc/network/interfaces
```

Another thing to check into is whether you want static or DHCP networking.

---

### Post by josephmills on 2011-04-23
hi there could we please see a **(you have to let it load)**
```

sudo lshw -C network

```  thanks

---

### Post by fdrake on 2011-04-23
it looks like you are connected to the router since you have an ip address...   
type 
```
router
```
maybe its the router.. did you try to reset it? is the Ethernet cable plug lighting or flashing a green color on the back of the pc?

---

### Post by dookiebowser on 2011-04-23
Thanks for your reply.

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


**Scratch the Wifi Intel 3945ABG issue**. This is most likely a router problem, just found out my wife's Windows box is doing the same thing...connecting at very low bit rate 11Mbps and having speed issues the same. No access to the router for now, it's probably on it's way out since I can't get factory reset to work. 

How do I approach the 82573L ethernet issue? 

Thanks again.

---

### Post by dookiebowser on 2011-04-23
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:8d:60:a9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.32-30-generic firmware=15.32.2.9 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:d8000000-d8000fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:da000000-da01ffff ioport:4000(size=32)

---

### Post by fdrake on 2011-04-23
sorry i mean 
```
route
```
not router... my bad

---

### Post by dookiebowser on 2011-04-23
> **fdrake said:**
> it looks like you are connected to the router since you have an ip address...   
type 
```
router
```maybe its the router.. did you try to reset it? is the Ethernet cable plug lighting or flashing a green color on the back of the pc?

The LED is active on the laptop and the router's LEDs for that port are fine.

There's an issue with the router, it won't do a factory reset for some reason. I have a desktop hardwired to the router and it's working perfectly, so the wired connections on the router are fine. Can't reset through router interface since I don't have access to the password, I might when I'm able to reach the person that set up the network though.

Router is a Linksys BEFW11S4 v2. Super old.

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by Ropes on 2011-04-23
> **dookiebowser said:**
> Thanks for your reply.

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


you'll need sudo privileges, but one problem I see is that your eth0 connection isn't being created on startup.
open the /etc/network/interfaces file, add 
[FONT=Arial]```

[FONT=Courier New][SIZE=2]auto eth0
iface eth0 inet dhcp[/SIZE][/FONT]
```[/FONT]
This will force your network to setup an eth0 network interface automatically.
Once you've updated the file, restart your connection.
```
sudo /etc/init.d/networking restart
```You'll probably want to eventually setup your connection with a static IP but this may get you going for starters.

---

### Post by fdrake on 2011-04-23
open firefox and on the address bar out "192.168.1.0" or "192.168.0.1"
if it asks you for username and password try admin(user) admin(password) or admin (user) password(password).it's worth a try, otherwise look for a tiny button on the back of the router and keep it pressed for 20~30 sec to reset.

---

### Post by dookiebowser on 2011-04-23
> **fdrake said:**
> open firefox and on the address bar out "192.168.1.0" or "192.168.0.1"
if it asks you for username and password try admin(user) admin(password) or admin (user) password(password).it's worth a try, otherwise look for a tiny button on the back of the router and keep it pressed for 20~30 sec to reset.

Yeah. It's actually 192.168.1.1 for mine, and I've tried all the default/master passwords. The factory reset button looks like it's resetting with the blinking LEDs, but it never goes to factory defaults. It's weird, first time I ever encountered it.

---

### Post by dookiebowser on 2011-04-23
> **Ropes said:**
> you'll need sudo privileges, but one problem I see is that your eth0 connection isn't being created on startup.
open the /etc/network/interfaces file, add 
[FONT=Arial]```

[FONT=Courier New][SIZE=2]auto eth0
iface eth0 inet dhcp[/SIZE][/FONT]
```[/FONT]
```
sudo /etc/init.d/networking restart
```

Edited /etc/network/interfaces
Tried to restart network

```

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

```

---

### Post by josephmills on 2011-04-24
lets take a look at this ```
cd /etc/modprobe.d
```then ```
less blacklist.conf 
```

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> lets take a look at this ```
cd /etc/modprobe.d
```then ```
less blacklist.conf 
```

# replaced by e100
blacklist eepro100

*relative to e1000/e1000e driver module for 82573L & eeprom?*

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

?????

the rest of blacklist.conf is [here]("http://pastebin.com/6jzg8uwr"), but i don't think anything else has to do with it.


also, i get an error when using modprobe for the appropriate driver module. module is current version but was occurring with the older driver that lucid is packed with:

```
$ lsmod
Module                  Size  Used by
e1000e                137755  0 

$ sudo rmmod -f e1000e
$ sudo modprobe e1000e
$ dmesg
[11566.893312] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10a-NAPI
[11566.893318] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[11566.893365] e1000e 0000:05:00.0: Disabling ASPM  L1
[11566.893429] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[11566.893487] e1000e 0000:05:00.0: setting latency timer to 64
[11566.893902] e1000e 0000:05:00.0: irq 30 for MSI/MSI-X
[11566.893928] e1000e 0000:05:00.0: Disabling ASPM L0s 
[11566.955421] e1000e 0000:05:00.0: (unregistered net_device): The NVM Checksum Is Not Valid
[11566.965813] e1000e 0000:05:00.0: PCI INT A disabled
[11566.965833] e1000e: probe of 0000:05:00.0 failed with error -5
```These lines concern me:
[B][11566.955421] e1000e 0000:05:00.0: (unregistered net_device): The NVM Checksum Is Not Valid
[11566.965833] e1000e: probe of 0000:05:00.0 failed with error -5[/B]

Thanks so much guys!

---

### Post by josephmills on 2011-04-24
please see [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> please see [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

Will try, but my device isn't listed [8086:109a], and the Intel docs tell me to use e1000e. 

Thanks again.

---

### Post by josephmills on 2011-04-24
> **dookiebowser said:**
> Will try, but my device isn't listed [8086:109a], and the Intel docs tell me to use e1000e. 

Thanks again.

ohh here is your e1000e driver [http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

---

### Post by josephmills on 2011-04-24
looks like this one is better [http://cateee.net/lkddb/web-lkddb/E1000E.html](http://cateee.net/lkddb/web-lkddb/E1000E.html)and here is one from intel [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng)

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> looks like this one is better [http://cateee.net/lkddb/web-lkddb/E1000E.html](http://cateee.net/lkddb/web-lkddb/E1000E.html)and here is one from intel [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng)


Sorry, don't mean to make you hold my hand, but I don't know what to do with this.

I have the latest e1000e driver from Intel. Is this an alternative? 

Thanks.

*yeah that's the intel one i have installed currently:
```

$ modinfo e1000e
filename:       /lib/modules/2.6.32-30-generic/kernel/drivers/net/e1000e/e1000e.ko
version:        1.3.10a-NAPI
```

---

### Post by josephmills on 2011-04-24
> **dookiebowser said:**
> Sorry, don't mean to make you hold my hand, but I don't know what to do with this.

I have the latest e1000e driver from Intel. Is this an alternative? 

Thanks.

*yeah that's the intel one i have installed currently:
```

$ modinfo e1000e
filename:       /lib/modules/2.6.32-30-generic/kernel/drivers/net/e1000e/e1000e.ko
version:        1.3.10a-NAPI
```

These are tar.gz files (unix gnu/linux). Is the driver that you have a windows driver? Where did you get it?      



**SOURCE chill555**([http://ubuntuforums.org/archive/index.php/t-1574477.html](http://ubuntuforums.org/archive/index.php/t-1574477.html))
e1000e is correct for your device:$ modinfo e1000e | grep 109A
alias: pci:v00008086d0000109Asv*sd*bc*sc*i*You might try a later version. Download the latest version here: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng)

With your wireless attached and an internet connection, please do:sudo apt-get install linux-headers-generic build-essential
By default, downloads go to your Downloads. Right-click the tar.gz file and select 'Extract Here.' Open a terminal and do:cd Downloads/e1000e-1.2.10/src
make
sudo make install
sudo rmmod -f e1000e
sudo modprobe e1000e
sudo ifconfig eth0 up
ifconfigDid an ethernet interface, eth0 perhaps, appear? If not, please run:dmesg | grep e1000ePost entries after 2688.xx; that is after the entries we've already seen.

I have this exact device and the module built perfectly for me. Post back if you get stuck.

Cross your fingers, everyone!

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> These are tar.gz files (unix gnu/linux). Is the driver that you have a windows driver? Where did you get it?      

I got it from the same intel link you posted. Looked up the chipset and got the linux drivers, built and installed it. Lucid came with a much earlier version that I had the same problem with (I think 1.0.9).



> **josephmills said:**
> **SOURCE chill555**([http://ubuntuforums.org/archive/index.php/t-1574477.html](http://ubuntuforums.org/archive/index.php/t-1574477.html))
e1000e is correct for your device:$ modinfo e1000e | grep 109A
alias: pci:v00008086d0000109Asv*sd*bc*sc*i*You might try a later version. Download the latest version here: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng)

With your wireless attached and an internet connection, please do:sudo apt-get install linux-headers-generic build-essential
By default, downloads go to your Downloads. Right-click the tar.gz file and select 'Extract Here.' Open a terminal and do:cd Downloads/e1000e-1.2.10/src
make
sudo make install
sudo rmmod -f e1000e
sudo modprobe e1000e
sudo ifconfig eth0 up
ifconfigDid an ethernet interface, eth0 perhaps, appear? If not, please run:dmesg | grep e1000ePost entries after 2688.xx; that is after the entries we've already seen.

I have this exact device and the module built perfectly for me. Post back if you get stuck.

Cross your fingers, everyone!


Did all of these steps. There is still no eth0, it never comes up. Modprobe fails:

```
$ sudo modprobe e1000e
$ dmesg | grep e1000e
[    0.808203] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.808207] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.808258] e1000e 0000:05:00.0: Disabling L1 ASPM
[    0.808285] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.808328] e1000e 0000:05:00.0: setting latency timer to 64
[    0.808534] e1000e 0000:05:00.0: irq 28 for MSI/MSI-X
[    0.883025] e1000e 0000:05:00.0: PCI INT A disabled
[    0.883033] e1000e: probe of 0000:05:00.0 failed with error -5

```

---

### Post by josephmills on 2011-04-24
are you getting wireless at all?

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> are you getting wireless at all?

Yeah I have wireless.

---

### Post by josephmills on 2011-04-24
do a ```
sudo apt-get update 
``` then ```
sudo apt-get upgrade 
``` anything ?

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> do a ```
sudo apt-get update 
``` then ```
sudo apt-get upgrade 
``` anything ?

```

$ sudo apt-get update
 
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/main Packages    
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources 
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid Release.gpg             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-backports-modules-wireless-lucid-generic linux-generic
  linux-headers-generic linux-image-generic
The following packages will be upgraded:
  brasero brasero-common compiz compiz-core compiz-gnome compiz-plugins dbus
  dbus-x11 desktopcouch gnome-screensaver initscripts libbrasero-media0
  libdbus-1-3 libdecoration0 libmetacity-private0 libsmbclient libwbclient0
  linux-firmware linux-libc-dev logrotate metacity metacity-common
  nvidia-current openssh-client pm-utils python-desktopcouch
  python-desktopcouch-records python-gnomeapplet python-gnomekeyring
  python-wnck samba-common samba-common-bin smbclient ssh-askpass-gnome
  sysv-rc sysvinit-utils tzdata w3m xkb-data
39 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 53.4MB/64.0MB of archives.
After this operation, 991kB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

---

### Post by josephmills on 2011-04-24
> **dookiebowser said:**
> ```

$ sudo apt-get update
 
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/main Packages    
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources 
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid Release.gpg             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-backports-modules-wireless-lucid-generic linux-generic
  linux-headers-generic linux-image-generic
The following packages will be upgraded:
  brasero brasero-common compiz compiz-core compiz-gnome compiz-plugins dbus
  dbus-x11 desktopcouch gnome-screensaver initscripts libbrasero-media0
  libdbus-1-3 libdecoration0 libmetacity-private0 libsmbclient libwbclient0
  linux-firmware linux-libc-dev logrotate metacity metacity-common
  nvidia-current openssh-client pm-utils python-desktopcouch
  python-desktopcouch-records python-gnomeapplet python-gnomekeyring
  python-wnck samba-common samba-common-bin smbclient ssh-askpass-gnome
  sysv-rc sysvinit-utils tzdata w3m xkb-data
39 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 53.4MB/64.0MB of archives.
After this operation, 991kB of additional disk space will be used.
Do you want to continue [Y/n]? y

```



I dont get it did you press y and then enter?

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> I dont get it did you press y and then enter?

yeah it was downloading. i just restarted and same issue. no eth0 and errors when e1000e is loaded.

```
$ dmesg | grep e1000e
[    0.831633] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10a-NAPI
[    0.831636] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    0.831662] e1000e 0000:05:00.0: Disabling ASPM  L1
[    0.831716] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.831758] e1000e 0000:05:00.0: setting latency timer to 64
[    0.832122] e1000e 0000:05:00.0: irq 29 for MSI/MSI-X
[    0.832142] e1000e 0000:05:00.0: Disabling ASPM L0s 
[    0.896185] e1000e 0000:05:00.0: (unregistered net_device): The NVM Checksum Is Not Valid
[    0.906415] e1000e 0000:05:00.0: PCI INT A disabled
[    0.906423] e1000e: probe of 0000:05:00.0 failed with error -5

```

```

$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:8d:60:a9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.32-30-generic firmware=15.32.2.9 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:d8000000-d8000fff

  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:da000000-da01ffff ioport:4000(size=32)
```

---

### Post by josephmills on 2011-04-24
after looking over you blacklist.conf file I think that it should be longer did you press the down button all the way till you seen an end?

---

### Post by dookiebowser on 2011-04-24
> **josephmills said:**
> after looking over you blacklist.conf file I think that it should be longer did you press the down button all the way till you seen an end?

this is all of it:

```

/etc/modprobe.d$ cat blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

---

### Post by sorcerer01 on 2011-07-01
issue probably solved, I've written an article...take a look at : 

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

---

