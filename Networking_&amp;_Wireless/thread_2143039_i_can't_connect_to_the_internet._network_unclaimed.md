---
title: "i can't connect to the internet. network unclaimed . (wired connection)"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by alpimj on 2013-05-07
im having a problem with my ethernet controller. the network is unclaimed when i type a command "lshw -c network". i am using a wired connection.
i am using ubuntu 12.04 LTS.

this is the output when i typed lshw -c network in terminal:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
       resources: memory:feaff000-feafffff ioport:bc00(size=64)

---

### Post by papibe on 2013-05-07
Hi alpimj.

Could you post the results of these commands?
```
lsmod | grep -i e100

apt-cache policy network-manager

cat /etc/network/interfaces
```
Regards.

---

### Post by alpimj on 2013-05-07
> **papibe said:**
> Hi alpimj.

Could you post the results of these commands?
```
lsmod | grep -i e100

apt-cache policy network-manager

cat /etc/network/interfaces
```
Regards.


# **lsmod | grep -i e100**
e1000e                183635  0 
e100                   36324  0 


#** apt-cache policy network-manager**
network-manager:
  Installed: 0.9.4.0-0ubuntu4.2
  Candidate: 0.9.4.0-0ubuntu4.2
  Version table:
 *** 0.9.4.0-0ubuntu4.2 0
        100 /var/lib/dpkg/status


# **cat /etc/network/interfaces**
auto lo
iface lo inet loopback

---

### Post by chili555 on 2013-05-07
May we also see:```
dmesg | grep e100
```

---

### Post by alpimj on 2013-05-07
.

---

### Post by alpimj on 2013-05-07
> **chili555 said:**
> May we also see:```
dmesg | grep e100
```


# **dmesg | grep e100**
[    0.335752] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    2.101807] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.101833] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.125427] e100 0000:03:08.0: (unregistered net_device): EEPROM corrupted
[    2.135164] e100: probe of 0000:03:08.0 failed with error -11
[   35.756338] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-NAPI
[   35.756346] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.

---

### Post by chili555 on 2013-05-07
Please try:```
sudo modprobe -r e100
sudo modprobe e100 eeprom_bad_csum_allow=1
dmesg | grep e100
```We are interested in messages after the timestamp above:> [ [COLOR="#FF0000"]2.135164[/COLOR]] e100: probe of 0000:03:08.0 failed with error -11If it works, we'll make it persistent.

---

### Post by alpimj on 2013-05-07
> **chili555 said:**
> Please try:```
sudo modprobe -r e100
sudo modprobe e100 eeprom_bad_csum_allow=1
dmesg | grep e100
```We are interested in messages after the timestamp above:If it works, we'll make it persistent.


it worked! thank you so much! :P

---

### Post by chili555 on 2013-05-07
Are you ready to make it permanent?```
gksudo gedit /etc/modprobe.d/e100.conf

```Add a single line:```
options e100 eeprom_bad_csum_allow=1
```Proofread, save and close gedit. Now do:```
sudo update-initramfs -u
```You should be all set.

---

### Post by alpimj on 2013-05-07
thank you once again! \\:D/ [CENTER][COLOR=#000000]:KS :D[/COLOR][/CENTER]

---

