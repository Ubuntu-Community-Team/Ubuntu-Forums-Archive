---
title: "Wired network problems"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by dirtblack on 2011-11-12
I've got an issue with no network.  I'm using a wired network and have made sure the driver isn't blacklisted.  It's the r8169.  I did the lspci -nnk to look for it and it's present.  But... when I looked at startup stuff in the panel it shows that the network isn't installed in the panel. But it is there and I can configure it but it won't work to no avail.  It was working fine until I upgraded it. Any help would be greatly appreciated.  I'm using 11.10

---

### Post by dirtblack on 2011-11-13
Anyone?

---

### Post by praseodym on 2011-11-13
Hi,

please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by vandamme on 2011-11-13
Well, if it's sympathy you want, I have the same problem. Upgraded to 11.10, no ethernet. Other OS's work fine (Mint Debian, Windoze). Another forum suggested how to turn on auto eth0, but I can't find it now.

---

### Post by dirtblack on 2011-11-13
> **praseodym said:**
> Hi,

please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
```

Here are the commands and output you wanted. Thanks very much for helping.  I do know if I go up into the panel and right click on my network that wired network and device not managed are grayed out. Also when looking at startup applications in the panel nm-applet says missing network in panel.  

uname -a
Linux ubuntu 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 athlon i386 GNU/Linux

lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5B [1043:81aa]
	Kernel driver in use: r8169

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:1d:34:be  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe1d:34be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22582 (22.5 KB)  TX bytes:8487 (8.4 KB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2332 (2.3 KB)  TX bytes:2332 (2.3 KB)

lsmod
Module                  Size  Used by
hidp                   22351  0 
bnep                   17923  2 
rfcomm                 38408  12 
btusb                  18160  2 
bluetooth             148839  24 hidp,bnep,rfcomm,btusb
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
psmouse                63474  0 
binfmt_misc            17292  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
i2c_piix4              13093  0 
nouveau               667307  3 
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   196322  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
parport_pc             32114  1 
video                  18908  1 nouveau
asus_atk0110           17742  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
hid_logitech           17405  0 
ff_memless             12945  1 hid_logitech
usbhid                 41905  1 hid_logitech
hid                    77367  3 hidp,hid_logitech,usbhid
usb_storage            44173  1 
uas                    17699  0 
floppy                 60310  0 
r8169                  47200  0 
pata_atiixp            12967  2 
ahci                   21634  0 
libahci                25761  1 ahci

cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.100
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 68.105.28.11

cat /etc/resolv.conf
# Generated by NetworkManager

---

### Post by praseodym on 2011-11-14
You are using a router? If yes, remove anything but the 2 "lo" lines from your /etc/network/interfaces

---

### Post by dirtblack on 2011-11-14
Well I gave that a shot and it didn't work.  After looking at the file it appeared to me that the router wasn't kicking out the correct stuff. I simply unplugged the cable and plugged it into a diff port on the router, and Bango!  Working now.  Thanks for your help.

---

