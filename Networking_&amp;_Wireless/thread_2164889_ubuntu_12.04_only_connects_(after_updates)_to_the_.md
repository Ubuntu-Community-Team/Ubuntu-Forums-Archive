---
title: "ubuntu 12.04 only connects (after updates) to the internet on certain networks"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by ibeetalk on 2013-08-02
I have ubuntu 12.04. Everything has been working great since upgrading last year. I did an update and suddenly, I cannot connect to the internet using my school wireless or wired networks! I can connect to wireless/wired (and internet) at home. 

I also found out that I cannot connect to the internet using my coffee shop's wireless network. I looked up this problem and found a few similar instances: 
([http://askubuntu.com/questions/298938/ubuntu-12-04-ping-8-8-8-8-does-not-work-on-one-network-only;](http://askubuntu.com/questions/298938/ubuntu-12-04-ping-8-8-8-8-does-not-work-on-one-network-only;) [http://ubuntuforums.org/archive/index.php/t-1399246.html;](http://ubuntuforums.org/archive/index.php/t-1399246.html;) [http://askubuntu.com/questions/40862/wireless-card-can-only-connect-to-certain-networks](http://askubuntu.com/questions/40862/wireless-card-can-only-connect-to-certain-networks)) but none of the suggested solutions work for me. 

You see, the problem is that I can connect to the network, but my browsers get timed out waiting for responses from websites. So I cannot do anything that requires internet connection.

I also have a live USB. Tried booting from that, but it hangs up too (something to do with network).

Please help?

---

### Post by chili555 on 2013-08-02
What is your wireless driver? Please run and post:```
sudo lshw -C network
nm-tool
```Thanks.

---

### Post by ibeetalk on 2013-08-02
chili555, thank you for your response! here are the results from those codes! 

kipchirchir@ubuntu:~$ sudo lshw -C network
[sudo] password for kipchirchir: 
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:a8:12:fb
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.7-7 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:4a:6a:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-51-generic firmware=8.83.5.1 build 33692 ip=192.168.1.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f69fe000-f69fffff
kipchirchir@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Lindenhaus] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:21:6A:4A:6A:60

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    theclash:        Infra, 2C:B0:5D:41:84:AC, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA2
    4E7CFD 5G:       Infra, 84:1B:5E:4E:7C:FB, Freq 5180 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    biatch:          Infra, B8:8D:12:5F:C7:6D, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Get Busy:        Infra, 00:14:6C:A0:AD:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    belkin.8b4:      Infra, 08:86:3B:B8:B8:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    error_code24873: Infra, E0:91:F5:EB:76:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    lerpe:           Infra, A0:21:B7:78:FE:3E, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    biatch:          Infra, 28:CF:DA:B9:9F:3E, Freq 5745 MHz, Rate 54 Mb/s, Strength 32 WPA2
    lazu308:         Infra, E0:91:F5:FB:49:54, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA
    E63E49:          Infra, 84:1B:5E:E6:3E:48, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Nancy-HP-Wireless: Infra, 00:22:3F:A7:B0:3B, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    6KWVJ:           Infra, 00:7F:28:A0:59:BF, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    biatch:          Infra, 28:CF:DA:B9:9F:3D, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    biatch:          Infra, B8:8D:12:5F:C7:6E, Freq 5745 MHz, Rate 54 Mb/s, Strength 29 WPA2
    THE HILL:        Infra, 20:AA:4B:6C:0B:CF, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    DDD3AB:          Infra, 84:1B:5E:DD:D3:AA, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    4E7CFD:          Infra, 84:1B:5E:4E:7C:FC, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    The Wire:        Infra, 20:4E:7F:31:3E:C4, Freq 2417 MHz, Rate 54 Mb/s, Strength 22 WPA2
    A.J Linksys:     Infra, C0:C1:C0:E6:CF:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Seltrik3:        Infra, 2C:B0:5D:86:73:E8, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    D64F66:          Infra, 84:1B:5E:D6:4F:65, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    A.J Linksys:     Infra, C0:C1:C0:E6:CF:E3, Freq 5785 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    296 Linden St., Apt. 3: Infra, 20:AA:4B:76:90:38, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Salcedo:         Infra, 9C:D3:6D:A0:25:3C, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    E63E49 5G:       Infra, 84:1B:5E:E6:3E:47, Freq 5180 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    EA8609:          Infra, 84:1B:5E:EA:86:08, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    LaylaLovesPurple:Infra, C4:3D:C7:71:07:3E, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WEP
    @HomeAD5C:       Infra, 00:1C:F0:50:BC:F0, Freq 2437 MHz, Rate 54 Mb/s, Strength 57
    pemadawa-guest:  Infra, 58:6D:8F:42:73:75, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    THE HILL-guest:  Infra, 26:AA:4B:6C:0B:CF, Freq 2452 MHz, Rate 54 Mb/s, Strength 27
    linksys:         Infra, 00:1A:70:68:AB:92, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    296 Linden St., Apt. 3-guest: Infra, 02:AA:4B:76:90:39, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    *Lindenhaus:     Infra, BC:AE:C5:AF:97:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA2
    belkin.472:      Infra, 08:86:3B:22:B4:72, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    NETGEAR-5G:      Infra, E0:91:F5:EB:76:BF, Freq 5180 MHz, Rate 54 Mb/s, Strength 19
    Indiana21:       Infra, F8:E4:FB:D3:E4:E5, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    belkin.01a:      Infra, 08:86:3B:2A:60:1A, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    PURGATORY:       Infra, A0:21:B7:B4:6F:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Capt Red Beard:  Infra, 28:CF:DA:AE:6A:F3, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA2
    07FX08104745:    Infra, 00:12:0E:88:F8:9E, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP

  IPv4 Settings:
    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             167.206.254.1
    DNS:             167.206.254.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:A8:12:FB

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


kipchirchir@ubuntu:~$

---

### Post by chili555 on 2013-08-02
Please try an experiment to see if we can get the wireless to connect. Then we'll fix the ethernet.```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```This goes away on reboot, so if you need to reboot, repeat the sequence. If it works, we'll amend one file and make it persistent.

---

### Post by ibeetalk on 2013-08-02
I did try these codes (sudo modprobe -r iwlwifi; sudo modprobe iwlwifi 11n_disable=1)  as you suggested and got these results:

kipchirchir@ubuntu:~$ sudo modprob -r iwlwifi
[sudo] password for kipchirchir: 
sudo: modprob: command not found
kipchirchir@ubuntu:~$ sudo modprobe -r iwlwifi
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-custom.save, it will be ignored in a future release.
kipchirchir@ubuntu:~$ sudo modprobe iwlwifi 11n_disable=1
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-custom.save, it will be ignored in a future release.
kipchirchir@ubuntu:~$ 

The other thing is, it wont connect to the wireless network now. It keeps asking for the password! Sorry for the slow response, I have to log in and out of ubuntu/windows!

---

### Post by chili555 on 2013-08-02
That's interesting. It ought to connect, even if not at N speeds. Let's dig deeper:```
dmesg | grep iwl
sudo iw reg get
cat  /etc/modprobe.d/blacklist-custom.save
```Let's see if the troublesome file is something we need or that we can rename or if it is, in fact, interfering with wireless.

---

### Post by ibeetalk on 2013-08-03
Here are the results. Over my head!

kipchirchir@ubuntu:~$ dmesg | grep iwl
[   36.690995] iwlwifi 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   36.691003] iwlwifi 0000:0c:00.0: setting latency timer to 64
[   36.691024] iwlwifi 0000:0c:00.0: pci_resource_len = 0x00002000
[   36.691026] iwlwifi 0000:0c:00.0: pci_resource_base = ffffc90000678000
[   36.691028] iwlwifi 0000:0c:00.0: HW Revision ID = 0x0
[   36.691105] iwlwifi 0000:0c:00.0: irq 47 for MSI/MSI-X
[   36.691140] iwlwifi 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   36.691194] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   36.712926] iwlwifi 0000:0c:00.0: device EEPROM VER=0x120, CALIB=0x4
[   36.712929] iwlwifi 0000:0c:00.0: Device SKU: 0Xf0
[   36.713020] iwlwifi 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   36.789114] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[   36.871813] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   44.242158] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   44.245119] iwlwifi 0000:0c:00.0: Radio type=0x0-0x2-0x0
[   44.397073] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   44.400053] iwlwifi 0000:0c:00.0: Radio type=0x0-0x2-0x0
kipchirchir@ubuntu:~$ sudo iw reg ret
[sudo] password for kipchirchir:
Usage:	iw [options] command
Options:
	--debug		enable netlink debugging
	--version	show version (3.2)
