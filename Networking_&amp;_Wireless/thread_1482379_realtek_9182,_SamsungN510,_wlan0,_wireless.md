---
title: "realtek 9182, SamsungN510, wlan0, wireless"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by aixroot on 2010-05-13
Hi there,

I trying to get my realtek wireless to work again after a recent update of my samsung n510

I copied some things underneath which I expect might help.

Please ask which ever file you need.

running 10.04

Regards,

Ferdinand



=================
ferdinand@ferdinand-netbook:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
ferdinand@ferdinand-netbook:~$ sudo ifconfig wlan up
[sudo] password for ferdinand: 
wlan: ERROR while getting interface flags: No such device
ferdinand@ferdinand-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions

ferdinand@ferdinand-netbook:~$ 
ferdinand@ferdinand-netbook:~$ more /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ferdinand@ferdinand-netbook:~$ cd rtl8192se_linux_2.6.0015.0127.2010/
ferdinand@ferdinand-netbook:~/rtl8192se_linux_2.6.0015.0127.2010$ ./wlan0upcp: cannot create regular file `/etc/acpi/events/RadioPower.sh': Permission denied
insmod: error inserting 'r8192se_pci.ko': -1 Operation not permitted
ferdinand@ferdinand-netbook:~/rtl8192se_linux_2.6.0015.0127.2010$ 
==========================

lspci 
<snip>
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
ferdinand@ferdinand-netbook:~/rtl8192se_linux_2.6.0015.0127.2010$ 

=================

---

