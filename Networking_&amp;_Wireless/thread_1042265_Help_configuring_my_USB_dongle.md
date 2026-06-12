---
title: "Help configuring my USB dongle"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by molly.moggins on 2009-01-17
I have bought a wireless cable router and got that working fine - annoyingly I can use wireless on my Windows Vista laptop straight away.

However, I am having all sorts of problems getting my Ubuntu 8.04 desktop working with wireless. 

I have a USB dongle - a Pluscom WU-ZD1211B - that is supposed to be Linux compatible and the instructions on the CD are here (in green);


  [COLOR="Teal"]  Driver Installation Guide for ZD1211 wireless adapter in Linux
It needs only a few steps to build and install the driver we provided. Before you begin to
build the driver, make sure (1) Kernel Source Tree is installed in your Linux system;
(2) Kernel wireless function (IEEE 802.11) is available.
Step 1: Package Extraction
Type this command: tar zxvf ZD1211LnxDrv_2_21_0_0.tar.gz
The purpose of this step is to extract this package by tar. After extracting this package,
you can see the source files. You should change directory into this directory for
proceeding the next step.
Step 2: Compile the driver
You just need to type the command &#8220;make&#8221;, and the driver module will be generated and
installed.
Step 3: Load the driver
Use the command &#8220;modprobe &#8211;i zd1211b&#8221; to load the driver. In order to check whether
the driver is loaded successfully, you can use the command &#8220;lsmod&#8221; for this check. If the
driver is loaded successfully, the following messages should be seen
...
zd1211 183576 0 (unused)
...
Please note that the number 183576 may vary in different systems.
Step 4: Configure the Wireless settings
Use the command &#8220;ifconfig&#8221; command to check the configurations, you can find
ethX(If there is already an Ethernet adapter exits it may be eth0,and the adapter
you just installed may be eth1 ,and so on). Then type in the command &#8220;iwconfig eth1
essid xxx&#8221; where &#8220;xxx&#8221; is the SSID of your router. The adapter will connect the
router automatically. Of course, make sure the router&#8217;s DHCP is enabled, Otherwise,
you should set the IP address of the adapter manually.

[/COLOR]

My problem is that if I try and do step 1 and extract the package I get the following error 

[COLOR="Blue"]drwxrwxrwx  7 carole carole  4096 2009-01-17 17:09 ZD1211LnxDrv_2_22_0_0.tar.gz
drwxr-xr-x  2 carole carole  4096 2008-07-02 16:56 ZIPPED
carole@carole-desktop:~$ tar zxvf ZD1211LnxDrv_2_21_0_0.tar.gz
tar: ZD1211LnxDrv_2_21_0_0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
carole@carole-desktop:~$ 
[/COLOR]

As you can see I have copied the folder from the CD and put it on my PC. I don't know what that zxvf stuff is. Is it some kind of command string or what?


I'd really appreciate fixing this as I really don't want to be stuck with a wired connection for Linux and wireless for Windows only, anyway, I have bought the dongle and I'd like to use it.

If anyone would prefer to email me with some help my addy is;

[email]molly.moggins@googlemail.com[/email]

OK I noticed the initial mismatch between the directory name and the instructions! If I try the tar command now I get this;

[COLOR="Blue"]carole@carole-desktop:~$ tar zxvf ZD1211LnxDrv_2_22_0_0.tar.gz
tar: ZD1211LnxDrv_2_22_0_0.tar.gz: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors
[/COLOR]

---

### Post by utnubuuser on 2009-01-17
Hi -- It kinda sounds like you're double clicking the package to extract?  If you are, don't. 
Just use the commands like they're written, except you might have to put "sudo" in front of them.

And are you "cd"ing (cd /newfolder) into the new folder that appears when the package is extracted?
The second set of commands are meant to be performed from within that folder.

---

### Post by molly.moggins on 2009-01-18
OK, I have got past this problem by doing the driver comppile from another set of instructions. I have a new problem now which I'll open a new thread for

Thanks.

---

### Post by molly.moggins on 2009-01-19
Here is where I have got to. Complete brick wall time.


Here are a load of displays from my terminal session. I just can't get the wireless working even though I know the newtork is OK because I can access it via a Windows laptop.

