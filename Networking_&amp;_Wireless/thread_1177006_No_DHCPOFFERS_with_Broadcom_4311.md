---
title: "No DHCPOFFERS with Broadcom 4311"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by cberube on 2009-06-02
Hi,

I've recently aquired a Compaq Presario C500 laptop on which I have replaced Vista with Ubuntu 9.04 (Jaunty).  It has the dreaded Broadcom 4311 wireless chipset.

I have followed all kinds of tutorials around the web, spending many many hours trying to get this wireless card to work.

I have used ndiswrapper, the Broadcom STA (wl) driver, and the b43 fwcutter.  

It is not getting the card to be recognized that is the problem.  With any of the methods I can get the driver to take control of the card so that the wireless status light comes on.

Network manager can see my network with a full signal.  The problem is, it can't connect.  It just attempts for about a minute and a half and fails.

When I run dhclient for the wireless card or look in the log it says that no DCHPOFFERS have been received.  

I have also tried static DNS with fully manual settings and it still will not connect.  Wired connection works without a hitch.

Any ideas?  I would greatly appreciate it!

--A frustrated Ubuntu user

---

### Post by superprash2003 on 2009-06-03
post output of **ifconfig **and **iwconfig** from your terminal

---

### Post by cberube on 2009-06-03
Hmm network manager is now reporting that the wireless device is not managed, even though the driver and module is loaded..

Anyways, output of ifconfig is: ```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:c1:af:04  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fec1:af04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:252293 (252.2 KB)  TX bytes:34307 (34.3 KB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:28:7c:6a  
          inet6 addr: fe80::21a:73ff:fe28:7c6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

``` (eth1 is the wireless connection)

And output of iwconfig is: ```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
```Also, as you can see from the output of lshw -C network, the wireless card has the driver and module loaded ```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:28:7c:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11

```Thanks for your help!

---

### Post by Ayuthia on 2009-06-03
Can you try the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
Please let us know if any wireless sites appear.  If not, please post the results of:
```
dmesg|grep wl
lspci -nn
```

---

### Post by cberube on 2009-06-03
Network manager still has the wireless as "device not managed", but following the commands you have posted successfully detected both wireless networks that are in my area. 

The output is: ```
eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:5B:F7:2C
                    ESSID:"CAREN"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:E0:98:D6:2A:20
                    ESSID:"Berube House"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-30 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

```

Cell 02 is the network I want to connect to.  It is unsecured currently with no MAC address filtering, so I am at a loss why I can't connect to it (other devices, including this computer with Vista on it, can connect fine, even with DHCP)

Thanks!

---

### Post by Iowan on 2009-06-03
Was the wireless interface configured through Network Manager, or via */etc/network/interfaces*?  (NM usually complains about the latter.)

---

### Post by Ayuthia on 2009-06-03
You might try blacklisting b43 and ssb:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
```
As Iowan was asking, we brought up the wl module manually so that is most likely why NetworkManager is not happy.  You can try blacklisting the b43 and ssb modules as I described above and reboot.  Hopefully NetworkManager will kick in just fine.  I don't use NetworkManager so I am not too sure about how to make that portion work.

---

### Post by cberube on 2009-06-03
I have previously edited the /etc/network/interfaces file but after setting it back to default, Network Manager is still giving problems.

I have had b43 and ssb blacklisted for a while and unfortunately that didn't solve the problem.

While Network Manager would be nice, I'd really just like to get the wireless working.  It is strange that it detects the networks but cannot connect..

The output of dhclient eth1 is as follows ```
Listening on LPF/eth1/00:1a:73:28:7c:6a
Sending on   LPF/eth1/00:1a:73:28:7c:6a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

DHCP or static configuration, nothing works.

---

### Post by Ayuthia on 2009-06-03
You can try killing the NetworkManager processes:
```
ps -ef|grep Network
sudo kill <pid>
```
Replace <pid> with the process id number for the NetworkManager processes.  Then you can try:```
sudo iwconfig eth1 essid "Berube House"
sudo dhclient eth1
```

---

### Post by cberube on 2009-06-03
I changed managed=false in /etc/NetworkManager/nm-system-settings.conf to managed=true and killed the process like you said and now Network Manager works again.


After changing the network settings, I finally got the wireless to work!  I'm not even sure what fixed it but I think it was just a series of bringing the network down and then back up again and re-setting all of the settings in the terminal.  After reboot, it still works.


Thanks for everyone's help!!

---

