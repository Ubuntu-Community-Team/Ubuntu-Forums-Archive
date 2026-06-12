---
title: "Toshiba C850-P0011 Network or Wifi not working"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by sridhar2do on 2013-02-09
Hi,

Brought Toshiba Satellite C850-P0011.

Installed Ubuntu 12.10 along with Windows 7 in Windows Wifi is working but in Ubuntu Wifi is not working even LAN (Networking) is also not working.

I have been working in Ubuntu for past 6 years, but i never found problem like this before. Please someone help me out, i can't install other software too because of this problem.

Give me a link so that i can atleast enable my Wifi. 

Thank you in advance

---

### Post by praseodym on 2013-02-09
Hi,

please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by sridhar2do on 2013-02-09
> **praseodym said:**
> Hi,

please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```


As per you have asked

**uname -a**
Linux sridhar-Satellite-C850 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


**lspci -nnk | grep -iA2 net**
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]


**lsmod**
Module                  Size  Used by
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_realtek    63356  1 
joydev                 17161  0 
bnep                   17707  2 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  12 
coretemp               13168  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rts5139               281367  0 
psmouse                84843  0 
serio_raw              13031  0 
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
microcode              18209  0 
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
videobuf2_memops       13184  1 videobuf2_vmalloc
toshiba_bluetooth      12711  0 
btusb                  17950  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             183228  22 bnep,rfcomm,btusb
mac_hid                13037  0 
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14599  1 snd
i915                  457161  3 
drm_kms_helper         45271  1 i915
mei                    35796  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
lpc_ich                16925  0 
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp


**iwconfig**
lo        no wireless extensions.


**rfkill list**
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Thank you

---

### Post by AMKawam on 2013-02-09
I had a similar problem with my machine, I tried re-installing the driver package and it worked fine!



> **sridhar2do said:**
> Hi,

Brought Toshiba Satellite C850-P0011.

Installed Ubuntu 12.10 along with Windows 7 in Windows Wifi is working but in Ubuntu Wifi is not working even LAN (Networking) is also not working.

I have been working in Ubuntu for past 6 years, but i never found problem like this before. Please someone help me out, i can't install other software too because of this problem.

Give me a link so that i can atleast enable my Wifi. 

Thank you in advance

---

### Post by sridhar2do on 2013-02-09
> **AMKawam said:**
> I had a similar problem with my machine, I tried re-installing the driver package and it worked fine!



Can to give me the link as well as the step. Thank you for sharing

---

### Post by sridhar2do on 2013-02-09
> **AMKawam said:**
> I had a similar problem with my machine, I tried re-installing the driver package and it worked fine!
I'm totally confused, so please help me by providing some steps

---

### Post by praseodym on 2013-02-09
Download these packages:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.5.0.23.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.5.0.23.29_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_i386.deb)

Save them in "Downloads" and install via:

```
sudo dpkg -i ~/Downloads/*.deb
```
Reboot. Cable connection should work now. Now install

```
sudo apt-get install build-essential dkms
```
and check the outputs again.

---

### Post by sridhar2do on 2013-02-11
Its not yet working...



uname -a
Linux sridhar-Satellite-C850 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:05:29 UTC 2013 i686 i686 i686 GNU/Linux


lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]


lsmod
Module                  Size  Used by
vesafb                 13478  1 
parport_pc             31969  0 
rfcomm                 37381  12 
ppdev                  12818  0 
bnep                   17708  2 
joydev                 17162  0 
microcode              18210  0 
btusb                  17951  0 
bluetooth             183163  22 rfcomm,bnep,btusb
lp                     13300  0 
alx                    71562  0 
parport                40754  3 parport_pc,ppdev,lp
video                  18848  0 
psmouse                84878  0 
compat                 14558  5 rfcomm,bnep,btusb,bluetooth,alx
serio_raw              13032  0


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2013-02-11
Ethernet is working? Please show
```

cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
route -n
```

---

### Post by sridhar2do on 2013-02-15
> **praseodym said:**
> Hi,

please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```


As you have asked me

uname -a
Linux sridhar-Satellite-C850 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:05:29 UTC 2013 i686 i686 i686 GNU/Linux


lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]


lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_realtek    63496  1 
joydev                 17162  0 
rfcomm                 37381  12 
parport_pc             31969  0 
bnep                   17708  2 
ppdev                  12818  0 
coretemp               13169  0 
binfmt_misc            17261  1 
rts5139               281401  0 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
snd_hda_intel          32516  3 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
videobuf2_memops       13213  1 videobuf2_vmalloc
toshiba_bluetooth      12712  0 
btusb                  17951  0 
bluetooth             183163  22 rfcomm,bnep,btusb
microcode              18210  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
alx                    71562  0 
compat                 14558  5 rfcomm,bnep,btusb,bluetooth,alx
psmouse                84878  0 
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13038  0 
serio_raw              13032  0 
i915                  457247  4 
drm_kms_helper         47304  1 i915
drm                   238811  5 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
video                  18848  1 i915
mei                    35797  0 
lpc_ich                16926  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by sridhar2do on 2013-02-15
> **praseodym said:**
> Ethernet is working? Please show
```

cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
route -n
```

cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:6c:1d:dc:49  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe1d:dc49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1092699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1187944 errors:0 dropped:0 overruns:0 carrier:25
          collisions:0 txqueuelen:1000 
          RX bytes:569485051 (569.4 MB)  TX bytes:254360791 (254.3 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:481961 (481.9 KB)  TX bytes:481961 (481.9 KB)


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0



But still WiFi is not working in my office i can able to work in wifi only.

So i have checked from outside now Ethernet is working fine, but i need to work in WiFi, i have updated everything and build- essential also.

Still i'm working in Windows 7, i hate working in that. please help me out. to configure my wifi drivers

---

### Post by praseodym on 2013-02-15
Driver installation:

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

