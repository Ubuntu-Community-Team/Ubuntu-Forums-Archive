---
title: "seemingly unsolvable problem with Wi-Fi"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by icu12345 on 2013-05-03
So, here it goes.. I have this extremely annoying problem with my wireless adapter that’s just making me seriously consider jumping off a bridge.. or even worse.. switching back to windows :P

This is my setup: Ubuntu 13.04, wireless adapter: intel PRO/Wireless 3945ABG [Golan]. Wireless driver: iwl3945. Wireless router Dlink DIR-615 with dd-wrt, 3 wirelessly connected laptops (2 of them have windows and 1 is with ubuntu) and one desktop pc with wired connection.

The problem is poor wireless performance of the ubuntu laptop. Transfer speeds are way worse than they should be. A series of internet bandwidth tests shows that I get about half the speed I used to get with the same laptop in windows environment (FYI the laptop had windows7 until last week and used to connect to the very same wireless network). Furthermore (like if that wasn't enough..), when copying files across the local network the speed is also far from pleasing... much slower it used to be. As a result, streaming a media file stored on another computer or device on the network is impossible. As this is what I'm primarily using this laptop for, it's a real pain that I can't get it working correctly.

What I've done so far: I tried disabling hardware scan:

```
modprobe -r iwl3945 
modprobe iwl3945 disable_hw_scan=1

```but this didn´t work so I didn´t bother making it permanent.
I also tried replacing the network manager with wicd - didn't help at all.
Tried 
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 11n_disable=1 
```
but the result was: 

```
ERROR: could not insert 'iwl3945': Invalid argument
```

So what else could it be? 
Here´s the output of lshw -C network:

```
    icefire@Toshiba:~$ sudo lshw -C network
    [sudo] password for icefire: 
    *-network               
    description: Ethernet interface
    product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: eth0
    version: 02
    serial: 00:1e:33:5d:46:ab
    size: 10Mbit/s
    capacity: 100Mbit/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical  tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-        NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
    resources: irq:44 ioport:4000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
 
    *-network
    description: Wireless interface
    product: PRO/Wireless 3945ABG [Golan] Network Connection
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@0000:03:00.0
    logical name: wlan0
    version: 02
    serial: 00:1f:3c:ae:d0:ea
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=iwl3945 driverversion=3.8.0-19-generic firmware=15.32.2.9 ip=192.168.1.20 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
    resources: irq:46 memory:d4200000-d4200fff

```Here´s what iwconfig outputs:
```
    icefire@Toshiba:~$ iwconfig
    wlan0     IEEE 802.11abg  ESSID:"dd-wrt"  
      Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:B1:62:EE   
      Bit Rate=54 Mb/s   Tx-Power=15 dBm   
      Retry  long limit:7   RTS thr:off   Fragment thr:off
      Power Management:off
      Link Quality=61/70  Signal level=-49 dBm  
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:6  Invalid misc:224   Missed beacon:0
 
     lo        no wireless extensions.
 
     eth0      no wireless extensions
```
and ifconfig:
```
    icefire@Toshiba:~$ ifconfig
    eth0      Link encap:Ethernet  HWaddr 00:1e:33:5d:46:ab  
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
     lo        Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:554 errors:0 dropped:0 overruns:0 frame:0
      TX packets:554 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:63267 (63.2 KB)  TX bytes:63267 (63.2 KB)
 
    wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:ae:d0:ea  
      inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
      inet6 addr: fe80::21f:3cff:feae:d0ea/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      RX packets:9773 errors:0 dropped:0 overruns:0 frame:0
      TX packets:6310 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:10377083 (10.3 MB)  TX bytes:1143412 (1.1 MB)

```

What else could I do? Please help..

---

### Post by connect2pgp on 2013-05-03
> **icu12345 said:**
> So, here it goes.. I have this extremely annoying problem with my wireless adapter that’s just making me seriously consider jumping off a bridge.. or even worse.. switching back to windows :P

This is my setup: Ubuntu 13.04, wireless adapter: intel PRO/Wireless 3945ABG [Golan]. Wireless driver: iwl3945. Wireless router Dlink DIR-615 with dd-wrt, 3 wirelessly connected laptops (2 of them have windows and 1 is with ubuntu) and one desktop pc with wired connection.

The problem is poor wireless performance of the ubuntu laptop. Transfer speeds are way worse than they should be. A series of internet bandwidth tests shows that I get about half the speed I used to get with the same laptop in windows environment (FYI the laptop had windows7 until last week and used to connect to the very same wireless network). Furthermore (like if that wasn't enough..), when copying files across the local network the speed is also far from pleasing... much slower it used to be. As a result, streaming a media file stored on another computer or device on the network is impossible. As this is what I'm primarily using this laptop for, it's a real pain that I can't get it working correctly.

What I've done so far: I tried disabling hardware scan:

```
modprobe -r iwl3945 
modprobe iwl3945 disable_hw_scan=1

```but this didn´t work so I didn´t bother making it permanent.
I also tried replacing the network manager with wicd - didn't help at all.
Tried 
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 11n_disable=1 
```
but the result was: 

```
ERROR: could not insert 'iwl3945': Invalid argument
```

So what else could it be? 
Here´s the output of lshw -C network:

```
    icefire@Toshiba:~$ sudo lshw -C network
    [sudo] password for icefire: 
    *-network               
    description: Ethernet interface
    product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: eth0
    version: 02
    serial: 00:1e:33:5d:46:ab
    size: 10Mbit/s
    capacity: 100Mbit/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical  tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-        NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
    resources: irq:44 ioport:4000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
 
    *-network
    description: Wireless interface
    product: PRO/Wireless 3945ABG [Golan] Network Connection
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@0000:03:00.0
    logical name: wlan0
    version: 02
    serial: 00:1f:3c:ae:d0:ea
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=iwl3945 driverversion=3.8.0-19-generic firmware=15.32.2.9 ip=192.168.1.20 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
    resources: irq:46 memory:d4200000-d4200fff

```Here´s what iwconfig outputs:
```
    icefire@Toshiba:~$ iwconfig
    wlan0     IEEE 802.11abg  ESSID:"dd-wrt"  
      Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:B1:62:EE   
      Bit Rate=54 Mb/s   Tx-Power=15 dBm   
      Retry  long limit:7   RTS thr:off   Fragment thr:off
      Power Management:off
      Link Quality=61/70  Signal level=-49 dBm  
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:6  Invalid misc:224   Missed beacon:0
 
     lo        no wireless extensions.
 
     eth0      no wireless extensions
```
and ifconfig:
```
    icefire@Toshiba:~$ ifconfig
    eth0      Link encap:Ethernet  HWaddr 00:1e:33:5d:46:ab  
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
     lo        Link encap:Local Loopback  
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
      RX packets:554 errors:0 dropped:0 overruns:0 frame:0
      TX packets:554 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:63267 (63.2 KB)  TX bytes:63267 (63.2 KB)
 
    wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:ae:d0:ea  
      inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
      inet6 addr: fe80::21f:3cff:feae:d0ea/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      RX packets:9773 errors:0 dropped:0 overruns:0 frame:0
      TX packets:6310 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000 
      RX bytes:10377083 (10.3 MB)  TX bytes:1143412 (1.1 MB)

```

What else could I do? Please help..

Try this [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by icu12345 on 2013-05-03
How could this help me? This is a driver for a realtek ethernet adapter. I'm having trouble with an intel wireless adapter.

---

### Post by icu12345 on 2013-05-06
Just want to add that I also tried changing the Wi-Fi channel (picked the one with the least interferences) and also tried temporarily removing all wireless security --> no difference. 

Don't know of this is relevant but I'm using ubuntu's default desktop environment, Unity.

---

### Post by varunendra on 2013-05-06
> **icu12345 said:**
> 
Tried 
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 11n_disable=1 
```
but the result was: 

```
ERROR: could not insert 'iwl3945': Invalid argument
```

Hello icu12345,

The iwl3945 driver does not have that option available, at least not on my 12.04 :)

Please try instead -
```
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945 swcrypto=1
```

---

### Post by ahallubuntu on 2013-05-06
~

---

### Post by icu12345 on 2013-05-07
> **varunendra said:**
> Hello icu12345,

The iwl3945 driver does not have that option available, at least not on my 12.04 :)

Please try instead -
```
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945 swcrypto=1
```
 
Hello varunendra, thanks for helping me out. The problem still persists. However, I must say that the worst of it is when trying to copy data from a remote computer using a virtual private network. It is a simple pptp vpn connection. The remote server is just a dd-wrt router. All other computers in my local network are getting transfer rates of 800-900 KB/s. The ubuntu laptops gets 200 KB/s at best. I'd think something is wrong with the vpn network I've set up but everything was fine before I got ubuntu, so I guess that the problem is not the vpn itself. 

> **ahallubuntu said:**
> If this is a Toshiba(?) laptop, you can probably upgrade the wireless card to an Intel WiFi Link 5100 - an "N" card to boot.  (As the 3945ABG doesn't do wireless 802.11n, which is why trying to disable it gave you an error.)  These cards can be had used from eBay for about $5 USD shipped.  I've upgraded a number of laptops with this card.  They work great in Ubuntu 12.04.

There are different variations of the 5100.  You want a FULL height (same size as existing wireless card) not a HALF height card, and you can use a card not just for a Toshiba but also Dell, Sony, Acer, etc.  - but DO NOT get the HP/Lenovo/IBM version of the card.  The sellers usually indicate which laptop the card came out of.

Depending on where in the laptop your wireless card is located, it could be pretty easy to upgrade it.  The hardest part is GETTING to the card - and if it's accessible under a panel on the bottom, then you simply need to remove a few screws and pop off the two antenna wires.  There are plenty of YouTube demo videos if you want to see how this is done.

FYI, if you are new to Ubuntu, I don't recommend version 13.04.  It will be supported only nine months, then you'll have to upgrade to get support.  Version 12.04 LTS is a "Long Term Support" version that will be supported until April 2017.  I've put 12.04 on many machines and highly recommend it.  At least one of them had the 3945ABG card (one I never got around to upgrading) and seems to work well with my DD-WRT router.

Thank you. It really is a Toshiba Satellite A300 laptop. Luckily for me, the wireless adapter is located in a really easy spot (I already have some experience taking apart this laptop model) so I could change it. However, I am keen to find what is causing my worse-than-windows performance...

---

### Post by varunendra on 2013-05-07
> **icu12345 said:**
> Hello varunendra, thanks for helping me out. The problem still persists. However, I must say that the worst of it is when trying to copy data from a remote computer using a virtual private network. It is a simple pptp vpn connection. The remote server is just a dd-wrt router. All other computers in my local network are getting transfer rates of 800-900 KB/s. The ubuntu laptops gets 200 KB/s at best.

Did you restart after applying the "swcrypto=1" paramerer? I hope you understand that was a temporary change and would be lost at reboot. So don't reboot after applying it. If you didn't and still there was no improvement, please follow the "Wireless Script" link in my signature and post back diagnostics report as mentioned in the linked post.

---

### Post by icu12345 on 2013-05-08
Thanks for your support. Yes, I am aware that what you suggested is not permanent and only works until restart. I kept this in mind but it didn't bring any difference. I downloaded your script and sincerely admire your desire to help people with linux :) 

I ran your script twice - with and without active VPN connection. The second one is when connected to VPN.

So, here it goes:

without vpn:
```


*************** info trace ****************






**** uname -a ****




Linux Toshiba 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:36:13 UTC 2013 i686 i686 i686 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1c]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1041]
    Kernel driver in use: iwl3945




