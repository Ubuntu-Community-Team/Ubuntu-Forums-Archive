---
title: "Wired Connection fails on new install"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by dufflepud on 2010-10-04
Hi,

I have a fresh 10.4.1 install on an IBM Intellistation E Pro  that does not have any network connectivity.  I am wired to a verizon  dsl modem which is working on my other winXP machine that is connected  to it.  I see lights on the ethernet port on the machine.

From looking through previous posts I think this might give some helpful info:

owner@owner-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QH [Radeon 8500] (rev 80)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)



owner@owner-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:38:f5:7f  
          inet6 addr: fe80::209:6bff:fe38:f57f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5470 (5.4 KB)  TX bytes:2178 (2.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6104 (6.1 KB)  TX bytes:6104 (6.1 KB)


caowner@owner-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


owner@owner-desktop:~$ sudo lshw -C network
[sudo] password for owner: 
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:09:6b:38:f5:7f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e100  driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=66  link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:d0100000-d0100fff ioport:3000(size=64)


Thanks for any help you are able to give this noob.

---

### Post by dineshs on 2010-10-05
1)Can you try ```
sudo dhclient eth0
```then post the output(to see whether eth0 is getting a valid IP)
2)Please also post the result of```
ipconfig /all
```in [COLOR="Red"]Windows XP[/COLOR]

---

### Post by dufflepud on 2010-10-05
Hi dineshs,

Here is the output:

owner@owner-desktop:~$ sudo dhclient eth0
[sudo] password for owner: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:09:6b:38:f5:7f
Sending on   LPF/eth0/00:09:6b:38:f5:7f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


This is the ipconfig from my windows XP machine which is another physical machine plugged into the same dsl modem:

Windows IP Configuration

        Host Name . . . . . . . . . . . . : REDROOM
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : myhome.westell.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : myhome.westell.com
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Controller
        Physical Address. . . . . . . . . : 00-0B-DB-BE-5C-4E
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.104
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
                                            192.168.1.1
        Lease Obtained. . . . . . . . . . : Monday, October 04, 2010 8:07:06 PM
        Lease Expires . . . . . . . . . . : Thursday, October 07, 2010 8:07:06 PM


Thank you very much for your help.

---

### Post by dineshs on 2010-10-06
I dont understand why you are not getting DHCP offers in ubuntu(I am not an expert).In my opinion you may try to assign IP manually as follows
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection 
select ipv4 
method-manual 
address [COLOR="Blue"]192.168.1.251[/COLOR]
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 192.168.1.1
then click apply 
Note :[COLOR="Blue"]Try to assign an IP address outside DHCP range[/COLOR]
Now run
```
sudo service network-manager stop
```
```
sudo service network-manager start
```
Please post the results of
```
ping 192.168.1.1 -c3
```and```
ping 4.2.2.1 -c3
```

---

### Post by dufflepud on 2010-10-06
Hi dineshs,

I hard coded the IP as you suggested and had no success for a bit.  Then I rebooted and looked at the back of the system again and the lights on the ethernet cable were out.  I jiggled the cable and they came back on.  After that I rebooted and made sure the lights were on and was able to ping the IP addresses you listed.
So it looks like I have some marginal (at best) hardware going on here.  The ethernet is on board for this machine so I might need to look into getting a card for it.
And now I now where to look for the IP info.  This has been an education so far.  I am hoping to learn a lot here in ubuntu-land.
Thank you so much for your help.

Kindest regards,
dufflepud

---