Commands:
	help
	event [-t] [-r] [-f]
	phy
	list
	phy <phyname> info
	dev
	dev <devname> info
	dev <devname> del
	dev <devname> interface add <name> type <type> [mesh_id <meshid>] [4addr on|off] [flags <flag>*]
	phy <phyname> interface add <name> type <type> [mesh_id <meshid>] [4addr on|off] [flags <flag>*]
	dev <devname> ibss join <SSID> <freq in MHz> [fixed-freq] [<fixed bssid>] [beacon-interval <TU>] [basic-rates <rate in Mbps,rate2,...>] [mcast-rate <rate in Mbps>] [key d:0:abcde]
	dev <devname> ibss leave
	dev <devname> station dump
	dev <devname> station set <MAC address> vlan <ifindex>
	dev <devname> station set <MAC address> plink_action <open|block>
	dev <devname> station del <MAC address>
	dev <devname> station get <MAC address>
	dev <devname> survey dump
	dev <devname> mesh leave
	dev <devname> mesh join <mesh ID> [<param>=<value>]*
	dev <devname> mpath dump
	dev <devname> mpath set <destination MAC address> next_hop <next hop MAC address>
	dev <devname> mpath new <destination MAC address> next_hop <next hop MAC address>
	dev <devname> mpath del <MAC address>
	dev <devname> mpath get <MAC address>
	dev <devname> scan [-u] [freq <freq>*] [ies <hex as 00:11:..>] [ssid <ssid>*|passive]
	dev <devname> scan trigger [freq <freq>*] [ies <hex as 00:11:..>] [ssid <ssid>*|passive]
	dev <devname> scan dump [-u]
	reg get
	reg set <ISO/IEC 3166-1 alpha2>
	dev <devname> connect [-w] <SSID> [<freq in MHz>] [<bssid>] [key 0:abcde d:1:6162636465]
	dev <devname> disconnect
	dev <devname> link
	dev <devname> offchannel <freq> <duration>
	dev <devname> cqm rssi <threshold|off> [<hysteresis>]
	phy <phyname> wowlan show
	phy <phyname> wowlan disable
	phy <phyname> wowlan enable [any] [disconnect] [magic-packet] [gtk-rekey-failure] [eap-identity-request] [4way-handshake] [rfkill-release] [patterns <pattern>*]
	dev <devname> roc start <freq> <time>
	phy <phyname> set antenna <bitmap> | all | <tx bitmap> <rx bitmap>
	dev <devname> set txpower <auto|fixed|limit> [<tx power in mBm>]
	phy <phyname> set txpower <auto|fixed|limit> [<tx power in mBm>]
	phy <phyname> set distance <distance>
	phy <phyname> set coverage <coverage class>
	phy <phyname> set netns <pid>
	phy <phyname> set rts <rts threshold|off>
	phy <phyname> set frag <fragmentation threshold|off>
	dev <devname> set channel <channel> [HT20|HT40+|HT40-]
	phy <phyname> set channel <channel> [HT20|HT40+|HT40-]
	dev <devname> set freq <freq> [HT20|HT40+|HT40-]
	phy <phyname> set freq <freq> [HT20|HT40+|HT40-]
	phy <phyname> set name <new name>
	dev <devname> set peer <MAC address>
	dev <devname> set 4addr <on|off>
	dev <devname> set type <type>
	dev <devname> set meshid <meshid>
	dev <devname> set monitor <flag>*
	dev <devname> set mesh_param <param>=<value> [<param>=<value>]*
	dev <devname> set power_save <on|off>
	dev <devname> set bitrates [legacy-<2.4|5> <legacy rate in Mbps>*]
	dev <devname> get mesh_param [<param>]
	dev <devname> get power_save <param>

