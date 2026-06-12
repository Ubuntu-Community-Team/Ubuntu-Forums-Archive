---
title: "Sitecom wireless card not working"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by Hythebob on 2010-04-06
I should have included some more info on my last post. 
When the laptop boots I get a very brief message to say "wireless network available, click on icon". But it disappears in a second.
I'm not clear whether my WL-140 card is in device wlan0 or wmaster0.
Here's what lshw -C network says...
*-network
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:0c:f6:14:a4:35
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=p54pci latency=64 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:20000000-20001fff

And iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Livebox-FFC0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      Link encap:Ethernet  HWaddr 00:00:39:54:09:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x6f80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:14:a4:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-F6-14-A4-35-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Any suggestions please?

---

### Post by chili555 on 2010-04-07
wmaster0 is a dummy for-internal-use-only interface that the system uses. You may safely ignore it.

Your settings look solid to me. If you click the Network Manager icon at the top right, do you see your network? Can you click it and connect? For security reasons, Ubuntu will not automatically connect to any old rogue, virus laden, identity stealing access point. You must command it to connect to your known, trusted network. You can, of course, the ask it to connect to your known, trusted network automatically on boot. Please see attached.

In my example, I want to connect to GBR1, so I click it and I am prompted for my WPA2 password and, if the password is correct, I connect.

---

### Post by gcmelzi on 2010-10-22
This looks very similar to the problem I have: my card was working on 9.10 until I decided to upgrade to 10.04, but upgrade showed up 2 main problems: grub -> grub2 and Wireless Card not working, so I decided to make a fresh install with 10.10 (fortunately I've /home on sdb1). 
Initially Wireless Card didn't show up at all even with 10.10: looking into DMESG output I found out a module was missing:
```
 (31.354152] p54pci 0000:01:0a.0: Cannot find firmware (isl3886pci)
```
I found this link [http://wireless.kernel.org/en/users/Drivers/p54](http://wireless.kernel.org/en/users/Drivers/p54) and tried almost all of the suggested drivers, even those not suggested for my kernel version, loading them into the /lib/firmare folder as isl3886pci and modprobing the p54pci module.
This worked, as WLAN0 came up, but I never got connected to any network. 
Through Network Manager I can see SSIDs and configure the card, but it never starts any session. See below output from ifcong and iwconfig (it has assigned IP, but it doesn't work even if I specify DHCP):
```
wlan0     Link encap:Ethernet  HWaddr 00:60:b3:08:0e:03  
          indirizzo inet:192.168.1.98  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::260:b3ff:fe08:e03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:18759 (18.7 KB)

wlan0     IEEE 802.11bg  ESSID:"SalamediVarzi"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:64:17:17:BB   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
You see: RX packets:0
Desperate, I removed Network Manager and installed WICD: same exactly result!
I suspected a card fault, but in 15 mins I was able to get it working with Puppy, downloading and mastering time included. 

Below details for the card: pretty much the same as the one in first post: 
```
01:0a.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
	Subsystem: Z-Com, Inc. XG-900 and clones Wireless Adapter
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e1800000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: p54pci
	Kernel modules: p54pci, prism54

```  
I've no other idea and I'm really considering moving back to 9.10
Is there anything else I can check, please? 
Thanks a lot.

---

### Post by gcmelzi on 2010-10-22
moving on a new Thread.

---

