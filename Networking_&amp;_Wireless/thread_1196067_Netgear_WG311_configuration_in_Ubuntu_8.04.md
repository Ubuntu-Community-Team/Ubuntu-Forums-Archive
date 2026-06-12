---
title: "Netgear WG311 configuration in Ubuntu 8.04"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by gangasabu on 2009-06-24
Hi 
I request someone to help me to sort out the issue of wireless configuration on my computer.
My operating system is Ubuntu 8.04, Modem is HUAWEI Quidway WA1003A, and Wireless adapter is NETGEAR WG311.
I tried configuring the connection using help available on web page [http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/).

**Details of the settings I made through terminal is given below.**
sabu@sabu-desktop:~$ sudo apt-get update
[sudo] password for sabu: 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
sabu@sabu-desktop:~$ apt-cache search ndiswrapper-utils
ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper Linux kernel module
sabu@sabu-desktop:~$  sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.4kB of archives.
After this operation, 213kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11.4kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19.0kB]
Fetched 30.4kB in 1s (15.5kB/s)               
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 115091 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...
sabu@sabu-desktop:~$ cd /tmp/
sabu@sabu-desktop:/tmp$ wget [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
--17:52:24--  [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
           => `wg311v3_1_0.zip'
Resolving downloads.netgear.com... 207.211.82.170
Connecting to downloads.netgear.com|207.211.82.170|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /files ... done.
==> PASV ... done.    ==> RETR wg311v3_1_0.zip ... done.
Length: 65,02,117 (6.2M) (unauthoritative)

100%[====================================>] 65,02,117    600.03B/s    ETA 00:00

20:48:24 (615.96 B/s) - Data transfer aborted.
Retrying.

--20:48:25--  [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
  (try: 2) => `wg311v3_1_0.zip'
==> CWD not required.
==> SIZE wg311v3_1_0.zip ... 
Error in server response, closing control connection.
Retrying.

--20:48:27--  [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
  (try: 3) => `wg311v3_1_0.zip'
Connecting to downloads.netgear.com|207.211.82.170|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /files ... done.
==> PASV ... done.    ==> RETR wg311v3_1_0.zip ... done.
wg311v3_1_0.zip has sprung into existence.
Retrying.

--20:48:33--  [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
  (try: 4) => `wg311v3_1_0.zip.1'
Connecting to downloads.netgear.com|207.211.82.170|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /files ... done.
==> PASV ... done.    ==> RETR wg311v3_1_0.zip ... done.
Length: 65,02,117 (6.2M) (unauthoritative)

100%[====================================>] 65,02,117    118.01K/s    ETA 00:00

20:51:58 (31.51 KB/s) - `wg311v3_1_0.zip.1' saved [6502117]

sabu@sabu-desktop:/tmp$  unzip wg311v3_1_0.zip
Archive:  wg311v3_1_0.zip
   creating: WG311v3 V1.0/Utility/
  inflating: WG311v3 V1.0/Utility/setup.exe  
   creating: WG311v3 V1.0/Driver/
   creating: WG311v3 V1.0/Driver/Windows XP/
  inflating: WG311v3 V1.0/Driver/Windows XP/WG311v3.INF  
 extracting: WG311v3 V1.0/Driver/Windows XP/WG311v3.cat  
  inflating: WG311v3 V1.0/Driver/Windows XP/WG311v3.sys  
  inflating: WG311v3 V1.0/Driver/Windows XP/WG311v3XP.sys  
   creating: WG311v3 V1.0/Driver/Windows ME/
  inflating: WG311v3 V1.0/Driver/Windows ME/WG311v3.INF  
  inflating: WG311v3 V1.0/Driver/Windows ME/WG311v3.sys  
   creating: WG311v3 V1.0/Driver/Windows 98/
  inflating: WG311v3 V1.0/Driver/Windows 98/WG311v3.INF  
  inflating: WG311v3 V1.0/Driver/Windows 98/WG311v3.sys  
   creating: WG311v3 V1.0/Driver/Windows 2000/
  inflating: WG311v3 V1.0/Driver/Windows 2000/WG311v3.INF  
 extracting: WG311v3 V1.0/Driver/Windows 2000/WG311v3.cat  
  inflating: WG311v3 V1.0/Driver/Windows 2000/WG311v3.sys  
  inflating: WG311v3 V1.0/Driver/Windows 2000/WG311v3XP.sys  
sabu@sabu-desktop:/tmp$ cd "/tmp/WG311v3 V1.0/Driver/Windows XP/"
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$  sudo ndiswrapper -i WG311v3.INF
[sudo] password for sabu: 
installing wg311v3 ...
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ sudo modprobe ndiswrappersabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ gksudo gedit /etc/wpa_supplicant.conf
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ sudo wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ sudo ifconfig wlan0 up
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$  sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$  sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6761
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ sudo dhclient wlan0
[sudo] password for sabu: 
There is already a pid file /var/run/dhclient.pid with pid 6828
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   LPF/wlan0/00:1e:2a:b5:13:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sabu@sabu-desktop:/tmp/WG311v3 V1.0/Driver/Windows XP$ 

Whenever I choose network settings "Wireless connection" with ESSID and with out "Enable roaming mode", network connection icon is the picture of two computers.

Whenever I choose network settings "Wireless connection" with "Enable roaming mode", network connection icon is the picture wireless signals.

In both the cases, Wireless networking is getting possible.

Screen shot of both situations are attached here with.
Regards
Gangasabu

---