**** lsusb ****




Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 006 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




**** iwconfig ****




wlan0     IEEE 802.11abg  ESSID:"lapa network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:117   Missed beacon:0






**** rfkill ****




1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




**** lsmod ****




Module                  Size  Used by
iwl3945                63619  0 
iwlegacy               87575  1 iwl3945
mac80211              526519  2 iwl3945,iwlegacy
cfg80211              436177  3 iwl3945,iwlegacy,mac80211
nls_iso8859_1          12617  1 
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  12 
bnep                   17669  2 
binfmt_misc            17260  1 
ext2                   63166  1 
btusb                  17986  0 
bluetooth             202069  22 bnep,btusb,rfcomm
snd_hda_codec_realtek    63791  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
radeon                870822  3 
arc4                   12543  2 
r592                   17707  0 
toshiba_acpi           18270  0 
coretemp               13131  0 
r852                   17873  0 
sm_common              16772  1 r852
nand                   49670  2 r852,sm_common
nand_ecc               13105  1 nand
nand_bch               13003  1 nand
bch                    17226  1 nand_bch
nand_ids                8547  1 nand
sparse_keymap          13658  1 toshiba_acpi
memstick               15842  1 r592
ttm                    71289  1 radeon
wmi                    18590  1 toshiba_acpi
video                  18894  0 
toshiba_bluetooth      12748  0 
mtd                    38922  2 nand,sm_common
snd                    56485  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
uvcvideo               71279  0 
drm_kms_helper         47545  1 radeon
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
drm                   228750  5 ttm,drm_kms_helper,radeon
joydev                 17097  0 
i2c_algo_bit           13197  1 radeon
lpc_ich                16925  0 
videodev               95806  2 uvcvideo,videobuf2_core
mac_hid                13037  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
psmouse                81038  0 
serio_raw              13031  0 
microcode              18286  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  1 
sdhci_pci              18158  0 
firewire_ohci          35292  0 
sdhci                  31824  1 sdhci_pci
firewire_core          61718  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  61531  0 
ahci                   25507  2 
libahci                26108  1 ahci




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: wlan0  [lapa network] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    WLAN_Meier:      Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Cisco-Home:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    FlamingoJung:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FairCity:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    064498:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    063fb2:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    belkin.3cd:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    HP-Print-bf-LaserJet 200: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97
    FlamingoJung-Gast: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    *lapa network:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA
    HDGBK2012:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Thom_D0042261:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off








