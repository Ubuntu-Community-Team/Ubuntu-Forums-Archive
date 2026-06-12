---
title: "Ubunut won't connect to my wireless router."
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by Morg131 on 2011-07-11
Hi guys. Just downloaded and installed Ubuntu yesterday (Haazzah) due to windows not wanting to work with my sound card drivers (Sound will not play when I boot into windows but it will in Ubuntu) but that isn't why I'm here. No matter how hard I try, I cannot get a wireless internet connection. I'm connecting to a BT Home Hub 2 type B and my wireless chip is a Intel WiFi Link 5100. When I try to connect to my wireless router, it simply goes around in circles forever not connecting OR it will say it has connected, but I have no internet capabilities. Can anyone walk me through what the necessary steps are to get this issue resolved? 

Again, I am new to Ubuntu and will need everything in dumb-talk ;D

Any help is appreciated!

I'm also on Ubuntu 11.04 if that helps!

---

### Post by dp20957 on 2011-07-11
I have the exact same problem. I got rid of Vista and installed Ubuntu 11.04. When I click on Network Tools and try and add my wireless network info (at least the parts I understand) the save button stays grayed out so I can't even save the info to see if it would work.

---

### Post by Morg131 on 2011-07-11
Well I don't have that exact issue, I can enter my Network information in by clicking the wireless button then the 'Add wireless network' (Or something like that button) and it will accept the information. Though It just won't connect, either getting stuck in a loop or saying it is connected when it is not. :/

It's good to know though, that I'm not the only one having issues with the WiFi.

---

### Post by Morg131 on 2011-07-12
Sorry to bump my own thread but I'm almost literally tearing my own hair out! Does anyone out there have any ideas on how to fix this!? I love Ubuntu, but It's such a shame I cannot use the internet without being constantly plugged in ](*,)

---

### Post by snapback77 on 2011-07-12
I finally got tired of trying to make ndiswrapper work with my adapter and went to  Ubuntu Certified hardware and found a D-Link USB adapter N160 and it worked right out of the box.  70 dollars at Office Depot.  
If you still want to try I think you need to learn about ndiswrapper. Good Luck.

---

### Post by Morg131 on 2011-07-13
Ok, I've now also tried a wireless dongle with all the correct drivers installed. But still no luck.

iwconfig results - 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"BTHomeHub2-GPN6"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: FA:86:22:3F:54:81   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"BTHomeHub2-GPN6"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: FA:86:22:3F:54:81   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

sudo lshw -C network results - 

```
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:f4:21:e6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.72 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f8500000-f8503fff ioport:2000(size=256) memory:c0400000-c041ffff
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:12:fb:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic-pae firmware=8.83.5.1 build 33692 ip=10.42.43.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:50 memory:f8600000-f8601fff
  *-network
       description: Wireless interface
       physical id: 4
       bus info: usb@2:3
       logical name: wlan1
       serial: 00:02:72:78:74:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.38-8-generic-pae firmware=4725 ip=10.42.44.1 link=yes multicast=yes wireless=IEEE 802.11bg

```
As you can see, wlan1 is the wireless dongle. Whereas wlan0 is my built-in Intel Wifi link 5100. Sometimes when I 'connect', the wireless icon goes inside what looks like a monitor. I am still unable to ping google and cannot access my hub's settings. Ideas?

---

### Post by chili555 on 2011-07-13
> wlan0     IEEE 802.11abg  ESSID:"BTHomeHub2-GPN6"  
          [COLOR="Red"]Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: FA:86:22:3F:54:81   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offSee that kiddos? That is what happens when you do:> I can enter my Network information in by clicking the wireless button then the [COLOR="Red"]'Add wireless network'[/COLOR] (Or something like that button) and it will accept the information. The actual meaning of 'Create New Wireless Network...' is actually: "Create new network in a computer-to-computer network to enable internet connection sharing." Is that what you intended? Probably not, since the title of the thread is won't connect to my ***router***. 

Please remove all those settings and make sure the mode is set to Infrastructure. Reboot. Now check again:```
iwconfig
```This time, it ought to say:> wlan0     IEEE 802.11abg  ESSID:"BTHomeHub2-GPN6"  
          [COLOR="Red"]Mode:Managed[/COLOR]  Frequency:2.412 GHz  Cell: FA:86:22:3F:54:81   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offIf not, make it so:```
sudo iwconfig wlan0 mode managed
```Now check the position of the wireless switch:```
rfkill list all
```If everything looks good, click the Network Manager icon, see your network and connect.

