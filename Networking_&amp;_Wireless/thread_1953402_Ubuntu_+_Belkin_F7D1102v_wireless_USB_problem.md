---
title: "Ubuntu + Belkin F7D1102v wireless USB problem"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by 4udi on 2012-04-06
Hi,
I am new to linux and now encountering serious problems with my new USB wireless stick when trying to istall it to my Ubuntu PC.

Here is what I have done so far:

I installed Ndiswrapper and I tried to use windows drivers which came on the install cd. Driver seems to be installed but still something is wrong:
 
hannele@hannele-desktop:~$ ndiswrapper -l
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. net8192cu : driver installed     device (050D:1102) present  

hannele@hannele-desktop:~$ sudo depmod -a 

hannele@hannele-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.   


hannele@hannele-desktop:~$ tail /var/log/messages
 Apr  6 14:10:33 hannele-desktop kernel: [   24.908238] UDF-fs: Partition marked readonly; forcing readonly mount 

Apr  6 14:10:33 hannele-desktop kernel: [   24.928271] UDF-fs INFO UDF: Mounting volume 'Belkin F7D1102v', timestamp 2011/07/06 09:33 (10b4)

 Apr  6 14:11:22 hannele-desktop kernel: [   73.520106] Marking TSC unstable due to cpufreq changes 

Apr  6 14:11:22 hannele-desktop kernel: [   73.520169] Switching to clocksource acpi_pm 

Apr  6 14:33:59 hannele-desktop kernel: [ 1430.426031] usbcore: deregistering interface driver ndiswrapper

 Apr  6 14:33:59 hannele-desktop kernel: [ 1430.426846] ndiswrapper (ntoskernel_exit:2677): object f460e320(2) was not freed, freeing it now 

Apr  6 14:33:59 hannele-desktop kernel: [ 1430.441063] ndiswrapper version 1.55 loaded (smp=yes, preempt=no) 

Apr  6 14:33:59 hannele-desktop kernel: [ 1430.564263] usb 1-4: reset high speed USB device using ehci_hcd and address 3 

Apr  6 14:33:59 hannele-desktop loadndisdriver: loadndisdriver: load_driver(358: couldn't load driver net8192cu

 Apr  6 14:33:59 hannele-desktop kernel: [ 1430.705582] usbcore: registered new interface driver ndiswrapper  

Here is all the info:
hannele@hannele-desktop:~$ lsusb

Bus 001 Device 003: ID 050d:1102 Belkin Components

hannele@hannele-desktop:~$ iwconfig lo        no wireless extensions.  eth1      no wireless extensions.  

 hannele@hannele-desktop:~$ dmesg | grep -i belkin 
 [   24.928271] UDF-fs INFO UDF: Mounting volume 'Belkin F7D1102v', timestamp 2011/07/06 09:33 (10b4) 
 

 hannele@hannele-desktop:~$ lsb_release -d 
 Description:    Ubuntu 10.04.2 LTS
 

 hannele@hannele-desktop:~$ uname -mr 
 2.6.32-32-generic i686
 

 Any help will be appreciated, thx! :p

 

 -4udi

---

### Post by praseodym on 2012-04-06
Install the driver from Realtek, and uninstall ndiswrapper before:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

Installation (you should update your system first, kernel 2.6.32-40 is up-to-date!):

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192 
```
Reboot.

---

### Post by 4udi on 2012-04-06
Thx for the reply. I updated me kernel and installed those realtek drivers. I got my wlan to work and for a while everything seemed to be ok but...
Now my ubuntu freezes right after the login. If I pull the usb stick out, everything works fine. Bad driver maybe ? :confused:

-4udi

---

### Post by praseodym on 2012-04-06
What computer is that? Please show

```
lsmod
lsusb
iwconfig
sudo iwlist scan
```

---

### Post by 4udi on 2012-04-06
The problem is I cannot execute those commands if I have the wireless stick on, it freezes right away after it starts to scan networks, after login. 

Should I uninstall the driver? What is correct command? Then I could maybe plug the wireless adapter back without getting the freeze.

-4udi

---

### Post by 4udi on 2012-04-06
This is what shows in the logs when I plug the adapter and when it freezes, so generally nothing that could help:

Apr  6 21:24:49 hannele-desktop kernel: [ 2350.572038] usb 1-1: new high speed USB device using ehci_hcd and address 3
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.707027] usb 1-1: configuration #1 chosen from 1 choice
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763227] 
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763231] rtw driver version=v3.3.2_3192.20120103
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763292] register rtw_netdev_ops to netdev_ops
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763298] CHIP TYPE: RTL8188C_8192C
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763306] 
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763308] usb_endpoint_descriptor(0):
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763311] bLength=7
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763314] bDescriptorType=5
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763317] bEndpointAddress=81
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763320] wMaxPacketSize=200
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763323] bInterval=0
Apr  6 21:24:49 hannele-desktop kernel: [ 2350.763326] RT_usb_endpoint_is_bApr  6 21:26:35 hannele-desktop kernel: imklog 4.2.0, log s
ource = /proc/kmsg started.

---

### Post by praseodym on 2012-04-07
Maybe this driver is "too new", uninstall it via

```
sudo dkms remove -m rtl8192cu -v 3.3.23192 --all 
sudo depmod -a
sudo update-initramfs -u
```
and try an earlier version:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/33/30/2844083-rtl8192cu-3.1.2590_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.1.2590_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```

---

### Post by 4udi on 2012-04-07
Many thanks, that seemed to fix the problem! ):P):P
-4udi

---

