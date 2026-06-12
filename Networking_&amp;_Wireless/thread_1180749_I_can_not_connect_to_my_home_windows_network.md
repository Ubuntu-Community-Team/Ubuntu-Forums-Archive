---
title: "I can not connect to my home windows network"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by panamallis on 2009-06-07
:KSI installed ubuntu 9.04 and I can not connect to my home windows network. When I had ubuntu 8.10 I did not have such a problem. What might be the problem? The windows metwok is working

---

### Post by Boondoklife on 2009-06-07
Could you give a little more information? Are you getting any error messages?

---

### Post by Iowan on 2009-06-07
Wired or wireless?
Static address or DHCP?
Please post results of: 
**ifconfig -a**
**lshw -C network**

---

### Post by panamallis on 2009-06-07
Wired 
DHCP
I use arouter to have access to internet and local area network

When I try PLAces network I see an icon of windows network but I get the message I canot mount 
Please find below the results of the commands you mentioned
administrator@pcgr:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:bf:93:9b:f9  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe93:9bf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1986511 (1.9 MB)  TX bytes:308217 (308.2 KB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2052 (2.0 KB)  TX bytes:2052 (2.0 KB)

pan0      Link encap:Ethernet  HWaddr 4e:62:41:fa:3e:5b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

administrator@pcgr:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 10
       serial: 00:50:bf:93:9b:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.3 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:62:41:fa:3e:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Iowan on 2009-06-07
Hmmm...  it's the filesharing that's not working? Can you **ping** the machine(s)?

---

### Post by panamallis on 2009-06-07
how can I do that?

---

### Post by panamallis on 2009-06-07
I tried network tools and yes I can pink them

---

### Post by superprash2003 on 2009-06-08
try accessing the windows shared folders via ip address
For reference : [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by dmizer on 2009-06-08
Also, take a look at the 6th link in my sig.

---

### Post by swerdna on 2009-06-08
Post here the Samba configuration file and we'll review your configuration. You can view it  with this command in a Gnome terminal: ```
cat /etc/samba/smb.conf > /home/yourusername/Desktop/smb.conf.txt
```That will place a copy of the file on your desktop for examination. Use the correct user name instead of "yourusername".

---

