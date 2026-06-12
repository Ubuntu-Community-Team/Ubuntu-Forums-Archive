---
title: "Lenovo thinkpad edge e520 wireless"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by Heiden on 2012-05-19
Hey everybody,

I recently received my Lenovo thinkpad edge e520. I put ubuntu 12.04 on it and everything worked out of the box except my wireless. It finds my network, but can't connect to it. Already tried putting on 11.10 to see if the problem was specific for 12.04, but no success. After a hours googling I haven't found a single solution, so in my desparation I'm turning to you :p
Some information:

nm-tool
> NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        74:E5:0B:AE:76:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    DOXENZO:         Infra, 00:0E:2E:C0:0D:55, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    linksys:         Infra, 00:25:9C:F4:2B:9C, Freq 2437 MHz, Rate 54 Mb/s, Strength 17


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:D0:AA:BD

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1



sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:d0:aa:bd
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.2.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:ae:76:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:44 memory:d1d00000-d1d01fff


dmesg
> [   17.452225] Copyright(c) 2003-2011 Intel Corporation
[   17.452295] iwlwifi 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.452325] iwlwifi 0000:08:00.0: setting latency timer to 64
[   17.452432] iwlwifi 0000:08:00.0: pci_resource_len = 0x00002000
[   17.452434] iwlwifi 0000:08:00.0: pci_resource_base = ffffc90005098000
[   17.452436] iwlwifi 0000:08:00.0: HW Revision ID = 0x0
[   17.452716] iwlwifi 0000:08:00.0: irq 44 for MSI/MSI-X
[   17.452826] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   17.452935] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   17.476116] iwlwifi 0000:08:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   17.476118] iwlwifi 0000:08:00.0: Device SKU: 0X50
[   17.476120] iwlwifi 0000:08:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   17.476135] iwlwifi 0000:08:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.716045] fbcon: inteldrmfb (fb0) is primary device
[   17.716137] Console: switching to colour frame buffer device 170x48
[   17.716161] fb0: inteldrmfb frame buffer device
[   17.716163] drm: registered panic notifier
[   17.772103] acpi device:43: registered as cooling_device4
[   17.772329] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   17.772393] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.772444] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.772593] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.772667] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.772702] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   17.881938] iwlwifi 0000:08:00.0: loaded firmware version 39.31.5.1 build 35138
[   17.882099] Registered led device: phy0-led
[   17.882133] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.952669] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.031111] init: failsafe main process (763) killed by TERM signal
[   18.484523] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.484590] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.662554] ppdev: user-space parallel port driver
[   18.825158] Bluetooth: Core ver 2.16
[   18.825175] NET: Registered protocol family 31
[   18.825177] Bluetooth: HCI device and connection manager initialized
[   18.825181] Bluetooth: HCI socket layer initialized
[   18.825183] Bluetooth: L2CAP socket layer initialized
[   18.825188] Bluetooth: SCO socket layer initialized
[   18.975169] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.975172] Bluetooth: BNEP filters: protocol multicast
[   19.025066] Bluetooth: RFCOMM TTY layer initialized
[   19.025074] Bluetooth: RFCOMM socket layer initialized
[   19.025076] Bluetooth: RFCOMM ver 1.11
[   19.185325] type=1400 audit(1337416624.236:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=846 comm="apparmor_parser"
[   19.185887] type=1400 audit(1337416624.236:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=846 comm="apparmor_parser"
[   19.302780] r8169 0000:02:00.0: eth0: link down
[   19.302792] r8169 0000:02:00.0: eth0: link down
[   19.303108] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.303368] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.304875] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   19.344629] type=1400 audit(1337416624.396:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=886 comm="apparmor_parser"
[   19.344983] type=1400 audit(1337416624.396:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=886 comm="apparmor_parser"
[   19.370288] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   19.438099] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.438612] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.809155] init: anacron main process (985) killed by TERM signal
[   21.030714] r8169 0000:02:00.0: eth0: link up
[   21.031238] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.583073] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[   21.585703] wlan0: authenticated
[   21.592290] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[   21.595895] wlan0: RX AssocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[   21.595910] wlan0: associated
[   21.600127] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.697232] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.874231] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   31.688305] eth0: no IPv6 routers present
[   32.615835] wlan0: no IPv6 routers present
[   52.562219] cfg80211: All devices are disconnected, going to restore regulatory settings
[   52.562225] cfg80211: Restoring regulatory settings
[   52.562229] cfg80211: Calling CRDA to update world regulatory domain
[   52.565656] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   52.565661] cfg80211: World regulatory domain updated:
[   52.565662] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   52.565665] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.565667] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   52.565669] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   52.565670] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.565672] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   53.113452] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[   53.115937] wlan0: authenticated
[   53.116287] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[   53.118818] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[   53.118821] wlan0: associated
[   67.365288] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[   67.433863] cfg80211: All devices are disconnected, going to restore regulatory settings
[   67.433871] cfg80211: Restoring regulatory settings
[   67.433893] cfg80211: Calling CRDA to update world regulatory domain
[   67.444432] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   67.444437] cfg80211: World regulatory domain updated:
[   67.444439] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   67.444443] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   67.444446] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   67.444449] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   67.444452] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   67.444454] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.767779] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[   71.769721] wlan0: authenticated
[   71.769998] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[   71.772581] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[   71.772588] wlan0: associated
[   82.225548] wlan0: no IPv6 routers present
[  102.541537] cfg80211: All devices are disconnected, going to restore regulatory settings
[  102.541544] cfg80211: Restoring regulatory settings
[  102.541548] cfg80211: Calling CRDA to update world regulatory domain
[  102.547032] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  102.547044] cfg80211: World regulatory domain updated:
[  102.547049] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  102.547058] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  102.547067] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  102.547075] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  102.547083] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  102.547090] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  103.075352] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  103.078051] wlan0: authenticated
[  103.078367] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  103.080941] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  103.080949] wlan0: associated
[  117.347334] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  117.380798] cfg80211: All devices are disconnected, going to restore regulatory settings
[  117.380804] cfg80211: Restoring regulatory settings
[  117.381549] cfg80211: Calling CRDA to update world regulatory domain
[  117.384991] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  117.384995] cfg80211: World regulatory domain updated:
[  117.384996] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  117.384999] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.385001] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  117.385002] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  117.385004] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.385006] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  120.582239] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  120.584841] wlan0: authenticated
[  120.585445] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  120.588055] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  120.588064] wlan0: associated
[  131.440931] wlan0: no IPv6 routers present
[  151.573271] cfg80211: All devices are disconnected, going to restore regulatory settings
[  151.573287] cfg80211: Restoring regulatory settings
[  151.573298] cfg80211: Calling CRDA to update world regulatory domain
[  151.581666] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  151.581676] cfg80211: World regulatory domain updated:
[  151.581680] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  151.581687] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  151.581693] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  151.581698] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  151.581703] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  151.581709] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  152.114519] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  152.117366] wlan0: authenticated
[  152.118060] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  152.120698] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  152.120709] wlan0: associated
[  166.351808] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  166.376610] cfg80211: All devices are disconnected, going to restore regulatory settings
[  166.376616] cfg80211: Restoring regulatory settings
[  166.376621] cfg80211: Calling CRDA to update world regulatory domain
[  166.381978] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  166.381985] cfg80211: World regulatory domain updated:
[  166.381987] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  166.381990] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  166.381993] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  166.381996] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  166.381998] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  166.382001] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  169.519352] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  169.521863] wlan0: authenticated
[  169.522273] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  169.524887] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  169.524897] wlan0: associated
[  180.008256] wlan0: no IPv6 routers present
[  200.568696] cfg80211: All devices are disconnected, going to restore regulatory settings
[  200.568708] cfg80211: Restoring regulatory settings
[  200.568715] cfg80211: Calling CRDA to update world regulatory domain
[  200.576557] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  200.576566] cfg80211: World regulatory domain updated:
[  200.576571] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  200.576578] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.576584] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  200.576590] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  200.576595] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.576600] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  201.052327] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  201.054935] wlan0: authenticated
[  201.055197] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  201.057805] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  201.057814] wlan0: associated
[  215.343344] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  215.364118] cfg80211: All devices are disconnected, going to restore regulatory settings
[  215.364129] cfg80211: Restoring regulatory settings
[  215.364138] cfg80211: Calling CRDA to update world regulatory domain
[  215.369796] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  215.369801] cfg80211: World regulatory domain updated:
[  215.369803] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  215.369807] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  215.369810] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  215.369812] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  215.369815] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  215.369818] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  397.194197] r8169 0000:02:00.0: eth0: link down
[  401.693922] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  402.206037] r8169 0000:02:00.0: PME# enabled
[  418.099916] r8169 0000:02:00.0: eth0: link up
[  418.100682] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  418.115601] r8169 0000:02:00.0: PME# disabled
[  418.115898] r8169 0000:02:00.0: eth0: link down
[  418.264318] r8169 0000:02:00.0: eth0: link down
[  419.781169] r8169 0000:02:00.0: eth0: link up
[  428.172995] eth0: no IPv6 routers present
[  515.561935] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  515.564790] wlan0: authenticated
[  515.565337] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  515.568105] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  515.568125] wlan0: associated
[  525.931758] wlan0: no IPv6 routers present
[  546.556056] cfg80211: All devices are disconnected, going to restore regulatory settings
[  546.556076] cfg80211: Restoring regulatory settings
[  546.556080] cfg80211: Calling CRDA to update world regulatory domain
[  546.561275] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  546.561283] cfg80211: World regulatory domain updated:
[  546.561285] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  546.561287] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  546.561289] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  546.561291] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  546.561293] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  546.561295] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  547.087624] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  547.287525] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 2)
[  547.298746] wlan0: authenticated
[  547.303938] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  547.306674] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  547.306684] wlan0: associated
[  561.345684] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  561.373250] cfg80211: All devices are disconnected, going to restore regulatory settings
[  561.373257] cfg80211: Restoring regulatory settings
[  561.373265] cfg80211: Calling CRDA to update world regulatory domain
[  561.377379] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  561.377383] cfg80211: World regulatory domain updated:
[  561.377385] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  561.377387] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  561.377389] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  561.377391] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  561.377393] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  561.377395] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  564.492103] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  564.494656] wlan0: authenticated
[  564.495201] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  564.497922] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  564.497932] wlan0: associated
[  575.035093] wlan0: no IPv6 routers present
[  595.576846] cfg80211: All devices are disconnected, going to restore regulatory settings
[  595.576862] cfg80211: Restoring regulatory settings
[  595.576871] cfg80211: Calling CRDA to update world regulatory domain
[  595.584827] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  595.584838] cfg80211: World regulatory domain updated:
[  595.584842] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  595.584849] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  595.584855] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  595.584860] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  595.584865] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  595.584870] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  596.134979] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  596.137714] wlan0: authenticated
[  596.138276] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  596.141062] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  596.141074] wlan0: associated
[  610.337523] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  610.360936] cfg80211: All devices are disconnected, going to restore regulatory settings
[  610.360943] cfg80211: Restoring regulatory settings
[  610.360948] cfg80211: Calling CRDA to update world regulatory domain
[  610.365894] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  610.365899] cfg80211: World regulatory domain updated:
[  610.365901] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  610.365904] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  610.365907] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  610.365910] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  610.365912] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  610.365915] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  613.560040] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  613.562556] wlan0: authenticated
[  613.563421] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  613.566089] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  613.566098] wlan0: associated
[  624.569481] wlan0: no IPv6 routers present
[  644.475816] cfg80211: All devices are disconnected, going to restore regulatory settings
[  644.475831] cfg80211: Restoring regulatory settings
[  644.475840] cfg80211: Calling CRDA to update world regulatory domain
[  644.483766] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  644.483776] cfg80211: World regulatory domain updated:
[  644.483780] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  644.483787] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  644.483793] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  644.483798] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  644.483803] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  644.483808] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  645.015686] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  645.018998] wlan0: authenticated
[  645.019608] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  645.022272] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  645.022279] wlan0: associated
[  659.304782] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  659.335948] cfg80211: All devices are disconnected, going to restore regulatory settings
[  659.335955] cfg80211: Restoring regulatory settings
[  659.335960] cfg80211: Calling CRDA to update world regulatory domain
[  659.341019] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  659.341027] cfg80211: World regulatory domain updated:
[  659.341029] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  659.341032] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  659.341035] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  659.341038] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  659.341041] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  659.341043] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  662.476649] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  662.479108] wlan0: authenticated
[  662.479799] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  662.482412] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  662.482422] wlan0: associated
[  672.848688] wlan0: no IPv6 routers present
[  693.415724] cfg80211: All devices are disconnected, going to restore regulatory settings
[  693.415739] cfg80211: Restoring regulatory settings
[  693.415750] cfg80211: Calling CRDA to update world regulatory domain
[  693.422575] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  693.422585] cfg80211: World regulatory domain updated:
[  693.422589] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  693.422596] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  693.422602] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  693.422607] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  693.422612] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  693.422617] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  693.906839] wlan0: authenticate with 00:0e:2e:c0:0d:55 (try 1)
[  693.909578] wlan0: authenticated
[  693.910143] wlan0: associate with 00:0e:2e:c0:0d:55 (try 1)
[  693.912879] wlan0: RX ReassocResp from 00:0e:2e:c0:0d:55 (capab=0x421 status=0 aid=2)
[  693.912890] wlan0: associated
[  708.281963] wlan0: deauthenticating from 00:0e:2e:c0:0d:55 by local choice (reason=3)
[  708.326703] cfg80211: All devices are disconnected, going to restore regulatory settings
[  708.326710] cfg80211: Restoring regulatory settings
[  708.326714] cfg80211: Calling CRDA to update world regulatory domain
[  708.331388] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  708.331394] cfg80211: World regulatory domain updated:
[  708.331396] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  708.331399] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  708.331401] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  708.331403] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  708.331405] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  708.331407] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


