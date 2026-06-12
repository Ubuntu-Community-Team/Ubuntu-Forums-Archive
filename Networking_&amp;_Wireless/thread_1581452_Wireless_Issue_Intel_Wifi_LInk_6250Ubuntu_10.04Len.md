---
title: "Wireless Issue_Intel Wifi LInk 6250/Ubuntu 10.04/Lenovo Thinkpad T510"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by hinduguy on 2010-09-25
It looks like the native Linux drivers do not support my wifi card, it might be doing something wrong but does anyone know how get a hold of the correct drivers and how to install them.....

Think link is stating i am out of luck but its old [http://www.linlap.com/wiki/lenovo+thinkpad+t510](http://www.linlap.com/wiki/lenovo+thinkpad+t510)

1) Laptop\Lenovo\ThinkPad T510

2) Wireless Brand, Model and Wireless Chip-set
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NVS 3100M (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35)
0d:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```3) Check Interface 

```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:37:ff:e3  
          inet addr:10.0.1.17  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe37:ffe3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9404043 (9.4 MB)  TX bytes:1062747 (1.0 MB)
          Memory:f2400000-f2420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

bpatel@bpatel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.


```4) Check for Modules

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
joydev                  8708  0 
nvidia               9961216  41 
snd_hda_intel          21941  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                105694  0 
iwlcore               105922  1 iwlagn
tpm_tis                 7390  0 
tpm                    13484  1 tpm_tis
thinkpad_acpi          68083  0 
uvcvideo               56990  0 
nvram                   6171  1 thinkpad_acpi
tpm_bios                5266  1 tpm
videodev               34361  1 uvcvideo
mac80211              205146  2 iwlagn,iwlcore
video                  17375  0 
output                  1871  1 video
btusb                  10925  2 
snd                    54148  16 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
v4l1_compat            13251  2 uvcvideo,videodev
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 iwlcore,thinkpad_acpi,sdhci
intel_agp              24119  0 
cfg80211              126517  3 iwlagn,iwlcore,mac80211
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
psmouse                63245  0 
soundcore               6620  1 snd
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ahci                   32200  2 
ieee1394               81181  1 ohci1394
e1000e                119824  0 

```

---

