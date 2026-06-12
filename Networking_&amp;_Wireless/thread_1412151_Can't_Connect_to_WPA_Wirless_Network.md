---
title: "Can't Connect to WPA Wirless Network"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by emagine on 2010-02-20
Hey Linux Community,

I just added WPA2-PSK[AES] security to my network with a pass phrase.  Everything works fine, except my Linux machine.  When I type in the pass phrase and try to connect, the little wireless thing just keeps rotating and then after a minute says "disconnected".  It worked fine before I added the pass phrase, but now, it won't connect. Any ideas?

---

### Post by northd_tech on 2010-02-20
Have you tried this:

[http://ubuntuforums.org/showpost.php?p=8812404&postcount=10](http://ubuntuforums.org/showpost.php?p=8812404&postcount=10)

It might help if you posted the results when you enter these commands in a terminal:

```
lsmod

sudo lshw -C network

ifconfig

iwconfig

sudo iwlist scan
```

---

### Post by emagine on 2010-02-20
> **northd_tech said:**
> Have you tried this:

[http://ubuntuforums.org/showpost.php?p=8812404&postcount=10](http://ubuntuforums.org/showpost.php?p=8812404&postcount=10)

It might help if you posted the results when you enter these commands in a terminal:

```
lsmod

sudo lshw -C network

ifconfig

iwconfig

sudo iwlist scan
```

lsmod

Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
b44                    28684  0 
ssb                    35364  1 b44
ndiswrapper           185532  0 
joydev                 10240  0 
pcmcia                 36808  0 
arc4                    1660  0 
ecb                     2524  0 
snd_atiixp_modem       11940  0 
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
sdhci_pci               7100  0 
snd_atiixp             15720  2 
snd_ac97_codec        101216  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1532  1 snd_ac97_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
psmouse                56500  0 
serio_raw               5280  0 
k8temp                  4188  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
tifm_7xx1               5372  0 
tifm_core               7832  1 tifm_7xx1
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 32272  0 
i2c_piix4               9932  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_atiixp_modem,snd_atiixp,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
8139too                22620  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
8139cp                 19260  0 
mii                     5212  3 b44,8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp




sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:d4:00:94
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:1a:be:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+ASUS,02/11/2005, 3.100.64.0 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:20 memory:c0204000-c0205fff





ifconfig


eth0      Link encap:Ethernet  HWaddr 00:c0:9f:d4:00:94  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fed4:94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1671009 (1.6 MB)  TX bytes:440052 (440.0 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:329 (329.0 B)  TX bytes:329 (329.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:1a:be:31  
          inet6 addr: fe80::214:a5ff:fe1a:be31/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:257825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:337631233 (337.6 MB)  TX bytes:19186620 (19.1 MB)
          Interrupt:20 Memory:c0204000-c0206000





iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






sudo iwlist scan


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:5A:3F:D2:41
                    ESSID:"2WIRE436"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1F:33:D3:55:18
                    ESSID:"Lucas1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by northd_tech on 2010-02-20
> **emagine said:**
> lsmod

Module                  Size  Used by
**b44**                    28684  0 
ssb                    35364  1 **b44**
ndiswrapper           185532  0 

8139too                22620  0 
8139cp                 19260  0 
mii                     5212  3 b44,8139too,8139cp


sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:d4:00:94
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Wireless interface
       product: **BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: **Broadcom** Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:1a:be:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+ASUS,02/11/2005, 3.100.64.0 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:20 memory:c0204000-c0205fff

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:d4:00:94  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fed4:94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1671009 (1.6 MB)  TX bytes:440052 (440.0 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:329 (329.0 B)  TX bytes:329 (329.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:1a:be:31  
          inet6 addr: fe80::214:a5ff:fe1a:be31/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:257825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:337631233 (**337.6 MB**)  TX bytes:19186620 (**19.1 MB**)
          Interrupt:20 Memory:c0204000-c0206000

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:5A:3F:D2:41
                    ESSID:"2WIRE436"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1F:33:D3:55:18
                    ESSID:"Lucas1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

That is a Broadcom 4318 wireless, and your cabled ethernet is a Realtek 8139 family.

It looks to me like you may have a conflict with that ndiswrapper and the "b44" modules.  The funny thing is I thought you needed a "b43" module for a Broadcom 4318, but maybe this is a new one (there has been considerable trouble with the 4318 for a while now).

Why don't you try what I posted at post #7 here to disable that ndiswrapper module:

[http://ubuntuforums.org/showpost.php?p=8857356&postcount=7](http://ubuntuforums.org/showpost.php?p=8857356&postcount=7)

I'm not certain whether that Broadcom STA driver on that thread will work for your Broadcom 4318 though- I seem to remember "b43" being the better choice there, but that thread has some good information about how to get rid of your ndiswrapper module that might be causing your wireless conflict.

Strangely, you appear to be seeing wireless networks and have connected for 340 MB on wlan0 though, so it is working somewhat.

The connection might be getting confused with both "b44" and "ndiswrapper" modules installed though.

---

### Post by northd_tech on 2010-02-20
On that Realtek 8139, you might want to see the strange problem that another person had on this thread:

[http://ubuntuforums.org/showthread.php?t=1406907](http://ubuntuforums.org/showthread.php?t=1406907)

Unfortunately, it doesn't sound like her problem got fixed, but you might have more luck with your computer.

Are you able to connect with a cabled ethernet connection with no problems?

---

### Post by bkratz on 2010-02-20
@emagine


You might want to see if you fall into this catagory, I did and never got WPA2 working with ndiswrapper (version 1.55) in 9.10.

You can check easily in dmesg

[http://ubuntuforums.org/showthread.php?t=1343847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=1343847&highlight=ndiswrapper)

---

### Post by emagine on 2010-02-20
> **northd_tech said:**
> That is a Broadcom 4318 wireless, and your cabled ethernet is a Realtek 8139 family.

It looks to me like you may have a conflict with that ndiswrapper and the "b44" modules.  The funny thing is I thought you needed a "b43" module for a Broadcom 4318, but maybe this is a new one (there has been considerable trouble with the 4318 for a while now).

Why don't you try what I posted at post #7 here to disable that ndiswrapper module:

[http://ubuntuforums.org/showpost.php?p=8857356&postcount=7](http://ubuntuforums.org/showpost.php?p=8857356&postcount=7)

I'm not certain whether that Broadcom STA driver on that thread will work for your Broadcom 4318 though- I seem to remember "b43" being the better choice there, but that thread has some good information about how to get rid of your ndiswrapper module that might be causing your wireless conflict.

Strangely, you appear to be seeing wireless networks and have connected for 340 MB on wlan0 though, so it is working somewhat.

The connection might be getting confused with both "b44" and "ndiswrapper" modules installed though.
This did not work.  When you say it "is working somewhat" because of the 340 MB, that is because It used to work, until I got WAP security. Before my network was "insecure" (no password), but then I added the WAP security and now it isn't working.

---

### Post by emagine on 2010-02-20
> **bkratz said:**
> @emagine


You might want to see if you fall into this catagory, I did and never got WPA2 working with ndiswrapper (version 1.55) in 9.10.

You can check easily in dmesg

[http://ubuntuforums.org/showthread.php?t=1343847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=1343847&highlight=ndiswrapper)

Yes, unfortunately I do fall into this category.  Should I attempt to build my own ndiswrapper like that guy did in the thread?

---

### Post by northd_tech on 2010-02-21
> **emagine said:**
> Yes, unfortunately I do fall into this category.  Should I attempt to build my own ndiswrapper like that guy did in the thread?
Well, the Broadcom 4318 shows to be in the "working" category for HP laptops here:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS)

Also, ndiswrapper is up to version 1.56 now:

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

I know that rebuilding ndiswrapper from sourcecode worked much better than the "early" default ndiswrapper on a few laptops that I've worked on (including my Broadcom "4328", but it likes the Broadcom STA driver that has been released since then).  You also need to make sure that they are the correct Windows drivers (32- vs. 64-bit), and I remember reading somewhere that the 64-bit XP drivers worked on one wireless card when the Vista/Win 7 64-bit drivers would not.

There has been a lot of trouble with the 4318 Broadcoms lately (I suspect Karmic 9.10 or a recent "update"):

[http://ubuntuforums.org/tags.php?tag=broadcom+4318](http://ubuntuforums.org/tags.php?tag=broadcom+4318)

edit:  Also, are you sure that wireless-tools is completely installed and configured?

---

### Post by northd_tech on 2010-02-21
> **northd_tech said:**
> That is a Broadcom 4318 wireless, and your cabled ethernet is a Realtek 8139 family.

It looks to me like you may have a conflict with that ndiswrapper and the "b44" modules.  The funny thing is I thought you needed a "b43" module for a Broadcom 4318, but maybe this is a new one (there has been considerable trouble with the 4318 for a while now).


OK- according to Broadcom's NIC FAQ on their website, on that "b44" module:

> 	[What are  the Linux tg3, bnx2, bnx2x and b44 drivers?]("http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#")  To better support users, Broadcom has been actively supporting, maintaining, and testing the **in-kernel Linux drivers** for the  NetXtreme, NetXtreme II, NetLink and **4401** product lines. The following is list of drivers supported for each product line: 

[LIST]
[*]NetXtreme and NetLink - tg3
[*]NetXtreme II - bnx2 1G
[*]NetXtreme II - bnx2x 10G
[*]4401 - **b44**
[/LIST]
 [http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#](http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#)

I don't think you have a Broadcom 4401 anything from the above output- it might be worth removing that module and running the command sequence listed here at post #5 if you have a working ethernet connection:

[http://ubuntuforums.org/showpost.php?p=8859692&postcount=5](http://ubuntuforums.org/showpost.php?p=8859692&postcount=5)

If you don't have a working ethernet connection to run that apt-get command, you will need to download the source files and compile or try to find a .deb package for the b43-fwcutter from this thread:

b43 Offline Install
[http://ubuntuforums.org/showthread.php?t=763995](http://ubuntuforums.org/showthread.php?t=763995)

I'm not sure what version of ubuntu or machine architecture you have, or I could have probably given a link to the ubuntu package location.  I'm guessing it will be Karmic 9.10 (that's the one having the most trouble with 4318's lately).  If so, here those are:

[http://packages.ubuntu.com/karmic/b43-fwcutter](http://packages.ubuntu.com/karmic/b43-fwcutter)

---

### Post by northd_tech on 2010-02-21
Also, if you are interested there is a newer open source (as in not proprietary Broadcom) "b43" driver that claims to work with the 4318 on this thread:

**Open Source Firmware for b43**
[http://ubuntuforums.org/showthread.php?t=1055078](http://ubuntuforums.org/showthread.php?t=1055078)

---

### Post by emagine on 2010-02-21
Thanks for the help guys.  I just switched my network to WEP security.  I know that isn't real secure, but it now allows me to connect with my Linux notebook.  I don't want to spend too much time on this, because I am using a temporary notebook while my primary is at HP getting repaired.  I am dual booting Vista and Ubuntu on that one.  I will try to get the WPA security to work with that one when it comes back. Thanks guys.

---

### Post by Dennis Kjær on 2010-02-21
I had the same problem and installed 9,04 that has done the job for me

---

