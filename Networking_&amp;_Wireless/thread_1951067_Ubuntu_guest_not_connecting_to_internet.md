---
title: "Ubuntu guest not connecting to internet"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by surfcast23 on 2012-04-01
Hi I am running Ubuntu 10.04 through Oracles VirtualBox on a Windows xp host. I have not used the Unbuntu side to connect to the internet for a few months and could not get a connection when I tried today. The only thing that has changed is that I updated VirtualBox to the latest version. I am using the NAT connection, but I have also tried a bridged with no success. I would appreciate any help in trouble shooting this problem. Thanks in advance

---

### Post by papibe on 2012-04-01
HI surfcast23.

Are you using the server or the desktop version?

Could you post the result of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig ubuntu.com
```
Regards.

---

### Post by surfcast23 on 2012-04-01
Hi papibe,

  The server or desktop of ubuntu or VBox?

the results are
[FONT=monospace]
**ifconfig**

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

**route -n**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

[B]nslookup ubuntu.com
[/B]
;; connection timed out; no servers could be reached
[B]dig ubuntu.com

[/B]; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
[/FONT]

---

### Post by papibe on 2012-04-01
I meant the Ubuntu version.

Your results clearly show no connection at all, no even an IP.

Does anything has change around the LAN where the XP machine lives?

Could you post the result of this command on XP?
```
ipconfig /all
```
Regards.

---

### Post by surfcast23 on 2012-04-01
Hi Papibe, 

 Here it is 

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\K>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : LENOVO-7F14482C
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 11a/b/g Wireless LAN Mini PCI Expres
s Adapter
        Physical Address. . . . . . . . . : 00-19-7E-85-95-E4
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Sunday, April 01, 2012 9:46:11 PM
        Lease Expires . . . . . . . . . . : Sunday, April 08, 2012 9:46:11 PM

Ethernet adapter VirtualBox Host-Only Network:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapte
r
        Physical Address. . . . . . . . . : 08-00-27-00-78-86
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.56.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :


I don't think anything has changed with the xp LAN
Thank you

---

### Post by papibe on 2012-04-01
It looks like VB DHCP is disable. Try enable it by doing:
[LIST]
[*]Turn off your virtual machine.
[*]Go to File -> Preferences.
[*]Select Network on the left list.
[*]Click the 'screw driver' icon to edit the network interface.
[*]In the new window go to the DHCP tab.
[*]Check the box 'Enable Server'.
[*]Turn on your virtual machine.
[/LIST]
Tell us how it goes.
Regards.

---

### Post by surfcast23 on 2012-04-01
I will try what you suggested. I just wanted to ask how you determined that the VB DHCP was disabled?

It seems as if the DHCP server is enabled

---

### Post by papibe on 2012-04-01
From the results of your ipconfig:
> **surfcast23 said:**
> 
Ethernet adapter VirtualBox Host-Only Network:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapte
r
        Physical Address. . . . . . . . . : 08-00-27-00-78-86
        **[COLOR="Red"]Dhcp Enabled. . . . . . . . . . . : No[/COLOR]**
        IP Address. . . . . . . . . . . . : 192.168.56.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Regards.

---

### Post by surfcast23 on 2012-04-01
Weird. When I look at file--> preferences -->networks it says that the DHCP server is enabled

---

### Post by papibe on 2012-04-01
May be we need to take a look at the Ubuntu settings.

Is this a Ubuntu Server or Desktop edition?

Regards.

---

### Post by surfcast23 on 2012-04-01
Desktop edition

---

### Post by papibe on 2012-04-01
Go to System -> Preferences -> Network Connections and check if DHCP is enable.

Select the interface and edit it. 'Connect Automatically' should be enabled. Also in the 'IPv4 Settings' tab the method should be: 'Automatic DHCP'

Tell us how it goes.
Regards.

---

### Post by surfcast23 on 2012-04-02
Is this in the guest or host?

---

### Post by surfcast23 on 2012-04-02
Where can I find the IPv4 Settings' tab

found it and it is set to auto

---

### Post by surfcast23 on 2012-04-02
in the guest after  System -> Preferences -> Network Connections there is noting to check to enable DHCP

---

### Post by papibe on 2012-04-02
What is the VB's version did you upgrade it from?
What is the actual VB's version?

Regards.

---

### Post by surfcast23 on 2012-04-02
I upgraded to version 4.1.10. To be honest I do not recall what the previous version was. The last time I upgraded was in May of 2011 I think.

---

### Post by surfcast23 on 2012-04-02
In System-->Prefrences-->Network Connections should I be using the wired or wireless connection for the guest system? The host is connected to the internet through a wireless router. Also should the host and guest be using the same MAC address?

---

### Post by papibe on 2012-04-02
> **surfcast23 said:**
> In System-->Prefrences-->Network Connections should I be using the wired or wireless connection for the guest system?
wired.

> **surfcast23 said:**
> Also should the host and guest be using the same MAC address?
No. They have to different.

Regards.

---

### Post by surfcast23 on 2012-04-02
Okay. So I have it set for a wired connection and it is using a different MAC address than the host. I have also made sure that all of the settings are as you advised, but still nothing.

---

### Post by papibe on 2012-04-02
Note that this should also be checked on:
```
Settings -> Network -> Advanced -> 'Cable Connected'
```
Regards.

---

### Post by surfcast23 on 2012-04-02
> **papibe said:**
> Note that this should also be checked on:
```
Settings -> Network -> Advanced -> 'Cable Connected'
```Regards.


In the VBox under the network setting cable connected is checked.

---

### Post by lJ9%3MR&gt;sa on 2012-04-02
Do you have the latest VBOX software installed inside Ubuntu? You may have to manually start the installer with:
 
```
 
sudo sh INSTALLERNAMEHERE.sh

```
I remember having to do that for everything to work correctly when updating VBOX.:p

---

### Post by surfcast23 on 2012-04-02
> **faxmanloveswaffles said:**
> Do you have the latest VBOX software installed inside Ubuntu? You may have to manually start the installer with:
 
```
 
sudo sh INSTALLERNAMEHERE.sh

```I remember having to do that for everything to work correctly when updating VBOX.:p

I need to update VBox in the guest as well?  Do you know where or how I can find the installer?

---

### Post by surfcast23 on 2012-04-02
> **faxmanloveswaffles said:**
> Do you have the latest VBOX software installed inside Ubuntu? You may have to manually start the installer with:
 
```
 
sudo sh INSTALLERNAMEHERE.sh

```I remember having to do that for everything to work correctly when updating VBOX.:p

Were you refering to the guest additions? If so I installed and still nothing.

---

### Post by surfcast23 on 2012-04-04
bump

---