rfkill list all
> 0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


---

### Post by chili555 on 2012-05-19
Please try a driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Disconnect the ethernet cable and see if you can connect. If so, write a file to make it permanent.```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or leafpad or vim if you don't have the text editor gedit. Add a single line:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit.

If your issue is resolved in just one reply, please use thread tools at the top to mark Solved.

---

### Post by Heiden on 2012-05-19
Thanks for the reply. Sadly, it didn't work. Still tries to connect, but just seems to give up after a while.

---

### Post by chili555 on 2012-05-19
Please try another:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi swcrypto=1
```Again, please try with the ethernet disconnected.

---

### Post by Heiden on 2012-05-19
Still no luck...

---

### Post by chili555 on 2012-05-19
> Wireless Access Points
DOXENZO: Infra, 00:0E:2E:C0:0D:55, Freq 2462 MHz, Rate 54 Mb/s, Strength 100Is your access point set for WPA and WPA2 mixed mode? Will you try WPA2 only?```
sudo iwlist wlan0 scan
```I am a bit puzzled by this:> [ 52.562229] cfg80211: Calling CRDA to update world regulatory domain
[ 52.565656] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 52.565661] cfg80211: World regulatory domain updated:  [COLOR="Red"]<---to 'blank'??[/COLOR]I'm not sure it's significant, but I wonder if we forced the CRDA to your country code it might connect. I note your AP is set to channel 11 which is, as far as I know, universal. What is your country?

