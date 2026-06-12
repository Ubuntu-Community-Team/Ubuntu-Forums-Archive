---
title: "Maverick Wireless problem on Toshiba a505-s6958"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by c0lored on 2011-02-20
After hours of searching and trying different methods I am still unable to get my wireless going.. I have tried the PPA method from Chilli and looked through craneman's thread. I have installed the proper realtek driver and done modprobe for the device to no avail. In Additional drivers nothing shows except for my ATI drivers. I would really appreciate some help. Also I am using Maverick.

here is some useful commands that may help diagnose


dnkbd@losnix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:bd:d5:10  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:febd:d510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:844456 (844.4 KB)  TX bytes:168503 (168.5 KB)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

dnkbd@losnix:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not permitted
dnkbd@losnix:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
dnkbd@losnix:~$ sudo lshw -C Network
  *-network DISABLED      
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:5f:98:f6:07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE ip=64.78.178.63 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:6000(size=256) memory:e7200000-e7203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:bd:d5:10
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:4000(size=256) memory:e1010000-e1010fff memory:e1000000-e100ffff memory:e1020000-e103ffff

---

### Post by c0lored on 2011-02-20
No help? really? I am so frustrated.... lshw -C Network shows that it is there, though it is marked disabled, that command also show that it is using the rtl8192e driver, which matches the card I have... I am running out of ideas please help

---

### Post by c0lored on 2011-02-20
bump in desperate need of help

---

### Post by eldergs on 2011-02-23
Hi. I have the same problem and notebook. But, readying so many forum and post, I resolved the problem.

Sorry for my bad english.

First, open your terminal.

Run the code:

**lsmod | grep 819**

I think will show:

r8192e_pci
r8192se_pci

This is the conflicting drivers.

Now, run this code (to add r8192se_pci in blacklist):

[B]sudo su
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
exit[/B]

**Reboot**

Now, Download the newest driver from realtek, they mail me with instructions and file (I post in some servers)

[http://eldergs.4shared.com](http://eldergs.4shared.com)
[http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html](http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html)
[http://www.megaupload.com/?d=F2R0S36T](http://www.megaupload.com/?d=F2R0S36T)

Now do what the support from realtek say:

[B]Hi Sir,               
 
Thanks for your email.
 
Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the updated one different from the one you used.
 
Just kindly remind, please install by the below steps.
The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
 
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).
 
If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delet it first before install:
 
 
    1) cd /lib/modules/2.6.3x.xx.xx/
    2) find -name "r8192e_pci.ko"
    3) delet all the r8192e_pci.ko
    4) install our RTL8192E driver
    5) reboot.
 
 
if there’s still any other problem, please let us know.
   Thanks a lot
 
Regards,
Kidman[/B]

Reboot

Now, You can use your Wireless and have fun.

:)

---

