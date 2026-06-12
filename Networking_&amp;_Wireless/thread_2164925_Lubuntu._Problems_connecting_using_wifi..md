---
title: "Lubuntu. Problems connecting using wifi."
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by FbFNHXC on 2013-08-02
Hello 

I installed Lubuntu 12.04 and it connects properly using ethernet cable but when trying to use wifi I select the network name, write the password but the system cannot connect.

Can anyone help? I really like Lubuntu because it gave a second life to my old laptop.

Here you can check the result of some commands:

```
adrian@ubuntu-arcade:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
adrian@ubuntu-arcade:~$ uname -a
Linux ubuntu-arcade 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:45:16 UTC 2013 i686 i686 i386 GNU/Linux
adrian@ubuntu-arcade:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c062 Logitech, Inc. LS1 Laser Mouse, corded
adrian@ubuntu-arcade:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
adrian@ubuntu-arcade:~$ lspci -nn|grep -i net
01:01.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
01:02.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 8b)
adrian@ubuntu-arcade:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:20:e8:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:e0001000-e0001fff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 8b
       serial: 00:40:d0:70:5f:10
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.1.37 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:3 ioport:c000(size=256) memory:e0000000-e00000ff
adrian@ubuntu-arcade:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

adrian@ubuntu-arcade:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:40:d0:70:5f:10  
          Direc. inet:192.168.1.37  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::240:d0ff:fe70:5f10/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:16048 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:8568 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:18931347 (18.9 MB)  TX bytes:1478221 (1.4 MB)
          Interrupción:3 Dirección base: 0xc000 

eth1      Link encap:Ethernet  direcciónHW 00:12:f0:20:e8:b0  
          Dirección inet6: fe80::212:f0ff:fe20:e8b0/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:13 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:3530 (3.5 KB)
          Interrupción:11 Dirección base: 0xc000 Memoria:e0001000-e0001fff 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:521 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:521 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:53435 (53.4 KB)  TX bytes:53435 (53.4 KB)

adrian@ubuntu-arcade:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39826  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
i915                  428021  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146210  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
psmouse                96718  0 
bnep                   17830  2 
parport_pc             32114  0 
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm                   197641  3 i915,drm_kms_helper
ppdev                  12849  0 
bluetooth             158479  10 rfcomm,bnep
serio_raw              13027  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14040  2 ipw2200,libipw
shpchp                 32265  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
via_rhine              27413  0 
```

Thanks in advance.

Adrián

---

### Post by GwL3eNC on 2013-08-02
Hi,

please excuse me, but which password do yout take. I dont know how familiar you are with this. Do you  take it from
your router or are you trying to take your Linux password?

In the file /var/log/syslog you can evtl find some answers. It's long and
i would take 

sudo gedit /var/log/syslog | grep eth1
or
sudo gedit /var/log/syslog | grep NetworkManager

if you use it. 
Also take care of a typeing errror in your password.

Ps. i have never seen such an ESSID :pg\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A

---

### Post by praseodym on 2013-08-02
The ESSID looks like a "hidden" network. Any chance to broadcast it (hiding NWs is not equal to more security!). Please also show
```

iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```
If "iwlist chan" shows only 11 channels, then change the channel to a fixed one between 1-11

---

### Post by slw210 on 2013-08-02
In the future, seperate your results per command. Makes it easier to go through.

Example:

my command

```
Results go Here
```

my 2nd command

```
Results go Here
```

Is wireless activated in the BIOS and turned on, there is usually a switch or F key to turn on off?

Might help to know what Laptop.

---

### Post by FbFNHXC on 2013-08-04
Hello and thanks for your interest

I am using the router password. I use the wifi in other devices at home without any issue at all. 

This is the result of the commands you proposed:

cat /var/log/syslog | grep eth1
```

Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth1, iface: eth1)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth1, iface: eth1): no ifupdown configuration found.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): using WEXT for WiFi device control
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): now managed
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): bringing up device.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): preparing device.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): deactivating device (reason 'managed') [2]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): supplicant interface state: starting -> ready
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): supplicant interface state: ready -> inactive
Aug  4 12:07:46 ubuntu-arcade avahi-daemon[745]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::212:f0ff:fe20:e8b0.
Aug  4 12:07:46 ubuntu-arcade avahi-daemon[745]: New relevant interface eth1.IPv6 for mDNS.
Aug  4 12:07:46 ubuntu-arcade avahi-daemon[745]: Registering new address record for fe80::212:f0ff:fe20:e8b0 on eth1.*.

```