For reference, here is the corresponding line from my system, also using iwlwifi:> cfg80211: Regulatory domain changed to country: [COLOR="Red"]US[/COLOR]

---

### Post by Heiden on 2012-05-19
Well, I bought the laptop from a webshop in the Netherlands and got it sent to Belgium (where I live). 


Btw, "sudo iwlist wlan0 scan" showed me this:
> wlan0     Scan completed :
          Cell 01 - Address: 00:0E:2E:C0:0D:55
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:off
                    ESSID:"DOXENZO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e0dcd968
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0007444F58454E5A4F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000000000000200000004000000060000000
                    IE: Unknown: DD07000C4301000000


---

### Post by chili555 on 2012-05-19
My oh my, as we say in the woods of South Carolina. No encryption at all. I suggest, after we get you connected, you switch to WPA2-AES quickly.

Let's try:```
sudo modprobe -r cfg80211
sudo gedit /etc/modprobe.d/cfg80211.conf
```Add one line:```
options cfg80211 ieee80211_regdom=BE
```Proofread, save and close gedit. Use nano, leafpad, vim or any other text editor if you don't have gedit. Proofread carefully, save and close gedit. Now do:```
sudo modprobe -rv iwlwifi
```It ought to have taken out cfg80211 at the same time.```
sudo modprobe iwlwifi
```Check if the module parameter loaded correctly:```
cat /sys/module/cfg80211/parameters/ieee80211_regdom
```It ought to return BE.

Now can you connect?

---

### Post by Heiden on 2012-05-19
No, still can't connect, but "sudo modprobe -r cfg80211" gives a
> FATAL: Module cfg80211 is in use.


---

### Post by chili555 on 2012-05-19
It's in use by iwlwifi. Please try:```
sudo modprobe -r iwlwifi
sudo modprobe -r cfg80211
sudo modprobe iwlwifi
```Then proceed as above.

---

### Post by Heiden on 2012-05-19
That doesn't seem to solve the problem, it still doesn't connect...

---

### Post by chili555 on 2012-05-19
Let's see what Network Manager is doing all this time. Reboot with the ethernet detached so we have a clean slate and try to connect. Then run and post:```
sudo cat /var/log/syslog | grep -e etwork | tail -n25
```

---

### Post by Heiden on 2012-05-19
Here you go: 
> May 19 22:42:53 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 19 22:42:54 arnout-ThinkPad-E520 NetworkManager[871]: <info> dhclient started with pid 1345
May 19 22:42:54 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Beginning IP6 addrconf.
May 19 22:42:54 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 19 22:42:54 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May 19 22:43:14 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): IP6 addrconf timed out or failed.
May 19 22:43:14 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 19 22:43:14 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 19 22:43:14 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 19 22:43:24 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): supplicant interface state: completed -> disconnected
May 19 22:43:24 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 19 22:43:25 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 19 22:43:25 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 19 22:43:25 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): supplicant interface state: associating -> completed
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <warn> (wlan0): DHCPv4 request timed out.
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1345
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <warn> Activation (wlan0) failed for access point (DOXENZO)
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <warn> Activation (wlan0) failed.
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): deactivating device (reason 'none') [0]
May 19 22:43:39 arnout-ThinkPad-E520 NetworkManager[871]: <info> (wlan0): supplicant interface state: completed -> disconnected


Thanks by the way for trying to figure this out ;)

---

### Post by chili555 on 2012-05-19
> <info> Activation (wlan0) Beginning [COLOR="Red"]IP6[/COLOR] addrconf.You might edit connections in Network Manager to set IPv6 Settings to Ignore. You might also power cycle the router. You might also reinstall Network Manager:```
sudo apt-get install --reinstall network-manager
```Have you made any changes in NMs conf files?

I'm frankly stumped. These Intel chips are usually rock-solid. I'm using one right now.

---

### Post by debankur on 2012-08-15
I had the same issue on my thinkpad t420 with an intel centrino wifi card. I added a script that will set the wireless domain zone as alpha2. I added this script to CORN and scheduled it to run every 10 minutes. I have been runing this for over a week and I have not see any disconnection. 

Create a file under root and name is wifi.sh or whatever you want and add the two lines.
```

#!/bin/bash
iw reg set alpha2

```

Provide it with execute permission.
```

chmod +x wifi.sh

```

Add it to the root crontab

```

su -
crontab -e 
*/10 * * * * /root/wifi.sh

```

Hopefull that fixes the issue for you.  

Thanks, 
Debankur

---

