---
title: "wifi on the dell, tried a lot of things"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by greenjah on 2013-01-30
hi all,
can someone help me ? i've already tried a lot of items but not one helped :(

output of commands:
$ rfkill list
2: hci0: Bluetooth
   Soft blocked: yes
   Hard blocked: no

$ iwconfig 
lo        no wireless extensions.
eth0      no wireless extensions.

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits

$ dmesg | grep wl
[ 1871.085616] wl: module license 'MIXED/Proprietary' taints kernel.

$ sudo apt-get install --reinstall bcmwl-kernel-source
...
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
...

commands:
$ sudo modprobe wl
$ sudo modprobe b43
were executed without any output

please, help!

---

### Post by chili555 on 2013-01-30
Please check here: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

---

