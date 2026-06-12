---
title: "No network after upgrade from 11.04 to 11.10"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by bobo123333 on 2011-12-03
What can i do?
no network any more
 
BTW, on the boos process it stack on "wait networking configuration"
 
Any suggestions?

---

### Post by praseodym on 2011-12-03
Hi,

please show the outputs of:
```
lspci -nnk | grep -iA2 net
iwconfig
lsusb
lsmod
rfkill list
sudo iwlist scan
```

---

### Post by bobo123333 on 2011-12-03
I have no internet in the pc so here is a summary of the output that i copy manually:
 
**lspci -nnk | grep -iA2 net**
ethernet controller [0200]: intel ....
kernal driver in use: e100
 
 
**iwconfig**
lo + eth0: no wireless
 
**lsusb:**
Bus 001-005 device 001: ID ... Linux foundation 20/1.1 root hub
 
**lsmod:**
lot of lines - what is relevant?
 
**rfkill list:**
No output
 
**sudo iwlist scan:**
lo + eth0:  Interface not support scanning
 
BTW, ther is a network card connect to the pc (onbaord?) no wifi card.
It used to work until the upgrade from 11.04 to 11.10

---

### Post by praseodym on 2011-12-03
Is the module **e100** loaded at "lsmod"? Please show:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.state
```

---

### Post by bobo123333 on 2011-12-03
> **praseodym said:**
> Is the module **e100** loaded at "lsmod"? 
Yes, the result of "lsmode | grep e100" is:
e100 30676 0
mii    4425  1 e100
 
 
> **praseodym said:**
> 
Please show:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.state
``` 
 
 
**cat /etc/network/interfaces:**
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet dhcp
 
 
**ifconfig -a:**
eth0: link encap: ethernet .. broadcast multicast mtu:1500 ...
 
lo loopback
....
 
 
**cat /var/lib/NetworkManager/NetworkManager.state:**
[main]
networkingenabled=true
wirelessenabled=true
wwamenable=true
 
**cat /etc/NetworkManager/NetworkManager.conf:**
[main]
plugins:ifupdown,keyfile
[ifupdown]
managed=false

---

### Post by praseodym on 2011-12-03
```
gksu gedit /etc/network/interfaces
```
remove anything _but_:
```
auto lo
iface lo inet loopback
```
Remove your wired profile in "wired" and "DSL" (if any) in the network-manager applet and reboot.

---

### Post by bobo123333 on 2011-12-03
> **praseodym said:**
> ```
gksu gedit /etc/network/interfaces
```
remove anything _but_:
```
auto lo
iface lo inet loopback
```

 
Done
 
> **praseodym said:**
> 
Remove your wired profile in "wired" and "DSL" (if any) in the network-manager applet and reboot.
 
Not sure what do you ask me to do.
I comment all in /etc/network/interfaces else what you ask.
I comment this
#auto eth0
#iface eth0 inet dhcp

 
I reboot and nothing change...

---

### Post by bobo123333 on 2011-12-04
> **bobo123333 said:**
> Done
 
 
 
Not sure what do you ask me to do.
I comment all in /etc/network/interfaces else what you ask.
I comment this
#auto eth0
#iface eth0 inet dhcp
 
 
I reboot and nothing change...
 
 
After several other reboots and other fixes (GUI issue) now there is network
Thanks!

---

### Post by slixz85 on 2011-12-04
> **bobo123333 said:**
> After several other reboots and other fixes (GUI issue) now there is network
Thanks!

i just upgraded from 11.04 to 11.10 as well and have this same problem. i can click on previous versions though in my grub loader and load up the old linux kernel 2.6 or whatever and the system shows the network and connects saying that it is 11.10. so i am not sure of the problem. i dont know alot but i looked at the files in etc/default/network and etc/network and the interfaces file etc. but all the info looks the same.

i just updated my system for a reason i would hate to keep clicking on previous versions and stuff in grub when i shouldn't have too.

thanks man if u remember what u did

---

### Post by praseodym on 2011-12-04
Hi,

please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
```

---

### Post by slixz85 on 2011-12-06
> **praseodym said:**
> Hi,

please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
```

this is the code from the ubuntu 11.10 kernel 3.0.0.13 (kernel 2.6 code below also) that is latest from the upgrade that won't see the wifi.

