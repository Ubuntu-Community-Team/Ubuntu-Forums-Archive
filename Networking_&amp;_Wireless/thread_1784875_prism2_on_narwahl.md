---
title: "prism2 on narwahl"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by wlanctl-ng on 2011-06-17
my thanks in advance.  i have a prism2 wireless card:
model: SMC2632W V.3
Part No: 99-012084-024

when i upgraded to narwahl i lost my previous wireless configuration, which i believe used linux-wlan-ng, i can't find the howto i used before, and linux-wlan-ng seems broken


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:04:8f:34  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe04:8f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3242577 (3.2 MB)  TX bytes:715166 (715.1 KB)
          Interrupt:11 Base address:0x6c00 

eth1      Link encap:Ethernet  HWaddr 00:04:e2:48:77:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: FF:00:00:00:00:00   
          Bit Rate:11 Mb/s   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


NetworkManager file

[connection]
id=flight
uuid=b550fcef-44f6-49d7-b64e-efdd7d6968d1
type=802-11-wireless
autoconnect=false

[802-11-wireless]
ssid=<removed>
mode=infrastructure
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=none
auth-alg=open
wep-key0=<removed>
wep-key-type=1

[ipv4]
method=auto

[ipv6]
method=ignore


lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]


rfkill list all
<nothing>


lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  78 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
atmel_cs               12735  1 
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
atmel                  40438  1 atmel_cs
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
binfmt_misc            13213  1 
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  1 atmel_cs
dcdbas                 14054  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
serio_raw              12990  0 
intel_rng              12700  0 
parport_pc             32111  1 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
ch7006                 22545  1 
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  2 ch7006,nouveau
drm                   180037  5 ch7006,nouveau,ttm,drm_kms_helper
firewire_ohci          31504  0 
3c59x                  37398  0 
firewire_core          56138  1 firewire_ohci
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
floppy                 60032  0 
crc_itu_t              12627  1 firewire_core


i installed the firmware-nonfree

modprobe -c | grep prism2
alias usb:v03F3p0020d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0411p0016d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0411p0027d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0411p0044d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v045Ep006Ed*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v049Fp0033d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v04BBp0922d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v04F1p3009d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0543p0F01d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v066Bp2212d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v066Bp2213d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v067Cp1022d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v07AAp0012d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v083Ap3503d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0846p4110d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v08DEp7A01d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0967p0204d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v09AAp3642d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0B3Bp1601d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0B3Bp1602d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0BAFp00EBd*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0BB2p0302d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0CDEp0002d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0CDEp0005d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v0D8Ep7A01d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v124Ap168Bd*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v124Ap4017d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v1668p0408d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v1668p0421d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v1668p6106d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v1915p2236d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v2001p3700d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v2001p3702d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v2821p3300d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v2821p3300d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v2C02p14EAd*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v413Cp8100d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v50C2p4013d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v8086p1111d*dc*dsc*dp*ic*isc*ip* prism2_usb
alias usb:v9016p182Dd*dc*dsc*dp*ic*isc*ip* prism2_usb
alias symbol:prism2_update_comms_qual hostap

sudo lshw

*-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:04:e2:48:77:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=atmel_cs multicast=yes wireless=IEEE 802.11-DS

---

### Post by blackmail on 2011-06-17
sorry i am not much of a wireless guru...

But here are some links you might want to visit in your endeavour:

[LinuxQuestions - SMC driver]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/smc2632w-driver-confusion-172533/")

