---
title: "Wireless will not connect to desktoop"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by jhouse59 on 2009-06-15
My wired connection on my laptop will connect to my desktop computer. But, the wireless won't. The wireless will connect to the internet.
I've added "eth1" to the > interfaces = 127.0.0.0/8 eth0, line in the smb.conf file.
To make it > interfaces = 127.0.0.0/8 eth0, eth1 Could this be what is causing my problem? Also, have I added that right? Because it still is not working.

---

### Post by MaindotC on 2009-06-16
I don't understand.  Are you trying to use your wireless adapter on your laptop to connect to the wireless adapter on your desktop?

---

### Post by superprash2003 on 2009-06-16
are the machines able to ping each other when connected wirelessly??

---

### Post by jhouse59 on 2009-06-16
> **strAlan said:**
> I don't understand.  Are you trying to use your wireless adapter on your laptop to connect to the wireless adapter on your desktop?

No, my desktop doesn't have wireless. I'm just trying to network my laptop and desktop. The wired connection on my laptop will connect to the wired on my desktop. When I have the wireless card in my laptop the computers can't see each other, either way.


> **superprash2003 said:**
> are the machines able to ping each other when connected wirelessly??
No I can't ping each other. My desktop doesn't have wireless.

---

### Post by superprash2003 on 2009-06-16
i mean when the laptop is connected wirelessly..

---

### Post by jhouse59 on 2009-06-16
> **superprash2003 said:**
> i mean when the laptop is connected wirelessly..

No they won't ping each other. Now they will work great if I've got the wire connected.
And, the wireless will connect to the internet.

---

### Post by MaindotC on 2009-06-16
I don't think the items you mentioned in your first post have anything to do with this issue and frankly I'd prefer you put them back the way the originally were.

Post the output of:
```

lshw -C network
ifconfig
iwconfig
iwlist scan

```

You say your wireless card can access Internet resources (like yahoo, google, ubuntu etc) so answer:  Can you ping your access point?

---

### Post by jhouse59 on 2009-06-17
> **strAlan said:**
> I don't think the items you mentioned in your first post have anything to do with this issue and frankly I'd prefer you put them back the way the originally were.

Did it.

This is what I got from **lshw -C network**.
> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:4b:d7:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.103 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:01:f4:ed:3a:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.06 ip=192.168.1.104 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

This is what I got from **ifconfig**.
> eth0      Link encap:Ethernet  HWaddr 00:d0:59:4b:d7:eb  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe4b:d7eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4374129 (4.1 MB)  TX bytes:700536 (684.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:01:f4:ed:3a:c3  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:f4ff:feed:3ac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28681 (28.0 KB)  TX bytes:7125 (6.9 KB)
          Interrupt:3 Base address:0x180 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:269302 (262.9 KB)  TX bytes:269302 (262.9 KB)


This is what I got from **iwconfig**.
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1A:70:E3:C9:B1   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/92  Signal level=-32 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

This is what I got from **iwlist scan**.
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:70:E3:C9:B1
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Signal level:-32 dBm  Noise level:-91 dBm
                    Encryption key:off

vboxnet0  Interface doesn't support scanning.

> You say your wireless card can access Internet resources (like yahoo, google, ubuntu etc) so answer:  Can you ping your access point?
If you mean my router. Yes I can.

---

### Post by Iowan on 2009-06-17
Both interfaces have addresses in the same subnet?  That'll probably confuse routing...

---

### Post by MaindotC on 2009-06-17
jhouse - is that output from your Desktop or your laptop?  If it's from your desktop I recommend you disable one of the interfaces.  Actually, whether it's your laptop or desktop you should only be using one interface unless there's more to this story...

---

### Post by jhouse59 on 2009-06-18
> **strAlan said:**
> jhouse - is that output from your Desktop or your laptop?  If it's from your desktop I recommend you disable one of the interfaces.  Actually, whether it's your laptop or desktop you should only be using one interface unless there's more to this story...

This is the output from my laptop. When your talking aout the interface. I'm guessing your talking of the "eth0 and . One is my wired (eth0) and the other is my wireless (eth1) connection. How would I disable the wired.

---

### Post by MaindotC on 2009-06-20
Disable the wired by typing:
[code]
sudo ifconfig eth0 down
[code]
or use the ifdown command.

---

### Post by jhouse59 on 2009-06-24
> **strAlan said:**
> Disable the wired by typing:
[code]
sudo ifconfig eth0 down
[code]
or use the ifdown command.

Thanks, strAlan
I disabled the wired. I can connect to my desktop now. Well I've tried it one time. They don't show up in the "Network Servers" as an icon. I have to type the IP address in the window address bar. But, so far it is working.

---

### Post by MaindotC on 2009-06-24
Typically you have to type in the IP address unless your DNS server has an entry that maps the machine name to an IP address, and you are using that DNS server, or if the machine's name (or alias) is in /etc/hosts.  Or I think another option is LDAP but that's way more documentation then I'm ever willing to do.

---