**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false




**** NetworkManager.conf-10.04 ****








**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"FlamingoJung"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001524eb9a979
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000C466C616D696E676F4A756E67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD6B0050F204104A0001101044000102103B00010310470010BE9864CEDA0C7B22BF0DA715860EB7EB102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FlamingoJung-Gast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001524eb9b5f9
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 0011466C616D696E676F4A756E672D47617374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"lapa network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000539560ad95
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C6C617061206E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0505003A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010D10
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"063fb2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024460e91198
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 0006303633666232
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"FairCity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000e68a4e3a46d
                    Extra: Last beacon: 336ms ago
                    IE: Unknown: 00084661697243697479
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500011D7A12
                    IE: Unknown: DD1E00904C336C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000400000000000000000000000000000000000000
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-bf-LaserJet 200"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000538f93a9b2
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 001848502D5072696E742D62662D4C617365724A657420323030
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101800027A4000003A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Cisco-Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016eccd61cb2
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A436973636F2D486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B0001031047001059F29FB1F1D47A5EAFA9D6A96F43AB7C102100074C696E6B7379731023000545313230301024000776322E302E30341042000234321054000800060050F2040001101100054531323030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"WLAN_Meier"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A574C414E5F4D65696572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"064498"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000038ba854631e
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 0006303634343938
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010F73E1AA92C8536D2405C695BD3DECBD910210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006303634343938100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"belkin.3cd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000205ec0a57d
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A62656C6B696E2E336364
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B000103104700104B5EB5C31AB05F9BB495A4507A5B85F11021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763110240007312E30302E31301042000E31323131353247463131313839321054000800060050F20400011011001D42656C6B696E204E363030444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"HDGBK2012"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005cfe8812180
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 0009484447424B32303132
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010004
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD270050F204104A0001101044000102104700103C3546A39EA1FB9509EF246511E52D10103C000103
          Cell 12 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Thom_D0042261"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006ed61f186
                    Extra: Last beacon: 9916ms ago
                    IE: Unknown: 000D54686F6D5F4430303432323631
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Sabine Lauterbachs Netzwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000024e730dc177
                    Extra: Last beacon: 5260ms ago
                    IE: Unknown: 001B536162696E65204C61757465726261636873204E65747A7765726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706444520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016B0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010668A86D606F0D
          Cell 14 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-932204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000335d549d01f
                    Extra: Last beacon: 2264ms ago
                    IE: Unknown: 000E45617379426F782D393332323034
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000B7A12
                    IE: Unknown: DD1E00904C336C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402000000000000000000000000000000000000000000






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1




**** blacklist.conf ****




# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac




**** dmesg ****




