---
title: "samsung media player yp-k3"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Red-Shield on 2008-06-06
i am looking for help for my media player it is the samsung yp-k3 i have tried using amarok i can erase media files on the device but not play them or add to them i feel i am close can some one help or provide some suggestions 


here are some of the print out's:


serial-killer@AMD64:~$ dmesg | tail
[  555.784000] usb 3-4: USB disconnect, address 3
[  600.232000] usb 3-4: new high speed USB device using ehci_hcd and address 4
[  600.380000] usb 3-4: configuration #1 chosen from 1 choice
[  706.964000] usb 3-4: usbfs: USBDEVFS_CONTROL failed cmd amarokapp rqt 192 rq 1 len 1024 ret -110
[  848.400000] usb 3-4: USB disconnect, address 4
[  878.492000] usb 3-4: new high speed USB device using ehci_hcd and address 5
[  878.640000] usb 3-4: configuration #1 chosen from 1 choice
[  996.004000] usb 3-4: USB disconnect, address 5
[ 1014.648000] usb 3-4: new high speed USB device using ehci_hcd and address 6
[ 1014.780000] usb 3-4: configuration #1 chosen from 1 choice


serial-killer@AMD64:~$ lsusb
Bus 003 Device 006: ID 04e8:5081 Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

serial-killer@AMD64:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

