---
title: "Micromax Q75 Dual SIm GPRS Model not connected"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by jsmanian on 2012-04-28
Dear All,

    I installed ubuntu 12.04 64bit in my desktop. As I used only 10.04 till now, it looks great for me. Thanks for excellent OS...

    I have only one issue. I could not connect to internet through my micromax Q75 mobile GPRS modem. It is dual sim mobile. I want to connect through sim-2. 

    When I connect my mobile through wire, ubuntu detected "New broadand.." I set my country and service provider and all details. 
When I click to connect, ubuntu is trying and I got message 

     "No wired connection detected" 

Please help me. I want to learn Openfoam software and internet connection is essential for this.

Note: I can connect to internet with same mobile in windows without any issues.

with regards,
Subramanian

---

### Post by jsmanian on 2012-04-28
Anyone could guide me to solve this issue????

---

### Post by alexfish on 2012-04-29
Are you connect bluetooth or usb cable

---

### Post by jsmanian on 2012-04-29
Hi,

     I am connecting through cable. Ubuntu detects it. But internet is not connected.

     Let me know if I need to give some more information

with regards,
Subramanian

---

### Post by alexfish on 2012-04-29
can post results of this command from the terminal
```
usb-devices

```

---

### Post by jsmanian on 2012-04-29
I got this output. I am using 64Bit Ubuntu 12.04. My machine configuration is Intel® Core™2 Duo CPU E4600 @ 2.40GHz × 2 with 2GB ram.


[PHP]subramanian@jsm:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0e8d ProdID=0003 Rev=01.00
S:  Manufacturer=MediaTek Inc
S:  Product=MT6235 
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
[/PHP]

---

### Post by alexfish on 2012-04-29
unless you got another modem connected then this looks like the device
the Two lines highted show cdma driver attatched
```
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0e8d ProdID=0003 Rev=01.00
S:  Manufacturer=MediaTek Inc
S:  Product=MT6235 
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
[COLOR=Blue]I:  If#= 0 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm[/COLOR]
```to see where it is in dev,s can post the results of
```

ls -al /dev/serial/by-id
```and
```
ls /dev/ttyACM*
```

---

### Post by jsmanian on 2012-04-29
Hi,

   No. I don't have CDMA modem connected. It looks like ubuntu is considering my GSM mobile like CDMA modem.
Thanks for your help and I got this output for these two commands

[PHP]subramanian@jsm:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 60 Apr 30 06:08 .
drwxr-xr-x 4 root root 80 Apr 30 06:08 ..
lrwxrwxrwx 1 root root 13 Apr 30 06:08 usb-MediaTek_Inc_MT6235-if01 -> ../../ttyACM0
subramanian@jsm:~$ ls /dev/ttyACM*
/dev/ttyACM0
[/PHP]

---

### Post by alexfish on 2012-04-29
can try an test modem

open up first terminal
```

cat /dev/ttyACM0
```open second terminal
```
echo -e "AT\r" > /dev/ttyACM0
```if get error from the terminals enter as root
```
sudo su
``` and try again

---

### Post by jsmanian on 2012-04-30
I could not reach my computer right now. Tonight,I will get back to you with output of these commands.

with regards,
Subramanian

---

### Post by jsmanian on 2012-04-30
This is the output of these commands
Terminal 1
[PHP]subramanian@jsm:~$ sudo su
[sudo] password for subramanian: 
root@jsm:/home/subramanian# cat /dev/ttyACM0

OK[/PHP]

Terminal 2 

[PHP]subramanian@jsm:~$ 
subramanian@jsm:~$ sudo su
[sudo] password for subramanian: 
root@jsm:/home/subramanian# echo -e "AT\r" > /dev/ttyACM0
root@jsm:/home/subramanian# ^C
root@jsm:/home/subramanian# [/PHP]

with regards,
Subramanian

---

### Post by jsmanian on 2012-04-30
This is the output of these commands

Terminal 1
[PHP]subramanian@jsm:~$ sudo su
[sudo] password for subramanian: 
root@jsm:/home/subramanian# cat /dev/ttyACM0

OK[/PHP]

Terminal 2 

[PHP]subramanian@jsm:~$ 
subramanian@jsm:~$ sudo su
[sudo] password for subramanian: 
root@jsm:/home/subramanian# echo -e "AT\r" > /dev/ttyACM0
root@jsm:/home/subramanian# ^C
root@jsm:/home/subramanian# [/PHP]

with regards,
Subramanian

---

### Post by alexfish on 2012-04-30
Ok

the modem is responding to the at commands : from the first terminal , sent AT short for ATTENTION modem responds  message = OK ,

What happens with Network Manger , can it connect ,

next time redo the commands to ensure the modem has been recognised as previous post , the
post results of this command from the terminal
```

nm-tool
``` , post only the lines which represent the device if any

---

### Post by jsmanian on 2012-04-30
Not success. I followed the same previous commands and after I tried to connect through network manager. It could not connect.

output of nm-tool is 
[PHP]root@jsm:/home/subramanian# echo -e "AT\r" > /dev/ttyACM0
root@jsm:/home/subramanian# nm-tool