By the way, if your settings are correct, the Intel will work perfectly. Take the USB back and get your money back.

---

### Post by Morg131 on 2011-07-13
Thanks for the reply!

iwconfig results - 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

rfkill list all resutls -

```
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-threeg: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

The USB was actually left over from switching a desktop PC from wireless to Ethernet, so no worries there :)

---

### Post by chili555 on 2011-07-13
> **Morg131 said:**
> Thanks for the reply!

iwconfig results - 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

rfkill list all resutls -

```
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-threeg: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

The USB was actually left over from switching a desktop PC from wireless to Ethernet, so no worries there :)So now does it connect like a champ?

---

### Post by Morg131 on 2011-07-13
Unfortunately no :/
It'll simply attempt to connect then time-out or say it has connected, but I cannot access the internet, my hub, or ping, and the connection speed is 'unknown'

---

### Post by chili555 on 2011-07-13
> say it has connected, but I cannot access the internet, my hub, or ping, and the connection speed is 'unknown'When that happens, please run and post:```
ifconfig
route -n
iwconfig
```Thanks.

---

### Post by Morg131 on 2011-07-13
> **chili555 said:**
> When that happens, please run and post:```
ifconfig
route -n
iwconfig
```Thanks.

Nevermind. I found out that, that was happening when I was making the mistake of clicking 'Create A New Wireless Network'

The timing out and never connecting however, isn't. :(

---

### Post by chili555 on 2011-07-13
Please be sure the USB wireless is disconnected. Also, I notice you have a wired ethernet connection. Network Manager is designed to disallow a wireless connection if wired is available. Please detach the ethernet cable and try to connect. Is the behavior the same? Are you challenged for your encryption key? If so, and it still won't connect, please post:```
sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25
```Thanks.

---

### Post by Morg131 on 2011-07-13
> **chili555 said:**
> Please be sure the USB wireless is disconnected. Also, I notice you have a wired ethernet connection. Network Manager is designed to disallow a wireless connection if wired is available. Please detach the ethernet cable and try to connect. Is the behavior the same? Are you challenged for your encryption key? If so, and it still won't connect, please post:```
sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25
```Thanks.

I am unable to access my Ubuntu until tomorrow, I shall run the terminal command then and post back. 
The USB has been disconnected as with the Ethernet cable when testing for connection however.

Thanks again for responding!

---

### Post by Morg131 on 2011-07-14
> **chili555 said:**
> If so, and it still won't connect, please post:```
sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25
```Thanks.

Hi, I am challenged for a pass-key and still no connection. USB and Ethernet were both disconnected. Here are the results:

```
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <warn> Activation (wlan0) failed for access point (BTHomeHub2-GPN6)
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> Marking connection 'Auto BTHomeHub2-GPN6' invalid.
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <warn> Activation (wlan0) failed.
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jul 14 15:17:14 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): deactivating device (reason: 0).
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) starting connection 'Auto BTOpenzone'
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): connection 'Auto BTOpenzone' requires no security.  No secrets needed.
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Config: added 'ssid' value 'BTOpenzone'
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Config: added 'scan_ssid' value '1'
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Config: added 'key_mgmt' value 'NONE'
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> Config: set interface ap_scan to 1
Jul 14 15:17:17 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  disconnected -> scanning

