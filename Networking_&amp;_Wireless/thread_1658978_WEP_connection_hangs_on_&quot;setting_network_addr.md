---
title: "WEP connection hangs on &quot;setting network address&quot;: security/hex box pops up"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by UbuNoob001 on 2011-01-03
So I just installed Kubuntu 10.04 on a dell Insprion 1545 (which has the broadcom bcm4312 ). 

I was able to enable the restricted sta driver (just like always with Ubuntu)

[B]However when I try and connect to a wireless network I have the following problem: 
[/B]
1. restarted computer 
2. clicked on network manager icon on bottom right panel 
3. clicked on create network connection at top of window
      - i now see a list of networks including the one i want to connect to 
4. i select it and click CONNECT
5. Connection name/security info imput box comes up
           -security is selected for wep already
           - key type is listed as passprhase for 128 bit
           -wep index is "1 Default"
           - authentication is OpenSystem

6. I enter password: xxxxxxx and click okay
         kde wallet opens and I enter password
                "the application KNetworkManager has requested access to open wallet kdewallet"  to which i reply Allow Always. 

7[I].a box pops up which is entitled "secrets for 2wire043-Knetwork manager"
             these are the following fields:values
                     security: wep
                    key type : Hex or Ascii Key for 64 or 128 bit
                   key *********************************** (26 digits i think)
	        wep index: 1 (default)
                   authentication Open System. [/I]

8. I click OK... at the bottom if i hover it says configuring interface, setting network addy...

9.**this loops and brings up the same box listed in 7 again**

Below are some parts of var/log/syslog that I thought might be helpful (though im not used to combing logs) as well as the output for iwconfig and lspci

```
Jan  3 11:37:26 laptop1 NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Jan  3 11:37:26 laptop1 NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1558
Jan  3 11:37:26 laptop1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  3 11:37:26 laptop1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  3 11:37:26 laptop1 NetworkManager: <info>  Activation (eth1/wireless): could not get IP configuration for connection '2WIRE043'.
Jan  3 11:37:26 laptop1 NetworkManager: <info>  (eth1): device state change: 7 -> 6 (reason 0)
Jan  3 11:37:26 laptop1 NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
Jan  3 11:37:26 laptop1 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  3 11:40:46 laptop1 wpa_supplicant[971]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  3 11:40:46 laptop1 NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
Jan  3 11:40:46 laptop1 NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Jan  3 11:40:49 laptop1 wpa_supplicant[971]: Associated with 00:26:50:54:83:61
Jan  3 11:40:49 laptop1 wpa_supplicant[971]: CTRL-EVENT-CONNECTED - Connection to 00:26:50:54:83:61 completed (reauth) [id=0 id_str=]
Jan  3 11:40:49 laptop1 NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associated
Jan  3 11:40:49 laptop1 NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed
Jan  3 11:41:11 laptop1 anacron[1656]: Anacron 2.3 started on 2011-01-03
Jan  3 11:41:11 laptop1 anacron[1656]: Normal exit (0 jobs run)
``` and 
```
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Waking up...
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): now managed
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): bringing up device.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): preparing device.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth0): now managed
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth0): bringing up device.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth0): preparing device.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan  3 11:43:55 laptop1 kernel: [ 1497.926536] sky2 eth0: enabling interface
Jan  3 11:43:55 laptop1 kernel: [ 1497.926910] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) starting connection '2WIRE043'
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1/wireless): access point '2WIRE043' has security, but secrets are required.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 6 -> 9 (reason 7)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) failed for access point (2WIRE043)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Marking connection '2WIRE043' invalid.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  Activation (eth1) failed.
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Jan  3 11:43:55 laptop1 NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Jan  3 11:43:57 laptop1 kernel: [ 1499.487871] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input13
Jan  3 11:43:57 laptop1 kernel: [ 1499.518035] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input14
Jan  3 11:43:57 laptop1 avahi-daemon[933]: Registering new address record for fe80::224:2cff:fe02:a11b on eth1.*.
Jan  3 11:44:03 laptop1 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan  3 11:44:03 laptop1 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan  3 11:44:03 laptop1 kernel: [ 1505.308261] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Jan  3 11:44:03 laptop1 kernel: [ 1505.308631] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan  3 11:44:03 laptop1 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  3 11:44:03 laptop1 NetworkManager: <info>  dhclient started with pid 1884
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan  3 11:44:03 laptop1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  3 11:44:03 laptop1 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  3 11:44:03 laptop1 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  3 11:44:03 laptop1 dhclient: All rights reserved.
Jan  3 11:44:03 laptop1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  3 11:44:03 laptop1 dhclient: 
Jan  3 11:44:03 laptop1 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan  3 11:44:03 laptop1 dhclient: Listening on LPF/eth0/00:23:ae:27:09:44
Jan  3 11:44:03 laptop1 dhclient: Sending on   LPF/eth0/00:23:ae:27:09:44
Jan  3 11:44:03 laptop1 dhclient: Sending on   Socket/fallback
Jan  3 11:44:04 laptop1 avahi-daemon[933]: Registering new address record for fe80::223:aeff:fe27:944 on eth0.*.
Jan  3 11:44:05 laptop1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan  3 11:44:05 laptop1 dhclient: DHCPOFFER of 192.168.1.76 from 192.168.1.254
Jan  3 11:44:05 laptop1 dhclient: DHCPREQUEST of 192.168.1.76 on eth0 to 255.255.255.255 port 67
Jan  3 11:44:06 laptop1 kernel: [ 1508.628087] eth1: no IPv6 routers present
Jan  3 11:44:06 laptop1 dhclient: DHCPACK of 192.168.1.76 from 192.168.1.254
Jan  3 11:44:06 laptop1 dhclient: bound to 192.168.1.76 -- renewal in 39419 seconds.
Jan  3 11:44:06 laptop1 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jan  3 11:44:06 laptop1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  3 11:44:06 laptop1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan  3 11:44:06 laptop1 NetworkManager: <info>    address 192.168.1.76
Jan  3 11:44:06 laptop1 NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan  3 11:44:06 laptop1 NetworkManager: <info>    gateway 192.168.1.254
Jan  3 11:44:06 laptop1 NetworkManager: <info>    nameserver '192.168.1.254'
Jan  3 11:44:06 laptop1 NetworkManager: <info>    domain name 'gateway.2wire.net'
Jan  3 11:44:06 laptop1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  3 11:44:06 laptop1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  3 11:44:06 laptop1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan  3 11:44:06 laptop1 avahi-daemon[933]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.76.
Jan  3 11:44:06 laptop1 avahi-daemon[933]: New relevant interface eth0.IPv4 for mDNS.
Jan  3 11:44:06 laptop1 avahi-daemon[933]: Registering new address record for 192.168.1.76 on eth0.IPv4.
Jan  3 11:44:07 laptop1 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan  3 11:44:07 laptop1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan  3 11:44:07 laptop1 NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan  3 11:44:07 laptop1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  3 11:44:13 laptop1 kernel: [ 1515.760065] eth0: no IPv6 routers present
Jan  3 11:44:18 laptop1 ntpdate[1930]: step time server 91.189.94.4 offset -0.880164 sec

```