The driver I need is the zd1211rw, so here I go;


carole@carole-desktop:~$ sudo modprobe zd1211rw
[sudo] password for carole:
Sorry, try again.
[sudo] password for carole:
carole@carole-desktop:~$ sudo modprobe zd1211rw
carole@carole-desktop:~$ lsmod
Module Size Used by
xt_TCPMSS 6272 0
nf_nat_irc 4352 0
nf_nat_ftp 5120 0
zd1211b 268412 0
zd1211rw 64008 0
ieee80211softmac 34688 1 zd1211rw
ieee80211 38344 2 zd1211rw,ieee80211softmac
ieee80211_crypt 8192 1 ieee80211
rfcomm 47392 2
l2cap 28800 13 rfcomm
bluetooth 67620 4 rfcomm,l2cap
ppdev 11400 0
powernow_k8 16608 0
cpufreq_powersave 3200 0
cpufreq_conservative 10632 0
cpufreq_ondemand 11152 1
cpufreq_stats 8416 0
freq_table 6464 3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace 6180 0
container 6656 0
video 23444 0
output 5632 1 video
dock 12960 0
sbs 17808 0
sbshc 8960 1 sbs
battery 16776 0
ipv6 311848 10
xt_limit 4608 8
xt_tcpudp 4992 10
ipt_LOG 8192 8
ipt_MASQUERADE 5504 1
ipt_TOS 3712 0
ipt_REJECT 6528 1
nf_conntrack_irc 8992 1 nf_nat_irc
nf_conntrack_ftp 11688 1 nf_nat_ftp
xt_state 4096 6
aes_x86_64 26920 0
dm_crypt 16776 0
dm_mod 71160 1 dm_crypt
ac 8328 0
sbp2 27272 0
lp 14916 0
af_packet 27272 6
parport_pc 41128 1
parport 44300 3 ppdev,lp,parport_pc
serio_raw 9092 0
evdev 14976 3
psmouse 46236 0
snd_intel8x0 40872 3
snd_ac97_codec 123224 1 snd_intel8x0
pcspkr 4992 0
nvidia 8858052 34
ac97_bus 3840 1 snd_ac97_codec
snd_pcm_oss 47648 0
snd_mixer_oss 20224 1 snd_pcm_oss
snd_pcm 92168 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
k8temp 7680 0
snd_seq_dummy 5764 0
snd_seq_oss 38912 0
shpchp 38172 0
pci_hotplug 34608 1 shpchp
snd_seq_midi 10688 0
snd_rawmidi 29856 1 snd_seq_midi
snd_seq_midi_event 10112 2 snd_seq_oss,snd_seq_midi
snd_seq 63232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 27912 2 snd_pcm,snd_seq
snd_seq_device 10644 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 70856 17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 10400 1 snd
snd_page_alloc 13200 2 snd_intel8x0,snd_pcm
usblp 17664 0
button 10912 0
i2c_nforce2 8704 0
i2c_core 28544 2 nvidia,i2c_nforce2
iptable_nat 9604 1
nf_nat 23980 4 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4 21904 8 iptable_nat
nf_conntrack 79216 9 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle 4480 0
iptable_filter 4608 1
ip_tables 24104 3 iptable_nat,iptable_mangle,iptable_filter
x_tables 23560 10 xt_TCPMSS,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3 149264 1
jbd 57000 1 ext3
mbcache 11392 1 ext3
usb_storage 82624 0
sr_mod 20132 0
cdrom 41512 1 sr_mod
sg 41880 0
sd_mod 33280 3
libusual 23648 1 usb_storage
pata_amd 16772 0
sata_nv 31752 2
pata_acpi 9856 0
floppy 69096 0
ohci1394 36532 0
ata_generic 9988 0
ieee1394 106968 2 sbp2,ohci1394
forcedeth 55564 0
libata 176560 4 pata_amd,sata_nv,pata_acpi,ata_generic
scsi_mod 178488 6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
ehci_hcd 41996 0
ohci_hcd 28956 0
usbcore 170288 8 zd1211b,zd1211rw,usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal 19744 0
processor 40424 2 powernow_k8,thermal
fan 6792 0
fbcon 46336 0
tileblit 4096 1 fbcon
font 10112 1 fbcon
bitblit 7424 1 fbcon
softcursor 3712 1 bitblit
fuse 56112 1
carole@carole-desktop:~$


