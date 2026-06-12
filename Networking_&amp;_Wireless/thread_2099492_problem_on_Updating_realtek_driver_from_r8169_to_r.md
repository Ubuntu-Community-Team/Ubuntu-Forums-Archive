---
title: "problem on: Updating realtek driver from r8169 to r8168?"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by GnuKian on 2012-12-29
I followed an instruction mentioned on this topic: **[Ubuntu 12.04 and realtek]("http://ubuntuforums.org/showpost.php?p=12199567&postcount=3") **at #3 answer[B]:
[/B]```
sudo gedit  /etc/modprobe.d/blacklist.conf
```[LEFT]Adding line: blacklist r8169[/LEFT]
```
sudo update-initramfs -u && cd ~/Downloads && tar xvf r8168-8.035.00.tar.bz2 && cd r8168-8.035.00 && sudo sh autorun.sh
```But I get this error:
[COLOR=red]
Check old driver and unload it
rmmod r8169
Build the module and install
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop
make[1]: *** [clean] Error 2
make: *** [clean] Error 2[/COLOR]

---

### Post by chili555 on 2012-12-29
> make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.I suspect the required build tools aren't yet installed:```
sudo apt-get install build-essential linux-headers-generic
```Then try to compile and install the driver again.

---

### Post by GnuKian on 2012-12-30
I installed "build-essential" and "linux-headers-generic" packages. But I still get that error:
```
 Check old driver and unload it.
Build the module and install
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make[1]: *** [clean] Error 2
make: *** [clean] Error 2
```

---

### Post by chili555 on 2012-12-30
I wonder if the dependent linux-headers matching your running kernel are correctly installed. Please do:```
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

Then try to re-compile r8168.

---

### Post by GnuKian on 2012-12-30
```
 sudo apt-get install --reinstall linux-headers-`uname -r`
```[sudo] password for kian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-headers-3.5.0-17-generic
0 upgraded, 1 newly installed, 0 to remove and 220 not upgraded.
Need to get 946 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Get:1 [http://ubuntu.trumpetti.atm.tut.fi/ubuntu/](http://ubuntu.trumpetti.atm.tut.fi/ubuntu/) quantal/main linux-headers-3.5.0-17-generic amd64 3.5.0-17.28 [946 kB]
Fetched 946 kB in 51s (18.4 kB/s)                                                                                
Selecting previously unselected package linux-headers-3.5.0-17-generic.
(Reading database ... 169034 files and directories currently installed.)
Unpacking linux-headers-3.5.0-17-generic (from .../linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb) ...
Setting up linux-headers-3.5.0-17-generic (3.5.0-17.28) ...

```
sudo update-initramfs -u && sudo sh autorun.sh
```Check old driver and unload it.
rmmod r8169
Build the module and install
Backup r8169.ko
rename r8169.ko to r8169.bak
DEPMOD 3.5.0-17-generic
load module r8168
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
Completed.

```
nm-tool
```
NetworkManager Tool
State: connected (global)
- Device: eth0  [Wired connection 1] 
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
  Wired Properties
    Carrier:         on
  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1


================================================

I done and it worked ([I]:
pleaes receive my best regards, @[/I][I][chili555]("http://ubuntuforums.org/member.php?u=35909").
[/I](It solved at last after one week!)

Just, I want to know what happened with the last command? -> linux-headers-`uname -r` **vs** linux-headers-generic

---

### Post by chili555 on 2012-12-30
linux-headers-generic is supposed to have as a dependency and correctly install the actual headers matching your running kernel, in your case 3.5.0-17-generic. For some reason, it doesn't always go as smoothly as it should and all the parts are not installed correctly. You verified that -generic was installed. We fixed 3.5.0-17.

Now that it's working, you might just double-check -generic:```
sudo apt-get install --reinstall linux-headers-generic
```Glad it's working!

---

### Post by GnuKian on 2013-01-01
Reinstalled. thanks for the help.

Another question:
[COLOR=DarkRed]Updating from r8169[/COLOR] [COLOR=SlateGray](internal driver within the kernel)[/COLOR] [COLOR=DarkRed]to r8168[/COLOR] [COLOR=SlateGray](the latest driver released by RealTek for my net card)[/COLOR] [COLOR=DarkRed]is recommended as I done?[/COLOR]

---

### Post by chili555 on 2013-01-01
The built-in r8169 works perfectly well for many. If it does, I wouldn't change to r8168. If it doesn't work perfectly for your card/router/modem/service provider combination, then I suggest you change the driver.

---

### Post by GnuKian on 2013-01-01
0. How can I understand r816[COLOR=Red]x[/COLOR] is working perfectly well for mine or not?
1. Is there a way to benchmark r816[COLOR=Red]9[/COLOR] vs r816[COLOR=Red]8[/COLOR]?

> **chili555 said:**
> If it doesn't work perfectly for your  card/router/modem/service provider combination, then I suggest you  change the driver.
I checked my network card here: [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

And this is my card:
```

lspci -vv |grep Ethernet

```03:00.0 Ethernet controller: Realtek Semiconductor Co.,[COLOR=Red] Ltd. RTL8111/8168B[/COLOR] [COLOR=Red]PCI Express Gigabit[/COLOR] Ethernet controller (rev 03)

---

### Post by chili555 on 2013-01-01
You might check here: [http://fixunix.com/networking/527067-tools-benchmark-ethernet-performance.html](http://fixunix.com/networking/527067-tools-benchmark-ethernet-performance.html)

netperf is in the Ubuntu repositories. 

Generally, if you connect, download, upload,etc. seamlessly, I'd think you're all good. Changing drivers is typically an option in the case where r8169 doesn't work at all.

---

