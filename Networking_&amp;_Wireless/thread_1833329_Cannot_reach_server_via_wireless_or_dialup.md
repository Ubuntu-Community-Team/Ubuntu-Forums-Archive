---
title: "Cannot reach server via wireless or dialup"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by AF1HS on 2011-08-25
I have my domain through godaddy.com and my DNS service through zoneedit.com. Everything appears OK on both those sites but I cannot reach my webserver by domain name from my wireless laptop or from a dial-up connection. At the Ubuntu 9.10 server and on a wired XP Pro desktop, I can get to the server by either the domain name ([www.af1hs.com]("http://www.af1hs.com")) or the IP address (dynamic 64.252.5.244). On my wireless laptop or by a dialup connection, I can only get to the website by the IP address.
 
I have ddclient running and it gives an error that it cannot update the IP. I've tried rebooting the server, the router and the modem and tried flushing the DNS, all to no avail.
 
Anybody help, please??
&#12288;
&#12288;
The following commands were all submitted on the server itself:
```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1
```
&#12288;
```
cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 68.94.156.1
nameserver 68.94.157.1
```
&#12288;
```
route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 100 0 0 eth0
```
&#12288;
```
ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:26:18:ed:66:8f
inet addr:192.168.1.105 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::226:18ff:feed:668f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:10553 errors:0 dropped:0 overruns:0 frame:0
TX packets:6982 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4413974 (4.4 MB) TX bytes:620334 (620.3 KB)
Interrupt:27 Base address:0x4000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:19219 errors:0 dropped:0 overruns:0 frame:0
TX packets:19219 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4208295 (4.2 MB) TX bytes:4208295 (4.2 MB)
```
&#12288;
```
iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
```
&#12288;
rfkill list
 
 
```
lsmod
Module Size Used by
binfmt_misc 8356 1
snd_hda_codec_realtek 203328 1
snd_hda_intel 27080 2
snd_hda_codec 75708 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 7200 1 snd_hda_codec
snd_pcm_oss 37920 0
snd_mixer_oss 16028 1 snd_pcm_oss
snd_pcm 75520 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 2656 0
snd_seq_oss 28608 0
snd_seq_midi 6464 0
iptable_filter 3100 0
ip_tables 11692 1 iptable_filter
snd_rawmidi 22176 1 snd_seq_midi
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 22276 2 snd_pcm,snd_seq
x_tables 16544 1 ip_tables
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 59236 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,
snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev 6688 0
psmouse 57332 0
asus_atk0110 8252 0
soundcore 7264 1 snd
i2c_piix4 10124 0
parport_pc 32228 1
lp 8964 0
serio_raw 5280 0
snd_page_alloc 9252 2 snd_hda_intel,snd_pcm
parport 35340 3 ppdev,parport_pc,lp
r8169 32480 0
mii 5212 1 r8169
usbhid 38304 3
ati_agp 6760 0
agpgart 35020 1 ati_agp
```
&#12288;
```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
Kernel driver in use: r8169
Kernel modules: r8169
```
&#12288;
```
netstat -nr
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
```
&#12288;
```
traceroute [www.af1hs.com]("http://www.af1hs.com") (done on server)
traceroute to [www.af1hs.com]("http://www.af1hs.com") (192.168.1.105), 30 hops max, 60 byte packets
1 [www.af1hs.com]("http://www.af1hs.com") (192.168.1.105) 0.035 ms 0.010 ms 0.008 ms
```
 
```
tracert [www.af1hs.com]("http://www.af1hs.com") (done on wireless laptop)
tracing route to [www.af1hs.com]("http://www.af1hs.com") [64.252.132.210] << should be 64.252.5.244!!
over a maximum of 30 hops:
1 9 ms 8 ms 9 ms 254.183.252.64.snet.net [64.252.183.254]
2 9 ms 9 ms 8 ms 64.148.52.2
3 9 ms 9 ms 8 ms se1.g5-2.mrdnct.sbcglobal.net [64.148.52.11]
```
 
```
tracert 64.252.5.244 (done on wireless laptop)
tracing route to 244.5.252.64.snet.net [64.252.5.244]
over a maximum of 30 hops:
1 <1 ms <1 ms <1 ms 244.5.252.64.snet.net [64.252.5.244]
Trace complete.
```
&#12288;
```
nslookup [www.af1hs.com]("http://www.af1hs.com") (from wireless)
Server:      192.168.1.1
Address:   192.168.1.1#53
```
 
```
Non-authoritative answer:
Name:       [www.af1hs.com]("http://www.af1hs.com")
Address:  64.252.132.210
```
 
(that above address has not been in use since mid-August!!)
&#12288;
&#12288;

---

### Post by Iowan on 2011-08-25
From Code of Conduct:
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

---

