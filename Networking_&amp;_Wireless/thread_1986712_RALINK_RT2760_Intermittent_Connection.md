---
title: "RALINK RT2760 Intermittent Connection"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by olig1905 on 2012-05-25
Hi, havent posted on these boards in a while. Been using arch and fedora for the last year or so. since ubuntu first used unity, now it has matured a bit i have returned.  Basically normally i use ethernet but i have moved back into my parents house for a while and need wireless. I can connect to a network and use the wireless for a short while then it just stops working and i have to reconnect to the network.

**lspci | grep Ralink:**

```

02:00.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R

```**iwconfig wlan0:**

```

wlan0     IEEE 802.11bgn  ESSID:"HOME"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1C:DF:D5:E5:CC   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1191  Invalid misc:82   Missed beacon:0

```[B]
lsmod | grep rt2[/B]

```

rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci

```[B]
dmesg | grep rt2[/B]

```

   16.592286] rt2800pci 0000:02:00.0: enabling device (0000 -> 0002)
[   16.592296] rt2800pci 0000:02:00.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   16.592304] rt2800pci 0000:02:00.0: setting latency timer to 64
[   16.670228] Registered led device: rt2800pci-phy0::radio
[   16.670242] Registered led device: rt2800pci-phy0::assoc
[   16.670254] Registered led device: rt2800pci-phy0::quality
[   17.552288] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

```[FONT=monospace]**sudo lshw -C network**

[/FONT]```

[FONT=monospace]   *-network               
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1c:df:8d:bf:93
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-24-generic firmware=0.34 ip=192.168.2.8 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:e8000000-e800ffff
[/FONT]
```[FONT=monospace] 
**iwlist wlan0 scan**

[/FONT]```

[FONT=monospace] wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:D5:E5:CC
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002171e3c152
                    Extra: Last beacon: 57740ms ago
                    IE: Unknown: 0004484F4D45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE110FFFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EE110FFFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340A070700000000000000000000000000000000000000
                    IE: Unknown: DD9F0050F204104A0001101044000102103B000103104700102880288028801880A880001CDFD5E5CC1021001242656C6B696E20436F72706F726174696F6E1023001642656C6B696E20576972656C65737320526F75746572102400034635441042000C3131313131313131313131311054000800060050F20400011011001642656C6B696E20576972656C65737320526F75746572100800020084103C000101
[/FONT]
```[FONT=monospace]

**lsbrelease -d**

[/FONT]```

[FONT=monospace] Description:    Ubuntu 12.04 LTS
[/FONT]
```[FONT=monospace] 
**uname -mr**

[/FONT]```

[FONT=monospace] 3.2.0-24-generic x86_64
[/FONT]
```[FONT=monospace] [B]
sudo /etc/init.d/networking restart[/B]

[/FONT]```

[FONT=monospace] * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...            
[/FONT]
```[FONT=monospace] 

So I hope someone can give me a hand. I have read about and found people saying to blacklist different modules however when i tried to blacklist the rt2x00 modules it just didnt happen

Thanks in advance
[/FONT][FONT=monospace]
[/FONT]

---

### Post by wildmanne39 on 2012-05-27
Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2800pci
sudo modprobe rt2800pci nohwcrypt=1
sudo ifconfig wlan0 up

```
do not reboot this is temporary if it works and it should we will need to make it permanent.
Thanks

---

### Post by freewheelnat on 2012-05-29
I am having a similar issue, I think.

I upgraded from 10.10 to 12.04 a couple of days ago and my wifi keeps dropping out, even though it still shows as connected. The workaround is easy - disconnect then reconnect - but as you can imagine, it is quite annoying. I had never had this issue with 10.10.

The issue isn't with the wifi - I have both a laptop and my Android phone connected to it and when I have issues with my desktop, both those devices wifi work properly.

Also, interestingly, the wifi power shows at about 60%, whereas before, with 10.10, it always showed at 100%.

Here is the technical info.

**lspci | grep Ralink**
```
0b:01.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R
nat@nat-PC:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"RedAndPurple"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 1C:BD:B9:2D:08:8C   
          Bit Rate=60 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:44  Invalid misc:55   Missed beacon:0