[Ubuntu - Wireless toubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

[Atmel]("http://atmelwlandriver.sourceforge.net/downloads.html")

[SMC Downloads]("http://www.smc.com/index.cfm?event=downloads.searchResults&localeCode=EN_USA&productCategory=9&partNumber=2709&modelNumber=413&knowsPartNumber=false&userPartNumber=")


Hope one of these can help you

---

### Post by wlanctl-ng on 2011-06-17
thanks, i think i'll need more help.  i followed the troubleshooting guide before, but forgot to include this:

sudo nm-tool
[sudo] password for chris: 

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            3c59x
  State:             connected
  Default:           yes
  HW Address:        00:08:74:04:8F:34

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            atmel_cs
  State:             disconnected
  Default:           no
  HW Address:        00:04:E2:48:77:ED

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 


the SMC driver download is wlan-ng, but maybe it works better than the ubuntu/apt-get version.  i'll try it if no one else responds

edit:

also iwlist scan gives: eth1      No scan results

and i think the device is missing in lspci

---

### Post by chili555 on 2011-06-17
> and i think the device is missing in lspciHow about in:```
lspcmcia -nn
```With the ethernet cable detached, do you see networks in Network Manager? Why do you think it's a prism2? It's pretty clearly an Atmel. May I see:```
dmesg | grep -e atmel -e eth1
```Thanks.

---

### Post by wlanctl-ng on 2011-06-17
sudo lspcmcia -nn
lspcmcia: invalid option -- 'n'
pcmciautils 015
Copyright (C) 2004-2005 Dominik Brodowski, (C) 1999 David A. Hinds
Report errors and bugs to <linux-pcmcia@lists.infradead.org>, please.
invalid or unknown argument
Usage: pccardctl COMMAND
Supported commands are:
    ls
    insert
    eject
    suspend
    resume
    reset
    info
    status
    config
    ident
chris@freebird:~$ sudo lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:01.0)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:01.1)
Socket 1 Device 0:    [atmel_cs]        (bus ID: 1.0)


i do not see networks in the network manager.  i think it's prism2 from some of the documentation i've seen.  for example wlan-ng.conf has:

card "SMC 2632W 11Mbps 802.11b WLAN Card"
   version "SMC", "SMC2632W", "Version 01.02"
   bind "prism2_cs"


... which may be part of the problem with wlan-ng (only loads prism2_usb).  and may also be part of the problem here (maybe ubuntu is not identifying the card correctly, tf driver?)

dmesg | grep -e atmel -e eth1
[   22.152061] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:48:77:ed
[   22.191877] eth1: card type is unknown: assuming at76c502 firmware is OK.
[   22.191887] eth1: if not, use the firmware= module parameter.
[   22.536155] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  508.140684] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1224.840117] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:48:77:ed
[ 1224.931034] eth1: card type is unknown: assuming at76c502 firmware is OK.
[ 1224.931043] eth1: if not, use the firmware= module parameter.
[ 1224.984360] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by chili555 on 2011-06-17
Oops! I goofed. Sorry; how about:```
sudo lspcmcia ident
ls /lib/firmware | grep atmel
```If the latter command shows that the firmware is missing, which I sort of doubt, please do:```
sudo apt-get install linux-firmware
```If you detach the ethernet cable and do:```
sudo ifconfig eth0 down
```Does Network Manager start the wireless, that is, do networks appears when you click the icon?

---

### Post by wlanctl-ng on 2011-06-17
sudo lspcmcia ident
[sudo] password for chris: 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:01.0)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:01.1)
Socket 1 Device 0:    [atmel_cs]        (bus ID: 1.0)

ls /lib/firmware | grep atmel
atmel_at76c502_3com.bin
atmel_at76c502.bin
atmel_at76c502d.bin
atmel_at76c502e.bin
atmel_at76c504_2958.bin
atmel_at76c504a_2958.bin
atmel_at76c504.bin
atmel_at76c506.bin


networks do not show up after detach and eth0 down

---

### Post by chili555 on 2011-06-17
With the ethernet cable detached, please do:```
sudo iwlist eth1 scan 
```If there is a warning or error message, please post it as it will be informative. Also, please post:```
sudo cat /var/log/syslog | grep -e atmel -e eth1 -e etwork | tail -n25
```Thanks.

---

### Post by wlanctl-ng on 2011-06-17
eth1      No scan results

