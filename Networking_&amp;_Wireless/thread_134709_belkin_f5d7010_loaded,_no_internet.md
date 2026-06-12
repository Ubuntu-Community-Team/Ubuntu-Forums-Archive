---
title: "belkin f5d7010 loaded, no internet"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by elp on 2006-02-22
1-laptop compaq presario R3220US
2- i can use braodcom wireless that comes with laptop in linux.
3- belkin f5d7010 v-3001 with rt2500
4- wireless loaded from the box
5- power light is on, signal is blinking
6- sbc-yahoo-dsl (2wire.com) with dns 192.168.1.254, wepkey 8300103966
7- no internet connection

elp7@ubuntu:~$ sudo lspci -v
Password:
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5833 (rev 02)
        Subsystem: ATI Technologies Inc: Unknown device 1234
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d2000000 (32-bit, prefetchable) [size=32M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [a0] AGP version 3.0

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc: Unknown device 434c
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]

0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc: Unknown device 434c
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]

0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: 66MHz, medium devsel
        I/O ports at 8040 [size=16]
        Memory at 28000000 (32-bit, non-prefetchable) [size=1K]

0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349 (prog-if 8a [Master SecP PriP])
        Subsystem: ATI Technologies Inc: Unknown device 4349
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8060 [size=16]

0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
        Subsystem: ATI Technologies Inc: Unknown device 434c
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=69
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 5
        Memory at d0003000 (32-bit, non-prefetchable) [size=256]

0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 5
        Memory at d0003400 (32-bit, non-prefetchable) [size=256]

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5835 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 16
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 12f4
        Flags: bus master, fast devsel, latency 64, IRQ 5
        Memory at d0200000 (32-bit, non-prefetchable) [size=8K]

0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, medium devsel, latency 128, IRQ 19
        I/O ports at a000 [size=256]
        Memory at d0204000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at 28001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 28400000-287ff000 (prefetchable)
        Memory window 1: 28800000-28bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 28002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 28c00000-28fff000 (prefetchable)
        Memory window 1: 29000000-293ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:02:07.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation USB
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:02:07.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation USB
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at d0203000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
        Subsystem: NEC Corporation USB 2.0
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at d0204400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

0000:03:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
        Subsystem: Belkin: Unknown device 701a
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at 28800000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

elp7@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elp7@ubuntu:~$ sudo iwlist ra0 scan
ra0       No scan results
elp7@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"2WIRE966"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:95:41:43:9A
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:8300-1039-66   Security mode:open
          Link Quality=73/100  Signal level=-36 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elp7@ubuntu:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:14:95:41:43:9A
                    Mode:Managed
                    ESSID:"2WIRE966"
                    Encryption key:on
                    Channel:6
                    Quality:74/100  Signal level:-102 dBm  Noise level:-193 dBm

elp7@ubuntu:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
elp7@ubuntu:~$

please help me solve this.

---

### Post by bscbrit on 2006-02-22
Do you mean just internet, or is there no network connection?  Can you ping the gateway? Are there other machines on the network?

---

### Post by elp on 2006-02-22
thanks for quick reply
I am new to linux.
there is only my laptop and a 2wire router
elp7@ubuntu:~$ ping -c 4 192.168.1.254
connect: Network is unreachable
elp7@ubuntu:~$ ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.038 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.027/0.035/0.039/0.004 ms
elp7@ubuntu:~$ ping -c 4 192.168.1.254
connect: Network is unreachable
elp7@ubuntu:~$ ping -c 4 192.168.1.68
connect: Network is unreachable
elp7@ubuntu:~$

---

### Post by bscbrit on 2006-02-22
The easiest way to set up networks is to start simple and, once you have a working network, start to add the additional features. But as you already have WEP working we might as well leave it there for the time being.

I can understand why you were pinging 192.168.1.254, but what is on 192.168.1.68?

You are using dhcp, about which I know relatively little, so I will have to consult my books and Google for some answers. What range of addresses is it set to issue?  I'm not sure that pinging 127.0.0.1 really proves anything useful in this instance.

I notice that your routing is set up for eth0, but the wireless card is named as ra0 - that will need changing I think.  Can you see the card when you open System -> Administration -> Networking?  If so, you can set your gateway there and make sure that the appropriate NIC is selected as your default.

---

### Post by elp on 2006-02-22
I downed all thru. automatix and according to somewhere in unbuntu.org this card with rt2500 should work. without any prb.

elp7@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface ra0 inet dhcp
wireless-essid 2WIRE966
wireless-key 8300103966




iface eth0 inet dhcp



auto ra0

auto eth0
elp7@ubuntu:~$

---

### Post by bscbrit on 2006-02-22
I'm not saying that it won't work - but it is not yet configured.  Are you only using the wireless network?  If you are, you can remove all configuration from the wired NIC (eth0).  For example, your interfaces file should look like this initially:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map ra0  ### NOTE CHANGE HERE

# The primary network interface
iface ra0 inet dhcp
wireless-essid 2WIRE966
wireless-key 8300103966

auto ra0 ### NOTE CHANGE HERE

### NOTE ALL REFERENCES TO ETH0 REMOVED

---

### Post by bscbrit on 2006-02-22
Sorry, forgot to ask:

