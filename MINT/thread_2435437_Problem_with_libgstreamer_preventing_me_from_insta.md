---
title: "Problem with libgstreamer preventing me from installing toggl desktop"
date: 2020-01-20
forum: MINT
---

### Post by bschilke.biz on 2020-01-20
I've been seeing errors when updating/installing packages lately.  I  tried installing toggl desktop a few days ago, couldn't, and the  documentation recommended running 

```
$ sudo apt install -f
```

which returned:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libgeos-3.5.0
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libgstreamer-plugins-base0.10-0
The following packages will be upgraded:
  libgstreamer-plugins-base0.10-0
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
7 not fully installed or removed.
Need to get 0 B/514 kB of archives.
After this operation, 546 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 565554 files and directories currently installed.)
Preparing to unpack .../libgstreamer-plugins-base0.10-0_0.10.36-2ubuntu0.2_amd64.deb ...
Unpacking libgstreamer-plugins-base0.10-0:amd64 (0.10.36-2ubuntu0.2) over (0.10.36-1) ...
dpkg: error processing archive /var/cache/apt/archives/libgstreamer-plugins-base0.10-0_0.10.36-2ubuntu0.2_amd64.deb (--unpack):
 trying  to overwrite shared  '/usr/share/doc/libgstreamer-plugins-base0.10-0/changelog.Debian.gz',  which is different from other instances of package  libgstreamer-plugins-base0.10-0:amd64
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgstreamer-plugins-base0.10-0_0.10.36-2ubuntu0.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Should I try to downgrade libgstreamer?  It seems like maybe a recent upgrade failed.

---

### Post by bschilke.biz on 2020-01-20
```
 $ inxi -b # all system info (everything)
System:    Host: bschilke-Mint17 Kernel: 4.4.0-141-generic x86_64 (64 bit) Desktop: Cinnamon 3.0.7
           Distro: Linux Mint 18 Sarah
Machine:   System: LENOVO (portable) product: 423946U v: ThinkPad T520
           Mobo: LENOVO model: 423946U Bios: LENOVO v: 8AET52WW (1.32 ) date: 09/15/2011
CPU:       Dual core Intel Core i5-2520M (-HT-MCP-) speed/max: 886/3200 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Intel 82579LM Gigabit Network Connection (Lewisville) driver: e1000e
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi
Drives:    HDD Total Size: 820.2GB (12.4% used)
Info:      Processes: 243 Uptime: 3 days Memory: 7959.8/15823.8MB Client: Shell (bash) inxi: 2.2.35 


```

---

### Post by mc4man on 2020-01-21
Well libgsteamer* in 16.04 hasn't been updated since 2016 so 'recent' isn't likely, maybe recent for you?
Or maybe just some  Mint issue...
I'd just try removing the mentioned file as it's unimportant and or will be replaced by package upgrade.
```
sudo rm /usr/share/doc/libgstreamer-plugins-base0.10-0/changelog.Debian.gz
```
Then try upgrading again.

---

### Post by deadflowr on 2020-01-21
*Thread moved to **MINT***

---