iwconfig: ```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:166
          Rx invalid nwid:0  invalid crypt:1188  invalid misc:0

```

lspci: ```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by PatchesTheCaveman on 2011-01-03
Is your user information correct in stating you are running Ubuntu 10.04 Lucid Lynx (LTS)?  

I ask because there is a faulty kernel update in 10.10 Maverick Meerkat which breaks Broadcom wireless devices.

---

### Post by UbuNoob001 on 2011-01-03
> **PatchesTheCaveman said:**
> Is your user information correct in stating you are running Ubuntu 10.04 Lucid Lynx (LTS)?  

I ask because there is a faulty kernel update in 10.10 Maverick Meerkat which breaks Broadcom wireless devices.

No, I have yet to update my profile. I am running Kubuntu 10.04 now. Was running Ubuntu 10.04 with no problems.

---

### Post by UbuNoob001 on 2011-01-07
Not to lobby for additional suggestions, but I may have to migrate back to Ubuntu from Kubuntu as I never had this problem before. Any final suggestions?

---

### Post by remosu on 2011-01-07
in step 5 of your procedure (key type) you need to select: 

    "Hex or Ascii Key (for 64 or 128 bit)"

---

### Post by UbuNoob001 on 2011-01-07
> **remosu said:**
> in step 5 of your procedure (key type) you need to select: 

    "Hex or Ascii Key (for 64 or 128 bit)"


wow, that simple. I can't thank you enough for your solution, I'm enjoying learning KDE and was hoping not to have to switch back to Ubuntu for now. Thanks so much.

If you get a second, could you briefly state how you knew it was important to select Hex/Ascii? Thanks again! 


B

---

### Post by PatchesTheCaveman on 2011-01-07
Kubuntu is just a special version of Ubuntu that includes KDE by default instead of GNOME.  You can have both GNOME and KDE installed at the same time if you want.  You don't have to reinstall (K)Ubuntu to switch.

To install GNOME and all the software included with a standard Ubuntu installation on a Kubuntu installation, run:
```
sudo apt-get install ubuntu-desktop
```

To do the opposite and install KDE and all the software included with a standard Kubuntu installation on top of an Ubuntu installation, just add a 'k' above to install *kubuntu-desktop* instead.

That being said, everyone knows KDE is vastly superior to GNOME in every way, so I don't know why you'd ever want to go back.  ;-)

---

### Post by remosu on 2011-01-08
> **UbuNoob001 said:**
> 

If you get a second, could you briefly state how you knew it was important to select Hex/Ascii? Thanks again! 


B

well... I have the same problem than you and googling I find this threat without answer. 
Frustrated for not find any solution for this I use the infallible/desperate solution: "try and error" changing all combinations :P

---