sudo cat /var/log/syslog | grep -e atmel -e eth1 -e etwork | tail -n25
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 17 13:38:44 freebird NetworkManager[427]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 17 13:38:44 freebird NetworkManager[427]: <info> dhclient started with pid 2832
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 17 13:38:44 freebird NetworkManager[427]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 17 13:38:44 freebird NetworkManager[427]: <info> (eth0): DHCPv4 state changed preinit -> expire
Jun 17 13:38:44 freebird NetworkManager[427]: <info> (eth0): DHCPv4 state changed expire -> preinit
Jun 17 13:38:44 freebird NetworkManager[427]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 17 13:38:44 freebird NetworkManager[427]: <info>   address 192.168.1.4
Jun 17 13:38:44 freebird NetworkManager[427]: <info>   prefix 24 (255.255.255.0)
Jun 17 13:38:44 freebird NetworkManager[427]: <info>   gateway 192.168.1.1
Jun 17 13:38:44 freebird NetworkManager[427]: <info>   hostname 'dhcppc2'
Jun 17 13:38:44 freebird NetworkManager[427]: <info>   nameserver '192.168.1.1'
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Scheduling stage 5
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Done scheduling stage 5
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 17 13:38:44 freebird NetworkManager[427]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 17 13:38:45 freebird NetworkManager[427]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun 17 13:38:45 freebird NetworkManager[427]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 17 13:38:45 freebird NetworkManager[427]: <info> Activation (eth0) successful, device activated.
Jun 17 13:38:45 freebird NetworkManager[427]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

---

### Post by chili555 on 2011-06-17
Off to take Mrs. Chili to supper; I'll check in later. Let's try:```
sudo cat /var/log/syslog | grep -e atmel -e eth1
```You have a stubborn card there!

---

