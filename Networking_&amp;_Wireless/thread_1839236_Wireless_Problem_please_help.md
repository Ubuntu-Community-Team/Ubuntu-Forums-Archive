---
title: "Wireless Problem please help"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by Katarnstar on 2011-09-05
Hi I'm new to Ubuntu.

I've been having problems with my wireless. It works fine in Windows 7 but in Ubuntu.

I've been in to 'Terimal' and asked for wireless/ethernet details.

 *-network                
        description: Network controller  
        product: BCM4306 802.11b/g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 7  
        bus info: pci@0000:04:07.0  
        version: 03  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=64  
        resources: irq:22 memory:feafe000-feafffff  
   *-network  
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        logical name: eth0  
        version: 06  
        serial: 48:5b:39:c9:3f:a0  
        size: 10MB/s  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  
        resources: irq:46 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febf0000-febfffff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:0f:66:f2:b6:29  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg  
 

From what I can see Ubuntu can see theres a wireless hareware install, but can't do anything with it, I don't know what to do.

I'm using Ubuntu 10.10.

Regards 

Katarnstar

---

### Post by SnowCrash89 on 2011-09-05
When I see " network DISABLED " in lshw this usually suggests I need to enable networking by right-clicking on the networking icon on the panel. Perhaps you should check that.

---

### Post by praseodym on 2011-09-05
Hello,

the device BCM4306 can have several chipsets installed. Please show the outputs of:

```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
sudo iwlist scan
dmesg | grep b43
```

---

### Post by Katarnstar on 2011-09-06
SnowCrash89: the icon in the panel says "firmware missing".

praseodym: I typed in the code, here it is:

robert@Orion:~$ lspcl -nnk | grep -iA2 net
No command 'lspcl' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lspcl: command not found
robert@Orion:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
robert@Orion:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
robert@Orion:~$ lsmod
Module                  Size  Used by
isofs                  30022  1 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
ums_cypress             2198  0 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
usb_storage            40172  2 ums_cypress
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
radeon                825934  2 
snd_seq_midi_event      6047  1 snd_seq_midi
b43                   168681  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  1 b43
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           11423  0 
cfg80211              144470  2 b43,mac80211
drm                   168054  4 radeon,ttm,drm_kms_helper
xhci_hcd               51737  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2633  1 b43
agpgart                32011  2 ttm,drm
k10temp                 2607  0 
i2c_algo_bit            5168  1 radeon
i2c_piix4               8635  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ssb                    39288  1 b43
pata_via                7300  0 
r8169                  36489  0 
mii                     4425  1 r8169
ahci                   19013  0 
libahci                21667  2 ahci
pata_atiixp             3288  2 
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
robert@Orion:~$ sudo iwlist scan
[sudo] password for robert: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

robert@Orion:~$ dmesg | grep b43
[    1.823323] b43-pci-bridge 0000:04:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.937633] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[    8.988938] Registered led device: b43-phy0::tx
[    8.988950] Registered led device: b43-phy0::rx
[    8.988960] Registered led device: b43-phy0::radio
[   10.190476] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.190479] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.190481] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
robert@Orion:~$

---

### Post by praseodym on 2011-09-06
Just install the missing firmware via

```
sudo apt-get install b43-fwcutter
```
If you update to 11.04 you additionally have to install the package **firmware-b43-installer**. This package is not available in 10.10.

You had a typo, it has to be **lspci** ( with i like internet) not **lspcl** (l like Lubuntu)

---

### Post by Katarnstar on 2011-09-12
That annoying its now saying it can't install b43-fwcutter.

---

### Post by praseodym on 2011-09-12
I attached the firmware package here. Unpack it from your Desktop via:

```
sudo tar xvf ~/Desktop/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