Did you try to see your card via System -> Administration -> Networking?  If yes, what did you see?

You are correct is saying that this 'should' work without any problems, but sometimes things just need a little help :-D

---

### Post by elp on 2006-02-22
Yes ra0 is configured and it shows in system, admin, network as active.

somehow I am not able to send you attachments.

---

### Post by bscbrit on 2006-02-22
OK, please re-run 'iwlist ra0 scan' and post the results.  It is probably easiest simply to cut and paste the results. A linux trick you might not be aware of.  Highlight the text you want to copy, say the results of the command above.  Move to where you want to copy it to, for example your next response in this thread, and simply press the middle mouse button.  Done!

When you go to Sys - Admin - Networking, is ra0 selected as the default gateway in the lower half of the dialogue?

---

### Post by elp on 2006-02-22
elp7@ubuntu:~$ sudo iwlist ra0 scan
Password:
ra0       Scan completed :
          Cell 01 - Address: 00:14:95:41:43:9A
                    Mode:Managed
                    ESSID:"2WIRE966"
                    Encryption key:on
                    Channel:6
                    Quality:76/100  Signal level:-102 dBm  Noise level:-192 dBm

---

### Post by bscbrit on 2006-02-22
We know the card is recognised by the computer because you can scan with it and detect your network. If you cannot ping your router then the card cannot get an IP address or gateway address because it is not establishing a link with your Access Point.

Just try to ping your router once more.

Still no luck?  No, in that case we will try a manual configuration to move on with. Modify your interfaces file as shown below.

> 
iface ra0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid 2WIRE966
wireless-channel 6
wireless-mode managed
wireless-ap 00:14:95:41:43:9A
wireless-key1 8300103966
wireless-defaultkey 1
wireless-keymode open

auto ra0


Restart your network (sudo /etc/init.d/networking restart) and try to ping your gateway again.  If you can, then off you go. If you can't, try to ping 192.168.1.1 just to check that your card is reachable - (but we know it is because you can scan with it).

---

### Post by bscbrit on 2006-02-22
I'm off to bed - but I'll be back here tomorrow! Good Luck :D

---

### Post by elp on 2006-02-22
1- could not ping router
2- copied and pasted to /etc/network/interfaces
elp7@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
##iface ra0 inet dhcp
##wireless-essid 2WIRE966
##wireless-key 8300103966




iface eth0 inet dhcp

iface ra0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid 2WIRE966
wireless-channel 6
wireless-mode managed
wireless-ap 00:14:95:41:43:9A
wireless-key1 8300103966
wireless-defaultkey 1
wireless-keymode open
wireless-key 8300103966

auto ra0




auto eth0
restarted the network but to no avail.

elp7@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]

I could not access any web-sites thru. the browser.

elp7@ubuntu:~$ ping -c 4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


elp7@ubuntu:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.057 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.038 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.039 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.036 ms
 good night see you in the morning as I need help.

---

### Post by bscbrit on 2006-02-23
There are 2 lines that I thought you removed from your interfaces file a few posts back:

> 
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map ra0 ### NOTE CHANGE HERE

# The primary network interface
iface ra0 inet dhcp
wireless-essid 2WIRE966
wireless-key 8300103966

auto ra0 ### NOTE CHANGE HERE

### NOTE ALL REFERENCES TO ETH0 REMOVED



map eth0  -> should read -> map ra0

The following line should NOT be in your interfaces file:

iface eth0 inet dhcp

If, after making your changes and restarting the network, you cannot ping your router, switch off all encryption from both the router and the wireless NIC.

---

### Post by bscbrit on 2006-02-23
As you were unable to get this wireless NIC working under MEPIS in January, ([http://www.mepis.org/node/8859](http://www.mepis.org/node/8859)) and now the same problem under Ubuntu, are you sure that it is fully up to spec?  Did you buy it from new?  Do you have a dual boot machine, and does it work under windows?

---

### Post by elp on 2006-02-23
1-I corrected the /etc/nework/interfaces but still no internet connection
2- I posted in mepis for a different card
3-I am not using this card in windows(dual with ubuntu)

elp7@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        ##map eth0
        map ra0
# The primary network interface
##iface ra0 inet dhcp
##wireless-essid 2WIRE966
##wireless-key 8300103966




##iface eth0 inet dhcp

iface ra0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid 2WIRE966
wireless-channel 6
wireless-mode managed
wireless-ap 00:14:95:41:43:9A
wireless-key1 8300103966
wireless-defaultkey 1
wireless-keymode open
wireless-key 8300103966








auto ra0

---

### Post by bscbrit on 2006-02-24
And have you tried switching off the encryption like I suggested a few posts back?  I'm rapidly running out of ideas....

---

### Post by Fitzcarraldo on 2006-10-17
elp,

If you are still trying to get the Belkin F5D7010 PCMCIA card working with ubuntu, perhaps the procedure on the following page might help:

[http://www.ubuntuforums.org/showthread.php?p=1626986](http://www.ubuntuforums.org/showthread.php?p=1626986)

Good luck!

---

### Post by TrueJk7 on 2006-10-23
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Check out this link too! It's been the best on getting this working. Had same problem and found the resolution here.

---

