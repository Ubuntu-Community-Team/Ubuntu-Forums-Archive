---
title: "help on ZD1211 plz"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by yieever on 2010-02-08
ii guyz..
emm..i got problem to install zd1211 to my ubuntu..i found a lot of guide to install it.. .i not understand in this part:
1.>>>>>>
_________________________________________________________________________
[I]One has to modify the Makefile according to the path of “kernel source tree” and the version of the kernel in your system. In the Makefile, you may see the following statements, 
# if the kernel is 2.6.x, turn on this 
#KERN_26=y 
#KERNEL_SOURCE=/usr/src/linux-2.6.7 
# if the kernel is 2.4.x, turn on this 
KERN_24=y 
KERNEL_SOURCE=/usr/src/linux-2.4.20-8 
If you want to build the kernel under the kernel of 2.4.x, one has to let the variable KERN_24=y and comment the KERN_26=y like that as the example above and modify the variable KERNEL_SOURCE to the path which you install the kernel source.[/I]
__________________________________________________________________________

and this one: 
________________________________________________________________________
[I]2.3 Install individual driver: 
If you only need driver of ZD1211 or ZD1211B, you can issue :

 make clean
 make ZD1211REV_B=0 (0 for ZD1211, 1 for ZD1211B)
 make ZD1211REV_B=0 install (0 for ZD1211, 1 for ZD1211B)

to install the driver.
________________________________________________________________________
[/I]
for information, im using :
ubuntu 9.10, 
kernel 2.6.31-19-generic-pae
smcwusb-eu g.

hope some1 gonna help me..

---

### Post by chili555 on 2010-02-08
I have this on my system and I suspect you do too:> /lib/modules/2.6.31-19-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.31-19-generic/updates/cw/zd1211rw.koThe *cw* version comes from *linux-backports-modules*.

Is the built-in version not working correctly?

---

### Post by yieever on 2010-02-08
then how to do that..im newbie ubuntu..i was google..but cannot fix my problem.

---

### Post by chili555 on 2010-02-08
Let's be sure the device you have is actually a zd1211 device. With the device inserted, please open a terminal and do:```
lsusb
```Please post the result.

Please also do:```
sudo modprobe zd1211rw
iwconfig
```Do you see a wireless interface now?

---

### Post by yieever on 2010-02-08
before, i was follow this guide, but i stop in half way, coz i not understand in some part
[http://ubuntuforums.org/archive/index.php/t-195259.html](http://ubuntuforums.org/archive/index.php/t-195259.html)

and..can ya add me : 1- [email]yie_4ever@yahoo.com[/email] or
                                2- [email]yie4ever85@hotmail.com[/email]

and this is result :
________________________________________________________________________________
akaboshi@akaboshi-TaKA:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
akaboshi@akaboshi-TaKA:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 083a:4505 Accton Technology Corp. SMCWUSB-G
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
akaboshi@akaboshi-TaKA:~$ sudo modprobe zd1211rw
[sudo] password for akaboshi: 
akaboshi@akaboshi-TaKA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

akaboshi@akaboshi-TaKA:~$
________________________________________________________________________________

---

### Post by chili555 on 2010-02-08
> wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated Here you are! Here is your wireless interface. Now can you click the Network Manager icon at the top right of your desktop, see your network and connect?

It appears you have two USB wireless devices. Do you know which one created the wlan0 wireless interface? Do you care? Do you just want one to work correctly?

---