You can omit the 'phy' or 'dev' if the identification is unique,
e.g. "iw wlan0 info" or "iw phy0 info". (Don't when scripting.)

Do NOT screenscrape this tool, we don't consider its output stable.

kipchirchir@ubuntu:~$ cat /etc/modprobe.d/blacklist-custom.save
cat: /etc/modprobe.d/blacklist-custom.save: Permission denied
kipchirchir@ubuntu:~$ sudo cat /etc/modprobe.d/blacklist-custom.save
# /etc/modprobe.d/blacklist-custom
# Custom blacklist file so I don&#8217;t mess with any of the files that come with
# the module-init-tools package.
blacklist dell-laptop

kipchirchir@ubuntu:~$

---

### Post by chili555 on 2013-08-03
> kipchirchir@ubuntu:~$ sudo cat /etc/modprobe.d/blacklist-custom.save
# /etc/modprobe.d/blacklist-custom
# Custom blacklist file so I don’t mess with any of the files that come with
# the module-init-tools package.
blacklist dell-laptopAhhh! I see. It is an altogether appropriate file; it is just mis-worded. Let's rename it:```
sudo mv /etc/modprobe.d/blacklist-custom.save /etc/modprobe.d/blacklist-custom.conf
```> kipchirchir@ubuntu:~$ sudo iw reg ret
[sudo] password for kipchirchir:
Usage: iw [options] command
Options:
--debug enable netlink debugging
--version show version (3.2)It is not 'ret' it is 'get.'```
sudo iw reg [COLOR="#FF0000"]get[/COLOR]
```What is your region domain, US? GB? IT? IN? In a few cases, the region domain gets mis-applied and tries to connect to non-existant channels.

I see nothing in dmesg that is an obvious barrier to connection.

---

### Post by ibeetalk on 2013-08-03
chili555

Sorry, my bad on the typo.

```
kipchirchir@ubuntu:~$ sudo mv /etc/modprobe.d/blacklist-custom.save /etc/modprobe.d/blacklist
[sudo] password for kipchirchir: 
kipchirchir@ubuntu:~$ sudo iw reg get
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
kipchirchir@ubuntu:~$
```

I am in the US, if that helps.

---

### Post by chili555 on 2013-08-03
> $ sudo mv /etc/modprobe.d/blacklist-custom.save /etc/modprobe.d/blacklist
[sudo] password for kipchirchir: Another typo. Let's carefully and deliberately correct it:```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist[COLOR="#FF0000"]-custom.conf[/COLOR]
```Now let's try to set the region and see if it helps:> kipchirchir@ubuntu:~$ sudo iw reg get
country [COLOR="#FF0000"]00[/COLOR]:Neither of us live in country zero-zero! Please do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo iw reg set US
```Any improvement?

---

### Post by ibeetalk on 2013-08-03
Sorry again, I should be careful on those. I am using a tiny screen to read the codes! I have a better way now.

```
kipchirchir@ubuntu:~$ sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist-custom.conf
[sudo] password for kipchirchir: 
kipchirchir@ubuntu:~$ sudo modprobe -r iwlwifi
kipchirchir@ubuntu:~$ sudo modprobe -r iwlwifi 11n_disable=1
FATAL: Module 11n_disable=1 not found.
kipchirchir@ubuntu:~$ sudo modprobe iwlwifi 11n_disable=1
kipchirchir@ubuntu:~$ sudo iw reg set US
kipchirchir@ubuntu:~$ sudo iw reg get
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
kipchirchir@ubuntu:~$ 

```

It is now asking for the network password, and cannot connect.

---

### Post by chili555 on 2013-08-03
We're closer! Now try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi [COLOR="#FF0000"]<--that is, without the 11n parameter![/COLOR]
```
Now does it connect?

Is this your home router? Which one is it from your nm-tool above? It isn't locked on N speeds only, is it?

---

### Post by ibeetalk on 2013-08-03
When I logged back in to ubuntu, I noticed that it automatically connected to the network!

I entered the codes above. It still does not connect! Lindenhaus is the network! It is my landlords network. I just emailed to see if it is locked on N speeds.

---

### Post by ibeetalk on 2013-08-05
Chili555, 

It is not locked on N speeds. Sorry it took a while to get this info. 

ibeetalk

---