ifconfig shows

carole@carole-desktop:~$ sudo ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:e6:57:02:cb
inet addr:192.168.1.100 Bcast:255.255.255.255 Mask:255.255.255.0
inet6 addr: fe80::216:e6ff:fe57:2cb/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1343 errors:0 dropped:0 overruns:0 frame:0
TX packets:1374 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:803678 (784.8 KB) TX bytes:208481 (203.5 KB)
Interrupt:21 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:71364 (69.6 KB) TX bytes:71364 (69.6 KB)

carole@carole-desktop:~$


iwconfig shows

carole@carole-desktop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"WR-BS78RE81" Nickname:"zd1211"
Mode:Managed Access Point: Invalid
Encryption key:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


"Mode:Managed Access Point: Invalid "

I have tried to find out what this means but I can't find an answer on the internet.

I have also done this display

carole@carole-desktop:~$ sudo ip link show
1: lo:
[Error: Irreparable invalid markup ('<loopback,up,lower_up>') in entry. Owner must fix manually. Raw contents below.]

Anyone able to help here?

Here are a load of displays from my terminal session. I just can't get the wireless working even though I know the newtork is OK because I can access it via a Windows laptop.

The driver I need is the zd1211rw, so here I go;


carole@carole-desktop:~$ sudo modprobe zd1211rw
[sudo] password for carole:
Sorry, try again.
[sudo] password for carole:
carole@carole-desktop:~$ sudo modprobe zd1211rw
carole@carole-desktop:~$ lsmod
Module Size Used by
xt_TCPMSS 6272 0
nf_nat_irc 4352 0
nf_nat_ftp 5120 0
zd1211b 268412 0
zd1211rw 64008 0
ieee80211softmac 34688 1 zd1211rw
ieee80211 38344 2 zd1211rw,ieee80211softmac
ieee80211_crypt 8192 1 ieee80211
rfcomm 47392 2
l2cap 28800 13 rfcomm
bluetooth 67620 4 rfcomm,l2cap
ppdev 11400 0
powernow_k8 16608 0
cpufreq_powersave 3200 0
cpufreq_conservative 10632 0
cpufreq_ondemand 11152 1
cpufreq_stats 8416 0
freq_table 6464 3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace 6180 0
container 6656 0
video 23444 0
output 5632 1 video
dock 12960 0
sbs 17808 0
sbshc 8960 1 sbs
battery 16776 0
ipv6 311848 10
xt_limit 4608 8
xt_tcpudp 4992 10
ipt_LOG 8192 8
ipt_MASQUERADE 5504 1
ipt_TOS 3712 0
ipt_REJECT 6528 1
nf_conntrack_irc 8992 1 nf_nat_irc
nf_conntrack_ftp 11688 1 nf_nat_ftp
xt_state 4096 6
aes_x86_64 26920 0
dm_crypt 16776 0
dm_mod 71160 1 dm_crypt
ac 8328 0
sbp2 27272 0
lp 14916 0
af_packet 27272 6
parport_pc 41128 1
parport 44300 3 ppdev,lp,parport_pc
serio_raw 9092 0
evdev 14976 3
psmouse 46236 0
snd_intel8x0 40872 3
snd_ac97_codec 123224 1 snd_intel8x0
pcspkr 4992 0
nvidia 8858052 34
ac97_bus 3840 1 snd_ac97_codec
snd_pcm_oss 47648 0
snd_mixer_oss 20224 1 snd_pcm_oss
snd_pcm 92168 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
k8temp 7680 0
snd_seq_dummy 5764 0
snd_seq_oss 38912 0
shpchp 38172 0
pci_hotplug 34608 1 shpchp
snd_seq_midi 10688 0
snd_rawmidi 29856 1 snd_seq_midi
snd_seq_midi_event 10112 2 snd_seq_oss,snd_seq_midi
snd_seq 63232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 27912 2 snd_pcm,snd_seq
snd_seq_device 10644 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 70856 17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 10400 1 snd
snd_page_alloc 13200 2 snd_intel8x0,snd_pcm
usblp 17664 0
button 10912 0
i2c_nforce2 8704 0
i2c_core 28544 2 nvidia,i2c_nforce2
iptable_nat 9604 1
nf_nat 23980 4 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4 21904 8 iptable_nat
nf_conntrack 79216 9 nf_nat_irc,nf_nat_ftp,ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle 4480 0
iptable_filter 4608 1
ip_tables 24104 3 iptable_nat,iptable_mangle,iptable_filter
x_tables 23560 10 xt_TCPMSS,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3 149264 1
jbd 57000 1 ext3
mbcache 11392 1 ext3
usb_storage 82624 0
sr_mod 20132 0
cdrom 41512 1 sr_mod
sg 41880 0
sd_mod 33280 3
libusual 23648 1 usb_storage
pata_amd 16772 0
sata_nv 31752 2
pata_acpi 9856 0
floppy 69096 0
ohci1394 36532 0
ata_generic 9988 0
ieee1394 106968 2 sbp2,ohci1394
forcedeth 55564 0
libata 176560 4 pata_amd,sata_nv,pata_acpi,ata_generic
scsi_mod 178488 6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
ehci_hcd 41996 0
ohci_hcd 28956 0
usbcore 170288 8 zd1211b,zd1211rw,usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal 19744 0
processor 40424 2 powernow_k8,thermal
fan 6792 0
fbcon 46336 0
tileblit 4096 1 fbcon
font 10112 1 fbcon
bitblit 7424 1 fbcon
softcursor 3712 1 bitblit
fuse 56112 1
carole@carole-desktop:~$


