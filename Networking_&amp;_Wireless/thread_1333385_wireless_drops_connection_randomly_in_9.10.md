---
title: "wireless drops connection randomly in 9.10"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by mecheng on 2009-11-21
My laptop h zt3380us worked great in 9.04. After the upgrade to 9.10 my touchpad didn't work (fixed now) and my wireless connection is randomly disconnecting and reconnecting. I use WPA and haven't touched the router yet. 

Here is my log during a outage:

```
Nov 21 07:56:43 mecheng dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov 21 07:56:43 mecheng dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 21 07:56:43 mecheng dhclient: All rights reserved.
Nov 21 07:56:43 mecheng dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 21 07:56:43 mecheng dhclient: 
Nov 21 07:56:43 mecheng NetworkManager: <info>  dhclient started with pid 8773
Nov 21 07:56:43 mecheng NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 21 07:56:43 mecheng NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Nov 21 07:56:43 mecheng NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Nov 21 07:56:43 mecheng NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Nov 21 07:56:43 mecheng NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 21 07:56:43 mecheng dhclient: Listening on LPF/eth1/00:0e:35:0b:80:5f
Nov 21 07:56:43 mecheng dhclient: Sending on   LPF/eth1/00:0e:35:0b:80:5f
Nov 21 07:56:43 mecheng dhclient: Sending on   Socket/fallback
Nov 21 07:56:45 mecheng dhclient: DHCPREQUEST of 192.168.0.103 on eth1 to 255.255.255.255 port 67
Nov 21 07:56:48 mecheng dhclient: DHCPREQUEST of 192.168.0.103 on eth1 to 255.255.255.255 port 67
Nov 21 07:56:48 mecheng dhclient: DHCPACK of 192.168.0.103 from 192.168.0.1
Nov 21 07:56:48 mecheng NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Nov 21 07:56:48 mecheng NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 21 07:56:48 mecheng NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Nov 21 07:56:48 mecheng NetworkManager: <info>    address 192.168.0.103
Nov 21 07:56:48 mecheng NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov 21 07:56:48 mecheng NetworkManager: <info>    gateway 192.168.0.1
Nov 21 07:56:48 mecheng NetworkManager: <info>    nameserver '68.87.76.182'
Nov 21 07:56:48 mecheng NetworkManager: <info>    nameserver '68.87.78.134'
Nov 21 07:56:48 mecheng NetworkManager: nm_ip4_config_add_nameserver: assertion `nameserver > 0' failed
Nov 21 07:56:48 mecheng NetworkManager: <info>    nameserver '0.0.0.0'
Nov 21 07:56:48 mecheng NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 21 07:56:48 mecheng NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 21 07:56:48 mecheng NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Nov 21 07:56:48 mecheng avahi-daemon[772]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.103.
Nov 21 07:56:48 mecheng avahi-daemon[772]: New relevant interface eth1.IPv4 for mDNS.
Nov 21 07:56:48 mecheng avahi-daemon[772]: Registering new address record for 192.168.0.103 on eth1.IPv4.
Nov 21 07:56:48 mecheng wpa_supplicant[790]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:56:48 mecheng wpa_supplicant[1129]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:56:48 mecheng dhclient: bound to 192.168.0.103 -- renewal in 242660 seconds.
Nov 21 07:56:49 mecheng NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Nov 21 07:56:49 mecheng NetworkManager: <info>  Policy set 'Auto 143_6020FL' (eth1) as default for routing and DNS.
Nov 21 07:56:49 mecheng NetworkManager: <info>  Activation (eth1) successful, device activated.
Nov 21 07:56:49 mecheng NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Nov 21 07:56:50 mecheng ntpdate[8824]: adjust time server 91.189.94.4 offset -0.001337 sec
Nov 21 07:56:53 mecheng wpa_supplicant[790]: Authentication with 00:21:29:ef:a3:af timed out.
Nov 21 07:56:53 mecheng wpa_supplicant[790]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 07:56:53 mecheng wpa_supplicant[1129]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 07:56:53 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
Nov 21 07:56:54 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 21 07:56:54 mecheng wpa_supplicant[1129]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:56:54 mecheng wpa_supplicant[1129]: Trying to associate with 00:21:29:ef:a3:af (SSID='143_6020FL' freq=2437 MHz)
Nov 21 07:56:54 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 21 07:56:54 mecheng wpa_supplicant[1129]: Association request to the driver failed
Nov 21 07:56:54 mecheng wpa_supplicant[790]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:56:54 mecheng wpa_supplicant[790]: Trying to associate with 00:21:29:ef:a3:af (SSID='143_6020FL' freq=2437 MHz)
Nov 21 07:56:54 mecheng wpa_supplicant[790]: Association request to the driver failed
Nov 21 07:56:54 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Nov 21 07:56:54 mecheng wpa_supplicant[790]: Associated with 00:21:29:ef:a3:af
Nov 21 07:56:54 mecheng wpa_supplicant[1129]: Associated with 00:21:29:ef:a3:af
Nov 21 07:56:55 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Nov 21 07:56:55 mecheng wpa_supplicant[790]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
Nov 21 07:56:55 mecheng wpa_supplicant[790]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Nov 21 07:56:55 mecheng wpa_supplicant[1129]: WPA: Key negotiation completed with 00:21:29:ef:a3:af [PTK=CCMP GTK=CCMP]
Nov 21 07:56:55 mecheng wpa_supplicant[1129]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:ef:a3:af completed (reauth) [id=2 id_str=]
Nov 21 07:56:55 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Nov 21 07:56:55 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Nov 21 07:57:05 mecheng wpa_supplicant[790]: Authentication with 00:21:29:ef:a3:af timed out.
Nov 21 07:57:05 mecheng wpa_supplicant[790]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: Trying to associate with 00:21:29:ef:a3:af (SSID='143_6020FL' freq=2437 MHz)
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: Association request to the driver failed
Nov 21 07:57:05 mecheng wpa_supplicant[790]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:05 mecheng wpa_supplicant[790]: Trying to associate with 00:21:29:ef:a3:af (SSID='143_6020FL' freq=2437 MHz)
Nov 21 07:57:05 mecheng wpa_supplicant[790]: Association request to the driver failed
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Nov 21 07:57:05 mecheng wpa_supplicant[790]: Associated with 00:21:29:ef:a3:af
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: Associated with 00:21:29:ef:a3:af
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Nov 21 07:57:05 mecheng wpa_supplicant[790]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
Nov 21 07:57:05 mecheng wpa_supplicant[790]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: WPA: Key negotiation completed with 00:21:29:ef:a3:af [PTK=CCMP GTK=CCMP]
Nov 21 07:57:05 mecheng wpa_supplicant[1129]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:ef:a3:af completed (reauth) [id=2 id_str=]
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Nov 21 07:57:05 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Nov 21 07:57:07 mecheng wpa_supplicant[790]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:07 mecheng wpa_supplicant[1129]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:15 mecheng wpa_supplicant[790]: Authentication with 00:21:29:ef:a3:af timed out.
Nov 21 07:57:15 mecheng wpa_supplicant[790]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 07:57:15 mecheng wpa_supplicant[1129]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 21 07:57:15 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
Nov 21 07:57:16 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 21 07:57:16 mecheng wpa_supplicant[1129]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:16 mecheng wpa_supplicant[1129]: Trying to associate with 00:21:29:ef:a3:af (SSID='143_6020FL' freq=2437 MHz)
Nov 21 07:57:16 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 21 07:57:16 mecheng wpa_supplicant[1129]: Association request to the driver failed
Nov 21 07:57:16 mecheng wpa_supplicant[790]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:16 mecheng wpa_supplicant[790]: Trying to associate with 00:21:29:ef:a3:af (SSID='143_6020FL' freq=2437 MHz)
Nov 21 07:57:16 mecheng wpa_supplicant[790]: Association request to the driver failed
Nov 21 07:57:16 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Nov 21 07:57:16 mecheng wpa_supplicant[790]: Associated with 00:21:29:ef:a3:af
Nov 21 07:57:16 mecheng wpa_supplicant[1129]: Associated with 00:21:29:ef:a3:af
Nov 21 07:57:16 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Nov 21 07:57:16 mecheng wpa_supplicant[790]: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
Nov 21 07:57:16 mecheng wpa_supplicant[790]: WPA: Could not verify EAPOL-Key MIC - dropping packet
Nov 21 07:57:16 mecheng wpa_supplicant[1129]: WPA: Key negotiation completed with 00:21:29:ef:a3:af [PTK=CCMP GTK=CCMP]
Nov 21 07:57:16 mecheng wpa_supplicant[1129]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:ef:a3:af completed (reauth) [id=2 id_str=]
Nov 21 07:57:16 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Nov 21 07:57:16 mecheng NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Nov 21 07:57:21 mecheng wpa_supplicant[790]: CTRL-EVENT-SCAN-RESULTS 
Nov 21 07:57:21 mecheng wpa_supplicant[1129]: CTRL-EVENT-SCAN-RESULTS 

