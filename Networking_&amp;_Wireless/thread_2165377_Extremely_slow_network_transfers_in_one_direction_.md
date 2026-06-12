---
title: "Extremely slow network transfers in one direction with RealTek RTL-8169 Gigabit card"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by Ben_Hallett on 2013-08-04
File transfers from my home server (running Ubuntu 12.04 Server) to any other PC on my LAN (all running Windows 7) are extremely slow, but file transfers in the other direction (uploading to the server) are fast.

I observed this with both Samba and SFTP transfers, so decided to verify it with iperf, and got the same results. The output on the server looked like this:
```
    iperf -s
    ------------------------------------------------------------
    Server listening on TCP port 5001
    TCP window size: 85.3 KByte (default)
    ------------------------------------------------------------
    [  4] local 192.168.1.95 port 5001 connected with 192.168.1.82 port 1309
    [ ID] Interval       Transfer     Bandwidth
    [  4]  0.0-10.0 sec   416 MBytes   349 Mbits/sec
    ------------------------------------------------------------
    Client connecting to 192.168.1.82, TCP port 5001
    TCP window size: 46.1 KByte (default)
    ------------------------------------------------------------
    [  4] local 192.168.1.95 port 59704 connected with 192.168.1.82 port 5001
    [  4]  0.0-12.2 sec  1.50 MBytes  1.03 Mbits/sec

```

The client (My Win 7 PC) produced this output for the same run:
```

    iperf.exe -c 192.168.1.95 -r
    ------------------------------------------------------------
    Server listening on TCP port 5001
    TCP window size: 64.0 KByte (default)
    ------------------------------------------------------------
    ------------------------------------------------------------
    Client connecting to 192.168.1.95, TCP port 5001
    TCP window size: 64.0 KByte (default)
    ------------------------------------------------------------
    [  4] local 192.168.1.82 port 1309 connected with 192.168.1.95 port 5001
    [ ID] Interval       Transfer     Bandwidth
    [  4]  0.0-10.0 sec   416 MBytes   349 Mbits/sec
    [  4] local 192.168.1.82 port 5001 connected with 192.168.1.95 port 59704
    [  4]  0.0-12.2 sec  1.50 MBytes  1.03 Mbits/sec

```

Similar results are observed from other clients. The computers are all connected to the same Gigabit wired switch. Exchanging the ports and cables between them gives the same result. I've done my best to google around similar problems, but I haven't found any relevant solutions yet. Does anyone have any ideas?

The following are some dumps of relevant debug commands, in case they're of any use to people more knowledgeable than me.

ethtool output for the ethernet card on the server:

```
    ethtool eth0
    Settings for eth0:
            Supported ports: [ TP MII ]
            Supported link modes:   10baseT/Half 10baseT/Full
                                    100baseT/Half 100baseT/Full
                                    1000baseT/Half 1000baseT/Full
            Supported pause frame use: No
            Supports auto-negotiation: Yes
            Advertised link modes:  10baseT/Half 10baseT/Full
                                    100baseT/Half 100baseT/Full
                                    1000baseT/Half 1000baseT/Full
            Advertised pause frame use: Symmetric Receive-only
            Advertised auto-negotiation: Yes
            Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                                 100baseT/Half 100baseT/Full
                                                 1000baseT/Half 1000baseT/Full
            Link partner advertised pause frame use: Symmetric Receive-only
            Link partner advertised auto-negotiation: Yes
            Speed: 1000Mb/s
            Duplex: Full
            Port: MII
            PHYAD: 0
            Transceiver: internal
            Auto-negotiation: on
            Supports Wake-on: pumbg
            Wake-on: g
            Current message level: 0x00000033 (51)
                                   drv probe ifdown ifup
            Link detected: yes

```

Mii-tool output:
```
    sudo mii-tool
    eth0: negotiated 1000baseT-HD flow-control, link ok

```

List of hardware returned by lspci:
```
    sudo lspci
    00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
    00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
    00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
    00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
    00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
    00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
    00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
    00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)

```

List of loaded drivers returned by lsmod:
```
    sudo lsmod
    Module                  Size  Used by
    usb_storage            39646  0
    vesafb                 13516  1
    ppdev                  12849  0
    arc4                   12473  2
    snd_via82xx            24718  0
    gameport               15060  1 snd_via82xx
    snd_ac97_codec        110213  1 snd_via82xx
    b43                   342801  0
    ac97_bus               12642  1 snd_ac97_codec
    snd_pcm                80916  2 snd_via82xx,snd_ac97_codec
    snd_timer              28931  1 snd_pcm
    snd_page_alloc         14108  2 snd_via82xx,snd_pcm
    snd_mpu401_uart        13865  1 snd_via82xx
    snd_rawmidi            25424  1 snd_mpu401_uart
    snd_seq_device         14172  1 snd_rawmidi
    snd                    62218  7 snd_via82xx,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
    mac80211              436493  1 b43
    soundcore              14635  1 snd
    serio_raw              13027  0
    i2c_viapro             12969  0
    cfg80211              178877  2 b43,mac80211
    bcma                   25651  1 b43
    parport_pc             32114  1
    shpchp                 32265  0
    mac_hid                13077  0
    via_cputemp            13031  0
    hwmon_vid              12723  1 via_cputemp
    lp                     17455  0
    parport                40930  3 ppdev,parport_pc,lp
    pata_via               13428  0
    ssb                    50691  1 b43
    r8169                  56396  0
    sata_via               13495  2

```

Driver info for the Gigabit card:
```
    sudo modinfo r8169
    filename:       /lib/modules/3.2.0-51-generic-pae/kernel/drivers/net/ethernet/realtek/r8169.ko
    version:        6.017.00-NAPI
    license:        GPL
    description:    RealTek RTL-8169 Gigabit Ethernet driver
    author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
    srcversion:     231149B837AF2B63F7C0271
    alias:          pci:v00001186d00004300sv00001186sd00004C00bc*sc*i*
    alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
    alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
    depends:
    vermagic:       3.2.0-51-generic-pae SMP mod_unload modversions 686
    parm:           speed:force phy operation. Deprecated by ethtool (8). (array of int)
    parm:           duplex:force phy operation. Deprecated by ethtool (8). (array of int)
    parm:           autoneg:force phy operation. Deprecated by ethtool (8). (array of int)
    parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
    parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
    parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

```

...and uname -a for good measure:
```
    uname -a
    Linux hotblack 3.2.0-51-generic-pae #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 i686 i686 i386 GNU/Linux

```

If anyone thinks any other debug output would be helpful to have, please don't hesitate to ask.

---