ifconfig shows

carole@carole-desktop:~$ sudo ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:e6:57:02:cb
inet addr:192.168.1.100 Bcast:255.255.255.255 Mask:255.255.255.0
inet6 addr: fe80::216:e6ff:fe57:2cb/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1343 errors:0 dropped:0 overruns:0 frame:0
TX packets:1374 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:803678 (784.8 KB) TX bytes:208481 (203.5 KB)
Interrupt:21 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:71364 (69.6 KB) TX bytes:71364 (69.6 KB)

carole@carole-desktop:~$


iwconfig shows

carole@carole-desktop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"WR-BS78RE81" Nickname:"zd1211"
Mode:Managed Access Point: Invalid
Encryption key:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


"Mode:Managed Access Point: Invalid "

I have tried to find out what this means but I can't find an answer on the internet.

I have also done this display

carole@carole-desktop:~$ sudo ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
link/ether 00:16:e6:57:02:cb brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
link/ether 00:1a:ee:01:69:d1 brd ff:ff:ff:ff:ff:ff
carole@carole-desktop:~$


carole@carole-desktop:~$ sudo ip route show
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.100
169.254.0.0/16 dev eth0 scope link metric 1000
default via 192.168.1.1 dev eth0
carole@carole-desktop:~$

carole@carole-desktop:~$ sudo lshw -C network
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: eth1
serial: 00:1a:ee:01:69:d1
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
carole@carole-desktop:~$

if I try and bring up eth1 I get this

carole@carole-desktop:~$ sudo ifconfig eth1 up
SIOCSIFFLAGS: Connection timed out
carole@carole-desktop:~$

Is there some other command to enable the networking???

Sorry to post so much but I have run out of ideas. I have the router configured for WPA2 and this is working fine on my Windows laptop - doesn't need a USB adaptor because it is WiFi enabled and it just worked straight off with a couple of parms added.

I can try using Gnome Network Manager and it sees the wireless network but I just can't get it online. Nothing I do gets it to show the network enabled.

I am using DHCP rather than static IP

Here is the contents of /etc/network/interfaces;

auto lo
iface lo inet loopback




iface eth1 inet dhcp
wpa-psk ea237620a57294846b99055469831e77b327c41979dcf9a5ddea7f19b2fbe472
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid WR-BS78RE81

auto eth1


I don't want to give up here, because it ought to work, the router is clearly broadcasting, it is just I can't get Linux to go wireless.

If anyone can help I'd appreciate it.

Thanks

Carole

---

### Post by zoubidoo on 2009-10-13
Hello Carole,

Did the dongle work for you in the end?

Do you still have to compile the driver or has it made its way into the kernel?

Cheers,
Zoubidoo

---

