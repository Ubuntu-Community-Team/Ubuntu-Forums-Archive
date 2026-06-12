---
title: "Ubuntu 10.04  LTS - Wireless Broadcom PCI Card"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by LifeOfRyan on 2011-06-15
Hello everyone, im guessing some of you have heard this a million times but yes i do need help setting up my wireless. I have managed to gather this information below using a script which i found at [http://www.linuxforums.org/forum/wireless-internet/137532-wireless-setup-start-here.html](http://www.linuxforums.org/forum/wireless-internet/137532-wireless-setup-start-here.html)

Any help advice will be much appreciated, many thanks, Ryan.

                     >    	 	 	 	pre { font-family: "Times New Roman"; }p { margin-bottom: 0.21cm; }  ============ lspci ============
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
	Kernel modules: intel-agp
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400 GS] [10de:0422] (rev a1)
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
	Kernel driver in use: r8169
	Kernel modules: r8169

============ lsusb ============
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 004 Device 002: ID 0566:3002 Monterey International Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 05dc:a788 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

============ lsmod ============
Module                  Size  Used by
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8933  2 
fat                    47767  1 vfat
usb_storage            39553  2 
aes_i586                7268  192 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
dm_crypt               11331  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   163524  0 
ppdev                   5259  0 
mac80211              205402  1 b43
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126528  2 b43,mac80211
led_class               2864  1 b43
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
nouveau               467048  2 
ttm                    49943  1 nouveau
drm_kms_helper         29329  1 nouveau
drm                   162409  4 nouveau,ttm,drm_kms_helper
ssb                    38934  1 b43
usbhid                 36110  0 
r8169                  34108  0 
mii                     4381  1 r8169
hid                    67064  1 usbhid
intel_agp              24375  0 
floppy                 53016  0 
agpgart                31724  3 ttm,drm,intel_agp
i2c_algo_bit            5028  1 nouveau

============ dmesg-firmware ============
[   10.648068] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   10.683375] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   10.697519] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   10.808429] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   10.822688] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   10.830596] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

============ kernel version ============
2.6.32-28-generic

============ ifconfig ============
eth0      Link encap:Ethernet  HWaddr 00:15:58:6e:c5:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680512 (680.5 KB)  TX bytes:680512 (680.5 KB)


============ iwconfig ============
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
           

---

### Post by chili555 on 2011-06-15
If you have an ethernet connection, open a terminal and do:```
sudo apt-get install b43-fwcutter
```Let it hum and whirr and buzz and when it's all done, detach the ethernet cable, reboot and enjoy your new wireless!

---

### Post by LifeOfRyan on 2011-06-15
thanks for the swift reply, i did as you said and under hardware drivers there is now a b43 broadcom driver, but i still cant detect any networks?

---

### Post by chili555 on 2011-06-15
Please reboot and let me see, from a terminal:```
dmesg | grep -i b43
```Thanks.

---

### Post by LifeOfRyan on 2011-06-16
The terminal shows 

> [    1.328567] b43-pci-bridge 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.219052] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.361352] Registered led device: b43-phy0::tx
[   10.361374] Registered led device: b43-phy0::rx
[   10.361395] Registered led device: b43-phy0::radio
[   11.076058] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   11.113274] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   11.124964] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   11.136811] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   11.292946] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)thanks

---

### Post by chili555 on 2011-06-16
It looks terrific! Now let's see:```
dmesg | grep -i b43
iwconfig
rfkill list all
```Thanks.

---

### Post by LifeOfRyan on 2011-06-16
the connection is now working thank you all for your help

---

