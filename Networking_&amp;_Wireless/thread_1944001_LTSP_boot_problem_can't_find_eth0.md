---
title: "LTSP boot problem can't find eth0"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by natureb456 on 2012-03-20
Hi,
 
Please help - my LTSP automation system is having problems at work!
 
I have had an LTSP server running Ubuntu 10.04 for over a year now at work and have never had a boot problem (We have had HP thin clients - LTSP always just seemed to work for them). Until we purchased some newer model HP thin clients and I can't get them to boot.
 
The original HP thin clients boot just fine with LTSP through PXE boot.
 
The new HP thin clients PXE boot just fine - but get hung up mid way through the processes with this error:
 
ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/init: .: 1: Can't open /tmp/net-eth0.conf
Kernel panic - not syncing: Attempted to kill init!
 
I used WUBI and installed Ubunut 10.04 through a USB drive very easily on the new HP thin clients and networking correctly works (lspci gives: BCM75580 ethernet PCIe adapter - and it uses TG3) 
 
For comparison I did the same thing with the original HP thin clients:
at a similar point in the boot process it says:
 
NET: Registered protocol family 17
IP_Config: eth0 hardware address :::: mtu 1500 DHCP RARP
Velocity in AUTO mode
(original HP thin clients have VIA Tech JT6120 ethernet adapters)
 
I have some knowledge of LTSP but this issue is beyond me - hence me trying various 'fixes' that I have found around by googling my problem.
 
I have tried multiple things all without avail: adding 'TG3' to:
/opt/ltsp/i386/etc/initramfs-tools/modules 
and 
/opt/ltsp/i386/usr/share/initramfs-tools/hook-functions
and /etc/initramfs-tools/modules
 
and then running (not necessarily in this order)
update-initramfs -u
sudo chroot /opt/ltsp/i386 update-initramfs -u
sudo ltsp-update-image
sudo ltsp-update-kernels 
sudo /etc/init.d/dhcp3-server restart
 
nothing seems to work. Please help.
 
Thanks in advance.

---

