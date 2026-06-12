---
title: "Ethernet Issues"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by broken sword on 2009-07-17
I need a lil assistance. I updated my system this morning ( I only mention this because this is the only thing that changed my system ). I noticed a dhcp-client update this morning, my system worked fine today, testing it on different networks, up until I ran into an issue when I was at a client who had two DHCP server enabled. After I disabled one of the DHCP server, my laptop wouldn't connect to the Internet.

It seems like my ethernet adapter is disabled, but the wireless works. When I restart networking, I get the following

>   * Reconfiguring network interfaces...                                          resolvconf: Error: /etc/resolv.conf must be a symlink
resolvconf: Error: /etc/resolv.conf must be a symlink
run-parts: /etc/network/if-down.d/resolvconf exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 19984
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:78:bf:d1
Sending on   LPF/wlan0/00:1d:e0:78:bf:d1
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
resolvconf: Error: /etc/resolv.conf must be a symlink
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
RTNETLINK answers: No such process
resolvconf: Error: /etc/resolv.conf must be a symlink
resolvconf: Error: /etc/resolv.conf must be a symlink
run-parts: /etc/network/if-down.d/resolvconf exited with return code 1
There is already a pid file /var/run/dhclient.eth0.pid with pid 20080
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1d:09:43:0c:84
Sending on   LPF/eth0/00:1d:09:43:0c:84
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
resolvconf: Error: /etc/resolv.conf must be a symlink
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:78:bf:d1
Sending on   LPF/wlan0/00:1d:e0:78:bf:d1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
resolvconf: Error: /etc/resolv.conf must be a symlink
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
resolvconf: Error: /etc/resolv.conf must be a symlink
run-parts: /etc/network/if-up.d/000resolvconf exited with return code 1
 * if-up.d/mountnfs[wlan0]: waiting for interface eth0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1d:09:43:0c:84
Sending on   LPF/eth0/00:1d:09:43:0c:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 192.168.1.101 -- renewal in 42360 seconds.
resolvconf: Error: /etc/resolv.conf must be a symlink
run-parts: /etc/network/if-up.d/000resolvconf exited with return code 1
                                                                         [ OK ] 

any assistance would be greatly appreciated

---

### Post by superprash2003 on 2009-07-17
seems to be similar to this [http://ubuntuforums.org/showthread.php?t=1168970](http://ubuntuforums.org/showthread.php?t=1168970)

---

### Post by 2uRcJQ34G1 on 2009-10-28
[FONT="Tahoma"][SIZE="6"][COLOR="Red"]I fixed it!!:guitar:[/COLOR][/SIZE][SIZE="4"]This is how:
if you see this error.
Error: /etc/resolv.conf must be a symlink

Here is the fix
$ cd /etc
$ sudo rm -rf /etc/resolv.conf
$/etc$ sudo ln -s /etc/resolvconf/run/resolv.conf

reboot the machine and try connecting again[/SIZE]
[SIZE="4"][COLOR="Blue"]Cheers to all those who tried to help.:KS[/COLOR][/SIZE][/FONT]

---

