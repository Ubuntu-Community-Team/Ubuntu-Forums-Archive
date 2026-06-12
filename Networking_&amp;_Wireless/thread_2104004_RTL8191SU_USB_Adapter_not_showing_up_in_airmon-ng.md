---
title: "RTL8191SU USB Adapter not showing up in airmon-ng"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by rockboy2003 on 2013-01-11
Im having an issue with my Wireless Adapter. I cannot get it to be detected with airmon-ng yet the device will pick up wireless networks using Applications/internet/Wicd Network Manager.
  I am using Backtrack 5 R1 32-bit version with VMWare 9.0
  root@bt:~# uname –a
  Linux bt 206.39.4 #1 SMP Thu Aug 18 13.:38:02 NZST 2011 i686 GNU/Linux
  The chipset of the wireless USB adapter is RTL8191SU.
  root@bt:~# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  When I run iwconfig and ifconfig I get
  root@bt:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@bt:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0c:29:bc:84:b9  
          inet addr:192.168.164.128  Bcast:192.168.164.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:febc:84b9/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:3718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3858560 (3.8 MB)  TX bytes:386062 (386.0 KB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9877 (9.8 KB)  TX bytes:9877 (9.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:72:3b:dc:0b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  I then ran “lshw –c network to see what drivers are being used
  root@bt:~# lshw -c network
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 10
       serial: 00:0c:29:bc:84:b9
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.4.0 duplex=full firmware=N/A ip=192.168.164.128 latency=64 link=yes maxlatency=255 mingnt=6 port=twisted pair speed=1GB/s
       resources: irq:19 ioport:2000(size=128) memory:dc400000-dc40ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:02:72:3b:dc:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
  Ok so everything indicates that Backtrack is detecting my device
  But when I run airmon-ng I get
  root@bt:~# airmon-ng


Interface    Chipset        Driver


root@bt:~#
   
  My guess is the driver that is being used is wrong so I began to run a series of commands
  root@bt:-~# apt-get update
  then
  root@bt:-~#  apt-get install reaver
  then
  root@bt:-~#  sudo apt-get install linux-headers
  then
  root@bt:-~#  prepare-kernel-sources
  root@bt:-~#  cd /usr/src/linux
  root@bt:-~#  cp -rf include/generated/* include/linux/
  then I found the linux  driver for my wireless device at 
  [http://www.wireless-driver.com/download/realtek/realtek-rtl8191se-rtl8192se-wireless-drivers-utility.htm](http://www.wireless-driver.com/download/realtek/realtek-rtl8191se-rtl8192se-wireless-drivers-utility.htm)
  I downloaded the file to the root directors of my computer and ran the following commands
  root@bt:-~#   tar zxf rtl8192se_linux_2.6.0015.0127.2010.tar.gz
  root@bt:-~#   cd rtl8192se_linux_2.6.0015.0127.2010
  root@bt:-~#   make
  root@bt:-~#   sudo make install
  root@bt:-~#   reboot
  once the computer restarted I again tried airmon-ng and again with the same result… NOTHING!
  I tried “lshw –c network” and saw that the wireless device was still showing “r8712u” as the driver
  So I tried to locate the r8712u.ko file and found it to be located at
  Lib/modles/2.6.39.4/kernel/drivers/staging/rtl8712
  I noticed that there was a folder named “rtl8192u and inside was a file r8192u_usb.ko
  So then I used 
  root@bt:-~#  modprobe  -r r8712u
  root@bt:-~#  modprobe r8192u_usb
  root@bt:-~#  airmon-ng
  AGAIN NOTHING!!! UGH
  Let it be noted that I tried this many more then several times and in different combinations trying “modprobe  -r r8712u” then removing the wireless adapter then “modprobe r8192u_usb” then reconnecting the adapter. I also tried 
  root@bt:-~#  modprobe  -r r8712u
  root@bt:-~#  ifconfig wlan0 down
  the disconnect adapter
  root@bt:-~#  modprobe r8192u_usb
  then reconnect adapter then
  root@bt:-~#  airmon-ng
  and again nothing
  Also after every failure of airmon-ng I would run
  root@bt:-~#  lshw  -c network 
  and see that the same r8712u driver was being used
  I then tried blacklisting the r8712u.ko file
  I will note that I did not know how to do this via “root@bt:-~# “ so i instead went to 
  Etc/modprobe.d
  Opened the file blacklist.conf
  And at the bottom wrote in “blacklist r8712u” and saved the file and did
  root@bt:-~#  reboot
  However after this when I connected the usb adapter it was not detected at all no ifconfig, iwconfig, lsusb nothing.
  I tried 
  root@bt:-~#  modprobe r8192u_usb
  then the same ifconfig, iwconfig, lsusb nothing. So I finally went back to the blacklist.conf file and removed my entry and reboot and it again detected my adapter.
  The best I can tell is I somehow failed to associate my wireless adapter with this driver or this driver it incorrect. So I went online again and found another linux driver for my adapter . I went to
  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
  downloaded the linux version of the driver. Sent it to my root folder and ran
  [FONT=&quot]root@bt:-~# tar zxvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz[/FONT]
  then
  root@bt:-~# sh install.sh
  received 2 compiling errors.
  Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.39.4/build M=/root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'
  CC [M]  /root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
In file included from /root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:77,
                 from /root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_io.h:36:28: error: linux/smp_lock.h: No such file or directory
make[2]: *** [/root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
  Made my way to the driver folder
  [FONT=&quot]rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/[/FONT] [FONT=&quot]rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver[/FONT]
  [FONT=&quot]ran[/FONT]
  root@bt:-~#  su
  root@bt:-~#  make
  same two errors. 
  Restarted computer any ways and ran airmon-ng again big surprise Zilch
  Ran lshw -c network
  And again same results as final post. Im at my whitts end someone please help me. Im out of ideas. Accept buying a different adapter. But I love the one that I have plus I cant return it

---