```

---

### Post by N00bDud3 on 2009-11-21
I have been having a similar problem. I have 9.10 on an Acer Aspire 3680 and the wireless connection randomly goes out, then connects two seconds later. If it helps, I am using a Linksys WRT54G router (HW rev. 6.0) How do you get a log file of the connection?

---

### Post by N00bDud3 on 2009-11-21
I just noticed something else. It may just be conflicting shortcut keys, but whenever I adjust my brightness the connection will drop. I can't seem to figure out why the shortcut keys would be conflicting though. What could it be?
EDIT: I didn't see the edit button or I would have placed this on my previous post.

---

### Post by mecheng on 2009-11-21
You can look in the folder /ver/log/ but I got mine from the System->Administration->Log Viewer

I have heard this may be driver related if it is a broadcom??

How do I get the driver specs from the CL again?

---

### Post by N00bDud3 on 2009-11-21
I'm not sure how to view drivers, try *lspci* or *sudo lshw*. They might have useful info. Whenever I adjust my brightness settings, this pops up in the logfiles
[B]NetworkManager: <info>  Wireless now disabled by radio killswitch
[/B]I think that the hotkeys may have been mixed up. How can I change the radio killswitch hotkey?

---

### Post by mecheng on 2009-11-21
here is the device info:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Compaq Computer Corporation Device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 4000 [size=256]
        I/O ports at 4880 [size=64]
        Memory at a0200000 (32-bit, non-prefetchable) [size=512]
        Memory at a0300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
```

