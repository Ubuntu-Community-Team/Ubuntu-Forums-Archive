---
title: "Network keeps timing out after a few amount of seconds -_-"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by airplanesimen on 2012-11-20
Hi guys -_-

I have a very irritating problem on my computer. I am connected to an EAP-PEAP Network, using MASCHAPV2, and WPA/WPA2 security.

This network is also using a proxy, and i am able to get online.. But not for a long time.

I am surfing Google, and all other websites, downloading things with apt-get, and each time i use this network, it suddenly "times out". It stays connected, but i am not able to enter any other pages. When i click a link, or tries to enter a web-page, it just loads and loads and loads for generations. Nothing appears, not even an error :/

So, is there any way to fail-check a such irritating thing? I need to "reconnect" to the network to make it work again, and it keeps doing the same over and over againprobook.

I am using a rt2860 driver on my HP ProBook 4330s.

---

### Post by Kirk Schnable on 2012-11-20
I am curious whether when it "times out" you are losing signal strength, AP association, IP address, or what specifically...this may lead us to an answer.

Please post the output of these commands, both when things are **working** and when they're **broken**.

```
sudo ifconfig
```

```
sudo iwconfig
```

Also, just for our reference as to exactly what hardware and driver you're using, please give us:
```
sudo lshw -C network
```

Thanks,
Kirk

---

### Post by airplanesimen on 2012-11-21
Hmm, while i was waiting for a reply, i restarted the computer, and it all looks like working perfectly well now. I'll let you know if it happens again :)

Regards

---

### Post by airplanesimen on 2012-11-28
**_-------> [SIZE="4"]ifconfig[/SIZE]_**

**_When connected, and able to surf online:_**
```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 64:31:50:a1:82:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:176618 (176.6 KB)  TX bytes:176618 (176.6 KB)

ra0       Link encap:Ethernet  HWaddr d0:df:9a:1d:43:16  
          inet addr:10.162.1.152  Bcast:10.162.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:712  Metric:1
          RX packets:6800 errors:7 dropped:2 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8819304 (8.8 MB)  TX bytes:410697 (410.6 KB)
          Interrupt:19 

"

```

**[SIZE="3"]--------->Timed out: [/SIZE]**
```

simen@SIMLA190995:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 64:31:50:a1:82:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:334783 (334.7 KB)  TX bytes:334783 (334.7 KB)

ra0       Link encap:Ethernet  HWaddr d0:df:9a:1d:43:16  
          inet addr:10.162.1.152  Bcast:10.162.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:712  Metric:1
          RX packets:4412 errors:3 dropped:2 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42646110 (42.6 MB)  TX bytes:2159538 (2.1 MB)
          Interrupt:19 
"


```
[SIZE="4"]-------> iwconfig[/SIZE]

**Connected:**

```

simen@SIMLA190995:~$ iwconfig
ra0       Ralink STA  ESSID:"TFK-Elev"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0B:85:84:31:3E   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=78/100  Signal level:-62 dBm  Noise level:-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions

```

**--------> Timed out:**

```

simen@SIMLA190995:~$ iwconfig
ra0       Ralink STA  ESSID:"TFK-Elev"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0B:85:84:3E:4E   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level:-68 dBm  Noise level:-74 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```

**[SIZE="4"]---------> sudo lshw -C network[/SIZE]**

```

simen@SIMLA190995:~$ sudo lshw -C network
[sudo] password for simen: 
  *-network               
       description: Wireless interface
       product: RT3592 Wireless 802.11abgn 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: ra0
       version: 00
       serial: d0:df:9a:1d:43:16
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 ip=10.162.1.152 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:d4700000-d470ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: eth0
       version: 06
       serial: 64:31:50:a1:82:b5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff

```





Same happened again today. Any help ?
-------------------------------------------

---

### Post by airplanesimen on 2012-12-04
Please anyone, ain't there any solution for a such annoying problem?

---

### Post by Kirk Schnable on 2012-12-04
You may find this useful:
[http://askubuntu.com/questions/181943/ubuntu-12-04-problem-with-3592-ralink-wireless-chipset](http://askubuntu.com/questions/181943/ubuntu-12-04-problem-with-3592-ralink-wireless-chipset)

---