```

**lsmod | grep rt2**
```
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
eeprom_93cx6           12725  1 rt2800pci
mac80211              506816  4 rt2800lib,rt2x00pci,rt2x00lib,iwlwifi
cfg80211              205544  3 rt2x00lib,iwlwifi,mac80211
```

**dmesg | grep rt2**
```
[37246.091710] rt2800pci 0000:0b:01.0: PCI INT A disabled
[37263.836155] rt2800pci: Unknown parameter `11n_disable'
[37331.172327] rt2800pci 0000:0b:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[37331.180683] Registered led device: rt2800pci-phy1::radio
[37331.180700] Registered led device: rt2800pci-phy1::assoc
[37331.180714] Registered led device: rt2800pci-phy1::quality
[37331.226754] phy1 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[37838.663300] rt2800pci 0000:0b:01.0: PCI INT A disabled
[37857.224799] rt2800pci 0000:0b:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[37857.233773] Registered led device: rt2800pci-phy2::radio
[37857.233820] Registered led device: rt2800pci-phy2::assoc
[37857.233868] Registered led device: rt2800pci-phy2::quality
[37857.282508] phy2 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

**sudo lshw -C network**
 ```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 20:cf:30:3d:e4:71
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:51 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:f6f00000-f6f0ffff
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:0b:01.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:90:d4:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-24-generic firmware=0.34 ip=192.168.0.103 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7ff0000-f7ffffff
```

**iwlist wlan0 scan**
```
wlan0     Scan completed :
          Cell 01 - Address: 1C:BD:B9:2D:08:8C
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"RedAndPurple"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fe808298ec
                    Extra: Last beacon: 60500ms ago
                    IE: Unknown: 000C526564416E64507572706C65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1605070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405070700000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700109CF5EE396830ACC9EB971CBDB92D088C10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
```

**uname -mr**
```
3.2.0-24-generic x86_64
```


Any ideas what may be causing this? I did try the suggestion above but it didn't work unfortunately.

---

### Post by wildmanne39 on 2012-05-29
Hi, please do:
```
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
Reboot

```
Then post the output of:
```
lspci -nnk | grep -iA2 net
lsmod | grep rt2
```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by freewheelnat on 2012-05-29
Done, here is the output:

**lspci -nnk | grep -iA2 net**
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169
--
0b:01.0 Network controller [0280]: Ralink corp. RT2760 Wireless 802.11n 1T/2R [1814:0701]
	Subsystem: Edimax Computer Co. Device [1432:7727]
	Kernel driver in use: rt2800pci
```

**lsmod | grep rt2**
```
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
```

**sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n55**
```
May 29 22:02:12 nat-PC NetworkManager[1018]: <info> (wlan0): bringing up device.
May 29 22:02:13 nat-PC kernel: [   17.669892] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
May 29 22:02:13 nat-PC NetworkManager[1018]: <info> (wlan0): preparing device.
May 29 22:02:13 nat-PC NetworkManager[1018]: <info> (wlan0): deactivating device (reason 'managed') [2]
May 29 22:02:13 nat-PC dbus[980]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
May 29 22:02:13 nat-PC kernel: [   17.694343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 29 22:02:13 nat-PC kernel: [   17.695177] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 29 22:02:13 nat-PC dbus[980]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
May 29 22:02:13 nat-PC NetworkManager[1018]: <info> wpa_supplicant started
May 29 22:02:13 nat-PC NetworkManager[1018]: <info> (wlan0): supplicant interface state: starting -> ready
May 29 22:02:13 nat-PC NetworkManager[1018]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 29 22:02:13 nat-PC NetworkManager[1018]: <info> (wlan0): supplicant interface state: ready -> inactive
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) starting connection 'Auto RedAndPurple'
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0/wireless): connection 'Auto RedAndPurple' has security, and secrets exist.  No new secrets needed.
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 29 22:02:14 nat-PC NetworkManager[1018]: <info> (wlan0): supplicant interface state: inactive -> scanning
May 29 22:02:16 nat-PC wpa_supplicant[1108]: Trying to authenticate with 1c:bd:b9:2d:08:8c (SSID='RedAndPurple' freq=2432 MHz)
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 29 22:02:16 nat-PC wpa_supplicant[1108]: Trying to associate with 1c:bd:b9:2d:08:8c (SSID='RedAndPurple' freq=2432 MHz)
May 29 22:02:16 nat-PC kernel: [   20.739600] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
May 29 22:02:16 nat-PC kernel: [   20.743481] wlan0: authenticated
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 29 22:02:16 nat-PC kernel: [   20.759593] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
May 29 22:02:16 nat-PC kernel: [   20.762801] wlan0: RX AssocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=2)
May 29 22:02:16 nat-PC kernel: [   20.762805] wlan0: associated
May 29 22:02:16 nat-PC wpa_supplicant[1108]: Associated with 1c:bd:b9:2d:08:8c
May 29 22:02:16 nat-PC wpa_supplicant[1108]: CTRL-EVENT-CONNECTED - Connection to 1c:bd:b9:2d:08:8c completed (auth) [id=0 id_str=]
May 29 22:02:16 nat-PC kernel: [   20.772039] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> (wlan0): supplicant interface state: associating -> completed
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'RedAndPurple'.
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May 29 22:02:16 nat-PC dhclient: Listening on LPF/wlan0/00:1f:1f:90:d4:fa
May 29 22:02:16 nat-PC dhclient: Sending on   LPF/wlan0/00:1f:1f:90:d4:fa
May 29 22:02:16 nat-PC dhclient: DHCPREQUEST of 192.168.0.103 on wlan0 to 255.255.255.255 port 67
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 29 22:02:16 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May 29 22:02:17 nat-PC NetworkManager[1018]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
May 29 22:02:17 nat-PC NetworkManager[1018]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 29 22:02:17 nat-PC NetworkManager[1018]: <info> Policy set 'Auto RedAndPurple' (wlan0) as default for IPv4 routing and DNS.
May 29 22:02:17 nat-PC NetworkManager[1018]: <info> Activation (wlan0) successful, device activated.
May 29 22:02:17 nat-PC NetworkManager[1018]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May 29 22:02:26 nat-PC kernel: [   31.534145] wlan0: no IPv6 routers present
```

