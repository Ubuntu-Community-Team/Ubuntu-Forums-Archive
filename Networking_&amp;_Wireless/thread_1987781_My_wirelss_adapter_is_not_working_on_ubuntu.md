---
title: "My wirelss adapter is not working on ubuntu"
date: 2012-05-26
forum: Networking &amp; Wireless
---

### Post by Bbrraadd on 2012-05-26
jean-marie@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

jean-marie@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d81 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:0137 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 413c:2110 Dell Computer Corp. 
Bus 001 Device 002: ID 413c:1010 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jean-marie@ubuntu:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
jean-marie@ubuntu:~$ lsb_release -d 
Description:    Ubuntu 10.04.3 LTS
jean-marie@ubuntu:~$

---

### Post by chili555 on 2012-05-26
Now let's see what you have for a driver:```
lsmod | grep -e b43 -e wl
```

---

### Post by Bbrraadd on 2012-05-26
jean-marie@ubuntu:~$ lsmod | grep -e b43 -e wl
b43                   182290  0 
mac80211              238896  1 b43
cfg80211              148341  2 b43,mac80211
led_class               3764  3 b43,hp_accel,sdhci
ssb                    45427  1 b43
jean-marie@ubuntu:~$

---

### Post by chili555 on 2012-05-26
Please hook up a temporary ethernet connection, if not already, and do:```
sudo su
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
apt-get install bcmwl-kernel-source dkms
exit
```Reboot and let us have your report. I need a quick Solved.

---

### Post by Bbrraadd on 2012-05-26
i dont understand 'hookup' sorry i am not too good with it :)

---

### Post by chili555 on 2012-05-26
In order to get new packages, in this case the correct driver for your wireless card, you need the ability to access the internet. Please attach an ethernet cable from the router to the laptop, make sure you have an internet connection and proceed.

---

### Post by Bbrraadd on 2012-05-26
jean-marie@ubuntu:~$ sudo su
[sudo] password for jean-marie: 
root@ubuntu:/home/jean-marie# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
root@ubuntu:/home/jean-marie# apt-get install bcmwl-kernel-source dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 114 not upgraded.
Need to get 967kB of archives.
After this operation, 3,342kB of additional disk space will be used.
Err [ftp://archive.sun.ac.za/ubuntu/](ftp://archive.sun.ac.za/ubuntu/) lucid-updates/main dkms 2.1.1.2-2ubuntu1
  504  Gateway Time-out [IP: 146.232.65.6 3128]
Err [ftp://archive.sun.ac.za/ubuntu/](ftp://archive.sun.ac.za/ubuntu/) lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  504  Gateway Time-out [IP: 146.232.65.6 3128]
Failed to fetch [ftp://archive.sun.ac.za/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2ubuntu1_all.deb](ftp://archive.sun.ac.za/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2ubuntu1_all.deb)  504  Gateway Time-out [IP: 146.232.65.6 3128]
Failed to fetch [ftp://archive.sun.ac.za/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb](ftp://archive.sun.ac.za/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb)  504  Gateway Time-out [IP: 146.232.65.6 3128]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/home/jean-marie#

---

### Post by chili555 on 2012-05-26
> Err [COLOR="Red"]ftp://archive.sun.ac.za/ubuntu/[/COLOR] lucid-updates/main dkms 2.1.1.2-2ubuntu1
504 Gateway Time-out [IP: 146.232.65.6 3128]I can't reach it either. Give me a few moments to start up my 10.04 computer. Be back in a few moments.

Edit: Please go to System > Administration > Software Sources and pick a different server than what you have now and try again. Please see attached.

---

### Post by Bbrraadd on 2012-05-26
jean-marie@ubuntu:~$ sudo su
[sudo] password for jean-marie: 
root@ubuntu:/home/jean-marie# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
root@ubuntu:/home/jean-marie# apt-get install bcmwl-kernel-source dkms
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/home/jean-marie#

---

### Post by chili555 on 2012-05-26
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. So, did you?```
sudo dpkg --configure -a
```

---

