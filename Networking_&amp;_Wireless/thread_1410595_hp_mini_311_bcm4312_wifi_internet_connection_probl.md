---
title: "hp mini 311 bcm4312 wifi internet connection problem"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by cnagu on 2010-02-18
Friends,

Need your help in resolving a problem I face in getting my wireless connection work. I am able to establish connection with my router and browse router configuration pages successfully. However, trying to access any other internet address (through browser or ping etc) results in intolerable poor performance (70% to 100% packet loss in ping). Ethernet connection (eth0) works perfectly though.

Am furnishing the details below:

Netbook: HP Mini 311
Product No: VM257UA#ABA
Model No:311-1000NR
Ubuntu Netbook Remix:
```

uname -r
2.6.31-19-generic
```

```
lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

I have installed Broadcom STA drivers. All ssb, b34 etc are blacklisted properly.

```
lsmod | grep wl
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
```

Connection gets established and interface gets defined properly

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:0F:A3:7C:11:B0
                    ESSID:"******"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-42 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:4a:69:a5  
          inet6 addr: fe80::226:9eff:fe4a:69a5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10201320 (10.2 MB)  TX bytes:3222993 (3.2 MB)
          Interrupt:22 Base address:0x8000 

eth2      Link encap:Ethernet  HWaddr 0c:60:76:80:5d:bb  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe80:5dbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1982 errors:0 dropped:0 overruns:0 frame:120
          TX packets:2698 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:937516 (937.5 KB)  TX bytes:418244 (418.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:373362 (373.3 KB)  TX bytes:373362 (373.3 KB)
```

Am able to ping and browse my router

```
ping 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_seq=1 ttl=128 time=3.16 ms
64 bytes from 192.168.1.10: icmp_seq=2 ttl=128 time=1.79 ms
64 bytes from 192.168.1.10: icmp_seq=3 ttl=128 time=1.86 ms
64 bytes from 192.168.1.10: icmp_seq=4 ttl=128 time=1.71 ms
64 bytes from 192.168.1.10: icmp_seq=5 ttl=128 time=1.87 ms
64 bytes from 192.168.1.10: icmp_seq=6 ttl=128 time=1.89 ms
64 bytes from 192.168.1.10: icmp_seq=7 ttl=128 time=3.01 ms
64 bytes from 192.168.1.10: icmp_seq=8 ttl=128 time=3.01 ms
64 bytes from 192.168.1.10: icmp_seq=9 ttl=128 time=3.02 ms
64 bytes from 192.168.1.10: icmp_seq=10 ttl=128 time=2.89 ms
64 bytes from 192.168.1.10: icmp_seq=11 ttl=128 time=1.83 ms
64 bytes from 192.168.1.10: icmp_seq=12 ttl=128 time=1.81 ms
64 bytes from 192.168.1.10: icmp_seq=13 ttl=128 time=1.86 ms
^C
--- 192.168.1.10 ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12018ms
rtt min/avg/max/mdev = 1.714/2.289/3.160/0.584 ms
```

However, I am unable to get onto any other internet sites. Either there is very long delay in resolving the address or it just fails in connecting. I have configured the DNS address properly on the router. Ethernet connection works fine with this configuration.

```
nslookup google.co.in
Server:		192.168.1.10
Address:	192.168.1.10#53

Non-authoritative answer:
Name:	google.co.in
Address: 216.239.61.104
```

```
ping 216.239.61.104
PING 216.239.61.104 (216.239.61.104) 56(84) bytes of data.
^C
--- 216.239.61.104 ping statistics ---
139 packets transmitted, 0 received, 100% packet loss, time 138282ms
```

Please help in resolving this issue, so that I can be on internet using my wifi connection.

Thanks a lot,
nagu.

---

### Post by northd_tech on 2010-02-18
Hi nagu.

Your Broadcom STA driver looks very close to functional to me- I don't think it is a driver problem.  I've recently been having very slow and very intermittent WiFi problems with my Broadcom 4321AG (that **lspci** calls "4328") lately under a 64-bit ubuntu 9.04 Jaunty Jackalope and the Broadcom STA driver.

