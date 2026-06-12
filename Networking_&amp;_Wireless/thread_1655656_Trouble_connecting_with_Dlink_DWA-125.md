---
title: "Trouble connecting with Dlink DWA-125"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by JamesBahn on 2010-12-29
I need some help getting my Dlink DWA-125 USB wifi adapter working.

I am a complete noob to Ubuntu so please bear with me.

I plugged in the adapter and it connects to my network just fine.  However, in Firefox, no pages will load as it does not see a connection.

Any help is greatly appreciated.

Cheers - Brian

---

### Post by PatchesTheCaveman on 2010-12-29
Hi JamesBahn!  I'm sorry you're having trouble accessing the Internet wirelessly.

I need to gather some information to try and figure out what the hangup is.  First, go to Applications > Accessories > Terminal in your top panel.  Then type the following in the black box that pops up and press Enter:
```
ifconfig -a
```

A bunch of information about your network setup will appear.  Copy and paste that into a reply to this thread.  Then type this into the terminal window and press Enter again:
```
sudo iwconfig
```
After you hit Enter, Ubuntu will ask for your password.  Type it in, press Enter, and a bunch of information about your wireless configuration will appear.  Copy and paste that into that reply too and send it off.

That will help us figure out what exactly is going on.  Thank you!

---

### Post by JamesBahn on 2010-12-30
Thank you very much for taking the time to help:

Here is my output:

 **[FONT=&quot]brian@Brian-ubuntu:~$ ifconfig -a[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]eth0      Link encap:Ethernet  HWaddr 00:18:8b:1e:3c:ac  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Interrupt:16 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]lo        Link encap:Local Loopback  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          inet6 addr: ::1/128 Scope:Host[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:56 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:0 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:4128 (4.1 KB)  TX bytes:4128 (4.1 KB)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]wlan0     Link encap:Ethernet  HWaddr 00:26:5a:7f:83:2a  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]brian@Brian-ubuntu:~$ sudo iwconfig[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot][sudo] password for brian: [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]lo        no wireless extensions.[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]eth0      no wireless extensions.[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]wlan0     IEEE 802.11bgn  ESSID:off/any  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Mode:Managed  Access Point: Not-Associated   Tx-Power=8 dBm   [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Encryption key:off[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Power Management:on[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]vboxnet0  no wireless extensions.[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]brian@Brian-ubuntu:~$ [/FONT]**

---

### Post by PatchesTheCaveman on 2010-12-30
According to that you are not connected to a wireless network at all.  Click on the wireless icon and make sure you are connected to the network.  Once you do, run those commands again and paste them here.

Also, run this command:
```
lspci -v
```
and copy and paste it here so we can see if there are any known problems with your particular hardware setup.

---

### Post by JamesBahn on 2010-12-30
Sorry about that.  Here is the output after being connected.  

 **[FONT=&quot]brian@Brian-ubuntu:~$ ifconfig -a[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]eth0      Link encap:Ethernet  HWaddr 00:18:8b:1e:3c:ac  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Interrupt:16 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]lo        Link encap:Local Loopback  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          inet6 addr: ::1/128 Scope:Host[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:800 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:800 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:0 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:60544 (60.5 KB)  TX bytes:60544 (60.5 KB)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]wlan0     Link encap:Ethernet  HWaddr 00:26:5a:7f:83:2a  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          inet6 addr: fe80::226:5aff:fe7f:832a/64 Scope:Link[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:4263 (4.2 KB)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]brian@Brian-ubuntu:~$ sudo iwconfig[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot][sudo] password for brian: [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]lo        no wireless extensions.[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]eth0      no wireless extensions.[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]vboxnet0  no wireless extensions.[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]wlan0     IEEE 802.11bgn  ESSID:"The Wireless"  [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 7E:14:1D:65:ED:8F   [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Tx-Power=10 dBm   [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Encryption key:F70B-BC76-7DE7-0425-9D6F-EB97-A94E-3A85-CD8A-EB9B-87B7-7324-CD8A-EB9B-87B7-7324[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          Power Management:on[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]          [/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]brian@Brian-ubuntu:~$ lspci -v[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]00:00.0 Host bridge: Intel Corporation 5000X Chipset Memory Controller Hub (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 2 (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=01, subordinate=05, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O behind bridge: 0000d000-0000dfff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dfc00000-dfefffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=06, subordinate=06, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dfb00000-dfbfffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:04.0 PCI bridge: Intel Corporation 5000X Chipset PCI Express x16 Port 4-7 (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=07, subordinate=0a, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: daf00000-dfafffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:05.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dae00000-daefffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:06.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 6 (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dad00000-dadfffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:07.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dac00000-dacfffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: i5000_edac[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: i7300_idle, i5000_edac, i5k_amb[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: i7300_idle, i5000_edac, i5k_amb[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: i7300_idle, i5000_edac, i5k_amb[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Intel Corporation Device 8086[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: fast devsel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0, IRQ 16[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dfffc000 (64-bit, non-prefetchable) [size=16K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: HDA Intel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: snd-hda-intel[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dab00000-dabfffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0, IRQ 21[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at ff80 [size=32][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: uhci_hcd[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0, IRQ 22[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at ff60 [size=32][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: uhci_hcd[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0, IRQ 18[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at ff40 [size=32][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: uhci_hcd[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0, IRQ 23[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at ff20 [size=32][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: uhci_hcd[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09) (prog-if 20)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0, IRQ 21[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at ff980800 (32-bit, non-prefetchable) [size=1K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: ehci_hcd[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9) (prog-if 01)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=00, secondary=0f, subordinate=0f, sec-latency=32[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: daa00000-daafffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: iTCO_wdt, intel-rng[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09) (prog-if 8a [Master SecP PriP])[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 0, IRQ 16[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at 01f0 [size=8][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at 03f4 [size=1][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at 0170 [size=8][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at 0374 [size=1][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at ffa0 [size=16][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: ata_piix[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1f.2 IDE interface: Intel Corporation 631xESB/632xESB/3100 Chipset SATA IDE Controller (rev 09) (prog-if 8f [Master SecP SecO PriP PriO])[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at fe00 [size=8][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at fe10 [size=4][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at fe20 [size=8][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at fe30 [size=4][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at fec0 [size=16][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at ff970000 (32-bit, non-prefetchable) [size=1K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: ata_piix[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: medium devsel, IRQ 5[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at ece0 [size=32][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: i2c-i801[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]01:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=01, secondary=02, subordinate=04, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]01:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=01, secondary=05, subordinate=05, sec-latency=64[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O behind bridge: 0000d000-0000dfff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dfc00000-dfdfffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]02:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=02, secondary=03, subordinate=03, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]02:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=02, secondary=04, subordinate=04, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: pcieport[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]05:0b.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068 PCI-X Fusion-MPT SAS (rev 01)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 1f08[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, 66MHz, medium devsel, latency 72, IRQ 24[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                I/O ports at dc00 [disabled] [size=256][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dfcec000 (64-bit, non-prefetchable) [size=16K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Expansion ROM at dfd00000 [disabled] [size=1M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: mptsas[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: mptsas[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]07:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dfafc000 (32-bit, non-prefetchable) [size=16K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=07, secondary=08, subordinate=0a, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: daf00000-df9fffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]08:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=08, secondary=09, subordinate=09, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: dd000000-df9fffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]08:01.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Bus: primary=08, secondary=0a, subordinate=0a, sec-latency=0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory behind bridge: daf00000-dcffffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: shpchp[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]09:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: nVidia Corporation Device 0334[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0, IRQ 16[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dd000000 (32-bit, non-prefetchable) [size=16M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at b0000000 (64-bit, prefetchable) [size=256M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at de000000 (64-bit, non-prefetchable) [size=16M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                [virtual] Expansion ROM at df900000 [disabled] [size=128K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: nvidia[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: nvidia-173, nvidiafb, nouveau[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]0a:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: nVidia Corporation Device 0334[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0, IRQ 17[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at db000000 (32-bit, non-prefetchable) [disabled] [size=16M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dc000000 (64-bit, non-prefetchable) [disabled] [size=16M][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                [virtual] Expansion ROM at daf00000 [disabled] [size=128K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: nvidia[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: nvidia-173, nvidiafb, nouveau[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]0e:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, fast devsel, latency 0, IRQ 57[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at dabf0000 (64-bit, non-prefetchable) [size=64K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Expansion ROM at <ignored> [disabled][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: tg3[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: tg3[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]0f:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Subsystem: Dell Device 01c0[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Flags: bus master, medium devsel, latency 64, IRQ 18[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at daafb800 (32-bit, non-prefetchable) [size=2K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Memory at daafc000 (32-bit, non-prefetchable) [size=16K][/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Capabilities: <access denied>[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel driver in use: ohci1394[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot]                Kernel modules: firewire-ohci, ohci1394[/FONT]**
  **[FONT=&quot][/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot] [/FONT]**
  **[FONT=&quot]brian@Brian-ubuntu:~$ [/FONT]**
  **[FONT=&quot][/FONT]**

---

### Post by PatchesTheCaveman on 2010-12-30
All that looks good.  Go back to the terminal and run:
```
ping 8.8.8.8
```
Let that run for about 15 seconds, then press CTRL+C.

At the bottom, it will say something like:
```
4 packets transmitted, 0 received, 100% packet loss, time 3024ms
```

If you're packet loss is 100% like that, post back and let me know.  If it's anything else, try this too:
```
ping google.com
```
Let than run for about 15 seconds too and then hit CTRL+C again and let me know what both packet losses were.

---

### Post by bkratz on 2010-12-30
Well actually it says he/she is in Ad-hoc mode


wlan0 IEEE 802.11bgn ESSID:"The Wireless" 

Mode:[COLOR="Red"]Ad-Hoc[/COLOR] Frequency:2.412 GHz Cell: 7E:14:1D:65:ED:8F 

i think I would try

sudo iwconfig wlan0 mode Managed

and see if that helps

---

### Post by JamesBahn on 2010-12-30
I tried setting mode to "Managed" and received this error:

Error for wireless request "Set Mode" (8B06)  :
      SET failed on device wlan0 ; Device or resource busy.


When I run the ping commands I get this error:

connect: Network is unreachable.


At the top, I do have the connection bars showing an active connection, however.

Thanks again for the assistance.  it is Greatly! appreciated.

---

### Post by PatchesTheCaveman on 2010-12-30
Do you connect to the Internet through a wireless router?  Or is it a direct connection to another laptop or a desktop with a wireless card?

---

### Post by JamesBahn on 2010-12-30
I connect through a wireless router.

---

### Post by PatchesTheCaveman on 2010-12-30
That's what I figured.  Click on the wireless icon and disconnect from your wireless network for now.  Right click on your wireless icon, and click *Edit Connections...*.  Switch to the *Wireless* tab.  Click on the wireless connection you are using and hit *Edit*.  Look for the drop-down box labeled *Mode*.  Does it say *Infrastructure* or *Ad-hoc*?  

If it says *Ad-hoc*, change it to *Infrastructure*.  Connect back to the wireless. 

If it says *Infrastructure* already, click *Cancel*.  Delete your connection.  Click *Close*.  Click back on the wireless icon again and click on the name of your network again.  Re-enter your WEP or WPA key if necessary.

After all that, retry ```
ping google.com
```
Remember to press CTRL+C after about 15 seconds.

---

### Post by JamesBahn on 2010-12-30
After changing it to Infastructure, the card no longer recognized the Wireless network.  When I manually connect through "Connect to hidden Wireless Network" I just get a perpetual "ball and orbit" symbol in the taskbar without ever making a connection.

---