```

Although after running this, it seemed to automatically connect to 'BTOpenzone', looks to be a neighbour's router that has no pass-key.

---

### Post by chili555 on 2011-07-14
Is BTHomeHub2-GPN6 your network? Have you carefully checked the encryption key? Is the router set for mixed WPA and WPA2 mode? Mixed mode is troublesome. You will have better luck with WPA or WPA2. May we see:```
sudo iwlist wlan0 scan
```

---

### Post by Morg131 on 2011-07-14
> **chili555 said:**
> Is BTHomeHub2-GPN6 your network? Have you carefully checked the encryption key? Is the router set for mixed WPA and WPA2 mode? Mixed mode is troublesome. You will have better luck with WPA or WPA2. May we see:```
sudo iwlist wlan0 scan
```

Yes, the BTHomeHub2-GPN6 is my home network that I wish to connect to. Not the BTOpenzone. It is using WPA & WPA2 encryption, though I did change that and still no difference.

The results you asked for (I didn't post all of the other devices, just my router):

```
 Cell 05 - Address: 00:D0:44:BB:6F:82
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-GPN6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007b04ce007
                    Extra: Last beacon: 3116ms ago
                    IE: Unknown: 000F4254486F6D65487562322D47504E36
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
```

Thanks for your time :)

---

### Post by chili555 on 2011-07-14
Let's see what the driver is doing all this time:```
sudo cat /var/log/syslog | grep -e wlan -e iwl
```Usually Intels and iwlagn are solid.

---

### Post by Morg131 on 2011-07-14
> **chili555 said:**
> Let's see what the driver is doing all this time:```
sudo cat /var/log/syslog | grep -e wlan -e iwl
```Usually Intels and iwlagn are solid.

Here are the results:

```
Jul 14 15:46:15 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:46:15 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:46:15 morgan-Aspire-5735 kernel: [ 2465.399171] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 15:48:34 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:48:46 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:48:46 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:48:46 morgan-Aspire-5735 kernel: [ 2616.174104] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-GPN6' has security, and secrets exist.  No new secrets needed.
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:48:53 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 14 15:48:56 morgan-Aspire-5735 kernel: [ 2626.126786] wlan0: authenticate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 15:48:56 morgan-Aspire-5735 kernel: [ 2626.130502] wlan0: authenticated
Jul 14 15:48:56 morgan-Aspire-5735 kernel: [ 2626.130553] wlan0: associate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 15:48:56 morgan-Aspire-5735 kernel: [ 2626.134643] wlan0: RX AssocResp from 00:d0:44:bb:6f:82 (capab=0x431 status=0 aid=3)
Jul 14 15:48:56 morgan-Aspire-5735 kernel: [ 2626.134650] wlan0: associated
Jul 14 15:48:56 morgan-Aspire-5735 kernel: [ 2626.136771] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-GPN6'.
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 14 15:48:56 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 14 15:48:56 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:48:56 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:48:56 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 15:48:56 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:48:58 morgan-Aspire-5735 avahi-daemon[631]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fe12:fb22.
Jul 14 15:48:58 morgan-Aspire-5735 avahi-daemon[631]: New relevant interface wlan0.IPv6 for mDNS.
Jul 14 15:48:58 morgan-Aspire-5735 avahi-daemon[631]: Registering new address record for fe80::222:faff:fe12:fb22 on wlan0.*.
Jul 14 15:48:59 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:49:03 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:49:06 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 7 -> 3 (reason 39)
Jul 14 15:49:06 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): deactivating device (reason: 39).
Jul 14 15:49:06 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 28167
Jul 14 15:49:06 morgan-Aspire-5735 kernel: [ 2635.710050] wlan0: deauthenticating from 00:d0:44:bb:6f:82 by local choice (reason=3)
Jul 14 15:49:07 morgan-Aspire-5735 kernel: [ 2636.712114] wlan0: no IPv6 routers present
Jul 14 15:50:46 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:50:46 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:50:46 morgan-Aspire-5735 avahi-daemon[631]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 14 15:50:46 morgan-Aspire-5735 avahi-daemon[631]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fe12:fb22.
Jul 14 15:50:46 morgan-Aspire-5735 avahi-daemon[631]: Withdrawing address record for fe80::222:faff:fe12:fb22 on wlan0.
Jul 14 15:50:46 morgan-Aspire-5735 kernel: [ 2736.154345] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-GPN6' has security, and secrets exist.  No new secrets needed.
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:50:49 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 15:50:51 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 5 -> 3 (reason 39)
Jul 14 15:50:51 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): deactivating device (reason: 39).
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 15:51:11 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-GPN6' has security, and secrets exist.  No new secrets needed.
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:51:22 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 14 15:51:25 morgan-Aspire-5735 kernel: [ 2775.106339] wlan0: authenticate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 15:51:25 morgan-Aspire-5735 kernel: [ 2775.109633] wlan0: authenticated
Jul 14 15:51:25 morgan-Aspire-5735 kernel: [ 2775.109682] wlan0: associate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 15:51:25 morgan-Aspire-5735 kernel: [ 2775.112217] wlan0: RX AssocResp from 00:d0:44:bb:6f:82 (capab=0x431 status=0 aid=1)
Jul 14 15:51:25 morgan-Aspire-5735 kernel: [ 2775.112224] wlan0: associated
Jul 14 15:51:25 morgan-Aspire-5735 kernel: [ 2775.114796] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): supplicant connection state:  associated -> completed
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-GPN6'.
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 14 15:51:25 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 14 15:51:25 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:51:25 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:51:25 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 15:51:25 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:51:27 morgan-Aspire-5735 avahi-daemon[631]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fe12:fb22.
Jul 14 15:51:27 morgan-Aspire-5735 avahi-daemon[631]: New relevant interface wlan0.IPv6 for mDNS.
Jul 14 15:51:27 morgan-Aspire-5735 avahi-daemon[631]: Registering new address record for fe80::222:faff:fe12:fb22 on wlan0.*.
Jul 14 15:51:28 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:51:28 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): device state change: 7 -> 3 (reason 39)
Jul 14 15:51:28 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): deactivating device (reason: 39).
Jul 14 15:51:29 morgan-Aspire-5735 NetworkManager[636]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 28352
Jul 14 15:51:29 morgan-Aspire-5735 kernel: [ 2778.605532] wlan0: deauthenticating from 00:d0:44:bb:6f:82 by local choice (reason=3)
Jul 14 15:51:36 morgan-Aspire-5735 kernel: [ 2785.800123] wlan0: no IPv6 routers present
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.180832] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.180835] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.180959] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.180968] iwlagn 0000:03:00.0: setting latency timer to 64
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.181003] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.201752] iwlagn 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.201755] iwlagn 0000:03:00.0: Device SKU: 0Xb
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.201881] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jul 14 15:56:47 morgan-Aspire-5735 kernel: [   10.201956] iwlagn 0000:03:00.0: irq 49 for MSI/MSI-X
Jul 14 15:56:48 morgan-Aspire-5735 kernel: [   10.744922] iwlagn 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
Jul 14 15:56:48 morgan-Aspire-5735 kernel: [   11.283176] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): now managed
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): bringing up device.
Jul 14 15:56:52 morgan-Aspire-5735 kernel: [   15.153737] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): preparing device.
Jul 14 15:56:52 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): deactivating device (reason: 2).
Jul 14 15:56:53 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant manager state:  down -> idle
Jul 14 15:56:53 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Jul 14 15:56:53 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant interface state:  starting -> ready
Jul 14 15:57:07 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:57:07 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:57:07 morgan-Aspire-5735 kernel: [   30.194091] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 15:57:43 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:57:43 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:57:44 morgan-Aspire-5735 kernel: [   66.602162] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 6 -> 3 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): deactivating device (reason: 0).
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 15:57:48 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-GPN6' has security, and secrets exist.  No new secrets needed.
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jul 14 15:57:55 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  scanning -> inactive
Jul 14 15:57:56 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jul 14 15:57:56 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  scanning -> inactive
Jul 14 15:57:57 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jul 14 15:57:57 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  scanning -> inactive
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  scanning -> inactive
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  inactive -> associating
Jul 14 15:57:58 morgan-Aspire-5735 kernel: [   81.256430] wlan0: authenticate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 15:57:58 morgan-Aspire-5735 kernel: [   81.259130] wlan0: authenticated
Jul 14 15:57:58 morgan-Aspire-5735 kernel: [   81.259162] wlan0: associate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 15:57:58 morgan-Aspire-5735 kernel: [   81.262359] wlan0: RX AssocResp from 00:d0:44:bb:6f:82 (capab=0x431 status=0 aid=3)
Jul 14 15:57:58 morgan-Aspire-5735 kernel: [   81.262363] wlan0: associated
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 14 15:57:58 morgan-Aspire-5735 kernel: [   81.264598] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-GPN6'.
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 14 15:57:58 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 14 15:57:58 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:57:58 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 15:57:58 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 15:57:58 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:57:59 morgan-Aspire-5735 avahi-daemon[883]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fe12:fb22.
Jul 14 15:57:59 morgan-Aspire-5735 avahi-daemon[883]: New relevant interface wlan0.IPv6 for mDNS.
Jul 14 15:57:59 morgan-Aspire-5735 avahi-daemon[883]: Registering new address record for fe80::222:faff:fe12:fb22 on wlan0.*.
Jul 14 15:58:01 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:58:05 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 15:58:06 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 7 -> 3 (reason 39)
Jul 14 15:58:06 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): deactivating device (reason: 39).
Jul 14 15:58:06 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2144
Jul 14 15:58:06 morgan-Aspire-5735 kernel: [   89.388276] wlan0: deauthenticating from 00:d0:44:bb:6f:82 by local choice (reason=3)
Jul 14 15:58:08 morgan-Aspire-5735 kernel: [   91.392028] wlan0: no IPv6 routers present
Jul 14 16:01:04 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 16:01:04 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 16:01:04 morgan-Aspire-5735 avahi-daemon[883]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 14 16:01:04 morgan-Aspire-5735 avahi-daemon[883]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fe12:fb22.
Jul 14 16:01:04 morgan-Aspire-5735 avahi-daemon[883]: Withdrawing address record for fe80::222:faff:fe12:fb22 on wlan0.
Jul 14 16:01:04 morgan-Aspire-5735 kernel: [  266.722727] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-GPN6' has security, and secrets exist.  No new secrets needed.
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 16:01:21 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 16:01:24 morgan-Aspire-5735 kernel: [  287.491562] wlan0: authenticate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 14 16:01:24 morgan-Aspire-5735 kernel: [  287.494869] wlan0: authenticated
Jul 14 16:01:24 morgan-Aspire-5735 kernel: [  287.494922] wlan0: associate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 16:01:24 morgan-Aspire-5735 kernel: [  287.498069] wlan0: RX AssocResp from 00:d0:44:bb:6f:82 (capab=0x431 status=0 aid=3)
Jul 14 16:01:24 morgan-Aspire-5735 kernel: [  287.498075] wlan0: associated
Jul 14 16:01:24 morgan-Aspire-5735 kernel: [  287.502450] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-GPN6'.
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 14 16:01:24 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 14 16:01:25 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 14 16:01:25 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 16:01:25 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 16:01:25 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 16:01:25 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:01:26 morgan-Aspire-5735 avahi-daemon[883]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fe12:fb22.
Jul 14 16:01:26 morgan-Aspire-5735 avahi-daemon[883]: New relevant interface wlan0.IPv6 for mDNS.
Jul 14 16:01:26 morgan-Aspire-5735 avahi-daemon[883]: Registering new address record for fe80::222:faff:fe12:fb22 on wlan0.*.
Jul 14 16:01:28 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:01:33 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:01:35 morgan-Aspire-5735 kernel: [  298.080024] wlan0: no IPv6 routers present
Jul 14 16:01:45 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 16:01:45 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:01:48 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:01:56 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 16:01:56 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:01:59 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:02:03 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:02:08 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 16:02:08 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <warn> (wlan0): DHCPv4 request timed out.
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2672
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <warn> Activation (wlan0) failed for access point (BTHomeHub2-GPN6)
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <warn> Activation (wlan0) failed.
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jul 14 16:02:10 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): deactivating device (reason: 0).
Jul 14 16:02:10 morgan-Aspire-5735 kernel: [  333.208111] wlan0: deauthenticating from 00:d0:44:bb:6f:82 by local choice (reason=3)

