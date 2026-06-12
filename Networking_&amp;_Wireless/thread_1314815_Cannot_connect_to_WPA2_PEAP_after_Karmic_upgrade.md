---
title: "Cannot connect to WPA2 PEAP after Karmic upgrade"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by WindPower on 2009-11-04
Hi, I recently upgraded to Kubuntu 9.10 64-bit and everything works so far except the wireless connectivity. My WEP network at home works, but my university network uses WPA2 with PEAP. While it took me a few days to figure out how to connect while using Jaunty, I did end up connecting successfully to the network (I had to select each SSL cert manually until I found the right one, /etc/ssl/certs/Thawte_Premium_Server_CA.pem... Why can Windows and OS X auto-select the certificate but Ubuntu can't?), but now I cannot connect at all using the same settings as before (Same SSL cert, same username/password, etc.), but not the same network manager since it was rewritten in Kubuntu 9.10. So I thought I'd downgrade knetworkmanager to get the old version back, and I did so by adding the official Jaunty packages in /etc/apt/sources.list, then installed knetworkmanager, but while it does let me set up new connections preferences, it only stores these connection preferences but never uses them (ie, it never touches the network interface). Running it as root didn't help.
So I thought I would downgrade the backend too, so I installed the old 0.7 network-manager package and tried using it from knetworkmanager, but that didn't work either.
So I removed the Jaunty packages source, reupgraded everything back to the Karmic version, and now I'm back to square one: WEP network works, WPA doesn't. Then I tried installing wicd, but it couldn't connect to my home wireless (WEP) network at all (dhclient times out), but I didn't try it on the WPA network yet. It's weird because I can connect to my home network just fine from the command line (ifconfig eth2 down, iwconfig eth2 essid myneworkname, iwconfig eth2 channel 11, iwconfig eth2 key mywepkey, ifconfig eth2 up, dhclient eth2).

I'm running Kubuntu 9.10 64-bit on a MacBook Pro 5,3 with the restricted Broadcom STA drivers enabled. What should I do?

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:26:b0:df:82:16
          inet6 addr: fe80::226:b0ff:fedf:8216/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7329261 (7.3 MB)  TX bytes:742956 (742.9 KB)
          Interrupt:28 Base address:0x6000

eth2      Link encap:Ethernet  HWaddr 00:26:bb:08:85:f2
          inet addr:192.168.0.121  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:bbff:fe08:85f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:338629 errors:1 dropped:0 overruns:0 frame:44856
          TX packets:286534 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:105654337 (105.6 MB)  TX bytes:30399785 (30.3 MB)
          Interrupt:22

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:601560 (601.5 KB)  TX bytes:601560 (601.5 KB)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:"<My home network's ESSID>"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:E9:7B:2F:BA
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-51 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:352  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:1   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```

lspci | grep network
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
```

Is there anything I can do? :( Otherwise I'll have to downgrade to Jaunty to get my network connection back. Unless there is a way to downgrade only the networking components? That would be cool.

---

### Post by WindPower on 2009-11-04
I added the Wicd PPA (deb [http://apt.wicd.net](http://apt.wicd.net) karmic extras) and now wicd is working with my home wireless connection. Will try to connect to the WPA network tomorrow with Wicd and report back :o

---

### Post by WindPower on 2009-11-05
Wicd works! :D
However, I have noticed that Wicd only works the first time it connects to a wireless network after booting. If I disconnect and reconnect, I get the same message as before (Unable to get IP address) until I reboot. So I can't move out of the wireless range and back in without rebooting, which isn't really practical but I can live with it. The same thing happens at home, but that's not really an issue.

---

### Post by degtukas on 2009-11-09
The same here, PEAP does not work. TTLS works fine though.

---

