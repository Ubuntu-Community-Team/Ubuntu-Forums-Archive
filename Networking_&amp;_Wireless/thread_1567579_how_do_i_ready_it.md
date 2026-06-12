---
title: "how do i ready it?"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by soryu on 2010-09-04
mint@mint-desktop ~ $ dmesg | grep -e ndis -e wlan
[   12.380275] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.963490] ndiswrapper: driver rt61 (Linksys, A Division of Cisco Systems, Inc.,03/09/2006, 1.01.00.0000) loaded
[   13.964681] ndiswrapper 0000:00:03.0: enabling device (0004 -> 0006)
[   13.965202] ndiswrapper 0000:00:03.0: PCI INT A -> Link[LNKA] -> GSI 3 (level, low) -> IRQ 3
[   13.979487] ndiswrapper: using IRQ 3
[   14.201685] wlan0: ethernet device 00:1e:e5:a9:72:3b using serialized NDIS driver: rt61, version: 0x10001, NDIS version: 0x500, vendor: 'Wireless-G Business PCI Adapter ', 1814:0401.5.conf
[   14.201734] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   14.237322] usbcore: registered new interface driver ndiswrapper
[   24.043345] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by scorp123 on 2010-09-04
Did you ask on the Mint forum?

---

### Post by soryu on 2010-09-04
i don't  think that there are to many people on there.
usually i get faster responses & more help here.:popcorn:

---

### Post by soryu on 2010-09-04
the card is installed and on. pci (light does blink)
ndiswrapper claims card .
should i blacklist the alternate driver?
where can i get some info on how to set up network tools?