[    0.791215] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 91de7a0b580f416d81726d1f7134a3ecef081207'
[   12.295183] wmi: Mapper loaded
[   12.345377] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.345382] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   12.441782] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.441787] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.441937] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[   12.489749] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.905356] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   15.972719] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.973078] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.791368] type=1400 audit(1367953853.486:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=984 comm="apparmor_parser"
[   22.984897] wlan0: authenticate with <MAC address removed>
[   22.985799] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.987548] wlan0: authenticated
[   22.988052] wlan0: associate with <MAC address removed> (try 1/3)
[   22.990678] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   22.992086] wlan0: associated
[   22.992116] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3500.216310] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3500.241905] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[ 3517.703053] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 3517.703058] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 3517.742527] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 3517.742536] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 3517.742712] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[ 3517.743202] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 3517.762040] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[ 3517.828996] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3517.829576] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3524.812931] wlan0: authenticate with <MAC address removed>
[ 3524.813866] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3524.815776] wlan0: authenticated
[ 3524.820057] wlan0: associate with <MAC address removed> (try 1/3)
[ 3524.822739] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 3524.824059] wlan0: associated
[ 3524.824108] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5057.504223] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 5061.057802] wlan0: authenticate with <MAC address removed>
[ 5061.060491] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5061.062505] wlan0: authenticated
[ 5061.064026] wlan0: associate with <MAC address removed> (try 1/3)
[ 5061.066688] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 5061.068412] wlan0: associated
[11138.504147] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[11142.057322] wlan0: authenticate with <MAC address removed>
[11142.057874] wlan0: send auth to <MAC address removed> (try 1/3)
[11142.062494] wlan0: authenticated
[11142.066331] wlan0: associate with <MAC address removed> (try 1/3)
[11142.069406] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11142.071249] wlan0: associated
[19225.500083] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[19229.061571] wlan0: authenticate with <MAC address removed>
[19229.062419] wlan0: send auth to <MAC address removed> (try 1/3)
[19229.064931] wlan0: authenticated
[19229.068071] wlan0: associate with <MAC address removed> (try 1/3)
[19229.070814] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[19229.072084] wlan0: associated
[33297.488223] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[33301.049120] wlan0: authenticate with <MAC address removed>
[33301.050033] wlan0: send auth to <MAC address removed> (try 1/3)
[33301.051837] wlan0: authenticated
[33301.057655] wlan0: associate with <MAC address removed> (try 1/3)
[33301.060412] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[33301.062964] wlan0: associated
[33576.488215] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[33580.041445] wlan0: authenticate with <MAC address removed>
[33580.042212] wlan0: send auth to <MAC address removed> (try 1/3)
[33580.044178] wlan0: authenticated
[33580.048038] wlan0: associate with <MAC address removed> (try 1/3)
[33580.050833] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[33580.052225] wlan0: associated
[52094.492179] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[52098.057078] wlan0: authenticate with <MAC address removed>
[52098.058692] wlan0: send auth to <MAC address removed> (try 1/3)
[52098.060534] wlan0: authenticated
[52098.065752] wlan0: associate with <MAC address removed> (try 1/3)
[52098.068507] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[52098.069812] wlan0: associated
[52184.492182] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[52188.049698] wlan0: authenticate with <MAC address removed>
[52188.050441] wlan0: send auth to <MAC address removed> (try 1/3)
[52188.052340] wlan0: authenticated
[52188.056206] wlan0: associate with <MAC address removed> (try 1/3)
[52188.058899] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[52188.062660] wlan0: associated
[54296.504225] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[54300.073339] wlan0: authenticate with <MAC address removed>
[54300.074573] wlan0: send auth to <MAC address removed> (try 1/3)
[54300.079239] wlan0: authenticated
[54300.084047] wlan0: associate with <MAC address removed> (try 1/3)
[54300.086832] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[54300.088198] wlan0: associated
[68342.504142] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[68346.061194] wlan0: authenticate with <MAC address removed>
[68346.062110] wlan0: send auth to <MAC address removed> (try 1/3)
[68346.064303] wlan0: authenticated
[68346.068839] wlan0: associate with <MAC address removed> (try 1/3)
[68346.073625] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[68346.075096] wlan0: associated
[75377.432324] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[75390.427894] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[75390.427898] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[75390.467280] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[75390.467286] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[75390.467437] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[75390.469106] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[75390.484397] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[75390.557161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75390.557755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75397.560937] wlan0: authenticate with <MAC address removed>
[75397.561744] wlan0: send auth to <MAC address removed> (try 1/3)
[75397.563618] wlan0: authenticated
[75397.564089] wlan0: associate with <MAC address removed> (try 1/3)
[75397.572289] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[75397.573815] wlan0: associated
[75397.573864] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready




**************** done ********************



```

with vpn:
```


*************** info trace ****************






**** uname -a ****




Linux Toshiba 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:36:13 UTC 2013 i686 i686 i686 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1c]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1041]
    Kernel driver in use: iwl3945




**** lsusb ****




Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 006 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




**** iwconfig ****




wlan0     IEEE 802.11abg  ESSID:"lapa network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:125   Missed beacon:0






**** rfkill ****




1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




**** lsmod ****




