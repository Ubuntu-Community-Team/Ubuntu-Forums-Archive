---
title: "Broadcom 4313 seems erratic ..."
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2013-04-29
... in my 3 day old kubuntu raring install, though I think it was giving me more problems under 12.04.  But it cuts out sometimes, and the signal strength indicator in system tray fluctuates occasionally.  So I'm not sure the configuration is quite right.  Everything else works great.

Here's some info, gleaned from other threads.  Hope it's enough.

$ lspci -nnd 14e4:
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```
$ rfkill list all
```
0: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
$ $ dmesg | grep wl
[   19.830152] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.831087] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.975070] wlan0: authenticate with 00:1a:70:4c:d4:30
[   41.977588] wlan0: send auth to 00:1a:70:4c:d4:30 (try 1/3)
[   41.980244] wlan0: authenticated
[   41.980841] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   41.980856] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   41.983797] wlan0: associate with 00:1a:70:4c:d4:30 (try 1/3)
[   41.985893] wlan0: RX AssocResp from 00:1a:70:4c:d4:30 (capab=0x401 status=0 aid=2)
[   41.987406] wlan0: associated
[   41.987467] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```
$ sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 04:7d:7b:50:97:53
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:40004000-40004fff memory:40000000-40003fff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:44000000-44003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:18:85:0e:f5:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-19-generic firmware=N/A ip=192.168.65.151 link=yes multicast=yes wireless=IEEE 802.11bgn

```
$ sudo lspci -vk | grep -iA13 net
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
        Subsystem: Acer Incorporated [ALI] Device 061f
        Flags: bus master, fast devsel, latency 0, IRQ 43
        I/O ports at 4000 [size=256]
        Memory at 40004000 (64-bit, prefetchable) [size=4K]
        Memory at 40000000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 80-05-00-00-36-4c-e0-00
--
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Foxconn International, Inc. Device e042
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 44000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-85-ff-ff-0e-c0-18
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: bcma-pci-bridge
```

$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 04:7d:7b:50:97:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:184382 (184.3 KB)  TX bytes:184382 (184.3 KB)

wlan0     Link encap:Ethernet  HWaddr c0:18:85:0e:f5:ac  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c218:85ff:fe0e:f5ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:665388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:525620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:580925921 (580.9 MB)  TX bytes:450966340 (450.9 MB)

```
$ iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"***deleted for privacy***"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:4C:D4:30   
          Bit Rate=24 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:115  Invalid misc:2531   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

$ lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            47684  1 
snd_hrtimer            12648  1 
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
arc4                   12543  2 
brcmsmac              521468  0 
cordic                 12518  1 brcmsmac
brcmutil               14355  1 brcmsmac
mac80211              526519  1 brcmsmac
coretemp               13131  0 
acer_wmi               27592  0 
cfg80211              436177  2 brcmsmac,mac80211
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek    63791  1 
snd_hda_codec_hdmi     36185  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
joydev                 17097  0 
videobuf2_core         39161  1 uvcvideo
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               95806  2 uvcvideo,videobuf2_core
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  3 snd_hrtimer,snd_pcm,snd_seq
mac_hid                13037  0 
rtsx_pci_ms            12875  0 
lpc_ich                16925  0 
memstick               15842  1 rtsx_pci_ms
snd                    56485  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
bcma                   39645  1 brcmsmac
soundcore              12600  1 snd
psmouse                81038  0 
serio_raw              13031  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
microcode              18286  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
rtsx_pci_sdmmc         17238  0 
gma500_gfx            167754  2 
i2c_algo_bit           13197  1 gma500_gfx
ahci                   25507  2 
libahci                26108  1 ahci
drm_kms_helper         47545  1 gma500_gfx
wmi                    18590  1 acer_wmi
drm                   228750  3 drm_kms_helper,gma500_gfx
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
video                  18894  2 acer_wmi,gma500_gfx
r8169                  61531  0 

```
$ cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

loop
lp
```

$ grep blacklist /etc/modprobe.d/blacklist.conf
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

```
$ lspci -vvnn | grep 14e4
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```
$ lsmod | grep brc
```
brcmsmac              521468  0 
cordic                 12518  1 brcmsmac
brcmutil               14355  1 brcmsmac
mac80211              526519  1 brcmsmac
cfg80211              436177  2 brcmsmac,mac80211
bcma                   39645  1 brcmsmac

```

I'm a bit weak re wireless, and after looking at all this i'm not even sure which driver I'm actually using.  According to what I've been able to find brcmsmac is the one I want, but I'm not sure in this case.

I have alson  found that searching can lead you to many more hits on the wrong way than the right way.  Hoping someone can point me in the right direction.

---

### Post by dandroid13 on 2013-04-29
Are you using bcmwl-kernel-source?
Edit: Try installing this ([http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)), it is what solved my issues with BCM4313.

---

### Post by Rob Sayer on 2013-04-29
I saw a reference to that.  I'll check it out.

Thanks for the response.

---

### Post by Rob Sayer on 2013-04-30
> **dandroid13 said:**
> Are you using bcmwl-kernel-source?
Edit: Try installing this ([http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)), it is what solved my issues with BCM4313.


I looked it up and found something regarding raring in a machine with the same wireless id (14e4:4727 ... there are more than one broadcom 4313 adapters).  He had to remove bcmwl-kernel-source.  Doesn't sound right to me at this point.

Thanks anyway.

Any other ideas?

---

