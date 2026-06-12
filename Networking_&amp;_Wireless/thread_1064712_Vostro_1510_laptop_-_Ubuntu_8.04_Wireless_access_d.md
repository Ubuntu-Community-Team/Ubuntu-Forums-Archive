---
title: "Vostro 1510 laptop - Ubuntu 8.04 Wireless access disappears."
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by twocats on 2009-02-09
Problem: I  have a Dell Vostro 1510 running Ubuntu LTS 8.04. Six months ago I had wireless running with the normal wireless network program but four months ago I lost wireless connection when the wireless option disapeared from my "network Settings" gui. I googled until I came across "wicd" which i installed and then all was good....until the other day when I lost the "wireless" setting again. I have uninstalled and reinstalled "wicd" without result. I tried "ndiswrapper" but could not get a Windows driver as an .inf file. I do not want to reinstall the system as I have got everything else running perfectly. Fortunately, I can run the computer on ethernet - blue cable - into my wireless base station. I have appended below the results of some searches recommended by this site. I know that this seems to be a common problem, but apart from ndiswrapper which I failed with,I have not seen any solutions. Bluetooth was also working but has now gone. This could also be significant. recently, on boot up the computer ran a complete self diagnostic check before it would start. That took about 45 minutes. When it started, the wireless and bluetooth had disappeared.

RESULTS FROM COMMAND LINE TESTS:

START 

lspci gives:
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61



ifconfig gives:
eth0      Link encap:Ethernet  HWaddr 00:1c:23:55:5f:d6
          inet addr:10.0.1.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe55:5fd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4968 errors:0 dropped:1118733627 overruns:0 frame:0
          TX packets:5130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5100894 (4.8 MB)  TX bytes:967570 (944.8 KB)
          Interrupt:218 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:104398 (101.9 KB)  TX bytes:104398 (101.9 KB)



iwconfig gives:
lo        no wireless extensions.

eth0      no wireless extensions.

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


iwconfig wlan0 gives:
wlan0     No such device


lsmod gives:
iwlwifi_mac80211      219108  1 iwl4965
(along with a lot of other stuff)


lsmod | grep "wlan_module_name" gives:
Nothing


sudo lshw -C network gives:
[sudo] password for tom:
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:55:5f:d6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.0.1.2 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s



iwlist scan gives:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


lsb_release -d gives:
Description:    Ubuntu 8.04.2

uname -mr gives:
2.6.24-23-generic i686


and last but not least...
sudo /etc/init.d/networking restart gives:
 * Reconfiguring network interfaces...                                                                                                  RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6403
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1c:23:55:5f:d6
Sending on   LPF/eth0/00:1c:23:55:5f:d6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.1.1 port 67
Ignoring unknown interface wlan1=wlan1.
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1c:23:55:5f:d6
Sending on   LPF/eth0/00:1c:23:55:5f:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
receive_packet failed on eth0: Network is down
Terminated
Failed to bring up eth0.

END:

OK, That's it. I have probably committed every sin in the  book!
I await your verdict.

---

### Post by wapa17 on 2009-03-10
OK.. I have a Vostro 1510 / Hardy Heron 8.04 too and I want tell you how I did:

1.) You have a Dell express-servicecode on the back of your laptop. Go to the Dell-homepage and with this servicecode you can download the (windows)-drivers. Select the XP-drivers and not the vista.

2.) the "Only" working results I got (with WiFi, sound, media-keys, headphone functionating) with kernel 2.6.24-19-generic !! With every kernelupdate I lost wifi, wired network and sound, So i decided to continue with this 2.6.24-19-generic-kernel. (Never change a winnning team ;-)

A "quick and dirty" workaround: you can edit the menu.lst in /boot/grub and set the default to the number of the 2.6.24-19-generic-kernel which should bring back Wifi.

---

