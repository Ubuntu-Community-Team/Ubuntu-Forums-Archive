---
title: "Wireless DSL on ubuntu"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by The musmula on 2013-07-19
I have quite a problem here, I`ve installed ubuntu on my friends pc and wanted to connect him to the internet, but I can do that only using DSL, BUT my friend is using wi-fi only, so he has no ethernet cable. I have googled this a 100 times and couldnt find anything, I have even tryed this:

[http://ubuntuforums.org/showthread.php?t=1610809](http://ubuntuforums.org/showthread.php?t=1610809) 

but it does not work.

It is 00:09 in the morning here in croatia, and I need to wake up at 7:00 and I am really tyred and I would like some help, thanks in advance.

---

### Post by praseodym on 2013-07-19
Hi,

please try in terminal:
```

sudo pppoeconf wlan0
```
Add login and password of your ISP and deactivate the network-manager in autostart

---

### Post by The musmula on 2013-07-19
thank you for your quick response, I did it and what now?

---

### Post by kc1di on 2013-07-19
Hello The musmula,

we need a little more information to be of help to you and your friend.

what wireless card is in the machine?

if you do not know please enter the following commands in a terminal and post the out put here.
```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

then

```
rfkill list all
```

---

### Post by The musmula on 2013-07-20
Thank you for helpinh, I have slept over the night and here is the output:
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
```  that was the forst one, here comes the second:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by praseodym on 2013-07-20
This is your LAN device. Check:
```

pccardctl info
lsusb
```

---

### Post by The musmula on 2013-07-20
this is what it says:
```
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by praseodym on 2013-07-20
Is it Ubuntu 13.04? If yes, you need a patched driver:

[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)

Save it in "Downloads" and install it via:

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by The musmula on 2013-07-20
It says:
```
Selecting previously unselected package rtl8192cu-tjp-dkms.
(Reading database ... 70%
(Reading database ... 161921 files and directories currently installed.)
Unpacking rtl8192cu-tjp-dkms (from .../rtl8192cu-tjp-dkms_1.6_all.deb) ...
dpkg: dependency problems prevent configuration of rtl8192cu-tjp-dkms:
 rtl8192cu-tjp-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.

dpkg: error processing rtl8192cu-tjp-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtl8192cu-tjp-dkms
ivan@Bubreg:~$ echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rtl8192cu

```
is that good?


btw it is 13.04

---

### Post by praseodym on 2013-07-20
You need the package dkms. Which Ubuntu version is that? 32 or 64 bit?

```
uname -a
```

---

### Post by The musmula on 2013-07-20
64 bit

---

### Post by praseodym on 2013-07-20
Here it is:

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb)

Also save it to Downloads and then the first line again.

---

### Post by The musmula on 2013-07-20
It is done, here is the output:
```
Selecting previously unselected package dkms.
(Reading database ... 162097 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu2_all.deb) ...
Preparing to replace rtl8192cu-tjp-dkms 1.6 (using .../rtl8192cu-tjp-dkms_1.6_all.deb) ...
Unpacking replacement rtl8192cu-tjp-dkms ...
Setting up dkms (2.2.0.3-1.1ubuntu2) ...
Processing triggers for man-db ...
Setting up rtl8192cu-tjp-dkms (1.6) ...
Loading new rtl8192cu-tjp-1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-19-generic
Building for architecture x86_64
Building initial module for 3.8.0-19-generic
Done.

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-19-generic/updates/dkms/

depmod......

Backing up initrd.img-3.8.0-19-generic to /boot/initrd.img-3.8.0-19-generic.old-dkms
Making new initrd.img-3.8.0-19-generic
(If next boot fails, revert to initrd.img-3.8.0-19-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic


```
what now?

---

### Post by praseodym on 2013-07-20
Reboot and check:
```

dmesg | grep 8192
iwconfig
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf
sudo iwlist scan
ifconfig -a
```

---

### Post by The musmula on 2013-07-20
it says:
```
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    7.437862] CHIP TYPE: RTL8188C_8192C
[    7.438404] ====> ReadAdapterInfo8192C
[    7.630065] readAdapterInfo_8192CU(): REPLACEMENT = 1
[    7.630069] <==== ReadAdapterInfo8192C in 192 ms
[    7.630890] usbcore: registered new interface driver rtl8192cu
ivan@Bubreg:~$ iwconfig
ppp0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ivan@Bubreg:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         193.198.190.248 0.0.0.0         UG    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
193.198.190.248 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
ivan@Bubreg:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto wlan0
iface wlan0 inet manual
ivan@Bubreg:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
ivan@Bubreg:~$ sudo iwlist scan
[sudo] password for ivan: 
Sorry, try again.
[sudo] password for ivan: 
ppp0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results


```

---

### Post by praseodym on 2013-07-20
Change the following file

```
gksu gedit /etc/network/interfaces
```
to```

auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto wlan0
iface wlan0 inet dhcp
     wpa-driver wext
     wpa-ssid [COLOR="#FF0000"]YourESSID[/COLOR]
     wpa-ap-scan 1
     wpa-proto RSN
     wpa-pairwise CCMP
     wpa-group CCMP
     wpa-key-mgmt WPA-PSK
     wpa-psk "[COLOR="#FF0000"]YourPassword[/COLOR]"
```
Restart the network:```

sudo /etc/init.d/networking restart
```
Then show the outputs again (all!)

---

### Post by The musmula on 2013-07-20
yeah, I messed it up.
I did change the file but I forgot to change the ssid, saved it, tryed reseting the network, it crashed, I restarted the pc, got a bit stuck on "starting network configuration" or something like this, finally ubuntu skipped it, and I am not at square one, I am behind square one, and btw how to reset that file?
nice wheather

---

### Post by praseodym on 2013-07-20
The same as above
```

gksu gedit /etc/network/interfaces
```

---

### Post by The musmula on 2013-07-20
The reason why I cant show you the output of network restarting is that unity chrashes all the time I try that :(

---

### Post by praseodym on 2013-07-20
Obviously a VGA problem. Please check
```

uname -a
lspci -nnk | grep -iA2 VGA
```

---

