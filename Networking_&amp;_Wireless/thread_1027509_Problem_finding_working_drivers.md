---
title: "Problem finding working drivers"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by bradwal on 2009-01-01
I just installed ubuntu 8.10 yesterday then tried learning it on the fly and Im pretty much lost. Ive spent about a day and a half now trying to figure out how to get my wireless working but after reading through countless guides and threads I still cant figure it out. Ive downloaded my windows drivers (.exe) then extracted them and 2/4 had .inf files in them that I installed using the "Windows Wireless Drivers" program so I might just need some simple fix. Could someone tell me what i need to do?


I have a Gateway 4520gz laptop, heres a link to my drivers that i downloaded  - 

[http://support.gateway.com/support/drivers/search.asp?st=pn&param=3727](http://support.gateway.com/support/drivers/search.asp?st=pn&param=3727)







Here's everything I tried doing in Terminal -


bad@bad-laptop:~$   sudo ndiswrapper -i ~/home/bad/Desktop/drivers/D00044-001-001/autorun.inf
[sudo] password for bad: 
couldn't open /home/bad/home/bad/Desktop/drivers/D00044-001-001/autorun.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
bad@bad-laptop:~$ sudo ndiswrapper -i ~/bad/desktop/drivers/D00044-001-001/autorun.inf
couldn't open /home/bad/bad/desktop/drivers/D00044-001-001/autorun.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
bad@bad-laptop:~$ sudo ndiswrapper -i ~/desktop/drivers/D00044-001-001/autorun.inf
couldn't open /home/bad/desktop/drivers/D00044-001-001/autorun.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
bad@bad-laptop:~$ network-admin
The program 'network-admin' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-network-admin
bash: network-admin: command not found
bad@bad-laptop:~$ sudo apt-get install gnome-network-admin
[sudo] password for bad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gnome-network-admin
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 274kB of archives.
After this operation, 688kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe gnome-network-admin 2.22.1-0ubuntu1 [274kB]
Fetched 274kB in 4s (65.9kB/s)                         
Selecting previously deselected package gnome-network-admin.
(Reading database ... 125285 files and directories currently installed.)
Unpacking gnome-network-admin (from .../gnome-network-admin_2.22.1-0ubuntu1_i386.deb) ...
Setting up gnome-network-admin (2.22.1-0ubuntu1) ...

bad@bad-laptop:~$ nm-applet

** (nm-applet:11844): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:11844): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
bad@bad-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
bad@bad-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
bad@bad-laptop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
bad@bad-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
bad@bad-laptop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
bad@bad-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:10:57:e9  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe10:57e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163665707 (163.6 MB)  TX bytes:6414982 (6.4 MB)
          Interrupt:10 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:27:e0:72  
          inet6 addr: fe80::20e:35ff:fe27:e072/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1819 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xa000 Memory:e0200000-e0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2092 (2.0 KB)  TX bytes:2092 (2.0 KB)

bad@bad-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bad@bad-laptop:~$ sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.
bad@bad-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
bad@bad-laptop:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
bad@bad-laptop:~$ sudo rm -r /etc/ndiswrapper/
bad@bad-laptop:~$ sudo rm -r /etc/modprobe.d/ndiswrapper
rm: cannot remove `/etc/modprobe.d/ndiswrapper': No such file or directory
bad@bad-laptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
bad@bad-laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
couldn't open /home/bad/Desktop/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
bad@bad-laptop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

bad@bad-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> done
bash: syntax error near unexpected token `done'
bad@bad-laptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
bad@bad-laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
couldn't open /home/bad/Desktop/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
bad@bad-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

bad@bad-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
bad@bad-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
bad@bad-laptop:~$ cd /home/bad/Desktop/drivers/D00044-001-001.exe
bash: cd: /home/bad/Desktop/drivers/D00044-001-001.exe: Not a directory
bad@bad-laptop:~$ cd /home/bad/Desktop/drivers/D00044001001.exe
bash: cd: /home/bad/Desktop/drivers/D00044001001.exe: Not a directory
bad@bad-laptop:~$ cd /desktop/drivers/D00044001001.exe
bash: cd: /desktop/drivers/D00044001001.exe: No such file or directory
bad@bad-laptop:~$ cd </home/bad/desktop/drivers/d00044001001.exe>
bash: syntax error near unexpected token `newline'

---

