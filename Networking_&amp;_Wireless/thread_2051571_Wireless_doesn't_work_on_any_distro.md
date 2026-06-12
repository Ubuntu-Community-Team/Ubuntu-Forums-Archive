---
title: "Wireless doesn't work on any distro"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by PPamaterasu on 2012-09-01
And when I say any distro, it's any distro.

I came back home from vacations, from USA I came back to Canadá, I tried wireless and nothing. I'm a slave of the cable. I was using Mint, then tried live CD's of Ubuntu, Mageia and Fedora and nothing. Installed Ubuntu, and nothing... 

GUYS: I now some things are in SPANISH but I think you will understand anyway

DMESG

```
miguel@miguel-Satellite-C650:~$ dmesg
[  356.944100] wlan0: disassociating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  356.978617] cfg80211: All devices are disconnected, going to restore regulatory settings
[  356.978628] cfg80211: Restoring regulatory settings
[  356.978669] cfg80211: Calling CRDA to update world regulatory domain
[  356.980347] wlan0: deauthenticating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  356.986786] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  356.986795] cfg80211: World regulatory domain updated:
[  356.986799] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  356.986806] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  356.986812] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  356.986818] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  356.986824] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  356.986829] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  357.847188] wlan0: authenticate with 5c:d9:98:6b:f3:7c (try 1)
[  357.848823] wlan0: authenticated
[  357.849310] wlan0: associate with 5c:d9:98:6b:f3:7c (try 1)
[  357.853155] wlan0: RX ReassocResp from 5c:d9:98:6b:f3:7c (capab=0x431 status=0 aid=1)
[  357.853166] wlan0: associated
[  367.845909] wlan0: disassociating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  367.888953] cfg80211: All devices are disconnected, going to restore regulatory settings
[  367.888964] cfg80211: Restoring regulatory settings
[  367.889004] cfg80211: Calling CRDA to update world regulatory domain
[  367.890692] wlan0: deauthenticating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  367.898292] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  367.898301] cfg80211: World regulatory domain updated:
[  367.898305] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  367.898312] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  367.898318] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  367.898324] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  367.898330] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  367.898335] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  368.757524] wlan0: authenticate with 5c:d9:98:6b:f3:7c (try 1)
[  368.759100] wlan0: authenticated
[  368.759418] wlan0: associate with 5c:d9:98:6b:f3:7c (try 1)
[  368.763174] wlan0: RX ReassocResp from 5c:d9:98:6b:f3:7c (capab=0x431 status=0 aid=1)
[  368.763186] wlan0: associated
[  378.755418] wlan0: disassociating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  378.799330] cfg80211: All devices are disconnected, going to restore regulatory settings
[  378.799346] cfg80211: Restoring regulatory settings
[  378.799384] cfg80211: Calling CRDA to update world regulatory domain
[  378.801182] wlan0: deauthenticating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  378.807139] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  378.807148] cfg80211: World regulatory domain updated:
[  378.807152] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  378.807159] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  378.807165] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  378.807171] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  378.807177] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  378.807182] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  386.932175] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  388.126989] wlan0: authenticate with 5c:d9:98:6b:f3:7c (try 1)
[  388.129321] wlan0: authenticated
[  388.129640] wlan0: associate with 5c:d9:98:6b:f3:7c (try 1)
[  388.140295] wlan0: deauthenticated from 5c:d9:98:6b:f3:7c (Reason: 2)
miguel@miguel-Satellite-C650:~$ 
miguel@miguel-Satellite-C650:~$ dmesg
[  356.944100] wlan0: disassociating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  356.978617] cfg80211: All devices are disconnected, going to restore regulatory settings
[  356.978628] cfg80211: Restoring regulatory settings
[  356.978669] cfg80211: Calling CRDA to update world regulatory domain
[  356.980347] wlan0: deauthenticating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  356.986786] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  356.986795] cfg80211: World regulatory domain updated:
[  356.986799] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  356.986806] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  356.986812] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  356.986818] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  356.986824] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  356.986829] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  357.847188] wlan0: authenticate with 5c:d9:98:6b:f3:7c (try 1)
[  357.848823] wlan0: authenticated
[  357.849310] wlan0: associate with 5c:d9:98:6b:f3:7c (try 1)
[  357.853155] wlan0: RX ReassocResp from 5c:d9:98:6b:f3:7c (capab=0x431 status=0 aid=1)
[  357.853166] wlan0: associated
[  367.845909] wlan0: disassociating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  367.888953] cfg80211: All devices are disconnected, going to restore regulatory settings
[  367.888964] cfg80211: Restoring regulatory settings
[  367.889004] cfg80211: Calling CRDA to update world regulatory domain
[  367.890692] wlan0: deauthenticating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  367.898292] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  367.898301] cfg80211: World regulatory domain updated:
[  367.898305] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  367.898312] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  367.898318] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  367.898324] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  367.898330] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  367.898335] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  368.757524] wlan0: authenticate with 5c:d9:98:6b:f3:7c (try 1)
[  368.759100] wlan0: authenticated
[  368.759418] wlan0: associate with 5c:d9:98:6b:f3:7c (try 1)
[  368.763174] wlan0: RX ReassocResp from 5c:d9:98:6b:f3:7c (capab=0x431 status=0 aid=1)
[  368.763186] wlan0: associated
[  378.755418] wlan0: disassociating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  378.799330] cfg80211: All devices are disconnected, going to restore regulatory settings
[  378.799346] cfg80211: Restoring regulatory settings
[  378.799384] cfg80211: Calling CRDA to update world regulatory domain
[  378.801182] wlan0: deauthenticating from 5c:d9:98:6b:f3:7c by local choice (reason=3)
[  378.807139] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  378.807148] cfg80211: World regulatory domain updated:
[  378.807152] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  378.807159] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  378.807165] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  378.807171] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  378.807177] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  378.807182] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  386.932175] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  388.126989] wlan0: authenticate with 5c:d9:98:6b:f3:7c (try 1)
[  388.129321] wlan0: authenticated
[  388.129640] wlan0: associate with 5c:d9:98:6b:f3:7c (try 1)
[  388.140295] wlan0: deauthenticated from 5c:d9:98:6b:f3:7c (Reason: 2)
miguel@miguel-Satellite-C650:~$ 

```IWconfig