```

I hope you know what this means because I have no idea :L

---

### Post by chili555 on 2011-07-14
It actually completes the authentication stages and then is not offered an IP address by the router. The router doesn't give any reasons; it just doesn't cooperate. I would love to see a log to compare with the router set to WPA2 only.

You might also try:```
sudo su
ifconfig wlan0 down
rmmod -f iwlagn
modprobe iwlagn swcrypto=1
ifconfig wlan0 up
exit
```Any improvement?

---

### Post by Morg131 on 2011-07-14
> **chili555 said:**
> 
You might also try:```
sudo su
ifconfig wlan0 down
rmmod -f iwlagn
modprobe iwlagn swcrypto=1
ifconfig wlan0 up
exit
```Any improvement?

Tried that, no improvements

> **chili555 said:**
> 
I would love to see a log to compare with the router set to WPA2 only.


This is what I got with WPA2 encryption only:

```
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) starting connection 'Auto BTHomeHub2-GPN6'
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): access point 'Auto BTHomeHub2-GPN6' has security, but secrets are required.
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless): connection 'Auto BTHomeHub2-GPN6' has security, and secrets exist.  No new secrets needed.
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 17:42:02 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 14 17:42:05 morgan-Aspire-5735 kernel: [ 6328.331052] wlan0: authenticate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 17:42:05 morgan-Aspire-5735 kernel: [ 6328.333289] wlan0: authenticated
Jul 14 17:42:05 morgan-Aspire-5735 kernel: [ 6328.333330] wlan0: associate with 00:d0:44:bb:6f:82 (try 1)
Jul 14 17:42:05 morgan-Aspire-5735 kernel: [ 6328.336450] wlan0: RX AssocResp from 00:d0:44:bb:6f:82 (capab=0x431 status=0 aid=2)
Jul 14 17:42:05 morgan-Aspire-5735 kernel: [ 6328.336456] wlan0: associated
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub2-GPN6'.
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 14 17:42:05 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 14 17:42:05 morgan-Aspire-5735 dhclient: Listening on LPF/wlan0/00:22:fa:12:fb:22
Jul 14 17:42:05 morgan-Aspire-5735 dhclient: Sending on   LPF/wlan0/00:22:fa:12:fb:22
Jul 14 17:42:05 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 17:42:05 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:08 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:13 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:25 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 17:42:25 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:28 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:32 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:39 morgan-Aspire-5735 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul 14 17:42:39 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:42 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:46 morgan-Aspire-5735 dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <warn> (wlan0): DHCPv4 request timed out.
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 5510
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <warn> Activation (wlan0) failed for access point (BTHomeHub2-GPN6)
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <warn> Activation (wlan0) failed.
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jul 14 17:42:51 morgan-Aspire-5735 NetworkManager[931]: <info> (wlan0): deactivating device (reason: 0).
Jul 14 17:42:51 morgan-Aspire-5735 kernel: [ 6374.209571] wlan0: deauthenticating from 00:d0:44:bb:6f:82 by local choice (reason=3)

