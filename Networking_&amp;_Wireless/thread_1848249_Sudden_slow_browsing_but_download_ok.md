---
title: "Sudden slow browsing but download ok"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by spandey on 2011-09-22
Hi,
I have Ubuntu 10.10 and it was working fine till few days back. Suddenly the net browsing has become very slow both in firefox and opera. But the downloads are perfectly fine. I use wired line for DSL.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
My Network Card:
spandey@spandey-desktop:~$ lspci -nnk | grep -iA2 net
02:06.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 8b)
    Subsystem: D-Link System Inc Device [1186:1405]
    Kernel driver in use: via-rhine
My LSMOD:
----------------------------------------------------------------------------------------------------------------------------------
spandey@spandey-desktop:~$ lsmod
Module                  Size  Used by
btrfs                 489658  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
ufs                    73069  0 
qnx4                    6877  0 
hfsplus                71344  0 
hfs                    41250  0 
minix                  25303  0 
ntfs                   95030  0 
vfat                    9201  0 
msdos                   6436  0 
fat                    48240  2 vfat,msdos
jfs                   171034  0 
xfs                   693288  0 
exportfs                3449  1 xfs
reiserfs              225974  0 
pppoe                   9015  2 
pppox                   2054  1 pppoe
binfmt_misc             6599  1 
pci_stub                1146  1 
vboxpci                15274  0 
vboxnetadp              6968  0 
vboxnetflt             16492  0 
vboxdrv               248433  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218460  1 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
i915                  295819  4 
ip6_tables             11796  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
nf_nat_irc              1168  0 
snd_seq_midi            4588  0 
nf_conntrack_irc        3348  1 nf_nat_irc
drm_kms_helper         30136  1 i915
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_rawmidi            17783  1 snd_seq_midi
drm                   168092  4 i915,drm_kms_helper
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_seq_midi_event      6047  1 snd_seq_midi
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1302  1 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ip_tables              10492  1 iptable_filter
snd_timer              19067  2 snd_pcm,snd_seq
x_tables               15921  9 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,iptable_filter,ip_tables
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
w83627ehf              19492  0 
intel_agp              26566  2 i915
hwmon_vid               2310  1 w83627ehf
coretemp                5326  0 
led_class               2633  0 
soundcore                880  1 snd
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
via_rhine              19038  0 
mii                     4425  1 via_rhine

---

### Post by varunendra on 2011-09-22
Who is your service provider? Try changing your DNS in /etc/resolv.conf file.

But before trying anything with setup, I recommend to boot from the live cd which you installed from, and see if there is any speed difference. Sometimes it is a problem at the service provider's end. Especially, if you live in India (and moreover, if your ISP is bsnl), then it is a possibility.

---

### Post by spandey on 2011-09-22
I am in India and BSNL is my service provider. 

LiveCD is working fine without any problem. Windows 7 is working fine in other partition.

---

### Post by varunendra on 2011-09-22
How does ping to the sites in question behave? For example,
```
ping -c 10 google.com
```

A couple of things to try:

[LIST]
[*]Change DNS (for example, use google's 4.2.2.2 and 4.2.2.4 instead of current ones)
[*]Cleanup browser cache
[/LIST]
If this does nothing good to the speeds, please post outputs of (after browsing a couple of minutes):
```
ifconfig
ping -c 4 google.com
ping -c 4 archive.ubuntu.com
cat /etc/resolv.conf
```

Also, can you give a figurative description of how slow it is compared to live cd or windows?

---

### Post by spandey on 2011-09-22
The problem is the pages load very slowly. For ex. [www.washingtonpost.com]("http://www.washingtonpost.com") will take more than 2 minutes to load. where as in LiveCD in loads in less than 30 sec.

I have tried clearing cache etc.
------------------------------------------------------------------------------------------------------
**spandey@spandey-desktop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21410758 (21.4 MB)  TX bytes:4240679 (4.2 MB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30363 (30.3 KB)  TX bytes:30363 (30.3 KB)

ppp0      Link encap oint-to-Point Protocol  
          inet addr:117.201.166.218  P-t-P:117.201.160.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:9434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9382229 (9.3 MB)  TX bytes:1213137 (1.2 MB)

--------------------------------------------------------------------------------------------------
**spandey@spandey-desktop:~$ ping -c 4 google.com**
PING google.com (74.125.236.84) 56(84) bytes of data.
64 bytes from 74.125.236.84: icmp_req=1 ttl=56 time=275 ms
64 bytes from 74.125.236.84: icmp_req=2 ttl=56 time=270 ms
64 bytes from 74.125.236.84: icmp_req=3 ttl=56 time=287 ms
64 bytes from 74.125.236.84: icmp_req=4 ttl=56 time=266 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 16794ms
rtt min/avg/max/mdev = 266.042/274.834/287.781/8.162 ms
----------------------------------------------------------------------------------------

**spandey@spandey-desktop:~$ ping -c 4 archive.ubuntu.com**
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_req=1 ttl=49 time=515 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_req=2 ttl=49 time=524 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_req=3 ttl=49 time=523 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_req=4 ttl=49 time=521 ms

--- archive.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 515.354/521.380/524.699/3.732 ms
--------------------------------------------------------------------------------------------------

**spandey@spandey-desktop:~$ cat /etc/resolv.conf**
# Generated by NetworkManager
nameserver 8.8.4.4
nameserver 8.8.8.8

---

### Post by varunendra on 2011-09-22
Assuming you have access to your adsl modem/router provided by bsnl, why don't you configure pppoe in itself so that it gets connected automatically whenever powered on? This will reduce complexity in connection configuration.

If you can, I'd say let's do it first, then see if a direct connection improves the status. And be assured - it is the standard way to connect via an adsl router, so this won't cause any problems with the windows installation.

Besides, the replying delay is too high than it normally should be. For google, it is usually no more than 80 (it is 65 here at my place), and for archive.ubuntu.com, it is currently 154 approx here (keeps varying). Accordingly, did you try changing the DNS address to something else that gives significantly shorter delays?

Also, in ppp0 connection, have you manually set the MTU to 1460 or is it automatically selected so? If there is a manual entry in Network Manager for MTU value being 1460, try changing it to "automatic".


**_EDIT_:**
For better readability, please wrap your outputs in [noparse]```
...and...
```[/noparse] tags. ([See How]("http://ubuntuforums.org/misc.php?do=bbcode#code"))

---

### Post by spandey on 2011-09-22
After some history check, I found that all these problems started after I installed Google Chrome 14 and  Moonlight. I went ahead and removed Google Chrome and Moonlight as well but the problem persists. 

In ppp0 connection, MTU by default gets to 1460. I will try PPP0e and report but with same set up LiveCD works great.

---

### Post by varunendra on 2011-09-22
As a wild shot, try changing MTU to 1492. Also, you didn't mention whether you tried changing DNS or not.

---

### Post by spandey on 2011-09-22
I changed the MTU to 1492. Doesn't seem to have any effect. By the way with 1492 some sites won't open like indianrail.gov.in 

I have tried different DNS but no improvement.

---

### Post by varunendra on 2011-09-22
Set it back to "automatic" then!:)

Let us see if configuring pppoe in the router itself makes things better. In the meanwhile, please post output of:
```
cat /etc/network/interfaces
```

As a side note, while or after making 'any' change, keep an eye on the values of "errors, dropped, overruns, frame carrier and collisions" in the output of **ifconfig**. Normally, all of them should be 0.

---

### Post by spandey on 2011-09-23
The output of 
cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

```

---