---

### Post by wildmanne39 on 2012-05-30
Hi, I think we should do:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```

Add one line:

```
options rt2800pci nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Then post:
```
nm-tool
sudo iwlist scan
dmesg | egrep 'rt2|firm|radio|switch|wlan0|etork'
```
Thanks

---

### Post by freewheelnat on 2012-05-30
I had done that yesterday already, but not as a permanent option, I had done it as per your first response on this thread, before I posted. 

Unfortunately, yesterday, it had made no difference but I have done it again. And today, it also has made no difference, my connection has already dropped out since I started typing this. As usual, the network manager shows me as connected but nothing loads - if I disconnect then connect, which thankfully is a quick process, it then works again.

Below is the output you asked for, thanks a lot for your help.


**nm-tool**

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [Auto RedAndPurple] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        00:1F:1F:90:D4:FA

  Capabilities:
    Speed:           90 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKYA4EAB:        Infra, 7C:03:4C:8A:4E:AC, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *RedAndPurple:   Infra, 1C:BD:B9:2D:08:8C, Freq 2432 MHz, Rate 54 Mb/s, Strength 56 WEP
    Tobys1:          Infra, 00:24:B2:55:B4:9E, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        20:CF:30:3D:E4:71

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

**sudo iwlist scan**
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:BD:B9:2D:08:8C
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"RedAndPurple"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000210d416344c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000C526564416E64507572706C65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1605070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405070700000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700109CF5EE396830ACC9EB971CBDB92D088C10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 02 - Address: 7C:03:4C:8A:4E:AC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKYA4EAB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ec115fe72
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 0008534B594134454142
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.
```

**dmesg | egrep 'rt2|firm|radio|switch|wlan0|etork'**
```
[    3.900408] Console: switching to colour frame buffer device 170x48
[   17.395620] rt2800pci 0000:0b:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.409458] Registered led device: rt2800pci-phy0::radio
[   17.409485] Registered led device: rt2800pci-phy0::assoc
[   17.409516] Registered led device: rt2800pci-phy0::quality
[   18.112963] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   18.137198] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.137813] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.186554] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[   21.187958] wlan0: authenticated
[   21.202496] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[   21.205807] wlan0: RX AssocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[   21.205812] wlan0: associated
[   21.214980] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.069125] wlan0: no IPv6 routers present
[ 2321.459239] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[ 2324.632931] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[ 2324.634332] wlan0: authenticated
[ 2324.634593] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[ 2324.637956] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[ 2324.637964] wlan0: associated
[ 2335.003982] wlan0: no IPv6 routers present
[ 5496.518942] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[ 5499.540960] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[ 5499.542457] wlan0: authenticated
[ 5499.542686] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[ 5499.546055] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[ 5499.546061] wlan0: associated
[ 5510.315247] wlan0: no IPv6 routers present
[ 6849.063268] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[ 6852.145268] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[ 6852.146795] wlan0: authenticated
[ 6852.147029] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[ 6852.150381] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[ 6852.150386] wlan0: associated
[ 6862.904720] wlan0: no IPv6 routers present
[ 7952.105922] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[ 7954.871632] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[ 7954.873099] wlan0: authenticated
[ 7954.873579] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[ 7954.876892] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[ 7954.876900] wlan0: associated
[ 7965.642683] wlan0: no IPv6 routers present
[ 8984.404067] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[ 8987.538016] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[ 8987.539488] wlan0: authenticated
[ 8987.539825] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[ 8987.543081] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[ 8987.543086] wlan0: associated
[ 8998.068838] wlan0: no IPv6 routers present
[11344.360144] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[11347.042916] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[11347.044417] wlan0: authenticated
[11347.044664] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[11347.048009] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[11347.048015] wlan0: associated
[11357.805095] wlan0: no IPv6 routers present
[11976.161338] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[11979.674438] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[11979.677015] wlan0: authenticated
[11979.677224] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[11979.680654] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[11979.680660] wlan0: associated
[11989.846136] wlan0: no IPv6 routers present
[13197.656250] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[13201.149445] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[13201.150888] wlan0: authenticated
[13201.151098] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[13201.154438] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[13201.154444] wlan0: associated
[13211.775990] wlan0: no IPv6 routers present
[14481.444447] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[14485.069365] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[14485.070871] wlan0: authenticated
[14485.071094] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[14485.074491] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[14485.074497] wlan0: associated
[14496.042883] wlan0: no IPv6 routers present
[15647.042196] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[15650.279811] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[15650.281429] wlan0: authenticated
[15650.281638] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[15650.286957] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[15650.286963] wlan0: associated
[15661.149790] wlan0: no IPv6 routers present
[18759.753323] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[18762.408078] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[18762.409541] wlan0: authenticated
[18762.409950] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[18762.413194] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[18762.413202] wlan0: associated
[18773.190151] wlan0: no IPv6 routers present
[19718.867630] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[19721.622217] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[19721.623691] wlan0: authenticated
[19721.624446] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[19721.627770] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[19721.627776] wlan0: associated
[19731.742210] wlan0: no IPv6 routers present
[28134.209741] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[28136.964311] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[28136.965793] wlan0: authenticated
[28136.966013] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[28136.969514] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[28136.969520] wlan0: associated
[28147.953762] wlan0: no IPv6 routers present
[31116.122067] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[31119.263834] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[31119.265347] wlan0: authenticated
[31119.265598] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[31119.269008] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[31119.269014] wlan0: associated
[31129.678977] wlan0: no IPv6 routers present
[33305.723376] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[33309.064836] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[33309.066314] wlan0: authenticated
[33309.066537] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[33309.069986] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[33309.069991] wlan0: associated
[33319.160656] wlan0: no IPv6 routers present
[33686.229205] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[33689.219441] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[33689.220879] wlan0: authenticated
[33689.221091] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[33689.224495] wlan0: RX ReassocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[33689.224500] wlan0: associated
[33700.173953] wlan0: no IPv6 routers present
[33976.036147] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[33976.163518] rt2800pci 0000:0b:01.0: PCI INT A disabled
[33998.006442] rt2800pci 0000:0b:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[33998.014107] Registered led device: rt2800pci-phy0::radio
[33998.014123] Registered led device: rt2800pci-phy0::assoc
[33998.014139] Registered led device: rt2800pci-phy0::quality
[33998.056203] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[33998.097321] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33998.098997] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[34001.149828] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[34001.152736] wlan0: authenticated
[34001.169786] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[34001.177763] wlan0: RX AssocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[34001.177769] wlan0: associated
[34001.187018] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[34011.943725] wlan0: no IPv6 routers present
[34412.943479] wlan0: deauthenticating from 1c:bd:b9:2d:08:8c by local choice (reason=3)
[34413.147204] rt2800pci 0000:0b:01.0: PCI INT A disabled
[34413.163526] rt2800pci 0000:0b:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[34413.171949] Registered led device: rt2800pci-phy1::radio
[34413.174960] Registered led device: rt2800pci-phy1::assoc
[34413.174982] Registered led device: rt2800pci-phy1::quality
[34413.207078] phy1 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[34413.248246] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[34413.374929] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[34413.435223] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[34413.440102] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[34413.526414] phy1 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[34413.555625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[34416.620163] wlan0: authenticate with 1c:bd:b9:2d:08:8c (try 1)
[34416.621663] wlan0: authenticated
[34416.636091] wlan0: associate with 1c:bd:b9:2d:08:8c (try 1)
[34416.639427] wlan0: RX AssocResp from 1c:bd:b9:2d:08:8c (capab=0xc31 status=0 aid=1)
[34416.639430] wlan0: associated
[34416.649060] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[34427.067248] wlan0: no IPv6 routers present
```

---

### Post by TBABill on 2012-05-30
Have you tried to enable the rt2860sta driver for the card and blacklist all the RT2800 and RT2x00 modules? I believe the 2860 will work for your 2760 device.

---

### Post by wildmanne39 on 2012-05-30
Hi, please post:
```
cat /etc/lsb-release; uname -a
```
your signal strength is weak, how far are you from your router?
to get into your router setting type 192.168.0.1 or something close to that into your web broswer and should open the settings window.

Then in your router settings change wep to wpa2 only if possible, and see if that helps.

While in the router settings make sure the wireless signal output is at 100 percent.

Click on the network manager icon in the top right corner of the screen, then edit connection, wireless and set your settings to match the screenshots.

In 12.04 the rt2860sta has been removed in favor of the rt2800pci.

I would leave the options rt2800pci nohwcrypt=1 in the file.
Thanks

---

### Post by ratcheer on 2012-05-30
Try to find the firmware binary for the RT2760. It is a .bin file. Copy it to /lib/firmware. Then run "sudo modprobe rt2800pci". It should start your network connection.

Tim

PS - It is the same file my card uses, rt2860.bin. It is small, I could email it to you. Or, you can download it from the Ralink web site. Or, it is in Debian package firmware-ralink.

---

### Post by freewheelnat on 2012-05-30
> **wildmanne39 said:**
> Hi, please post:
```
cat /etc/lsb-release; uname -a
```


```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux nat-PC 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

> **wildmanne39 said:**
> your signal strength is weak, how far are you from your router?
Everything should be OK, I have always had 100% wifi on this desktop with Ubuntu 10.10 and also with Windows 7 (I have dual boot). Also, my laptop which is near my desktop gets 100% wifi (with both Windows 7 and Ubuntu 10.04), so issue isn't the wifi, nothing has changed regarding the wifi, I've always had perfect connection on this desktop with Ubuntu 10.10.

> **wildmanne39 said:**
> 
Then in your router settings change wep to wpa2 only if possible, and see if that helps.
I'd rather not change the settings of my router because I have several Android devices connected to it (I'm an Android app developer so I have many devices to test) and I'd rather not have to change them all.... It worked before so I wonder why it wouldn't work now, it seems to me that it's an issue with the driver and not my wifi?


