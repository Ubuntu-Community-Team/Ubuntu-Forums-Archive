---
title: "BCM4318 [AirForce One 54g] 802.11g Wireless install on Ubuntu 9.10"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by sharobim on 2009-11-22
Thanks for accepting me as a new friend – I am new to Ubuntu and have used the version 8.10, 9.4 and  now 9.10 just for experimenting (nice system).
 Version 9.4 installed my wireless without intervention and worked fine on Dell Latitude D600. After reformatting the disk and installing XP (wireless OK here) I thought installing 9.10 for dual boot. (all works fine execpt for the wireless)
 I followed all leads in the forum to reinstall the WIRELESS and unfortunately could not get it going. It sees all wireless but after trying to connect to mine, it comes back with enter password?again and again

 Here are some of the printout that could be relevant to the problem but as I have no clue where to look or what to do, I hope some one can lead me to the solution.
 

 Thanks
 

 

 

 /devices/platform/i8042/serio1/input/input8 
 [    7.853017] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded  
 [    7.853303] ndiswrapper 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5  
 [    7.861234] ndiswrapper: using IRQ 5 
 [    8.050430] __ratelimit: 3 callbacks suppressed  
 [    8.050435] type=1505 audit(1258568821.583:12): operation="profile_replace" pid=723 name=/usr/share/gdm/guest-session/Xsession  
 

 &&&&&&
 

 [    8.097880] type=1505 audit(1258568821.631:21): operation="profile_replace" pid=728 name=/usr/sbin/tcpdump  
 [    8.220858] wlan0: ethernet device 00:0e:9b:d5:85:27 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf  
 [    8.220901] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK  
 [    8.220982] usbcore: registered new interface driver ndiswrapper  
 [   12.118545]  sdb1  
 [   12.137104] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [   12.137111] sd 2:0:0:0: [sdb] Attached SCSI disk  
 [   12.420451] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:011d]  
 x mode  
 [   23.543541] pci 0000:01:00.0: putting AGP V2 device into 4x mode  
 [   23.783849] [drm] Setting GART location based on new memory map  
 [   23.783861] [drm] Loading R200 Microcode  
 [   23.783916] [drm] writeback test succeeded in 2 usecs  
 [   31.192029] eth0: no IPv6 routers present  
 [   34.477912] ndiswrapper (iw_set_auth:1602): invalid cmd 12  
 [   34.996097] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 [   45.188036] wlan0: no IPv6 routers present  
 [   83.692042] Clocksource tsc unstable (delta = -170007931 ns)  
 

 mike@mike-laptop:~$ sudo lshw -C network  
 [sudo] password for mike:  
   *-network:0              
        description: Ethernet interface  
        product: NetXtreme BCM5705M Gigabit Ethernet  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 01  
        serial: 00:11:43:42:71:1a  
        size: 100MB/s  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 66MHz  
        capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5705-v3.16 ip=192.168.2.16 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s  
        resources: irq:11 memory:faff0000-faffffff  
   *-network:1  
        description: Wireless interface  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 3  
        bus info: pci@0000:02:03.0  
        logical name: wlan0  
        version: 02  
        serial: 00:0e:9b:d5:85:27  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master ethernet physical wireless  
        configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,10/12/2006, 4.100. latency=32 link=no multicast=yes wireless=IEEE 802.11g  
        resources: irq:5 memory:fafee000-fafeffff  
   
 mike@mike-laptop:~$ lsb_release -d  
 Description:    Ubuntu 9.10  
   
 mike@mike-laptop:~$ uname -mr  
 2.6.31-14-generic i686  
 

 mike@mike-laptop:~$ sudo /etc/init.d/networking restart  
 
[LIST]
[*]Reconfiguring network     interfaces...
[*] Ignoring unknown interface     eth0=eth0.
[/LIST]
                                                                             [ OK ]  
 mike@mike-laptop:~$  
 

 

 mike@mike-laptop:~$ sudo apt-get install cabextract 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 cabextract is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 mike@mike-laptop:~$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
 --2009-11-13 08:44:42--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
            => `sp34152.exe' 
 Resolving ftp.compaq.com... 15.193.32.70 
 Connecting to ftp.compaq.com|15.193.32.70|:21... connected. 
 Logging in as anonymous ... Logged in! 
 ==> SYST ... done.    ==> PWD ... done. 
 ==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done. 
 ==> SIZE sp34152.exe ... 4494456 
 ==> PASV ... done.    ==> RETR sp34152.exe ... done. 
 Length: 4494456 (4.3M) 
  
 100%[======================================>] 4,494,456    179K/s   in 20s      
  
 2009-11-13 08:45:04 (216 KB/s) - `sp34152.exe' saved [4494456] 
  
 mike@mike-laptop:~$ cabextract sp33008.exe 
 

 mike@mike-laptop:~$ sudo dhclient wlan0 
 

 

 [sudo] password for mike:  
 Internet Systems Consortium DHCP Client V3.1.2 
 Copyright 2004-2008 Internet Systems Consortium. 
 All rights reserved. 
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
  
 Listening on LPF/wlan0/00:0e:9b:d5:85:27 
 Sending on   LPF/wlan0/00:0e:9b:d5:85:27 
 Sending on   Socket/fallback 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
 No DHCPOFFERS received. 
 No working leases in persistent database - sleeping. 
  * Reloading /etc/samba/smb.conf smbd only 
    ...done. 
 mike@mike-laptop:~$  
 

 

 mike@mike-laptop:~$ ndiswrapper -l 
 WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. 
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. 
 bcmwl5 : driver installed 
     device (14E4:4318) present (alternate driver: ssb) 
 mike@mike-laptop:~$

---

