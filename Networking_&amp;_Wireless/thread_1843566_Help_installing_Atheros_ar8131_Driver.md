---
title: "Help installing Atheros ar8131 Driver"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by chezza on 2011-09-13
Hi

Sorry if my first post is a wall of text but Im still finding my way around ubuntu and Im not sure what info will be useful.

I built a new PC today the motherboard is asus p54g41t-M LX

So the driver i need to install is  Atheros ar8131

Im using 10.04 (lynx)

Ive searched and tried to follow the help and the readme file but have got stuck and I dont understand enough about what im doing.

The driver is on the desktop = AR8131_AR8132-linux-v1.0.0.10.tar

I can 

1,

tar zxf AR8131_AR8132-linux-v1.0.0.10.tar.gz

which unzips

2,

I can then 
cd src

3,

make install

4, 
This is where I am stuck, the readme file says

insmod <parameter>=<value> 

What are goes in the <  >=<  >

Or am I way off with what Im attempting?

Thanks in advance

---

### Post by praseodym on 2011-09-13
Hi,

if the installation procedure was successful, you can just reboot. If the device ID is part of the driver, it will be loaded at boot-up.

Check after that:

```
lspci -nnk
```

---

### Post by chezza on 2011-09-13
Thanks, but now Ive looked at the terminal I think I need walking through the whole how to install if some one could do this please.

I have on the desktop 
AR8131_AR8132-linux-v1.0.0.10.tar

using the terminal I can unzip with 

tar zxf AR8131_AR8132-linux-v1.0.0.10.tar.gz

Which gives me a src folder and 6 .txt files

using terminal I can cd src 

The read me says to type

make install

which I do but then get the following in the terminal 


chez@TheBox:~/Desktop/src$ make install
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/chez/Desktop/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/chez/Desktop/src/atl1e_main.o
/home/chez/Desktop/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/chez/Desktop/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:117: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
/home/chez/Desktop/src/atl1e_main.c: In function ‘atl1e_probe’:
/home/chez/Desktop/src/atl1e_main.c:287: error: ‘struct net_device’ has no member named ‘open’
/home/chez/Desktop/src/atl1e_main.c:288: error: ‘struct net_device’ has no member named ‘stop’
/home/chez/Desktop/src/atl1e_main.c:289: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/chez/Desktop/src/atl1e_main.c:290: error: ‘struct net_device’ has no member named ‘get_stats’
/home/chez/Desktop/src/atl1e_main.c:291: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/chez/Desktop/src/atl1e_main.c:292: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/chez/Desktop/src/atl1e_main.c:293: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/chez/Desktop/src/atl1e_main.c:294: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/chez/Desktop/src/atl1e_main.c:305: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/chez/Desktop/src/atl1e_main.c:313: error: ‘struct net_device’ has no member named ‘vlan_rx_register’
/home/chez/Desktop/src/atl1e_main.c:316: error: ‘struct net_device’ has no member named ‘poll_controller’
make[2]: *** [/home/chez/Desktop/src/atl1e_main.o] Error 1
make[1]: *** [_module_/home/chez/Desktop/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [default] Error 2


so its not working but I dont know what to do ?

thanks

---

### Post by praseodym on 2011-09-13
Run

```
sudo make install
```
Did you install the kernel-headers and compiling tools?

Please show:

```
uname -a
lspci -nnk
lsmod
```

---

### Post by chezza on 2011-09-13
Thankyou

sudo make install (from the src folder) gives

chez@TheBox:~$ cd Desktop/src
chez@TheBox:~/Desktop/src$ sudo make install
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/chez/Desktop/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/chez/Desktop/src/atl1e_main.o
/home/chez/Desktop/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/chez/Desktop/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:117: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
/home/chez/Desktop/src/atl1e_main.c: In function ‘atl1e_probe’:
/home/chez/Desktop/src/atl1e_main.c:287: error: ‘struct net_device’ has no member named ‘open’
/home/chez/Desktop/src/atl1e_main.c:288: error: ‘struct net_device’ has no member named ‘stop’
/home/chez/Desktop/src/atl1e_main.c:289: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/chez/Desktop/src/atl1e_main.c:290: error: ‘struct net_device’ has no member named ‘get_stats’
/home/chez/Desktop/src/atl1e_main.c:291: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/chez/Desktop/src/atl1e_main.c:292: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/chez/Desktop/src/atl1e_main.c:293: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/chez/Desktop/src/atl1e_main.c:294: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/chez/Desktop/src/atl1e_main.c:305: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/chez/Desktop/src/atl1e_main.c:313: error: ‘struct net_device’ has no member named ‘vlan_rx_register’
/home/chez/Desktop/src/atl1e_main.c:316: error: ‘struct net_device’ has no member named ‘poll_controller’
make[2]: *** [/home/chez/Desktop/src/atl1e_main.o] Error 1
make[1]: *** [_module_/home/chez/Desktop/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [default] Error 2
chez@TheBox:~/Desktop/src$ 

I have not installed kernel-headers and compiling tools, I dont really know what these are, also no internet on the pc in 
question :redface

uname -a gives
chez@TheBox:~$ uname -a
Linux TheBox 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux


lspci -nnk gives
chez@TheBox:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
	Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e31] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
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
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:68f9]
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)

lsmod gives

chez@TheBox:~$ uname -a
Linux TheBox 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
chez@TheBox:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
	Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e31] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
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
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:68f9]
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
chez@TheBox:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  0 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 36110  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
hid                    67032  1 usbhid
parport_pc             25962  1 
asus_atk0110            9017  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
lp                      7028  0 
snd                    54148  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
vgastate                8961  1 vga16fb
parport                32635  3 ppdev,parport_pc,lp
intel_agp              24119  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  1 intel_agp
chez@TheBox:~$ 


Thanks again.

---

### Post by praseodym on 2011-09-13
You need these files:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.43_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.43_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb)

Save them on your desktop and install them via:

```
sudo dpkg -i ~/Desktop/*.deb
mkdir ~/Desktop/AR81xx
```
Then insert your installation CD/DVD, add it to your software sources, and install the package **build-essential** from it.

Imho your driver is too old, I attached a newer one, unpack it on your Desktop **into the folder AR81xx** and install:

```
cd ~/Desktop/AR81xx
make
sudo make install
```
Reboot and check the connection. If it works update your system:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-headers-generic dkms
```

---

### Post by chezza on 2011-09-13
You are awesome - will try this now

It did work, the internet is working and it is updating as I type.

I accidently missed the step with the installation cd, hopefully this wont be a problem in the future.

Again thank you, would never have got this working without your assistance

---

### Post by praseodym on 2011-09-14
:popcorn:

Just to be sure:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) dkms build-essential
```

---