cat /var/log/syslog | grep NetworkManager
```

Aug  4 12:07:44 ubuntu-arcade kernel: [   19.230570] type=1400 audit(1375610863.095:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> DNS: loaded plugin dnsmasq
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: init!
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: update_system_hostname
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPluginIfupdown: management mode: unmanaged
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth1, iface: eth1)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/net/eth1, iface: eth1): no ifupdown configuration found.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:02.0/net/eth0, iface: eth0)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:02.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: end _init.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    Ifupdown: get unmanaged devices count: 0
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: (150626080) ... get_connections.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    SCPlugin-Ifupdown: (150626080) ... get_connections (managed=false): return empty list.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]:    Ifupdown: get unmanaged devices count: 0
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> modem-manager is now available
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/ieee80211/phy0/rfkill0) (driver (unknown))
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> Networking is enabled by state file
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): using WEXT for WiFi device control
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): now managed
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): bringing up device.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): preparing device.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): deactivating device (reason 'managed') [2]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): carrier is OFF
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): new Ethernet device (driver: 'via-rhine' ifindex: 2)
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): now managed
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): bringing up device.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): preparing device.
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> Added default wired connection 'Conexión cableada 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:02.0/net/eth0
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> wpa_supplicant started
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): supplicant interface state: starting -> ready
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <info> (eth1): supplicant interface state: ready -> inactive
Aug  4 12:07:44 ubuntu-arcade NetworkManager[735]: <warn> Trying to remove a non-existant call id.
Aug  4 12:07:46 ubuntu-arcade kernel: [   22.213215] type=1400 audit(1375610866.079:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=805 comm="apparmor_parser"
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> (eth0): carrier now ON (device state 20)
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Auto-activating connection 'Conexión cableada 1'.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) starting connection 'Conexión cableada 1'
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> dhclient started with pid 1249
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Beginning IP6 addrconf.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug  4 12:09:30 ubuntu-arcade NetworkManager[735]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info> (eth0): DHCPv4 state changed preinit -> bound
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info>   address 192.168.1.37
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info>   prefix 24 (255.255.255.0)
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info>   gateway 192.168.1.1
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info>   nameserver '80.58.61.250'
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info>   nameserver '80.58.61.254'
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info>   domain name 'lan'
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug  4 12:09:31 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug  4 12:09:32 ubuntu-arcade NetworkManager[735]: <info> DNS: starting dnsmasq...
Aug  4 12:09:32 ubuntu-arcade NetworkManager[735]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug  4 12:09:32 ubuntu-arcade NetworkManager[735]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug  4 12:09:32 ubuntu-arcade NetworkManager[735]: <info> Policy set 'Conexión cableada 1' (eth0) as default for IPv4 routing and DNS.
Aug  4 12:09:32 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) successful, device activated.
Aug  4 12:09:32 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Aug  4 12:09:53 ubuntu-arcade NetworkManager[735]: <info> (eth0): IP6 addrconf timed out or failed.
Aug  4 12:09:53 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug  4 12:09:53 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug  4 12:09:53 ubuntu-arcade NetworkManager[735]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

Honestly I do not know why my ESSID looks that way but it is not a hidden network is named "OPTACCESS".

The results of the commands:

iwlist chan
```

eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Channel:0

```

sudo iwlist scan
```

eth1      Scan completed :
          Cell 01 - Address: 00:26:5B:45:A1:28
                    ESSID:"ONOA120"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 584ms ago
          Cell 02 - Address: A0:21:B7:5A:25:D2
                    ESSID:"ONO25D2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1300ms ago
          Cell 03 - Address: 00:A0:26:7C:55:8C
                    ESSID:"OPTACCESS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=75/100  Signal level=-54 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 136ms ago
          Cell 04 - Address: 00:19:70:69:E1:E1
                    ESSID:"Orange-7cda"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 60ms ago
          Cell 05 - Address: 64:68:0C:4C:8F:E6
                    ESSID:"WLAN_8FE3"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 472ms ago
          Cell 06 - Address: 64:16:F0:E0:24:93
                    ESSID:"vodafone2492"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 10156ms ago
          Cell 07 - Address: 00:01:38:F8:A6:22
                    ESSID:"carmen"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    Extra: Last beacon: 1892ms ago
          Cell 08 - Address: 40:4A:03:9E:D3:22
                    ESSID:"WLAN_64"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 372ms ago
          Cell 09 - Address: 00:01:38:F8:A6:23
                    ESSID:"ONO0801"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1892ms ago
          Cell 10 - Address: 00:1A:2B:19:02:1B
                    ESSID:"JAZZTEL_B4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 16ms ago
          Cell 11 - Address: BC:14:01:0D:22:78
                    ESSID:"angkor"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-65 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1820ms ago
          Cell 12 - Address: 88:03:55:03:EE:86
                    ESSID:"Orange-EE84"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 328ms ago
          Cell 13 - Address: 00:1A:2B:8E:FF:BF
                    ESSID:"WLAN_C5FD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1968ms ago
          Cell 14 - Address: 70:71:BC:CF:21:ED
                    ESSID:"ONO240467"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=23/100  Signal level=-85 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3560ms ago
          Cell 15 - Address: E0:91:53:0A:A1:47
                    ESSID:"WLAN_57"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    Extra: Last beacon: 2692ms ago
          Cell 16 - Address: 64:68:0C:6C:E0:B3
                    ESSID:"Wifi 2013"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 324ms ago
          Cell 17 - Address: 38:72:C0:45:B4:F5
                    ESSID:"JAZZTEL_B4F5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1312ms ago
          Cell 18 - Address: 00:01:38:F8:8B:F6
                    ESSID:"ONO9388"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    Extra: Last beacon: 16ms ago
          Cell 19 - Address: 00:01:38:F8:8B:F7
                    ESSID:"ONO0611"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 16ms ago

```

cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search lan

```

As you see there are only 11 channels but I do not know how to set a fixed channel.

And finally the wifi is activated at boot time.

Thanks again.

Adrián.

---

### Post by praseodym on 2013-08-04
Check the router manual how to enter the router interface

---

