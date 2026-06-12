---
title: "How do you load driver?"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by jacknet52 on 2011-11-09
I have a driver in my additional drivers sys settings box. My boss got it in there for me today and I don't have clue as to how to load it. It says it's activated but not in use. Thanks

---

### Post by praseodym on 2011-11-09
Hi,

please show the terminal outputs of

```
lspci -nnk
lsmod
iwconfig
```
Which driver is that?

---

### Post by jacknet52 on 2011-11-09
jacknet@jacknet-P5GZ-MX:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85728 (85.7 KB)  TX bytes:85728 (85.7 KB)
01:04.0 Ethernet controller [0200]: SysKonnect SK-9871 V2.0 Gigabit 
Ethernet 1000Base-ZX Adapter, PCI64, Fiber ZX/SC [1148:4320] (rev 10)
	Subsystem: SysKonnect SK-9871 V2.0 Gigabit Ethernet 1000Base-ZX
 Adapter, PCI64, Fiber ZX/SC [1148:4320]
	Kernel driver in use: skge
	Kernel modules: sk98lin, skge
jacknet@jacknet-P5GZ-MX:~$ lsmod
skge                   44767  0
@praseodym: does this tell you anything?
I'm trying to get my Marvell Yukon ethernet onboard card to work.

---

### Post by praseodym on 2011-11-10
Some Marvell cards are buggy and need:

```
sudo ifconfig eth0 mtu 1500
```
Dou you want to connect via a router/modem or a single modem?

---

### Post by jacknet52 on 2011-11-10
thanks for responding praseodym: that command didn't do anything. I'm working through a router/switch to a DSL modem. It was fine at work yesterday and something got reset/lost at shutdown. I just need to figure out how to reload the driver. Thanks

---

### Post by praseodym on 2011-11-10
Please show:

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by jacknet52 on 2011-11-10
Ethernet controller [0200]: SysKonnect SK-9871 V2.0 Gigabit Ethernet 1000Base-ZX Adapter, PCI64, Fiber ZX/SC [1148:4320] (rev 10)
	Subsystem: SysKonnect SK-9871 V2.0 Gigabit Ethernet 1000Base-ZX Adapter, PCI64, Fiber ZX/SC [1148:4320]
	Kernel driver in use: skge
	Kernel modules: sk98lin, skge
jacknet@jacknet-P5GZ-MX:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
i915                  505108  2 
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
asus_atk0110           17742  0 
snd_timer              28932  2 snd_pcm,snd_seq
drm_kms_helper         32889  1 i915
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   192226  3 i915,drm_kms_helper
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
skge                   44767  0 
floppy                 60310  0
@Praseodym: I hope this helps. Thanks

---

### Post by praseodym on 2011-11-10
The driver **skge** is loaded, try to reload it:

```
sudo service network-manager stop
sudo modprobe -rfv skge
sudo modprobe -v skge
sudo service network-manager start
```

---

### Post by jacknet52 on 2011-11-10
Here's what I got and nothing changed:

jacknet@jacknet-P5GZ-MX:~$ sudo service network-manager stop
[sudo] password for jacknet: 
network-manager stop/waiting
jacknet@jacknet-P5GZ-MX:~$ sudo modprobe -rfg skge
modprobe: invalid option -- 'g'
Usage: modprobe [-v] [-V] [-C config-file] [-d <dirname> ] [-n] [-i] [-q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
jacknet@jacknet-P5GZ-MX:~$ sudo modprobe -rf skge
jacknet@jacknet-P5GZ-MX:~$ sudo modprobe -v skge
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/skge.ko 
jacknet@jacknet-P5GZ-MX:~$ sudo service network-manager start
network-manager start/running, process 1817
jacknet@jacknet-P5GZ-MX:~$

---

### Post by jacknet52 on 2011-11-10
thanks fellas - My boss finally called:
cd ~/DriverInstall
sudo ./install.sh
This reloaded the sk98lin driver. I also had a system driver that it was trying to use called skge. The install deleted that one and installed the correct one. I'm now back on my Ubuntu machine using my ethernet. thanks again for your help.

---

