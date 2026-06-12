---
title: "Wireless problems in Jaunty"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by opprobrium on 2009-10-05
Hi I'm running a Dell Inspiron 1525, bought with Hardy and subsequently upgraded to Intrepid and now Jaunty. I have had my wireless working. Yesyerday we set up a new network, using the name of the previous one, but with a new password. This was working fine and then stopped last night. (In all likelihood because I did something, but I don't know what.)

I kept being prompted for the keyring. I've managed to turn this off via Applications > Accessories > Passwords and Encryption Keys, but still can't get onto the wireless.

I've tried editing the network connections in the applet, making it available to all users, but to no avail. Not sure if I'm doing something wrong or this is the consequence of something I upgraded...

Output of lspic -v:

```
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1021
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    Memory at fe7ff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

```Iwconfig:

```
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:23:ae:04:f4:55  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe04:f455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25762437 (25.7 MB)  TX bytes:1955506 (1.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10536 (10.5 KB)  TX bytes:10536 (10.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:c9:84:be  
          inet6 addr: fe80::21f:3cff:fec9:84be/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:50616 (50.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-C9-84-BE-34-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by opprobrium on 2009-10-05
Oh, forgot to mention that I keep finding an Auto connection in the edit connection box. This apparently did something 7 months ago (the network applet is so simplified as to be confusing). I've deleted this several times, but it keeps coming back.

---

### Post by Iowan on 2009-10-05
Eth0 is getting IP address. Unless it is configured in */etc/network/interfaces*, that may explain why wireless is not getting address - Network Manager only manages one interface at a time.  Have you had both interfaces active in the past?

---

