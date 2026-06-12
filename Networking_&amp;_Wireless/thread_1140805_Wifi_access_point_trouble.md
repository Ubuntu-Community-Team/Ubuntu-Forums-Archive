---
title: "Wifi access point trouble"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Nathan G. on 2009-04-27
Hi guys!

Long time lurker first time poster.  I'm having some wifi laptop networking trouble.  I'm familiar with Linux and the big picture overview of how it's set up (I'm comfortable with command line stuff), but just assume I'm a complete noob and spell it out for me since I'm always learning more about Ubuntu.

I've installed 8.04 previously on a Toshiba Satellite Pro and now I'm attempting a wifi networking setup.  I have been through the tutorial many times and after many attempts at configuring /etc/network/interfaces and /etc/wpa_supplicant.conf manually, I determined to ask here.  

I have an Edimax we-7108PCg wireless LAN cardbus PC card.  I popped it into the laptop and viola, a link, but no activity.  I ran iwconfig and got this:

```


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"****"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```Following are the contents of those two files:

/etc/network/interfaces

```


auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.105
gateway 192.168.1.1
netmask 255.255.255.0
#pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
wpa-driver wext
wireless-essid ****
wpa-ap-scan 2
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt ****
wpa-psk ********

#iface eth0 inet dhcp

#auto eth0



```/etc/wpa_supplicant

```


ctrl_interface=/var/run/wpa_supplicant
ctrl_intervace_group=0

eapol_version=1
ap_scan=1
fast+reauth=1

network={
        ssid="****"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk="****"
        psk=********
}




```Here is the output of lspci -v

```


$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: fd000000-fdffffff
    Prefetchable memory behind bridge: dbf00000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at efe0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at ef80 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 18c0 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=0c, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fce00000-fcefffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at cfa0 [size=16]
    Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1000 [size=256]
    I/O ports at 1880 [size=64]

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: medium devsel, IRQ 11
    I/O ports at 1400 [size=256]
    I/O ports at 1800 [size=128]

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at dc000000 (32-bit, prefetchable) [size=64M]
    Memory at dbf80000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at dbf00000 [disabled] [size=128K]
    Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
    Subsystem: Toshiba America Info Systems EtherExpress PRO/100 VE
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at fceff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at df40 [size=64]
    Capabilities: <access denied>

02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
    Subsystem: Lucent Technologies Unknown device ab01
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at fce00000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=04, sec-latency=176
    Memory window 0: 34000000-37fff000 (prefetchable)
    Memory window 1: 38000000-3bfff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001

02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, slow devsel, latency 168, IRQ 11
    Memory at fce01000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=05, subordinate=08, sec-latency=0
    Memory window 0: 3c000000-3ffff000 (prefetchable)
    Memory window 1: 40000000-43fff000
    I/O window 0: 0000d800-0000d8ff
    I/O window 1: 0000dc00-0000dcff
    16-bit legacy interface ports at 0001

02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: bus master, slow devsel, latency 168, IRQ 11
    Memory at fce02000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=09, subordinate=0c, sec-latency=0
    Memory window 0: 44000000-47fff000 (prefetchable)
    Memory window 1: 48000000-4bfff000
    I/O window 0: 00001c00-00001cff
    I/O window 1: 00002000-000020ff
    16-bit legacy interface ports at 0001

02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
    Subsystem: Toshiba America Info Systems Unknown device 0001
    Flags: medium devsel, IRQ 255
    Memory at fce03000 (32-bit, non-prefetchable) [disabled] [size=512]
    Capabilities: <access denied>



```What have I set up incorrectly?  What else do you guys need to see?  Thank you for you help and replies in advance!

Best,
Nathan G.

---

### Post by Nathan G. on 2009-04-28
Hey folks,
 
Anyone? Maybe a few thoughts? *bump*
 
Thank you,
Nathan G.

---