and lshw:

```
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:0b:80:5f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.0.103 latency=128 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
                resources: irq:5 memory:90000000-90000fff

```

---

### Post by mecheng on 2009-11-21
solved. 

The issue is with the network monitor. I had to uninstall it from synaptic "network-manager". 

I added the following to /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <ssid>
wpa-ap-scan 1
wpa-psk <psk-key>

```

I had a backup from an old install when this happened before. The update reinstalled network-manager.

There are tutorials out there for this so use the search function!!!

---

### Post by rowanq on 2009-12-02
Hey Mecheng,
  Sorry if I'm a little slow on the uptake here, but I think I need a little clarification. I seem to have the same problem; dropping network connection when changing the screens brightness. I had switched to wicd, and while that fixed the dropped connections, it caused me other problems.
 Are you saying that you reinstalled "network-manager"? What's the update that you refer to?

Rowan

---

### Post by phh on 2009-12-09
How do you uninstall network-manager and install wicd if you dont have anetwork connection?

---

### Post by rowanq on 2009-12-09
> **phh said:**
> How do you uninstall network-manager and install wicd if you dont have anetwork connection?

You'd have to either plug in an ethernet cable and update over wire or use another computer to download a Wicd .deb package to a cd or USB drive.

---

### Post by lucho64 on 2009-12-27
> **mecheng said:**
> solved. 

The issue is with the network monitor. I had to uninstall it from synaptic "network-manager". 

I added the following to /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <ssid>
wpa-ap-scan 1
wpa-psk <psk-key>

```

I had a backup from an old install when this happened before. The update reinstalled network-manager.

There are tutorials out there for this so use the search function!!!

Man! I had exactly the same problem, and like you, I had solved it before and I had forgotten. When I went and look at the /etc/network/interfaces file I had the backup file made by my editor pointing to the file being modified before! arrgh ... after all this years (I was using 8.04 and upgraded all the way to Karmic) and the problem is still there. Anyway, thanks for posting

---

### Post by GadgetsGuy on 2010-08-03
Could somebody create an update script for us Ubuntu newbs so we can also fix our wifi connection?

thanks

---

### Post by GadgetsGuy on 2010-08-03
ok .... I tried following the above instructions ... I uninstalled network-manager from synaptic, and added the lines to **/etc/network/interfaces**

now I cannot connect to the internet at all!  :(

and without an internet connection, I cannot even reinstall network-manager.

My Ubuntu netbook is now FUBAR.

please advise

---

### Post by GadgetsGuy on 2010-10-04
Anybody????

I have Ubuntu installed on my netbook, and cannot even use it - I have to boot into XP to use it!  :(

---

### Post by klemes on 2010-10-04
Maybe you could post the output of ```
sudo /etc/init.d/networking restart
```
for others to see what is wrong with your connection.
Also I have to ask you if you are using WEP or WPA data encryption in your wireless network because the above settings are for WPA encryption and there different settings are required for WEP.

---

### Post by GadgetsGuy on 2010-12-18
> **klemes said:**
> Maybe you could post the output of ```
sudo /etc/init.d/networking restart
```
for others to see what is wrong with your connection.
Also I have to ask you if you are using WEP or WPA data encryption in your wireless network because the above settings are for WPA encryption and there different settings are required for WEP.

laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for a1web: 
 * Reconfiguring network interfaces...                                                                                       ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
                                                                                                                      [ OK ]
laptop:~$

---

### Post by GadgetsGuy on 2011-01-08
I guess if nobody has an answer for me, I will delete the partition and re-install all over again .. although I was really hoping to learn what I screwed up, and how to un-screw it ... :confused:

---