Module                  Size  Used by
ppp_mppe               12850  2 
ppp_async              17205  1 
crc_ccitt              12627  1 ppp_async
iwl3945                63619  0 
iwlegacy               87575  1 iwl3945
mac80211              526519  2 iwl3945,iwlegacy
cfg80211              436177  3 iwl3945,iwlegacy,mac80211
nls_iso8859_1          12617  1 
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  12 
bnep                   17669  2 
binfmt_misc            17260  1 
ext2                   63166  1 
btusb                  17986  0 
bluetooth             202069  22 bnep,btusb,rfcomm
snd_hda_codec_realtek    63791  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
radeon                870822  3 
arc4                   12543  4 
r592                   17707  0 
toshiba_acpi           18270  0 
coretemp               13131  0 
r852                   17873  0 
sm_common              16772  1 r852
nand                   49670  2 r852,sm_common
nand_ecc               13105  1 nand
nand_bch               13003  1 nand
bch                    17226  1 nand_bch
nand_ids                8547  1 nand
sparse_keymap          13658  1 toshiba_acpi
memstick               15842  1 r592
ttm                    71289  1 radeon
wmi                    18590  1 toshiba_acpi
video                  18894  0 
toshiba_bluetooth      12748  0 
mtd                    38922  2 nand,sm_common
snd                    56485  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
uvcvideo               71279  0 
drm_kms_helper         47545  1 radeon
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
drm                   228750  5 ttm,drm_kms_helper,radeon
joydev                 17097  0 
i2c_algo_bit           13197  1 radeon
lpc_ich                16925  0 
videodev               95806  2 uvcvideo,videobuf2_core
mac_hid                13037  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
psmouse                81038  0 
serio_raw              13031  0 
microcode              18286  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  1 
sdhci_pci              18158  0 
firewire_ohci          35292  0 
sdhci                  31824  1 sdhci_pci
firewire_core          61718  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  61531  0 
ahci                   25507  2 
libahci                26108  1 ahci




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: wlan0  [lapa network] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    WLAN_Meier:      Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Cisco-Home:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    FlamingoJung:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FairCity:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    064498:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    063fb2:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    belkin.3cd:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    HP-Print-bf-LaserJet 200: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97
    FlamingoJung-Gast: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    *lapa network:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA
    HDGBK2012:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Thom_D0042261:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    EasyBox-932204:  Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Sabine Lauterbachs Netzwerk: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Cisco:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    FRITZ!Box Fon WLAN 7050: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- VPN:  [VPN connection 1] -----------------------------------------------------
  State:             connected
  Default:           yes


  Message:








**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false




**** NetworkManager.conf-10.04 ****








**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"lapa network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000539d73d9cf
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C6C617061206E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050034127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"HDGBK2012"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005cff0913180
                    Extra: Last beacon: 528ms ago
                    IE: Unknown: 0009484447424B32303132
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010004
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD270050F204104A0001101044000102104700103C3546A39EA1FB9509EF246511E52D10103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"FlamingoJung"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015256da5433
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000C466C616D696E676F4A756E67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD6B0050F204104A0001101044000102103B00010310470010BE9864CEDA0C7B22BF0DA715860EB7EB102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"FlamingoJung-Gast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015256da60b3
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 0011466C616D696E676F4A756E672D47617374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Cisco-Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016ed4f6ef3c
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A436973636F2D486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B0001031047001059F29FB1F1D47A5EAFA9D6A96F43AB7C102100074C696E6B7379731023000545313230301024000776322E302E30341042000234321054000800060050F2040001101100054531323030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Thom_D0042261"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f603519b
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 000D54686F6D5F4430303432323631
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-bf-LaserJet 200"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000053980653ca
                    Extra: Last beacon: 468ms ago
                    IE: Unknown: 001848502D5072696E742D62662D4C617365724A657420323030
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101800027A4000003A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"WLAN_Meier"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A574C414E5F4D65696572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7050"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009fea01b19f
                    Extra: Last beacon: 5560ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037303530
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"FairCity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000e68acf3b48f
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 00084661697243697479
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001147A12
                    IE: Unknown: DD1E00904C336C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000400000000000000000000000000000000000000
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"belkin.3cd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002066d85d1a
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A62656C6B696E2E336364
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B000103104700104B5EB5C31AB05F9BB495A4507A5B85F11021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303220763110240007312E30302E31301042000E31323131353247463131313839321054000800060050F20400011011001D42656C6B696E204E363030444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"063fb2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024468fc5614
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0006303633666232
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1




**** blacklist.conf ****




# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac




**** dmesg ****




