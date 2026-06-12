---
title: "Instructions on installing driver for Edimax 7722In 11.10"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by mjsdude on 2012-03-30
I recently built my computer and everything works so far except the wireless adapter. I have looked on the forum and can not seem to make heads or tails of the solutions.I currently have the driver saved on my desktop as both the .zip, and the .tar.bz2 named EW-7722In_RT3062_Linux_STA_v2.4.0.0 with their appropriate file extensions. Any help whatsoever would be appreciated.

---

### Post by praseodym on 2012-03-31
Hi,

please show the outputs of:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Normally, you dont need to compile. If you want to do so, you need to install the tools for this via cable:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
tar xvf ~/Desktop/EW-7722In_RT3062_Linux_STA_v2.4.0.0.tar.bz2
cd ~/Desktop/EW-7722In_RT3062_Linux_STA_v2.4.0.0
make
sudo make install
```

---

### Post by mjsdude on 2012-03-31
Thanks for the reply. I went through the steps to compile, and wireless card still doesn't work. So here is the code you wanted. I noticed wireless card wasn't in all the way. Lights are now on, but I can't connect to the wi-fi at my house.
```
mjsdude@mjsdude-desktop:~$ uname -a
Linux mjsdude-desktop 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux
mjsdude@mjsdude-desktop:~$ lspci -nnk | grep -iA2 net
03:05.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Edimax Computer Co. Device [1432:7722]
	Kernel driver in use: rt2800pci
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet] [10ec:8168]
	Kernel driver in use: r8169
	Kernel modules: r8169
mjsdude@mjsdude-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 002: ID 1019:0c55 Elitegroup Computer Systems (ECS) Flash Reader, Desknote UCR-61S2B
mjsdude@mjsdude-desktop:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254163  1 
rt3562sta             814931  0 
snd_hda_codec_hdmi     31426  1 
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
usb_storage            44173  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uas                    17699  0 
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                73673  0 
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172427  2 rt2x00lib,mac80211
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rt2800pci
k10temp                12990  0 
i2c_piix4              13093  0 
snd_timer              28932  2 snd_seq,snd_pcm
fglrx                2595537  92 
snd                    55902  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci
pata_atiixp            12967  0 
xhci_hcd               72982  0 
mjsdude@mjsdude-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mjsdude@mjsdude-desktop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by praseodym on 2012-03-31
"lsusb" with stick plugged!

---

### Post by mjsdude on 2012-03-31
By stick you mean usb flash drive right?
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 002: ID 1019:0c55 Elitegroup Computer Systems (ECS) Flash Reader, Desknote UCR-61S2B
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36

```

---

### Post by praseodym on 2012-03-31
The wireless adapter is not shown! Check the BIOS settings and/or maybe resetting the BIOS to default.

---

### Post by mjsdude on 2012-03-31
Restored bios to defaults the device does show up under the first command you had posted ```
03:05.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Edimax Computer Co. Device [1432:7722]
	Kernel driver in use: rt2800pci
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet] [10ec:8168]
	Kernel driver in use: r8169
	Kernel modules: r8169

```. I also had noticed under additional drivers in settings it does shows that once I had plugged it into the pci slot properly a new driver showed up and is installed, and active. Problem now seems to be the inability to connect to a network.

---

### Post by mjsdude on 2012-03-31
I ended up getting it working using instructions from the other forum post all is well now. Thanks for your help. It really got the ball rolling to get this working.

---

### Post by placid2000 on 2012-05-01
> **mjsdude said:**
> I ended up getting it working using instructions from the other forum post all is well now. Thanks for your help. It really got the ball rolling to get this working.


Hello

I'm encoutering the same problem.

could you please give the url of the other forum?

Thanks in advance!

---