### Post by wlanctl-ng on 2011-06-17
sudo cat /var/log/syslog | grep -e atmel -e eth1
Jun 17 08:38:11 freebird kernel: [   23.742676] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:48:77:ed
Jun 17 08:38:11 freebird NetworkManager[437]: <error> [1308325091.236043] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 95)
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): driver does not support SSID scans (scan_capa 0x00).
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): new 802.11 WiFi device (driver: 'atmel_cs' ifindex: 3)
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): now managed
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): bringing up device.
Jun 17 08:38:11 freebird kernel: [   23.899621] eth1: card type is unknown: assuming at76c502 firmware is OK.
Jun 17 08:38:11 freebird kernel: [   23.899631] eth1: if not, use the firmware= module parameter.
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): preparing device.
Jun 17 08:38:11 freebird NetworkManager[437]: <info> (eth1): deactivating device (reason: 2).
Jun 17 08:38:11 freebird kernel: [   24.168233] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 17 08:38:11 freebird NetworkManager[437]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1)
Jun 17 08:38:11 freebird NetworkManager[437]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun 17 08:38:12 freebird NetworkManager[437]: <info> (eth1): supplicant interface state:  starting -> ready
Jun 17 08:38:12 freebird NetworkManager[437]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Jun 17 10:26:25 freebird kernel: [   22.289463] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:48:77:ed
Jun 17 10:26:25 freebird NetworkManager[435]: <error> [1308331585.694542] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 95)
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): driver does not support SSID scans (scan_capa 0x00).
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): new 802.11 WiFi device (driver: 'atmel_cs' ifindex: 3)
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): now managed
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): bringing up device.
Jun 17 10:26:25 freebird kernel: [   22.361280] eth1: card type is unknown: assuming at76c502 firmware is OK.
Jun 17 10:26:25 freebird kernel: [   22.361290] eth1: if not, use the firmware= module parameter.
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): preparing device.
Jun 17 10:26:25 freebird NetworkManager[435]: <info> (eth1): deactivating device (reason: 2).
Jun 17 10:26:25 freebird kernel: [   22.577133] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 17 10:26:25 freebird NetworkManager[435]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1)
Jun 17 10:26:25 freebird NetworkManager[435]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun 17 10:26:26 freebird NetworkManager[435]: <info> (eth1): supplicant interface state:  starting -> ready
Jun 17 10:26:26 freebird NetworkManager[435]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Jun 17 10:54:32 freebird kernel: [   22.152061] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:48:77:ed
Jun 17 10:54:32 freebird NetworkManager[427]: <error> [1308333272.528336] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 95)
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): driver does not support SSID scans (scan_capa 0x00).
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): new 802.11 WiFi device (driver: 'atmel_cs' ifindex: 3)
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): now managed
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): bringing up device.
Jun 17 10:54:32 freebird kernel: [   22.191877] eth1: card type is unknown: assuming at76c502 firmware is OK.
Jun 17 10:54:32 freebird kernel: [   22.191887] eth1: if not, use the firmware= module parameter.
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): preparing device.
Jun 17 10:54:32 freebird NetworkManager[427]: <info> (eth1): deactivating device (reason: 2).
Jun 17 10:54:32 freebird NetworkManager[427]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1)
Jun 17 10:54:32 freebird kernel: [   22.536155] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 17 10:54:32 freebird NetworkManager[427]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun 17 10:54:33 freebird NetworkManager[427]: <info> (eth1): supplicant interface state:  starting -> ready
Jun 17 10:54:33 freebird NetworkManager[427]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Jun 17 11:02:38 freebird kernel: [  508.140684] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 17 11:13:10 freebird avahi-daemon[423]: Withdrawing workstation service for eth1.
Jun 17 11:13:10 freebird NetworkManager[427]: <info> (eth1): now unmanaged
Jun 17 11:13:10 freebird NetworkManager[427]: <info> (eth1): device state change: 3 -> 1 (reason 36)
Jun 17 11:13:10 freebird NetworkManager[427]: <info> (eth1): cleaning up...
Jun 17 11:13:10 freebird NetworkManager[427]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1)
Jun 17 11:13:11 freebird wpa_supplicant[476]: Could not read interface eth1 flags: No such device
Jun 17 11:14:35 freebird kernel: [ 1224.840117] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:48:77:ed
Jun 17 11:14:35 freebird NetworkManager[427]: <error> [1308334475.268802] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 95)
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): driver does not support SSID scans (scan_capa 0x00).
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): new 802.11 WiFi device (driver: 'atmel_cs' ifindex: 4)
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): now managed
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): bringing up device.
Jun 17 11:14:35 freebird kernel: [ 1224.931034] eth1: card type is unknown: assuming at76c502 firmware is OK.
Jun 17 11:14:35 freebird kernel: [ 1224.931043] eth1: if not, use the firmware= module parameter.
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): preparing device.
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): deactivating device (reason: 2).
Jun 17 11:14:35 freebird NetworkManager[427]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1)
Jun 17 11:14:35 freebird kernel: [ 1224.984360] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 17 11:14:35 freebird NetworkManager[427]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.1/1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): supplicant interface state:  starting -> ready
Jun 17 11:14:35 freebird NetworkManager[427]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Jun 17 13:37:58 freebird kernel: [ 9827.976850] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by chili555 on 2011-06-17
> <error> [1308334475.268802] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 95)This looks scary, however, entries in syslog seem to proceed normally afterwards. On the other hand, this looks like a deal-killer:> <info> (eth1): driver does not support SSID scans (scan_capa 0x00).If the card won't see available networks, how can it connect; and it didn't when we tried:> eth1 No scan results
Let's try the manual method, although it is often difficult to do so with Network Manager running:```
sudo /etc/init.d/network-manager stop
sudo iwconfig eth1 essid <yourrouter>
sudo iwconfig eth1 key <yourWEPkey>
sudo dhclient eth1
```As before, any error or warning messages may be helpful, so please report them.

---

### Post by wlanctl-ng on 2011-06-17
sudo /etc/init.d/network-manager stop
[sudo] password for chris: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
network-manager stop/waiting
chris@freebird:~$ sudo iwconfig eth1 essid flight
chris@freebird:~$ sudo iwconfig eth1 key 
chris@freebird:~$ sudo dhclient eth1

took ~2 minutes - longer than normal

chris@freebird:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:04:8f:34  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe04:8f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106882695 (106.8 MB)  TX bytes:7448274 (7.4 MB)
          Interrupt:11 Base address:0x6c00 

eth1      Link encap:Ethernet  HWaddr 00:04:e2:48:77:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0xe100 

eth1:avahi Link encap:Ethernet  HWaddr 00:04:e2:48:77:ed  
          inet addr:169.254.10.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26528 (26.5 KB)  TX bytes:26528 (26.5 KB)

this is doesn't look right to me. for one, that address is not from my network.  and i'm not able to ping google with cable unplugged

---

### Post by chili555 on 2011-06-17
> chris@freebird:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:08:74:04:8f:34
inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0All this must be done with ethernet detached and eth0 down:```
sudo ifconfig eth0 down
```> chris@freebird:~$ sudo iwconfig eth1 key Is your network encrypted? Did you put the key in? Is it 10 or 26 characters?> eth1:avahi Link encap:Ethernet HWaddr 00:04:e2:48:77:ed
inet addr:169.254.10.30You are quite correct, this is a place-holder when the wireless router declined to give an IP address.

---

### Post by wlanctl-ng on 2011-06-17
i can try again, but should i "undo" anything?

there is a key, i removed it from the post.  i did mean to ask - does it require a 0x prefix?

---

### Post by chili555 on 2011-06-17
> there is a key, i removed it from the post. i did mean to ask - does it require a 0x prefixYou did the right thing! No 0x prefix required. Just detach the cable, take down eth0, stop NM and try again. I am going to take 53 aspirin and get some sleep. I may have nightmares about Atmel. Can you read and post the exact model and version of the SMC card?

---

### Post by wlanctl-ng on 2011-06-17
retry gave the same results

model: SMC2632W V.3
Part No: 99-012084-024

i'm pretty sure it's a driver problem and i'll have to use wlan-ng.  know anything about pcmcia-cs source code?

also, i think my old startup script was something like this:

#!/bin/bash
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset
mibattribute=dot11WEPDefaultKey0="<key>"
wlanctl-ng wlan0 lnxreq_autojoin ssid="flight" authtype="sharedkey"
sleep 2
dhclient wlan0

---

### Post by chili555 on 2011-06-18
I found this buried deep in the C code:> /* list of cards we know about and their firmware requirements.
   Go either by Manfid or version strings.
   Cards not in this list will need a firmware parameter to the module
   in all probability. Note that the SMC 2632 V2 and V3 have the same
   manfids, so we ignore those and use the version1 strings. */

static struct { 
	int manf, card;
	char *ver1;
	AtmelFWType firmware;
	char *name;
} card_table[] = {
	{ 0, 0, "WLAN/802.11b PC CARD", ATMEL_FW_TYPE_502D, "Actiontec 802CAT1" },  
	{ 0, 0, "ATMEL/AT76C502AR", ATMEL_FW_TYPE_502, "NoName-RFMD" }, 
	{ 0, 0, "ATMEL/AT76C502AR_D", ATMEL_FW_TYPE_502D, "NoName-revD" }, 
	{ 0, 0, "ATMEL/AT76C502AR_E", ATMEL_FW_TYPE_502E, "NoName-revE" },
	{ 0, 0, "ATMEL/AT76C504", ATMEL_FW_TYPE_504, "NoName-504" },
	{ 0, 0, "ATMEL/AT76C504A", ATMEL_FW_TYPE_504A_2958, "NoName-504a-2958" },
	{ 0, 0, "ATMEL/AT76C504_R", ATMEL_FW_TYPE_504_2958, "NoName-504-2958" },
	{ MANFID_3COM, 0x0620, NULL, ATMEL_FW_TYPE_502_3COM, "3com 3CRWE62092B" }, 
	{ MANFID_3COM, 0x0696, NULL, ATMEL_FW_TYPE_502_3COM, "3com 3CRSHPW196" }, 
	{ 0, 0, "SMC/2632W-V2", ATMEL_FW_TYPE_502, "SMC 2632W-V2" },
	[COLOR="Red"]{ 0, 0, "SMC/2632W", ATMEL_FW_TYPE_502D, "SMC 2632W-V3" },[/COLOR]
	{ 0xd601, 0x0007, NULL, ATMEL_FW_TYPE_502, "Sitecom WLAN-011" }, 
	{ 0x01bf, 0x3302, NULL, ATMEL_FW_TYPE_502E, "Belkin F5D6020-V2" }, 
	{ 0, 0, "BT/Voyager 1020 Laptop Adapter", ATMEL_FW_TYPE_502, "BT Voyager 1020" },
	{ 0, 0, "IEEE 802.11b/Wireless LAN PC Card", ATMEL_FW_TYPE_502, "Siemens Gigaset PC Card II" },
	{ 0, 0, "IEEE 802.11b/Wireless LAN Card S", ATMEL_FW_TYPE_504_2958, "Siemens Gigaset PC Card II" },
	{ 0, 0, "CNet/CNWLC 11Mbps Wireless PC Card V-5", ATMEL_FW_TYPE_502E, "CNet CNWLC-811ARL" },
	{ 0, 0, "Wireless/PC_CARD", ATMEL_FW_TYPE_502D, "Planet WL-3552" },
	{ 0, 0, "OEM/11Mbps Wireless LAN PC Card V-3", ATMEL_FW_TYPE_502, "OEM 11Mbps WLAN PCMCIA Card" },
	{ 0, 0, "11WAVE/11WP611AL-E", ATMEL_FW_TYPE_502E, "11WAVE WaveBuddy" },
	{ 0, 0, "LG/LW2100N", ATMEL_FW_TYPE_502E, "LG LW2100N 11Mbps WLAN PCMCIA Card" },
};
Your card wants 502D firmware. For some reason, it loads:> Jun 17 11:14:35 freebird kernel: [ 1224.931034] eth1: card type is unknown: [COLOR="Red"]assuming at76c502 firmware is OK[/COLOR].
Jun 17 11:14:35 freebird kernel: [ 1224.931043] eth1: if not, use the firmware= module parameter.Let's see if specifying the firmware helps us. Please do:```
sudo gedit /etc/modprobe.d/atmel.conf
```A new blank file will open. Add one line:```
options atmel firmware=atmel_at76c502d.bin
```Proofread carefully, save and close gedit. Detach the ethernet cable, reboot and see if it connects. If not, please let us see:```
sudo cat /var/log/syslog | grep -e atmel -e eth1
```We will be interested in the firmware loading lines. If the syslog is lengthy, just post the last twenty lines or so.

---

### Post by wlanctl-ng on 2011-06-18
you are a genie ... that did it!  many thanks!

---

### Post by chili555 on 2011-06-18
Awesome! I am having a T-shirt printed today:> atmel d00dThanks; I love a mystery. You will have helped some searchers, too.

There is anothe 502d firmware called atmel_at76c502d-wpa.bin. I can only guess it allows connection to a WPA encrypted network. You could amend the conf file to:```
options atmel firmware=atmel_at76c502d-wpa.bin
```If it connects, then you have enhanced your security by stepping up to WPA; if not, simply revert to the version that you know works.

---

### Post by blackmail on 2011-06-19
> **chili555 said:**
> Awesome! I am having a T-shirt printed today:Thanks; I love a mystery. You will have helped some searchers, too.

There is anothe 502d firmware called atmel_at76c502d-wpa.bin. I can only guess it allows connection to a WPA encrypted network. You could amend the conf file to:```
options atmel firmware=atmel_at76c502d-wpa.bin
```If it connects, then you have enhanced your security by stepping up to WPA; if not, simply revert to the version that you know works.

I usually don't do this but Mr Chili, congratz on solving this problem!!!
This was a real pain in the @#$ type of problem...
*bow*

---

### Post by chili555 on 2011-06-19
Thank you for your very kind words. I was lucky that the developer did a good job of commenting the C file and I was able to see it on line. I hope it helps some searchers, too.

---