```

---

### Post by chili555 on 2011-07-14
Please try another parameter:```
sudo su
ifconfig wlan0 down
rmmod -f iwlagn
modprobe iwlagn 11n_disable=1
ifconfig wlan0 up
exit
```Also, be sure that when you click the Network Manager icon and Edit connections, select Wireless and IPv6 settings, it is set to ignore.

---

### Post by Morg131 on 2011-07-14
I tried the parameters you said - No change.

IPv6 is also set to ignore. Still timing out

---

### Post by chili555 on 2011-07-14
I am running very low on ideas. Are you sure the router is not set to MAC filtering? May I see:```
route -n
```It has evidently connected previously and had an IP address, because it does:> DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67I am mystified why it worked at least once previously but not now. Please Edit Connections and let me know what your corresponding entries are compared to my attached.

---

### Post by Morg131 on 2011-07-14
route -n results (With Ethernet):

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

and without:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

[QUOTE=chili555]It has evidently connected previously and had an IP address[/QUOTE]

Could this be because it has connected to this laptop before on Windows (the laptop is duel booted with Windows Vista)?

Attached screen shot shows my Edit Connections entries. Hope this helps to resolve the issue! Thanks for your help and time on this so far.

---

### Post by dp20957 on 2011-07-27
There are a lot of people showing to check or add code. How do you even do this?

---

### Post by chili555 on 2011-07-27
> **dp20957 said:**
> There are a lot of people showing to check or add code. How do you even do this?Open a terminal, found in Applications > Terminal in the latest version of Ubuntu or in Applications > Accessories > Terminal in older versions. At the prompt, type in your command and press Enter. Please try an experiment. Open a terminal and find out the configuration of your wireless interface.```
iwconfig
```It is a harmless command that asks for information.

Be careful about adding code or making changes. Be sure the change applies to you and your situation. Make sure you have the same network card. For example, it does no good to download and install firmware for Broadcom cards if you have an Atheros card. 

Here is the output from my computer:> chili@LAPTOP60:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:56:2A:D7:99   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:49   Missed beacon:0That tells us theat I have a wireless interface wlan0. It is connected to a network called GBR1 at 54 Mb/s.

Also, be very cautious about malicious commands. Please see here: [http://ubuntuforums.org/announcement.php?f=336](http://ubuntuforums.org/announcement.php?f=336)

---

### Post by mimi040 on 2012-04-15
Had the same problem solved it as follows:

-Disconnected all networks and deleted them from the network list
-Disconnected all lan cables
-Rebooted router via web interface using different PC
-Restart linux (on boot it doesn't connect with any thing network related)
-Went to network thingy on top right corner and connected with that network I wanted to connect with. (By clicking its SSID and entering network key and admin key when prompted)
-internet connections wirelessly houray
-Plugged cables back in for ICS nou desktops connected to this bridge pc have internet again houray some more

sorry for bad english and ductape solution

---

