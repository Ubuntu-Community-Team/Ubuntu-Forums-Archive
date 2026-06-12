---
title: "drastically slow internet"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by busstopbill44 on 2012-02-01
hello there, i installed ubuntu alongside windows 7 on my Dell XPS 1647. after installation i noticed the wifi in 11.10 is extremely slow, ive been all over the internet and cant figure it out, please help, thanks in advance! here are some info/codes.
lspci
> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
04:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
07:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
lsusb
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:640f Microdia 
Bus 002 Device 003: ID 03f0:8307 Hewlett-Packard 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 005: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 006: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 002 Device 007: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
ifconfig
> eth0      Link encap:Ethernet  HWaddr f0:4d:a2:60:4b:e3  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:fe60:4be3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16218897 (16.2 MB)  TX bytes:1630016 (1.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:27:10:b8:05:c0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:10ff:feb8:5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2519156 (2.5 MB)  TX bytes:405095 (405.0 KB)iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:4E:7F:0D:7F:7E   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1127  Invalid misc:66   Missed beacon:0iwconfig wlan0
> [FONT=monospace]wlan0     IEEE 802.11abgn  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:4E:7F:0D:7F:7E   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1127  Invalid misc:66   Missed beacon:0[/FONT]lsmod
> Module                  Size  Used by
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
btusb                  18160  2 
bluetooth             148839  23 rfcomm,bnep,btusb
arc4                   12473  2 
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_lirc_codec          12770  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
fglrx                2595537  121 
lirc_dev               18700  1 ir_lirc_codec
joydev                 17393  0 
ir_sony_decoder        12493  0 
snd_seq_midi           13132  0 
ir_jvc_decoder         12490  0 
iwlagn                273937  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
rc_rc6_mce             12454  0 
ir_rc5_decoder         12490  0 
mac80211              393459  1 iwlagn
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172427  2 iwlagn,mac80211
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
dell_wmi               12601  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
sparse_keymap          13658  1 dell_wmi
ir_nec_decoder         12490  0 
ite_cir                24743  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,ite_cir
intel_ips              17753  0 
psmouse                63474  0 
serio_raw              12990  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  18908  0 
wmi                    18744  1 dell_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25761  1 ahci
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
tg3                   132972  0

---

### Post by busstopbill44 on 2012-02-02
150 views, someone has to know something. maybe?

---

### Post by BlinkinCat on 2012-02-02
> **busstopbill44 said:**
> 150 views, someone has to know something. maybe?

Hi and welcome to the forums,

All workers here are volunteers - It may be possible that some-one with the expertize to solve your problem is simply just not around.

B.T.W. It is normal practice here to bump your thread after 24 hours - all the best - :)

---

### Post by jonobr on 2012-02-03
Hello


Have you tried the IPV6 fix or changing MTU to see if this affects your speed.

May be good to compare your settings to your windows install also.

Also, compare DNS settings between the two to see if your getting the same in ubuntu as in windows.

---

### Post by praseodym on 2012-02-03
Hi,

the N-mode of the driver is buggy. You can deactivate it via:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```

---

### Post by busstopbill44 on 2012-02-04
awesome! thanks a bunch praseodym, speed is back to normal, now to take advantage of this awesome OS

---

### Post by BlinkinCat on 2012-02-07
> **busstopbill44 said:**
> awesome! thanks a bunch praseodym, speed is back to normal, now to take advantage of this awesome OS

Really glad you got it fixed.

It could help others if you marked this thread as "solved" using the thread tools at top of page - :)

---

### Post by sandyeggoboy on 2012-02-10
WOW! You guys have no idea how many months i have been looking for this solution. 

THANK YOU!!!!:popcorn:

---