```
miguel@miguel-Satellite-C650:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


```IFCONFIG
```
eth0      Link encap:Ethernet  direcciónHW 00:26:6c:c9:36:54  
          Direc. inet:192.168.0.100  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::226:6cff:fec9:3654/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:43927 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:31493 errores:0 perdidos:0 overruns:0 carrier:3
          colisiones:0 long.colaTX:1000 
          Bytes RX:55533157 (55.5 MB)  TX bytes:4184059 (4.1 MB)
          Interrupción:44 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:2287 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2287 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:270950 (270.9 KB)  TX bytes:270950 (270.9 KB)

wlan0     Link encap:Ethernet  direcciónHW e0:ca:94:12:4b:e6  
          Dirección inet6: fe80::e2ca:94ff:fe12:4be6/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:218 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:216 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:24634 (24.6 KB)  TX bytes:33912 (33.9 KB)

```NM-TOOL
```
miguel@miguel-Satellite-C650:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        E0:CA:94:12:4B:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ROGERSD2FE:      Infra, 00:60:64:4D:50:C8, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    dlink:           Infra, 00:19:5B:D6:12:94, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA
    BELL143:         Infra, 00:23:51:4F:E6:99, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    Hellink666:      Infra, 00:18:39:49:93:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA
    gallegosnet:     Infra, 5C:D9:98:6B:F3:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 99 WPA
    linksys:         Infra, 00:18:F8:5E:1C:A9, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    belkin.3664:     Infra, 94:44:52:C5:B6:64, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2


- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:6C:C9:36:54

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


miguel@miguel-Satellite-C650:~$ 

```SUDO LSHW -C NETWORK
```
miguel@miguel-Satellite-C650:~$ sudo lshw -C network
[sudo] password for miguel: 
  *-network               
       descripción: Ethernet interface
       producto: AR8152 v2.0 Fast Ethernet
       fabricante: Atheros Communications Inc.
       id físico: 0
       información del bus: pci@0000:01:00.0
       nombre lógico: eth0
       versión: c1
       serie: 00:26:6c:c9:36:54
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       recursos: irq:44 memoria:c0500000-c053ffff ioport:3000(size=128)
  *-network
       descripción: Interfaz inalámbrica
       producto: RTL8188CE 802.11b/g/n WiFi Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: wlan0
       versión: 01
       serie: e0:ca:94:12:4b:e6
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=rtl8192ce driverversion=3.2.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:17 ioport:2000(size=256) memoria:c0400000-c0403fff
miguel@miguel-Satellite-C650:~$ 

```

LSPCI
```
miguel@miguel-Satellite-C650:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
miguel@miguel-Satellite-C650:~$ 

```
The modem is a D-LINK DIR 601

---

### Post by jmate24 on 2012-09-01
how long have you had the modem? if it is over a year then call your isp to replace it.
how long have you had the wireless card? if it is more than 5 years I suggest you buy a new one.

it also might be the driver that may have updated while you were away. then again it might be the modem you could call your isp for assistance. 

it mainlly looks like it is your modem.

your wifi card looks fine.

best of luck.

jmate24

---

### Post by WishForHelp on 2012-09-01
I feel your pain, so far I'm testing it with Ubuntu & Mint, no luck either, and if I see your post, I don't think I need to waste my time anymore with searching/downloading other distro's, which I was planning to do now. ](*,)

---

### Post by PPamaterasu on 2012-09-01
No way. It was the password. After a week of suffering with the cable, today my papa came back from his trip to Colombia. Hi had never used GNU/Linux before, but looking at the network manager settings he discovered the password had the numbers switched of places. (the same numbers, but where they where not suposed to be)

Anyway, thank you for your help.

**Thank God it was only the password**

---

