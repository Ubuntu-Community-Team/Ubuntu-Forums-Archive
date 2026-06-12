---
title: "Configure wireless PCI NIC in 10.10 server"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by dfresh4130 on 2010-11-12
I've installed 10.10 server edition on a box I just want to use for file storage/backup, uPnP server, etc.  The area I need to put the box doesn't have ethernet as an option so I'm trying to get this wireless NIC configured.  It's a Buffalotech WLI2-PCI-G54S which runs the Broadcom 4306 chipset.  I've managed to get the drivers for the card installed via the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

The drivers are working properly as I can run ```
iwlist scan
``` and see all the wireless networks it detects.  I found the info here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) to complete the configuration, but I'm still unable to get it right.  My wireless router is configured to use WPA2-PSK with AES.  I could just try installing gnome and get the GUI network config, but would like to avoid that if possible.  Any ideas/suggestions are greatly appreciated.

---

### Post by chili555 on 2010-11-12
If it's a server, I'd assume you want a static IP address. I suggest you amend /etc/network/interfaces like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108  <---or any IP address you prefer
netmask 255.255.255.0
gateway 192.168.1.1    <---your gateway or router's IP
wpa-ssid your_router
wpa-psk your_key

#auto eth0
iface eth0 inet dhcp
```Restart networking:```
sudo /etc/init.d/networking restart
```You probably also want to set up /etc/resolv.conf:```
nameserver 192.168.1.1
```Check to see if you are connected:```
ping -c3 www.google.com
```

---

### Post by dfresh4130 on 2010-11-12
Still no luck. Looks like it's having issues finding/connecting to the correct access point. Here's the output of my commands and various configs:

```

sudo iwconfig

wlan0     IEEE 802.11bg     ESSID:off/any
             Mode: Managed  Frequency: 2.462 GHz Access Point: Not-Associated  
             Tx-Power=20 dBm
             Retry long limit: 7  RTS thr:off  Fragment thr:off
             Encryption key: off
             Power Management: off

```Note that I tried a few of the options I found in another posting, but commented them out to match the suggested config.

```

cat /etc/network/interfaces

auto wlan0
iface wlan0 inet static
address 192.168.1.11
gateway 192.168.1.254
dns-nameservers 192.168.1.254
netmask 255.255.255.0
# wpa-driver b43
wpa-ssid <removed>
#wpa-ap-scan 2
#wpa-proto RSN
#wpa-pairwiase AES
#wpa-group AES
#wpa-key-mgmt WPA-PSK
#wpa-psk <removed hex value>
  wpa-psk <removed ASCII value>

```I'm only showing the below output for my network.  I'm also getting a different output from the command below than before I made these changes.  The values below are from earlier, but now I just get "Interface doesn't support scanning: Device or resource busy."
```

sudo iwlist scan

Cell 02 - Address: 00:21:7C:8D:F6:59
Channel: 11
Frequency:2.462 GHz (Channel-11)
Quality=64/70  Signal level=-46 dBm
Encryption key: on
ESSID:"<removed>"
Bit Rates: 1 Mb/s; 2 MB/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode: Master
Extra:tsf=000000115f0904181
IE: IEEE 802.11i/WPA2 Version 1
  Group Ciper: TKIP
  Pairwise Ciphers (2): CCMP TKIP
  Authentication Suites (1): PSK

``````

sudo lshw -C network

*-network
     description: Network Controller
     product: BCM4306 802.11b/g Wireless LAN Controller
     vendor: Broadcom Corporation
     physical id: a
     bus info: pci@0000:00:0a.0
     version: 03
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master
     configuration: driver=b43-pci-bridge latency=32
     resources: irq:18 memory:e3000000-e3001fff
*-network
     description: Wireless interface
     physical id: 1
     logical name: wlan0
     serial: 00:0d:0b:cf:74:ed
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=b43 driverversion:2.6.35-22-generic-pae firmware=N/A ip=192.168.1.11 link=no multicast=yes wireless=802.11bg

```

---

### Post by chili555 on 2010-11-12
May I see:```
dmesg | grep -e b43 -e wlan
```Thanks.

---

### Post by dfresh4130 on 2010-11-14
Well, this is strange.  I just now got a chance to get back and get your  info.  I shut down the system completely last night and unplugged the  power.  Now, when I booted up I have a successful connection.  I  rebooted several times last night so not sure why it's now working  properly.  Below is the info from the command you requested though.

```

dmesg | grep -e b43 -e wlan
[    1.674124] b43-pci-bridge 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.007383] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.236816] Registered led device: b43-phy0::tx
[   10.236843] Registered led device: b43-phy0::rx
[   10.236869] Registered led device: b43-phy0::radio
[   10.952128] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   11.078834] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.240442] wlan0: authenticate with 00:21:7c:8d:f6:59 (try 1)
[   13.241833] wlan0: authenticated
[   13.264158] wlan0: associate with 00:21:7c:8d:f6:59 (try 1)
[   13.265844] wlan0: RX AssocResp from 00:21:7c:8d:f6:59 (capab=0x431 status=0 aid=4)
[   13.265854] wlan0: associated
[   13.266607] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.064012] wlan0: no IPv6 routers present

```Here's the output from some of the other commands as well.

```

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE136"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:7C:8D:F6:59
          Bit Rate=48 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

sudo lshw -C network
[sudo] password for dstrick:
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:e3000000-e3001fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:0b:cf:74:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43  driverversion=2.6.35-22-generic-pae firmware=N/A ip=192.168.1.11  link=yes multicast=yes wireless=IEEE 802.11bg

``````

cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet static
#       address 192.168.1.10
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.254
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 192.168.1.254

#Added manually 11-10-10
auto wlan0
iface wlan0 inet static
        address 192.168.1.11
        gateway 192.168.1.254
        dns-nameservers 192.168.1.254
        netmask 255.255.255.0
#       wpa-driver b43-pci-bridge
        wpa-ssid <SSID>
        wpa-ap-scan 2
        wpa-proto RSN
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-key-mgmt WPA-PSK
#       wpa-psk <HEX key>
        wpa-psk <ASCII key>

```

---

### Post by chili555 on 2010-11-14
It looks perfect! I'm glad it's working.

---