NetworkManager Tool

State: disconnected

- Device: ttyACM0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:
[/PHP]

---

### Post by alexfish on 2012-04-30
MM! not sure if problem lays with Network Manager or Modem Manager or if the Actual device is stalling

again check to see the device is recognised and when not connecting

can try killing the MM daemon with this command
```

sudo killall modem-manager
```wait a while then try the connection , if not successful unplug the device and replug

need to know if the kill command works or if re-plugging works and also if the (echo -e "AT\r"  ) command in all cases.

see what happens

---

### Post by jsmanian on 2012-04-30
Hi,

   Finally the kill command is working for sim1 connection for internet. "**sudo killall modem-manager**":p:lolflag:

[PHP]subramanian@jsm:~$ 
subramanian@jsm:~$ sudo killall modem-manager
subramanian@jsm:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: ttyACM0  [Airtel Default] --------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             connected
  Default:           yes
[/PHP]

   Is it possible to connect through sim2. Both are different service provider. I tried in the same way. But it is not connecting through sim2. I thinking that I am disturbing you much. But if it possible to connect through sim2, my all problems are solved.

Thanks in advance...

---

### Post by jsmanian on 2012-05-01
I am facing another issue. Ubuntu hangs on while shutting down. Sometimes is shutting down properly. But many times it hangs on by showing "**ubuntu" background in pink color**. I checked syslog. I think that network manager is causing this problem. I attached syslog here. 