( Q: Who cuts the grass on Walton's )
( Mountain? A: Lawn Boy.            )
 -----------------------------------
  o
   o
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
mint@mint-desktop ~ $ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt61 : driver installed
	device (1814:0401) present (alternate driver: rt61pci)
mint@mint-desktop ~ $

---

### Post by scorp123 on 2010-09-04
The problem is that Mint does a lot of things differently than Ubuntu ...

---

### Post by dmizer on 2010-09-04
Have you simply tried to use Network-Manager to connect? If not, is there anything in System -> Administration -> Networking?

It seems like everything is working correctly, you just need to configure the card. So use the graphical networking tools available to you in Mint.

---

### Post by soryu on 2010-09-04
here goes a shot of system>admin>network tools.
wireless interface(wlan0) shows it's enabled.
but what do i need to do next?

currently using the ethernet interface(eth0).

---

### Post by dmizer on 2010-09-04
No, not network tools ... networking.

Look for a network configuration tool in your toolbar (perhaps in the top right corner), not in the menu.

---

### Post by dmizer on 2010-09-04
No, not network tools ... networking.

Look for a network configuration tool in your toolbar (perhaps in the top right corner), not in the menu.

---

### Post by linux18 on 2010-09-04
lshw -C network | grep "driver"  # take a note of the driver
modprobe $driver #replace $driver with the driver 
ifconfig wlan0 down #reset interface
dhclient -r wlan0 #set up dhcp
ifconfig wlan0 up #turn on wireless capabilitiy
iwlist scan | grep ESSID; echo #find your network essid, take note, case sensative
iwconfig wlan0 essid "$essid" #replace $essid with your essid, keep the quotes
iwconfig wlan0 mode managed #allow interface to communicate between computer and router
dhclient wlan0 #get a DHCP lease and start networking

your done with command line network configuration! enjoy!

P.S. many of these commands require sudo.

---

### Post by soryu on 2010-09-04
i have network tools and windows wireless drivers in administration and network connections and network proxy in preferences.

---

### Post by soryu on 2010-09-04
> **linux18 said:**
> lshw -C network | grep "driver"  # take a note of the driver
modprobe $driver #replace $driver with the driver 
ifconfig wlan0 down #reset interface
dhclient -r wlan0 #set up dhcp
ifconfig wlan0 up #turn on wireless capabilitiy
iwlist scan | grep ESSID; echo #find your network essid, take note, case sensative
iwconfig wlan0 essid "$essid" #replace $essid with your essid, keep the quotes
iwconfig wlan0 mode managed #allow interface to communicate between computer and router
dhclient wlan0 #get a DHCP lease and start networking

your done with command line network configuration! enjoy!

P.S. many of these commands require sudo.




can you explain the steps?

---

### Post by linux18 on 2010-09-04
the notes are in the comment lines (lines starting with #) here is a clearer example:

1. this will find your wireless driver and ethernet driver
  lshw -C network | grep "driver"  

2. this will load your driver, replace your_driver with the driver from the first step
 modprobe your_driver

3. these set up your wireless interface
 ifconfig wlan0 down
 dhclient -r wlan0
 ifconfig wlan0 up
 
4. this will scan your network for wireless networks, take note of your essid
 iwlist scan | grep ESSID

5. replace your_essid with the essid from the previous step, it's case sensative, requires those quotes, and doesn't work on encrypted networks
  iwconfig wlan0 essid "your_essid"

6. this connects your wireless interface with the internet
 iwconfig wlan0 mode managed
 dhclient wlan0

if you get permission denied, use sudo

---

### Post by soryu on 2010-09-05
mint@mint-desktop ~ $ lshw -C network | grep "driver" 
WARNING: you should run this program as super-user.
       configuration: broadcast=yes driver=ndiswrapper+rt61 driverversion=1.55+Linksys, A Division of Cisc latency=66 multicast=yes wireless=IEEE 802.11g
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=66 maxlatency=64 mingnt=32 multicast=yes
mint@mint-desktop ~ $ modprobe your_driver
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module your_driver not found.
mint@mint-desktop ~ $ 
:???:

---

### Post by linux18 on 2010-09-05
> **soryu said:**
> mint@mint-desktop ~ $ lshw -C network | grep "driver" 
WARNING: you should run this program as super-user.
       configuration: broadcast=yes driver=ndiswrapper+rt61 driverversion=1.55+Linksys, A Division of Cisc latency=66 multicast=yes wireless=IEEE 802.11g
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=66 maxlatency=64 mingnt=32 multicast=yes
mint@mint-desktop ~ $ modprobe your_driver
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module your_driver not found.
mint@mint-desktop ~ $ 
:???:
I said replace your_driver with the driver name from the previous step, yours is ndiswrapper so it's probably already loaded, proceed with the next steps

---

### Post by houndi on 2010-09-05
Look for a network configuration tool in your toolbar (perhaps in the top right corner), not in the menu.

---

### Post by soryu on 2010-09-05
here goes the commands.

________________________________________
/ Q: Why do mountain climbers rope       \
| themselves together? A: To prevent the |
\ sensible ones from going home.         /
 ----------------------------------------
  \
   \
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
mint@mint-desktop ~ $ ifconfig wlan0 down
SIOCSIFFLAGS: Permission denied
mint@mint-desktop ~ $ sudo ifconfig wlan0 down
[sudo] password for mint: 
mint@mint-desktop ~ $ dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Open a socket for LPF: Operation not permitted
mint@mint-desktop ~ $ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:e5:a9:72:3b
Sending on   LPF/wlan0/00:1e:e5:a9:72:3b
Sending on   Socket/fallback
mint@mint-desktop ~ $ sudo ifconfig wlan0 up
mint@mint-desktop ~ $ iwlist scan | grep ESSID
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                    ESSID:"J5V76"
                    ESSID:"BPJ52"
                    ESSID:"RQFN0"
                    ESSID:"Freeman"
                    ESSID:""
                    ESSID:"68PGU"
mint@mint-desktop ~ $ sudo iwconfig wlan0 essid "J5V76"
mint@mint-desktop ~ $ sudo iwconfig wlan0 mode managed
mint@mint-desktop ~ $ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:e5:a9:72:3b
Sending on   LPF/wlan0/00:1e:e5:a9:72:3b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
mint@mint-desktop ~ $

---

### Post by soryu on 2010-09-05
> **houndi said:**
> Look for a network configuration tool in your toolbar (perhaps in the top right corner), not in the menu.

there isn't one in mint.
just   mintupdate.

---

### Post by linux18 on 2010-09-05
post the output of iwlist scan, it looks like there are 6 networks in your range

---

### Post by soryu on 2010-09-05
mint@mint-desktop ~ $ nm-tool

NetworkManager Tool

State: connected


** (process:3306): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        00:1E:E5:A9:72:3B
 what about this?

---

### Post by linux18 on 2010-09-05
try nm-applet

---

### Post by soryu on 2010-09-05
how do i keep that there, it goes when i close the terminal.

---

### Post by linux18 on 2010-09-05
nm-applet & disown nm-applet

---

### Post by soryu on 2010-09-05
HEy NOw!:KS

just needed that applet to switch connection.
 now connected wireless.
thank's for all the help.):P

---

### Post by linux18 on 2010-09-05
and...












































SOLVED!!!
if it still works on reboot

---

### Post by soryu on 2010-09-05
how do i add that applet at start up?

---

### Post by linux18 on 2010-09-05
[http://forums.linuxmint.com/viewtopic.php?f=175&t=51560](http://forums.linuxmint.com/viewtopic.php?f=175&t=51560)

---

### Post by soryu on 2010-09-05
thank's linux18.

wonder why but i
had to reinstall nvidia drivers resolution got stuck at 800x600.
just added nm-applet at startup.

---

### Post by linux18 on 2010-09-05
press <ctrl>+<alt>+<F1> to get to a prompt then:
sudo /etc/init.d/gdm stop (you might have lxdm not gdm, replace if necessary)
nvidia-xconfig
sudo /etc/init.d/gdm stop (or lxdm if necessary)
once back into the desktop:
gksudo nvidia-settings
then change the resolution to whatever you want

---