root@ThinkCentre:~# lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
	Subsystem: Lenovo Device [17aa:1017]
	Kernel driver in use: tg3
root@ThinkCentre:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
root@ThinkCentre:~# lsmod
Module                  Size  Used by
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_analog    75090  1 
iptable_nat            13016  0 
nf_nat                 24958  1 iptable_nat
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
nf_conntrack           70103  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_seq_midi           13132  0 
iptable_mangle         12646  0 
snd_rawmidi            25241  1 snd_seq_midi
iptable_filter         12706  0 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  30 
ppdev                  12849  0 
snd                    55902  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
parport_pc             32114  1 
nv_tco                 13399  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
tg3                   132972  0 
floppy                 60310  0 
pata_amd               13753  0 
sata_nv                23379  3 
root@ThinkCentre:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:ad:62:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13376 (13.3 KB)  TX bytes:13376 (13.3 KB)

root@ThinkCentre:~# iwconfig




and this is the code from the 2.6 kernel that lets me type this online right now.


root@ThinkCentre:~# lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
	Subsystem: Lenovo Device [17aa:1017]
	Kernel driver in use: tg3
root@ThinkCentre:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
root@ThinkCentre:~# lsmod
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  30 
ipt_LOG                12784  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  20 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13106  0 
xt_state               12514  6 
sco                    17827  2 
bnep                   17785  2 
rfcomm                 38125  0 
l2cap                  48656  6 bnep,rfcomm
bluetooth              65493  6 sco,bnep,rfcomm,l2cap
vesafb                 13449  1 
iptable_nat            12977  0 
nf_nat                 24827  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19024  9 iptable_nat,nf_nat
nf_conntrack           69744  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12615  1 
iptable_filter         12706  1 
ip_tables              18125  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21907  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
nvidia              10390874  30 
snd_hda_codec_analog    75442  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
rt2870sta             410104  1 
parport_pc             32111  1 
crc_ccitt              12595  1 rt2870sta
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
k8temp                 12872  0 
nv_tco                 13331  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
floppy                 60032  0 
tg3                   131476  0 
sata_nv                23176  3 
pata_amd               13762  0 
root@ThinkCentre:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:ad:62:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2712 (2.7 KB)  TX bytes:2712 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 20:11:30:70:1b:9f  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1587885 (1.5 MB)  TX bytes:146918 (146.9 KB)

root@ThinkCentre:~# iwconfig



thanks for helpin

---

### Post by slixz85 on 2011-12-06
i notice that the problem is obvious that it is missing wlan0 in the 3.0 latest kernel but the system boots into the same thing with all the same programs installed and stuff of course and so i figure the wifi drivers are installed correctly but dont understand why it aint working since the same system does just with another kernel

---

### Post by praseodym on 2011-12-06
In 11.04 the driver was rt2870sta (with rt2800usb blacklisted?). This driver is no longer part of the Linux kernel 3.x. Take rt2800usb from the blacklist and reboot.

---

### Post by slixz85 on 2011-12-06
> **praseodym said:**
> In 11.04 the driver was rt2870sta (with rt2800usb blacklisted?). This driver is no longer part of the Linux kernel 3.x. Take rt2800usb from the blacklist and reboot.

i had some wifi issues with the rt2800usb driver.a website said to blcklist it and use the rt2870sta driver instead and now i no longer have a wifi idle issue with the kernel 2.6...
so my question is if i enable the rt2800 usb with the new kernel how would i find out if this has been fixed in the new kernel?
i just dont understand all this wifi driver stuff with my ralink. others have said it has issues.

i would much rather have a stable connection instead of one that takes 3minutes to load a website on wifi lol. thats horrible.

i just dont want to screw this wifi up. i am sharing someone connection. so i would be stuck. i dont even got a flash drive to bring files back to pc right now. (i just like having a system up to date)

---

### Post by chmibrown on 2011-12-06
I, too,am having this issue, but I'm much more of a basic user: I do not understand where to find the above listed code to check.  Any very basic pointers?

---

### Post by praseodym on 2011-12-07
@chmibrown: Open a terminal with CTRL+ALT+T and copy/paste the commands one by one into it, press ENTER after each one:
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
```

@slixz85: Please show:

```
grep rt2 /etc/modprobe.d/
```
You can try the latest Ralink driver ferom here:
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

**RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB**

---