[PHP]May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): disconnecting for new activation request.
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: activated -> disconnected (reason 'none') [100 30 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): deactivating device (reason 'none') [0]
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): canceled DHCP transaction, DHCP client pid 6124
May  1 21:31:08 jsm avahi-daemon[793]: Withdrawing address record for 192.168.42.150 on usb0.
May  1 21:31:08 jsm avahi-daemon[793]: Leaving mDNS multicast group on interface usb0.IPv4 with address 192.168.42.150.
May  1 21:31:08 jsm NetworkManager[744]: <info> DNS: starting dnsmasq...
May  1 21:31:08 jsm avahi-daemon[793]: Interface usb0.IPv4 no longer relevant for mDNS.
May  1 21:31:08 jsm dnsmasq[6142]: exiting on receipt of SIGTERM
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): writing resolv.conf to /sbin/resolvconf
May  1 21:31:08 jsm dnsmasq[6238]: started, version 2.59 cache disabled
May  1 21:31:08 jsm dnsmasq[6238]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  1 21:31:08 jsm dnsmasq[6238]: warning: no upstream servers configured
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) starting connection 'Wired connection 2'
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) scheduled...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) started...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) scheduled...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) complete.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) starting...
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: prepare -> config (reason 'none') [40 50 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) successful.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) complete.
May  1 21:31:08 jsm dbus[701]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) started...
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  1 21:31:08 jsm NetworkManager[744]: <info> dhclient started with pid 6247
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Beginning IP6 addrconf.
May  1 21:31:08 jsm avahi-daemon[793]: Withdrawing address record for fe80::e864:aeff:feda:7d72 on usb0.
May  1 21:31:08 jsm avahi-daemon[793]: Leaving mDNS multicast group on interface usb0.IPv6 with address fe80::e864:aeff:feda:7d72.
May  1 21:31:08 jsm avahi-daemon[793]: Interface usb0.IPv6 no longer relevant for mDNS.
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) complete.
May  1 21:31:08 jsm dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  1 21:31:08 jsm dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  1 21:31:08 jsm dbus[701]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  1 21:31:08 jsm dhclient: All rights reserved.
May  1 21:31:08 jsm dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  1 21:31:08 jsm dhclient: 
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): DHCPv4 state changed nbi -> preinit
May  1 21:31:08 jsm dhclient: Listening on LPF/usb0/ea:64:ae:da:7d:72
May  1 21:31:08 jsm dhclient: Sending on   LPF/usb0/ea:64:ae:da:7d:72
May  1 21:31:08 jsm dhclient: Sending on   Socket/fallback
May  1 21:31:08 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 255.255.255.255 port 67
May  1 21:31:08 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 21:31:08 jsm dhclient: bound to 192.168.42.150 -- renewal in 1581 seconds.
May  1 21:31:08 jsm NetworkManager[744]: <info> (usb0): DHCPv4 state changed preinit -> reboot
May  1 21:31:08 jsm NetworkManager[744]: <info>   address 192.168.42.150
May  1 21:31:08 jsm NetworkManager[744]: <info>   prefix 24 (255.255.255.0)
May  1 21:31:08 jsm NetworkManager[744]: <info>   gateway 192.168.42.129
May  1 21:31:08 jsm NetworkManager[744]: <info>   hostname 'jsm'
May  1 21:31:08 jsm NetworkManager[744]: <info>   nameserver '192.168.42.129'
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  1 21:31:08 jsm NetworkManager[744]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) started...
May  1 21:31:08 jsm avahi-daemon[793]: Joining mDNS multicast group on interface usb0.IPv4 with address 192.168.42.150.
May  1 21:31:08 jsm avahi-daemon[793]: New relevant interface usb0.IPv4 for mDNS.
May  1 21:31:08 jsm avahi-daemon[793]: Registering new address record for 192.168.42.150 on usb0.IPv4.
May  1 21:31:09 jsm dnsmasq[6238]: exiting on receipt of SIGTERM
May  1 21:31:09 jsm NetworkManager[744]: <info> DNS: starting dnsmasq...
May  1 21:31:09 jsm NetworkManager[744]: <info> (usb0): writing resolv.conf to /sbin/resolvconf
May  1 21:31:09 jsm dnsmasq[6265]: started, version 2.59 cache disabled
May  1 21:31:09 jsm dnsmasq[6265]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  1 21:31:09 jsm dnsmasq[6265]: using nameserver 192.168.42.129#53
May  1 21:31:09 jsm NetworkManager[744]: <info> (usb0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  1 21:31:09 jsm NetworkManager[744]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
May  1 21:31:09 jsm NetworkManager[744]: <info> Activation (usb0) successful, device activated.
May  1 21:31:09 jsm NetworkManager[744]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) complete.
May  1 21:31:10 jsm avahi-daemon[793]: Joining mDNS multicast group on interface usb0.IPv6 with address fe80::e864:aeff:feda:7d72.
May  1 21:31:10 jsm avahi-daemon[793]: New relevant interface usb0.IPv6 for mDNS.
May  1 21:31:10 jsm avahi-daemon[793]: Registering new address record for fe80::e864:aeff:feda:7d72 on usb0.*.
May  1 21:31:19 jsm kernel: [20745.568019] usb0: no IPv6 routers present
May  1 21:31:28 jsm NetworkManager[744]: <info> (usb0): IP6 addrconf timed out or failed.
May  1 21:31:28 jsm NetworkManager[744]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  1 21:31:28 jsm NetworkManager[744]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  1 21:31:28 jsm NetworkManager[744]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  1 21:31:36 jsm ntpdate[6299]: adjust time server 91.189.94.4 offset 0.025567 sec
May  1 21:57:29 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 21:57:29 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 21:57:29 jsm dhclient: bound to 192.168.42.150 -- renewal in 1505 seconds.
May  1 21:57:29 jsm NetworkManager[744]: <info> (usb0): DHCPv4 state changed reboot -> renew
May  1 21:57:29 jsm NetworkManager[744]: <info>   address 192.168.42.150
May  1 21:57:29 jsm NetworkManager[744]: <info>   prefix 24 (255.255.255.0)
May  1 21:57:29 jsm NetworkManager[744]: <info>   gateway 192.168.42.129
May  1 21:57:29 jsm NetworkManager[744]: <info>   hostname 'jsm'
May  1 21:57:29 jsm NetworkManager[744]: <info>   nameserver '192.168.42.129'
May  1 21:57:29 jsm dbus[701]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  1 21:57:29 jsm dbus[701]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  1 22:17:01 jsm CRON[6355]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 22:22:34 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 22:22:34 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 22:22:34 jsm dhclient: bound to 192.168.42.150 -- renewal in 1645 seconds.
May  1 22:49:59 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 22:49:59 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 22:49:59 jsm dhclient: bound to 192.168.42.150 -- renewal in 1435 seconds.
May  1 23:13:54 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 23:13:54 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 23:13:54 jsm dhclient: bound to 192.168.42.150 -- renewal in 1465 seconds.
May  1 23:17:01 jsm CRON[6414]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 23:38:19 jsm dhclient: DHCPREQUEST of 192.168.42.150 on usb0 to 192.168.42.129 port 67
May  1 23:38:19 jsm dhclient: DHCPACK of 192.168.42.150 from 192.168.42.129
May  1 23:38:19 jsm dhclient: bound to 192.168.42.150 -- renewal in 1450 seconds.[/PHP]

---

### Post by alexfish on 2012-05-02
try

```
kill -9 dhclient
```

---

### Post by jsmanian on 2012-05-02
Hi, 

    Shall I need to use this command to kill dhclient every time  before shut down the machine? 

    There is any other way to avoid this? I will be in vocation for next four days. I will check and get back to you after my vocation.

Thanks for response;)

---

### Post by jsmanian on 2012-05-07
Hi Alexfish,

   I came from vocation):P. Sorry for the interruption in our discussion.

   I didn't faced hanging issue while shut down the system. I will let you know the output for "kill -9 dhclient" command when it is happened.

   Whenever I want to connect to internet, I need to issue "sudo killall modem-manager" command. Otherwise I can not connect to internet. I don't know how to solve this and another issue is connecting through sim-2 to the internet. I tried and I could not succeed. 

 Please give your comments...

with regards,
subramanian

---

### Post by alexfish on 2012-05-07
Hi , hope had a good one .

will look through the info , then will post asp , as to possible solution. 

alexfish

---

### Post by jsmanian on 2012-05-09
Hi,

   Do you have any comments or suggestion?

with regards,
Subramanian

---

