---
title: "Lenovo Thinkpad E420 Wireless not working"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by dosh on 2011-12-30
Have just got a new Lenovo Thinkpad E420 and as stated elsewhere the Wireless networking does not work. I have tried a number of solutions, such as "blacklist acer_wmi", nothing seems to work.

I ran a  lspci result as below

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
08:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)

Any help much appreciated.

---

### Post by dosh on 2011-12-30
Here is more information for the problem.

After running the following commands

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 5986:03b3 Acer, Inc 
Bus 002 Device 003: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
```


ifconfig
```
eth0      Link encap:Ethernet  HWaddr f0:de:f1:ae:6e:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```


lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
wl                   2646601  0 
btusb                  18160  2 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
thinkpad_acpi          73942  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvram                  14029  1 thinkpad_acpi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
lib80211               14570  1 wl
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
psmouse                73673  0 
drm_kms_helper         32889  1 i915
serio_raw              12990  0 
bluetooth             148839  23 bnep,rfcomm,btusb
drm                   192226  4 i915,drm_kms_helper
bcma                   19571  0 
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  3 
sdhci_pci              13658  0 
libahci                25727  1 ahci
sdhci                  27360  1 sdhci_pci
r8169                  43104  0
```

sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:ae:6e:7d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:d1d00000-d1d03fff
```

lsb_release -d
```
Description:	Ubuntu 11.10
```

uname -mr
```
3.0.0-12-generic i686
```

sudo /etc/init.d/networking restart
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```

---

### Post by dosh on 2011-12-30
more informationon the problem

Broadcom STA wirless driver - is showing "This driver is activated and currently in use.

the Network Icon (near clock) is not showing Wireless item.

---

### Post by wildmanne39 on 2011-12-30
Hi, go to this link:
[http://ubuntuforums.org/showthread.php?p=11573648#post11573648](http://ubuntuforums.org/showthread.php?p=11573648#post11573648)
Run  the last three commands in post 4 then unplug your wired connection and reboot.
Thanks

---

### Post by dosh on 2011-12-31
wildmanne39 thanks so much that worked well  :P
HAPPY NEW YEAR

---

### Post by wildmanne39 on 2011-12-31
Hi, your welcome! Glad it worked.
Enjoy

---

### Post by _nex_ on 2012-01-05
That didn't work on my Ubunu 11.10 :S 

Vivek Kapoor [FIX]("http://exain.wordpress.com/2011/10/16/wireless-on-ubuntu-11-10-and-lenovo-thinkpad-e420/") worked on my machine.

It was fixed adding *acer_wmi* to the blacklist

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d
/blacklist.conf
```

---