[    0.791215] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 91de7a0b580f416d81726d1f7134a3ecef081207'
[   12.295183] wmi: Mapper loaded
[   12.345377] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.345382] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   12.441782] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.441787] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.441937] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[   12.489749] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.905356] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   15.972719] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.973078] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.791368] type=1400 audit(1367953853.486:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=984 comm="apparmor_parser"
[   22.984897] wlan0: authenticate with <MAC address removed>
[   22.985799] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.987548] wlan0: authenticated
[   22.988052] wlan0: associate with <MAC address removed> (try 1/3)
[   22.990678] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   22.992086] wlan0: associated
[   22.992116] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3500.216310] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3500.241905] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[ 3517.703053] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 3517.703058] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 3517.742527] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 3517.742536] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 3517.742712] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[ 3517.743202] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 3517.762040] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[ 3517.828996] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3517.829576] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3524.812931] wlan0: authenticate with <MAC address removed>
[ 3524.813866] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3524.815776] wlan0: authenticated
[ 3524.820057] wlan0: associate with <MAC address removed> (try 1/3)
[ 3524.822739] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 3524.824059] wlan0: associated
[ 3524.824108] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5057.504223] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 5061.057802] wlan0: authenticate with <MAC address removed>
[ 5061.060491] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5061.062505] wlan0: authenticated
[ 5061.064026] wlan0: associate with <MAC address removed> (try 1/3)
[ 5061.066688] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 5061.068412] wlan0: associated
[11138.504147] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[11142.057322] wlan0: authenticate with <MAC address removed>
[11142.057874] wlan0: send auth to <MAC address removed> (try 1/3)
[11142.062494] wlan0: authenticated
[11142.066331] wlan0: associate with <MAC address removed> (try 1/3)
[11142.069406] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11142.071249] wlan0: associated
[19225.500083] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[19229.061571] wlan0: authenticate with <MAC address removed>
[19229.062419] wlan0: send auth to <MAC address removed> (try 1/3)
[19229.064931] wlan0: authenticated
[19229.068071] wlan0: associate with <MAC address removed> (try 1/3)
[19229.070814] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[19229.072084] wlan0: associated
[33297.488223] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[33301.049120] wlan0: authenticate with <MAC address removed>
[33301.050033] wlan0: send auth to <MAC address removed> (try 1/3)
[33301.051837] wlan0: authenticated
[33301.057655] wlan0: associate with <MAC address removed> (try 1/3)
[33301.060412] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[33301.062964] wlan0: associated
[33576.488215] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[33580.041445] wlan0: authenticate with <MAC address removed>
[33580.042212] wlan0: send auth to <MAC address removed> (try 1/3)
[33580.044178] wlan0: authenticated
[33580.048038] wlan0: associate with <MAC address removed> (try 1/3)
[33580.050833] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[33580.052225] wlan0: associated
[52094.492179] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[52098.057078] wlan0: authenticate with <MAC address removed>
[52098.058692] wlan0: send auth to <MAC address removed> (try 1/3)
[52098.060534] wlan0: authenticated
[52098.065752] wlan0: associate with <MAC address removed> (try 1/3)
[52098.068507] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[52098.069812] wlan0: associated
[52184.492182] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[52188.049698] wlan0: authenticate with <MAC address removed>
[52188.050441] wlan0: send auth to <MAC address removed> (try 1/3)
[52188.052340] wlan0: authenticated
[52188.056206] wlan0: associate with <MAC address removed> (try 1/3)
[52188.058899] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[52188.062660] wlan0: associated
[54296.504225] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[54300.073339] wlan0: authenticate with <MAC address removed>
[54300.074573] wlan0: send auth to <MAC address removed> (try 1/3)
[54300.079239] wlan0: authenticated
[54300.084047] wlan0: associate with <MAC address removed> (try 1/3)
[54300.086832] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[54300.088198] wlan0: associated
[68342.504142] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[68346.061194] wlan0: authenticate with <MAC address removed>
[68346.062110] wlan0: send auth to <MAC address removed> (try 1/3)
[68346.064303] wlan0: authenticated
[68346.068839] wlan0: associate with <MAC address removed> (try 1/3)
[68346.073625] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[68346.075096] wlan0: associated
[75377.432324] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[75390.427894] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[75390.427898] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[75390.467280] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[75390.467286] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[75390.467437] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[75390.469106] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[75390.484397] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[75390.557161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75390.557755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75397.560937] wlan0: authenticate with <MAC address removed>
[75397.561744] wlan0: send auth to <MAC address removed> (try 1/3)
[75397.563618] wlan0: authenticated
[75397.564089] wlan0: associate with <MAC address removed> (try 1/3)
[75397.572289] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[75397.573815] wlan0: associated
[75397.573864] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready




**************** done ********************



```

---

### Post by varunendra on 2013-05-08
Nothing looks suspicious in there except that you are currently using the most used channel in the neighborhood. But you already tried changing the channel, as you posted earlier, with no improvements. So at the moment, I'm left with only a few more suggestions :

[LIST=1]
[*]Try changing the channel again with a least used one (maybe channel 6, if that is allowed based on your regional settings.)
[*]Permanently disable IPv6 as mentioned in this post : [http://ubuntuforums.org/showthread.php?t=2139065&p=12631003#post12631003](http://ubuntuforums.org/showthread.php?t=2139065&p=12631003#post12631003)
[*]If the encryption is set to WPA/WPA2 mixed mode, try changing it to WPA2 only in the router. You may try the swcrypto=1 parameter again if the encryption is changed.
[*]The bit rate seems to be on auto. Try fixing it to a decent speed, say, 48 Mbps : ```
sudo iwconfig wlan0 rate 48M
```
[/LIST]

Try one at a time (leave the IPv6 disabled, you are not using it anyway). If none of this helps, then I'm out of ideas I'm afraid, but still I'd like to see-
```
ifconfig
[s]grep -iR [0-9a-z] /sys/module/[COLOR="#FF0000"]iwl_legacy[/COLOR]/parameters/[/s]
grep -iR [0-9a-z] /sys/module/**iwl-legacy**/parameters/
grep -iR [0-9a-z] /sys/module/iwl3945/parameters/
```
..without much hope.

---

### Post by chili555 on 2013-05-08
@Varun--

I am troubled by this:> ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after **500ms**, disconnecting.There is a parameter here:```
$ modinfo mac80211
filename:       /lib/modules/3.8.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2B2B66D5E403FA4D5C2715F
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
[COLOR="#FF0000"]parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)[/COLOR]
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