> **wildmanne39 said:**
> 
Click on the network manager icon in the top right corner of the screen, then edit connection, wireless and set your settings to match the screenshots.



Done.

---

### Post by freewheelnat on 2012-05-30
> **TBABill said:**
> Have you tried to enable the rt2860sta driver for the card and blacklist all the RT2800 and RT2x00 modules? I believe the 2860 will work for your 2760 device.

No, I haven't tried. Where would I find this driver?

---

### Post by freewheelnat on 2012-05-30
> **ratcheer said:**
> Try to find the firmware binary for the RT2760. It is a .bin file. Copy it to /lib/firmware. Then run "sudo modprobe rt2800pci". It should start your network connection.

Tim

PS - It is the same file my card uses, rt2860.bin. It is small, I could email it to you. Or, you can download it from the Ralink web site. Or, it is in Debian package firmware-ralink.

I have the rt2860.bin file in /etc/firmware already.

According to [http://packages.debian.org/squeeze/firmware-ralink]("http://packages.debian.org/squeeze/firmware-ralink"), re2860.bin is the one needed for rt2760 as well "* Ralink RT2760/RT2790/RT2860/RT2890 (RT2700P[D]/RT2700E[D]/RT2800P[D]/RT2800E[D] chipset) firmware, version 11 (rt2860.bin)".

---

### Post by freewheelnat on 2012-05-30
> **freewheelnat said:**
> 
> Originally Posted by wildmanne39  
Click on the network manager icon in the top right corner of the screen, then edit connection, wireless and set your settings to match the screenshots.

Done.

Had issue again since doing this so no luck with this :(

---

### Post by jawilljr on 2012-05-30
Freewheelnat your error message:

```
phy2 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

appears to be the same as in [this thread.](http://ubuntuforums.org/showthread.php?t=1973881&highlight=mcu) Which Chili fixed in [this post](http://ubuntuforums.org/showpost.php?p=11908967&postcount=6)

All he did was install linux-backports-modules-cw-3.3-precise-generic, the reboot. Hopefully it fixes yours too.

Jerry

---

### Post by wildmanne39 on 2012-05-30
Hi jawilljr, thanks for posting that link I google that error message and did not see that link that is a good one to try.

---

### Post by freewheelnat on 2012-05-30
> **jawilljr said:**
> Freewheelnat your error message:

```
phy2 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

appears to be the same as in [this thread.](http://ubuntuforums.org/showthread.php?t=1973881&highlight=mcu) Which Chili fixed in [this post](http://ubuntuforums.org/showpost.php?p=11908967&postcount=6)

All he did was install linux-backports-modules-cw-3.3-precise-generic, the reboot. Hopefully it fixes yours too.

Jerry

Thanks a lot for that. I'll try it now, will report on how it is working later tonight or tomorrow.

---

### Post by ratcheer on 2012-05-30
> **freewheelnat said:**
> 

According to [http://packages.debian.org/squeeze/firmware-ralink](http://packages.debian.org/squeeze/firmware-ralink), re2860.bin is the one needed for rt2760 as well "* Ralink RT2760/RT2790/RT2860/RT2890 (RT2700P[D]/RT2700E[D]/RT2800P[D]/RT2800E[D] chipset) firmware, version 11 (rt2860.bin)".

Yes, that is what I said.

Somehow, this approach worked for me, yesterday, on both Debian and Ubuntu. I had never before gotten my RT3062 to connect without installing the rt3562sta/rt2860 driver, but now it is working with rt2800pci.

Oh well, it was worth a try. Good luck!

Tim

---

### Post by freewheelnat on 2012-05-30
> **wildmanne39 said:**
> Hi jawilljr, thanks for posting that link I google that error message and did not see that link that is a good one to try.

I think jawilljr is a search maestro because I had also googled that error (before posting on here) and like you, I did not find that link... ;)

---

### Post by freewheelnat on 2012-05-30
> **ratcheer said:**
> Yes, that is what I said.


I know, I was just confirming that you were right about that ;)

---

### Post by jawilljr on 2012-05-30
> **freewheelnat said:**
> I think jawilljr is a search maestro because I had also googled that error (before posting on here) and like you, I did not find that link... ;)

Thanks for the kind word...but I actually didn't search...I just remebered the error message and Chili's fix...

Jerry

---

### Post by freewheelnat on 2012-05-30
> **jawilljr said:**
> Thanks for the kind word...but I actually didn't search...I just remebered the error message and Chili's fix...

Jerry

Well, your memory is better than Google's memory then ;)

---

### Post by freewheelnat on 2012-05-31
Well, I'm pleased to report that my connection hasn't dropped out at all since I booted my computer 5 hours ago so it seems that the fix mentioned by jawilljr did the trick :)

---

### Post by wildmanne39 on 2012-05-31
Hi, that is great, please use thread tools to mark the thread solved.
Thanks

---

### Post by freewheelnat on 2012-06-01
I wanted to do it yesterday but I don't have that option, because I didn't actually start this thread. The original poster hasn't posted since their first post... Have sent a PM to original poster...

---

### Post by sagivloubaton on 2012-07-08
i have a similar issue...

---

### Post by kobudo on 2012-08-24
I have been having the same headache with my RT2760 card since upgrading to 12.04 as well. Installing linux-backports-modules-cw-3.3-precise-generic has helped improve stability, but it still stops frequently. The only step that I have taken that is not listed above is restricting the -n speed of the card in terminal. I wonder if re-enabling -n speed would help, but I have been unable to find the original article (I really can't use terminal without tons of research) and I don't know how to turn that switch back on. Any assistance, please? I would like to get this thing working well.

---

