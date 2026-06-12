---
title: "Ubuntu always identifies network, but rarely connects to it"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by GoS_ on 2012-01-02
Hi everyone.
I have an Edimax b/g wireless card that worked perfectly on Ubuntu 8.04 and 9.10 in the past.  It also worked perfectly with the most recent Debian release after I installed a driver for it.
With Ubuntu 11.10 I have to log out and back in many times before I, seemingly by luck, am connected to the internet.
When it does connect it does so instantly and with no problems in speed or stability as far as I can tell.
I am using the same wireless router as before and I have no problems with the connection in Windows.  Any suggestions? :(

Sorry if this issue has been posted before.  I have been searching for a solution for quite a while.
Thanks.

---

### Post by drdos2006 on 2012-01-02
Go back to an earlier version of Ubuntu eg Version 10.4 LTS ( Live CD ) and see if that fixes the problem.

regards

---

### Post by GoS_ on 2012-01-02
Okay, I'll try that.  I have slow internet, so I'll download 10.04 overnight and reply tomorrow with the results.
If 10.04 works, is there hope for a solution with 11.10?  Ideally I would be able to use the most recent release.

---

### Post by wildmanne39 on 2012-01-02
Hi, please post the output of the following commands from 11.10:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by GoS_ on 2012-01-02
Thanks a lot wildmanne39!  I hope this means something to you.  This is the output of the commands with a functional connection.  I am in the middle of a download right now, but I'll post the output from when I can not connect if it helps later.

```
bryce@behemoth:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux behemoth 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
bryce@behemoth:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7380]
	Kernel driver in use: forcedeth
--
08:07.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Ralink corp. EW-7108PCg [1814:2561]
	Kernel driver in use: rt61pci
bryce@behemoth:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:9C:3C:08   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:46  Invalid misc:83   Missed beacon:0

bryce@behemoth:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
bryce@behemoth:~$ lsmod
Module                  Size  Used by
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                88963  0 
hfs                    54782  0 
minix                  36322  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61475  2 vfat,msdos
jfs                   186662  0 
xfs                   831526  0 
reiserfs              248828  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
binfmt_misc            17540  1 
snd_seq_midi           13324  0 
arc4                   12529  2 
rt61pci                32257  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
adt7475                31231  0 
hwmon_vid              12746  1 adt7475
crc_itu_t              12707  1 rt61pci
rt2x00pci              14578  1 rt61pci
rt2x00lib              50325  2 rt61pci,rt2x00pci
mac80211              310872  2 rt2x00pci,rt2x00lib
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
joydev                 17693  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               728662  3 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236330  5 nouveau,ttm,drm_kms_helper
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 rt2x00lib,mac80211
nv_tco                 13687  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
i2c_nforce2            13058  0 
eeprom_93cx6           12725  1 rt61pci
video                  19412  1 nouveau
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
forcedeth              67563  0 
sata_nv                32305  3 
pata_amd               14121  0 
ahci                   26002  0 
libahci                26861  1 ahci
pata_jmicron           12747  0 

```

---

### Post by wildmanne39 on 2012-01-03
Hi, give this a try please:
```
gksudo gedit /etc/modprobe.d/rt61pci.conf
```
Add a single line:
```
options rt61pci nohwcrypt=1
```
Proofread carefully, save and close gedit.
Then reboot.
Thanks

---

### Post by GoS_ on 2012-01-03
Thanks wildmanne39, but unfortunately nothing seemed to happen.  Also, the file was either empty or didn't exist.

---

### Post by simonmoon42 on 2012-01-03
Same issue with the rt61. I created the rt61pci.conf file, turned off hw crypt and still nothing. Not sure what to do now.

---

### Post by wildmanne39 on 2012-01-03
Hi, open this file please:
```
gksudo gedit /etc/modprobe.d/rt61pci.conf
```
and post the contents here so I can look at it and it should only be one line.
Thanks

---

### Post by GoS_ on 2012-01-05
Hi, here is the contents of the file
```
options rt61pci nohwcrypt=1

```

---

### Post by wildmanne39 on 2012-01-05
Hi, please post the output of the following commands:
```
nm-tool
```
```
sudo iwlist scan
```
the following command need to be ran with your wired connection unplugged.
```
sudo cat /var/log/syslog | grep -e rt6 -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by GoS_ on 2012-01-06
Hope this is helpful.  
```
bryce@behemoth:~$ nm-tool 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [NETGEAR] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        00:0E:2E:FF:D1:8E

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *NETGEAR:        Infra, 00:18:4D:9C:3C:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 80

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1D:92:34:6C:E7

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


bryce@behemoth:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:9C:3C:08
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f70afef1da
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101000EFF7F
                    IE: Unknown: DD1A00037F030100000000184D9C3C0802184D9C3C0864002C010E08

bryce@behemoth:~$ sudo cat /var/log/syslog | grep -e rt6 -e firmware -e wpa -e wlan -e etork | tail -n75
Jan  5 22:51:16 behemoth NetworkManager[819]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  5 22:51:17 behemoth wpa_supplicant[910]: Trying to authenticate with 00:18:4d:9c:3c:08 (SSID='NETGEAR' freq=2462 MHz)
Jan  5 22:51:17 behemoth NetworkManager[819]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  5 22:51:17 behemoth kernel: [41814.568670] wlan0: authenticate with 00:18:4d:9c:3c:08 (try 1)
Jan  5 22:51:18 behemoth kernel: [41814.768028] wlan0: authenticate with 00:18:4d:9c:3c:08 (try 2)
Jan  5 22:51:18 behemoth kernel: [41814.968020] wlan0: authenticate with 00:18:4d:9c:3c:08 (try 3)
Jan  5 22:51:18 behemoth kernel: [41815.168020] wlan0: authentication with 00:18:4d:9c:3c:08 timed out
Jan  5 22:51:19 behemoth NetworkManager[819]: <info> (wlan0): roamed from BSSID 00:18:4D:9C:3C:08 (NETGEAR) to (none) ((none))
Jan  5 22:51:32 behemoth NetworkManager[819]: <warn> (wlan0): link timed out.
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2592
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) starting connection 'NETGEAR'
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0/wireless): connection 'NETGEAR' requires no security.  No secrets needed.
Jan  5 22:51:32 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  5 22:51:32 behemoth avahi-daemon[821]: Withdrawing address record for 192.168.1.4 on wlan0.
Jan  5 22:51:32 behemoth avahi-daemon[821]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jan  5 22:51:32 behemoth avahi-daemon[821]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  5 22:51:35 behemoth NetworkManager[819]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  5 22:51:36 behemoth wpa_supplicant[910]: Trying to authenticate with 00:18:4d:9c:3c:08 (SSID='NETGEAR' freq=2462 MHz)
Jan  5 22:51:36 behemoth NetworkManager[819]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  5 22:51:36 behemoth kernel: [41833.621351] wlan0: authenticate with 00:18:4d:9c:3c:08 (try 1)
Jan  5 22:51:37 behemoth kernel: [41833.820018] wlan0: authenticate with 00:18:4d:9c:3c:08 (try 2)
Jan  5 22:51:37 behemoth wpa_supplicant[910]: Trying to associate with 00:18:4d:9c:3c:08 (SSID='NETGEAR' freq=2462 MHz)
Jan  5 22:51:37 behemoth wpa_supplicant[910]: Associated with 00:18:4d:9c:3c:08
Jan  5 22:51:37 behemoth wpa_supplicant[910]: CTRL-EVENT-CONNECTED - Connection to 00:18:4d:9c:3c:08 completed (reauth) [id=0 id_str=]
Jan  5 22:51:37 behemoth kernel: [41833.828716] wlan0: authenticated
Jan  5 22:51:37 behemoth kernel: [41833.829224] wlan0: associate with 00:18:4d:9c:3c:08 (try 1)
Jan  5 22:51:37 behemoth kernel: [41833.831047] wlan0: RX ReassocResp from 00:18:4d:9c:3c:08 (capab=0x421 status=0 aid=2)
Jan  5 22:51:37 behemoth kernel: [41833.831050] wlan0: associated
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> (wlan0): supplicant interface state: authenticating -> completed
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NETGEAR'.
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan  5 22:51:37 behemoth avahi-daemon[821]: Withdrawing address record for fe80::20e:2eff:feff:d18e on wlan0.
Jan  5 22:51:37 behemoth avahi-daemon[821]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::20e:2eff:feff:d18e.
Jan  5 22:51:37 behemoth avahi-daemon[821]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  5 22:51:37 behemoth NetworkManager[819]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  5 22:51:37 behemoth dhclient: Listening on LPF/wlan0/00:0e:2e:ff:d1:8e
Jan  5 22:51:37 behemoth dhclient: Sending on   LPF/wlan0/00:0e:2e:ff:d1:8e
Jan  5 22:51:37 behemoth dhclient: DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67
Jan  5 22:51:38 behemoth avahi-daemon[821]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::20e:2eff:feff:d18e.
Jan  5 22:51:38 behemoth avahi-daemon[821]: New relevant interface wlan0.IPv6 for mDNS.
Jan  5 22:51:38 behemoth avahi-daemon[821]: Registering new address record for fe80::20e:2eff:feff:d18e on wlan0.*.
Jan  5 22:51:39 behemoth NetworkManager[819]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan  5 22:51:39 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  5 22:51:39 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan  5 22:51:39 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  5 22:51:39 behemoth avahi-daemon[821]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jan  5 22:51:39 behemoth avahi-daemon[821]: New relevant interface wlan0.IPv4 for mDNS.
Jan  5 22:51:39 behemoth avahi-daemon[821]: Registering new address record for 192.168.1.4 on wlan0.IPv4.
Jan  5 22:51:40 behemoth NetworkManager[819]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan  5 22:51:40 behemoth NetworkManager[819]: <info> Policy set 'NETGEAR' (wlan0) as default for IPv4 routing and DNS.
Jan  5 22:51:40 behemoth NetworkManager[819]: <info> Activation (wlan0) successful, device activated.
Jan  5 22:51:40 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  5 22:51:40 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  5 22:51:47 behemoth kernel: [41844.324302] wlan0: no IPv6 routers present
Jan  5 22:51:57 behemoth NetworkManager[819]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan  5 22:51:57 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan  5 22:51:57 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jan  5 22:51:57 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  5 22:51:57 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  5 22:51:57 behemoth NetworkManager[819]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.

```
Thanks a lot for your help.

---

### Post by wildmanne39 on 2012-01-06
Hi, try this then reboot.
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Thanks

---