```You might try 1000 or 2000 to see if it helps. Post back or PM if you need help.

I strongly suggest channel 1 or 11 and WPA2-PSK only.

---

### Post by varunendra on 2013-05-08
> **chili555 said:**
> @Varun--

I am troubled by this...

Never really looked at it. But there are many things in outputs (in fact most of things in syslog, and dmesg) that I still keep ignoring because I don't understand them and/or don't know values they can take.

Thanks for the input doc, I'll wait for the feedback more eagerly now. :)

---

### Post by icu12345 on 2013-05-09
> **varunendra said:**
> Nothing looks suspicious in there except that you are currently using the most used channel in the neighborhood. But you already tried changing the channel, as you posted earlier, with no improvements. So at the moment, I'm left with only a few more suggestions :

[LIST=1]
[*]Try changing the channel again with a least used one (maybe channel 6, if that is allowed based on your regional settings.)
[*]Permanently disable IPv6 as mentioned in this post : [http://ubuntuforums.org/showthread.php?t=2139065&p=12631003#post12631003](http://ubuntuforums.org/showthread.php?t=2139065&p=12631003#post12631003)
[*]If the encryption is set to WPA/WPA2 mixed mode, try changing it to WPA2 only in the router. You may try the swcrypto=1 parameter again if the encryption is changed.
[*]The bit rate seems to be on auto. Try fixing it to a decent speed, say, 48 Mbps : ```
sudo iwconfig wlan0 rate 48M
```
[/LIST]

Try one at a time (leave the IPv6 disabled, you are not using it anyway). If none of this helps, then I'm out of ideas I'm afraid, but still I'd like to see-
```
ifconfig
grep -iR [0-9a-z] /sys/module/iwl_legacy/parameters/
grep -iR [0-9a-z] /sys/module/iwl3945/parameters/
```
..without much hope.

Tried a lot of different channels before starting the thread.. So I guess we can rule wrong wireless channel out. Disabled IPv6 and set speed to 48 Mb/s. I am still about to change the encryption. Will give feedback immediately after I give it a try. Here's the output of the commands you requested:
 ```
icefire@Toshiba:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:5d:46:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117090 (117.0 KB)  TX bytes:117090 (117.0 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.1.200  P-t-P:192.168.1.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:317287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:437969928 (437.9 MB)  TX bytes:15159602 (15.1 MB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:ae:d0:ea  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:385049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:329009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:528594052 (528.5 MB)  TX bytes:45125380 (45.1 MB)



```
```
icefire@Toshiba:~$ grep -iR [0-9a-z] /sys/module/iwl_legacy/parameters/grep: /sys/module/iwl_legacy/parameters/: No such file or directory

```
```

icefire@Toshiba:~$ grep -iR [0-9a-z] /sys/module/iwl3945/parameters/
/sys/module/iwl3945/parameters/swcrypto:1
/sys/module/iwl3945/parameters/fw_restart:1
/sys/module/iwl3945/parameters/disable_hw_scan:1
/sys/module/iwl3945/parameters/antenna:0



```
> **chili555 said:**
> @Varun--

I am troubled by this:There is a parameter here:```
$ modinfo mac80211
filename:       /lib/modules/3.8.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2B2B66D5E403FA4D5C2715F
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
[COLOR=#FF0000]parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)[/COLOR]
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

```You might try 1000 or 2000 to see if it helps. Post back or PM if you need help.

I strongly suggest channel 1 or 11 and WPA2-PSK only.

Thanks for helping ;) I am very new to linux and need some more explanation.. sorry for that. So, just to make sure I've got it right, I did the following:
1. [COLOR=#000000][FONT=verdana]sudo gedit /etc/modprobe.d/mac80211.conf
2. Added this line: [/FONT][/COLOR][COLOR=#000000][FONT=verdana]options mac80211 probe_wait_ms=1000
[/FONT][/COLOR]
Did I get i right?

Otherwise, the overall internet performance is sometimes ok, however, it is not constant. What is always causing trouble is my vpn connection. It's just a simple pptp vpn.. why is it so slow on this computer? This is what's troubling me..

---

### Post by varunendra on 2013-05-09
> **icu12345 said:**
> ```
icefire@Toshiba:~$ grep -iR [0-9a-z] /sys/module/**[COLOR="#FF0000"]iwl_legacy[/COLOR]**/parameters/grep: /sys/module/iwl_legacy/parameters/: [COLOR="#FF0000"]No such file or directory[/COLOR]

```
My mistake! It was a hyphen, not an underscore :
```
grep -iR [0-9a-z] /sys/module/[COLOR="#FF0000"]iwl-legacy[/COLOR]/parameters/
```

The other parameters look okay to me.


> ....just to make sure I've got it right, I did the following:
1. sudo gedit /etc/modprobe.d/mac80211.conf
2. Added this line: options mac80211 probe_wait_ms=1000

Did I get i right?
Looks right to me. Just make sure there are no spaces before or after the line : **options mac80211 probe_wait_ms=1000**

---

### Post by chili555 on 2013-05-09
> Looks right to me. And to me. Now are there any more "...No probe response from AP <MAC address removed> after 1000ms, disconnecting...." in dmesg?

---

### Post by icu12345 on 2013-05-09
I kinda tried all possible options..:
```
grep: /sys/module/iwl-legacy/parameters/: No such file or directoryicefire@Toshiba:~$ grep -iR [0-9a-z] /sys/module/iwllegacy/parameters/
grep: /sys/module/iwllegacy/parameters/: No such file or directory
icefire@Toshiba:~$ grep -iR [0-9a-z] /sys/module/iwl-legacy/parameters/
grep: /sys/module/iwl-legacy/parameters/: No such file or directory
icefire@Toshiba:~$ grep -iR [0-9a-z] /sys/module/iwl_legacy/parameters/
grep: /sys/module/iwl_legacy/parameters/: No such file or directory

```

[COLOR=#000000]"No probe response from AP <MAC address removed> after *xxxx* ms" doesn't seem to appear any more...[/COLOR]


```

**** dmesg ****
[    0.791360] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 91de7a0b580f416d81726d1f7134a3ecef081207'
[   12.932471] wmi: Mapper loaded
[   13.179849] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.179854] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   13.234176] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.234182] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.234331] iwl3945 0000:03:00.0: irq 48 for MSI/MSI-X
[   13.241510] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.844903] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   17.912841] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.306207] type=1400 audit(1368114146.001:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=986 comm="apparmor_parser"
[   24.889838] wlan0: authenticate with <MAC address removed>
[   24.892498] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.896052] wlan0: authenticated
[   24.900031] wlan0: associate with <MAC address removed> (try 1/3)
[   24.902795] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   24.904164] wlan0: associated
[   24.904192] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

