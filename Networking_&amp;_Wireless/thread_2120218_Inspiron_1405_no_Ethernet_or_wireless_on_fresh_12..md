---
title: "Inspiron 1405 no Ethernet or wireless on fresh 12.04 install"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by Ditchdoc7893 on 2013-02-26
Hello all! Tonight I was doing a fresh install of 12.04 on my husband's Dell Inspiron 1405. After successful install of the OS, neither the Ethernet connection or wireless connection were working. I believe that this machine has the Broadcom 4311 on it. Since I am unable to connect to the Internet in any way from this machine, I have no way to directly install the appropriate driver directly from the Internet. I have multiple other machines at my disposal with more than adequate connectivity, so surely there is a way that I can get the appropriate driver to the affected machine. I also know that this machine will work with 12.04, as it was previously running on this machine. We needed to format it and start from scratch due to having previously upgraded multiple times from previous versions of Ubuntu, and it running ridiculously slowly (no thanks to zeitgeist... Which I have no idea how to deal with). Can anyone assist me in how best to accomplish this?  

Thank you in advance for any assistance you can offer!

Ditchdoc

---

### Post by Bucky Ball on 2013-02-26
*Thread moved to **Networking & Wireless**.*

---

### Post by ahallubuntu on 2013-02-26
~

---

### Post by Ditchdoc7893 on 2013-02-26
Yes, the power cable was plugged into the wall. I have checked my networking settings just to make sure that networking was enabled, and it is.

---

### Post by Ditchdoc7893 on 2013-02-26
As an update to this problem, I reinstalled Ubuntu AGAIN (for the 4th time), when I initially log in immediately after the reboot when the installation completes, I have ethernet capability. I also note that in the restricted drivers, the Broadcom driver is in use. Then I install the necessary updates via the Update Manager. It requires a system reboot when finished, so I reboot. When I log in after the reboot, my ethernet connectivity is gone. When I check under the restricted drivers in system settings, it now does not show that the Broadcom driver is even there. 

Anyone have any fresh ideas?

---

### Post by ahallubuntu on 2013-02-26
~

---

### Post by ahallubuntu on 2013-02-26
~

---

### Post by Ditchdoc7893 on 2013-02-26
Interestingly enough, I initially had tried using the newest kernel (12.04.2), thinking along the same lines as you. This was when I discovered the problem. So I went back to the older kernel and then was able to at least get ethernet connectivity. Then when I went to update the broadcom driver after having installed synaptic. Once I updated the broadcom driver, I then lost all connectivity. Give me just a minute and I'll post the output of the commands you asked for.

---

### Post by Ditchdoc7893 on 2013-02-26
Here is the output of those commands:

```
steve@SteveLaptop:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:70:78:09
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.7 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
steve@SteveLaptop:~$ 

```

```
steve@SteveLaptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
steve@SteveLaptop:~$ 


```

I see that the wireless LAN shows a hard block. I have no idea why. There is no physical switch that I am aware of (other than the FN+F2, which is not doing anything other than turning the Bluetooth on and off).

---

### Post by ahallubuntu on 2013-02-26
~

---

### Post by Ditchdoc7893 on 2013-02-26
I actually got it working, however it was not using any of the above methods. Here's how:

In Synaptic:
-uninstall bcmwl-kernel-source completely
-install firmware-b43-installer and b43-fwcutter 
 
In terminal:
```

cat /etc/modprobe.d/* | egrep 'bcm'

```

See if 'blacklist bcm43xx' shows up. If it does, type in terminal:

```

cd /etc/modprobe.d/

```
then...
```

sudo gedit blacklist.conf

```

Find the line "blacklist bcm43xx" and comment it out by placing a # in front of it.
Save the file.
Reboot the system.

---

### Post by Ditchdoc7893 on 2013-02-26
Thanks everyone for your assistance. I will mark as solved!

---

### Post by Bucky Ball on 2013-02-26
Good news and thanks for sharing the fix. ;)

---