I think I got that slow problem fixed (or as fixed as my slow connection at work will allow) earlier today.

Let me reboot into ubuntu and take a look at a few of my network settings with the [faster] home ISP in a few minutes.

---

### Post by northd_tech on 2010-02-19
> **cnagu said:**
> 
```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:0F:A3:7C:11:B0
                    ESSID:"******"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-42 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
``````
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:4a:69:a5  
          **inet6 addr: fe80::226:9eff:fe4a:69a5/64 Scope:Link**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10201320 (10.2 MB)  TX bytes:3222993 (3.2 MB)
          Interrupt:22 Base address:0x8000 

eth2      Link encap:Ethernet  HWaddr 0c:60:76:80:5d:bb  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
         ** inet6 addr: fe80::e60:76ff:fe80:5dbb/64 Scope:Link**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1982 errors:0 dropped:0 overruns:0 frame:120
          TX packets:2698 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:937516 (937.5 KB)  TX bytes:418244 (418.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
         ** inet6 addr: ::1/128 Scope:Host**
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:373362 (373.3 KB)  TX bytes:373362 (373.3 KB)
```Am able to ping and browse my router


OK, I'm back under ubuntu (using wicd instead of Gnome's Network Manager applet since some people had recommended that change for slow connections).

According to a firefox bandwidth plugin, I'm now getting a download speed of 14091 kbps (13.76 Mbps or about 10 times the T1 bar's 1500 kbps).  My speed at work had improved from 250-1300 kbps to about 2000-3000 kbps with the "fixes" that I tried today.  My upload speed is still in mid-DSL range at 414 kbps.

I was reading in the bugfix forum about the older "IPv6" and slow internet connections.  Since the one was such an easy fix on my machine, I thought I'd give it a try (my WiFi internet has been dropping out every few minutes at work when I've been running ubuntu- and of course Vista was fine).

I added some kernel options to my GRUB "menu.lst" file (of course after I backed that file up a couple of times before making any of the changes) to disable any of the newer "IPv6" modules and other stuff.  I remember reading about a Firefox setting that also should be changed, but I didn't find that thread and haven't modified that yet.  Firefox seems to work just fine though.

Opinions vary on the IPv6 thing from what I read, but it gave me about 10x as much speed just today, and I only changed about 10 lines or so in my configuration files.

You can test out whether your ISP and router are using IPv4 or IPv6 at these websites:

[http://www.ip4.me](http://www.ip4.me)
[http://www.ip6.me](http://www.ip6.me)
[http://www.whatismyv6.com](http://www.whatismyv6.com)
[http://www.wantismyipv6address.com](http://www.wantismyipv6address.com)

Here is more on the IPv6 thing:

IPv6 Bug
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218)

That "inet6" makes me think that you might be seeing this "IPv6" problem, especially since my working Broadcom WiFi connection says this tonight in **ifconfig** (you will note that I have no "inet6" line below):

> eth1      Link encap:Ethernet  HWaddr 00:29:00:33:54:19  
          inet addr:192.xx.xx.xx  Bcast:192.xx.xx.xx  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3405 errors:0 dropped:0 overruns:0 frame:1659
          TX packets:3307 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2250193 (2.2 MB)  TX bytes:654874 (654.8 KB)
          Interrupt:19 also, **iwconfig** gives this:

> eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
Before you make any changes though, do you think you could post the results of this command?

```
lsmod
```Again, I've also got a Broadcom WiFi using the STA driver, and my connection is MUCH faster tonight than it has been for a long time under ubuntu.

There have been a TON of threads about this slow connection thing lately too:

[http://ubuntuforums.org/showthread.php?t=1405129&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1405129&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1076199&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1076199&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1195755&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1195755&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1407910&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1407910&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1406817&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1406817&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1405789&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1405789&highlight=slow+internet+IPv6)

---

### Post by cnagu on 2010-02-19
Thanks for quick response  northd_tech.

I managed to get onto internet with the speed equal to ethernet connection by making following changes:

[LIST=1]
[*] I configured OpenDNS address  208.67.222.222 & 208.67.220.220 on the router. But, I dont think this made the difference.

[*] In Network Manager->Edit Connections->Wireless->Edit->IPV4 Settings->Method, instead of "Automatic (DHCP)", I selected "Automatic (DHCP) Addresses only" and then provided OpenDNS address manually. Doing this adds nameserver entries in /etc/resolv.conf accordingly.

[*] Disconnected wireless by unchecking "Enable Wireless" option and reconnected by checking that option again.
[/LIST]

Above three steps helped me get onto internet. However, it lasted only for few minutes (didn't time it). I not only lost the connection with internet, but also with my router. Also, please note that I didn't have to do above three steps for my Ethernet connection.

To keep the connection alive, I just ran "ping 208.67.222.222" non-stop on a terminal window. That kept me on internet without any instability. I am posting this reply through my wireless connection :D

To summarize, wireless connection needs [LIST=a]
[*] explicit DNS configuration and [*] connection that is kept alive.
[/LIST]

There must be some parameters that might help achieve these two things.

Thanks again for your attention.

Regards,
nagu.

---

### Post by northd_tech on 2010-02-19
So did you try running the IPv6 test at this website then?

[http://www.ip6.me/](http://www.ip6.me/)

Be sure to try both the IPv4 and IPv6 versions at that link- if they both work then your settings might be OK.

edit:  I'm still wondering which modules you have loaded too (** lsmod** command).

---

### Post by cnagu on 2010-02-19
lsmod with grep wl is provided in the original post. I verified that ssb and b43 etc are not loaded. Let me know if you need the entire output of lsmod. 

I ran the IPV6 test. Understandably it doesn't work as my router doesn't support IPV6. IPV4 test works fine.

Do you know of any kernel/driver parameter to configure to get DNS address from router and to keep the connection alive? I am yet to go through all the links you provided. Thanks again.

Regards,
nagu.

---

### Post by northd_tech on 2010-02-19
> **cnagu said:**
> lsmod with grep wl is provided in the original post. I verified that ssb and b43 etc are not loaded. Let me know if you need the entire output of lsmod. 
  I've seen modules stick around persistently before with all the multiple scripts and configuration files (I suspect depending upon how the updates, configuration scripts, etc. were run or installed in the past).  That's one reason why I nearly always look at the entire **lsmod** (and **lspci** ) output- sometimes **grep** will "hide" what is really going on (like the old joke about the 3 blind men and the elephant).
> 
I ran the IPV6 test. Understandably it doesn't work as my router doesn't support IPV6. IPV4 test works fine.

Do you know of any kernel/driver parameter to configure to get DNS address from router and to keep the connection alive? I am yet to go through all the links you provided. Thanks again.
If you are interested in getting rid of that IPv6 thing, here are the comment lines from my /boot/grub/menu.lst configuration file:

# pass the 'i[COLOR=Blue]pv6.disable=1[/COLOR]' kernel parameter (in your menu.lst)
# configure your net manually, deleting all 'ipv6' strings (in /etc/network/interfaces or in /etc/resolv.conf)

You would need to paste the the [COLOR=Blue]ipv6.disable=1[/COLOR] part at the end of your "kernel /boot/vmlinuz..." line in "menu.lst" if you are running GRUB.  If you have multiple kernels, then you could just change one of the menu choices and test that one (with "spares" to fall back on).

How to assign those Open DNS settings will depend upon whether you are using Gnome Network Manager, wicd, KDE, etc.  I believe there is a place to put those in one of the /etc/... configuration files too (but that might depend upon your setup).  What version/kernel of ubuntu are you running?

---

### Post by cnagu on 2010-02-19
```
lsmod
Module                  Size  Used by
michael_mic             2204  8 
arc4                    1660  4 
cbc                     3516  194 
aes_i586                8124  195 
aes_generic            27484  1 aes_i586
ecb                     2524  5 
joydev                 10240  0 
usbhid                 38208  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
dm_crypt               12928  0 
snd_hda_codec_nvhdmi     4828  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip     8636  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
iptable_filter          3100  0 
v4l1_compat            14496  2 uvcvideo,videodev
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
psmouse                56500  0 
serio_raw               5280  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
nvidia               9586440  52 
agpgart                34988  1 nvidia
i2c_nforce2             6784  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
forcedeth              54152  0 
video                  19380  0 
output                  2780  1 video

```



```
lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [Quadro FX 470M] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

```
sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:26:9e:4a:69:a5
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:53106000-53106fff ioport:30e0(size=8) memory:53109000-531090ff memory:53109300-5310930f
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 0c:60:76:80:5d:bb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.14 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:53000000-53003fff

```


for now, i'll not bother about IPV6...

Thanks & Regards,
nagu.

---

### Post by northd_tech on 2010-02-20
> **cnagu said:**
> lsmod
Module                  Size  Used by

dm_crypt               12928  0 
lib80211_crypt_tkip     8636  0 

**wl **                  1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,**wl**

i2c_nforce2             6784  0 

[COLOR=Red]forcedeth              54152  0 [/COLOR]

```
lspci
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```
```
sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:26:9e:4a:69:a5
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:53106000-53106fff ioport:30e0(size=8) memory:53109000-531090ff memory:53109300-5310930f
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 0c:60:76:80:5d:bb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.14 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:53000000-53003fff

```

Your HP mini 311 looks extremely similar to my 2+ year old HP DV98xx laptop- they use related wireless and ethernet interfaces.  I'm guessing that they essentially miniaturized my 17-inch laptop into that and called it an NVIDIA "MCP79" bridge.

It seems a little odd that yours does not appear to have 802.11n support though.  That "[COLOR=Red]forcedeth[/COLOR]" should be the nForce ethernet controller (which I believe is an updated version of an ancient IBM ethernet interface) and I highlighted that in [COLOR=Red]red[/COLOR].

I have edited your responses down to what I think might be remotely related to networking, and here is some of what my [working] **lsmod** shows that is likely network related:

> Module                  Size  Used by

ipt_MASQUERADE         11520  1 
iptable_nat            14724  1 
nf_nat                 30100  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      24216  4 iptable_nat,nf_nat
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
nf_conntrack           84752  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             11776  2 
xt_tcpudp              11776  4 
iptable_filter         11392  1 
ip_tables              28304  2 iptable_nat,iptable_filter
x_tables               31624  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables

ieee80211_crypt_tkip    17920  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,**wl**
**wl **                  1286352  0

[COLOR=Red]forcedeth              68368  0 [/COLOR]


Here is my **sudo lshw -c network**:

> 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1a:6a:5a:5a:09
       capacity: 100MB/s
    **   width: 32 bits**
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR=Red]driver=forcedeth[/COLOR] driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 [COLOR=Red]module=forcedeth [/COLOR]multicast=yes port=MII
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:27:00:18:21:19
**       width: 64 bits**
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=wl0 driverversion=5.10.91.9 **ip=192.xx.xx.xx latency=0 module=wl multicast=yes **wireless=IEEE 802.11abgn**
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: c8:e5:9c:5a:5c:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.xx.xx.xx link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:8b:46:ff:bd:3c
       capabilities: ethernet physical
       configuration: br

It seems a little strange that we both appear to have 32-bit ethernet "[COLOR=Red]forcedeth[/COLOR]" interfaces, where the wireless is 64-bit.

Let me know if you need me to check or post any more of the settings on my Broadcom WiFi.  My connection has been much more reliable since I disabled the IPv6 (but it is still far from perfect).

Oh, here is what my **iwconfig** looks like:

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:170
          Rx invalid nwid:0  invalid crypt:302  invalid misc:0

virbr0    no wireless extensions.

pan0      no wireless extensions.

---

### Post by cnagu on 2010-03-03
Sorry for the delay in posting any further updates. My success in getting wireless work didn't last for long. Once I restarted the netbook, everything got back to normal (problematic) state.

I could not predict/repeat as when, how & why it doesn't work. I have given up on this for now - expecting that this problem will be solved later.

Thanks & Regards...

---