However, vpn performance is still tragic. Internet and LAN performance is OK at the moment but it changes over time and isn't constantly good. I thought that speedtest.net is maybe not a reliable speed testing tool, so I tried downloading the ubuntu 13.04 iso file from ubuntu.com on the laptop in question and then on another laptop (the other laptop is very similar to the one in question). The other one had a constant speed of 2,3 MB/s and this one had variable speed between 1 and 2,3 MB/s....

---

### Post by ahallubuntu on 2013-05-09
Let me suggest that to solve this problem, you need to simplify it as much as possible and isolate the most simple test cases.  You said in your first post that copying files over the local network is slow.  FIX THAT FIRST, and worry about your VPN performance (if still an issue) later.

If you've determined that your local network really is as fast as it should be - then it's probably a VPN configuration problem, not a "network" problem.  But, if you can plug in the laptop to a wired ethernet connection and try it without wireless connected, that also might tell you something about "VPN performance" without wireless as a variable.

And I repeat what I said earlier: by choosing to go with the very new 13.04, you are choosing to make it harder for yourself than sticking with the much more stable 12.04 LTS release that is supported until April 2017.  I've been using Ubuntu for years and haven't even booted 13.04 (and perhaps never will).  12.04 works very well for me.  Experienced Linux users who want the latest and greatest versions of everything can go ahead and trailblaze with the newer versions.

You might consider upgrading your wireless card anyway, even though I doubt it will have any impact on your current problems.  But you'll get N connections to an N router; for the cheap upgrade price, well worth it.

---

### Post by varunendra on 2013-05-09
> **icu12345 said:**
> I kinda tried all possible options..
Figured out! In 13.04, they've changed the name of the module (why do they keep doing this??) : iwlegacy.
However, be informed that the command was meant to only show us what parameters the module is loaded with. It is only the 'bt_coex_active' parameter that I was initially interested in, but with another review of the description of the problem, it hardly seems relevant.

> **ahallubuntu said:**
> Let me suggest that to solve this problem, you need to simplify it as much as possible and isolate the most simple test cases.
..
..by choosing to go with the very new 13.04, you are choosing to make it harder for yourself than sticking with the much more stable 12.04 LTS release that is supported until April 2017.
..
..You might consider upgrading your wireless card anyway, even though I doubt it will have any impact on your current problems.  But you'll get N connections to an N router; for the cheap upgrade price, well worth it.
I agree with what he said, although there is no guarantee of an improved performance with an LTS.
You may try a live cd of 12.04 to see if it makes any difference. I'd suggest to go with 64 bit if your laptop supports it.

---

### Post by icu12345 on 2013-05-10
I have already tried live cds with Xubuntu 12.10 and Ubuntu 12.04 LTS before starting the thread but didn't mention this as it seemed hardly relevant....

At the moment I am getting LAN transfer speeds of 1,0 MB/s which is a significant improvement over the initial state. How did this happen? I guess the modification of the parse time had a positive effect because nothing else has changed..
 
However the VPN problem remains. I'm going to hook it up to a wired connection and see what happens.

---

### Post by icu12345 on 2013-05-10
Update: Tried a wired connection and the VPN transfer speed was as miserable as when using wireless. So this is a VPN issue..

For the time being I would focus on the vpn issue as it is a bigger problem...

The settings at the moment are like this:

[IMG]http://img90.imageshack.us/img90/7405/screenshotfrom201305101.png[/IMG]

Use Point-to-Point encryption must be checked, because the server is set up to reject not encrypted connections. Tried playing with the other options (stateful encryption, BSD data compression, Deflate data compression and TCP header compression) but there was no difference... Also tried send PPP echo packets but it didn't bring anything..

---

### Post by icu12345 on 2013-05-10
...and my dd-wrt setup...
[IMG]http://img7.imageshack.us/img7/92/selection002ax.png[/IMG]

---

### Post by varunendra on 2013-05-10
icu12345,

It seems your wireless issue has been sorted out and the VPN issue, as you found yourself, is unrelated and a whole different thing that we may not be able to help with.

Accordingly, I think you may thank Dr. Chili555 and mark this thread as [Solved], as it does contain a solution (suggested by him) that improves the wireless connectivity.

As for the VPN issue, I'm sure you'll get much better help if you post the problem in "Sever Platforms" section of the forums. You may start a new thread there and post a link to this thread in it, if seems relevant, as reference. Alternately you may request the mods (using the "Report Post" button) to move your last two posts to a new thread in a suitable section with a title that is more relevant to the VPN issue.

Since wireless and VPN are different issues, it will also be more helpful for others looking for help on one of the issues, if the two problems are discussed separately.

Just an opinion :)

Good Luck!

---

### Post by icu12345 on 2013-05-10
[COLOR=#000000]Dr. Chili555, thank you for your support, you really helped me out here.
[/COLOR]varunendra, thanks for your advice. The thread now moves here: [http://ubuntuforums.org/showthread.php?t=2144004&p=12642539](http://ubuntuforums.org/showthread.php?t=2144004&p=12642539)
(in order to keep the thread clean my last 2 posts could be deleted)

---

