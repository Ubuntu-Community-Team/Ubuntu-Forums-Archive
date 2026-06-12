---
title: "Download Speeds 700kb/sec out of 15MB/sec"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2012-12-19
(EDIT: THREAD IS KINDA SOLVED IN WIERD WAY)
it does appear as tech has told me that I have wrong drivers anyway however half of my speed came back from SIMPLY disabling/removing the firefox addon of anonymox. apparently it limits your speed if you dont buy the full version somehow. I found this out from researchin after I read that someone else had their internet speed reduced as well while using it. My speed was a drastic change though from 7-10MB/sec down to 700kb so if you use this maybe test your speed at [www.testmy.net](www.testmy.net) to find out. something as simple as though got my speed back to 7MB/sec so with this speed I am content in not completely doing the work below that Tech was nice enough to take the time to point out. Plus just worry I could screw it up worse.  Thanks again Tech. LMAO part of this over a firefox addon who would of thought!




Hi. How's it goin Pro's? 
I am using Lubuntu 12.10 this WAS the first operating system I have come by that finally was downloading at speeds nearly what I am paying for.  My internet plan is a staggering 15MB/sec with Suddenlink.  I have been using many os's and all of them downloading at what I am now about 700kb/sec now that horrible of course for an internet plan of 15MB/sec.
What Lubuntu 12.10 was downloading at was 10-12MB/sec until I applied all of the NORMAL updates it asked for from sudo apt-get dist-upgrade this is all I did. I believe this is where the problem is coming from but not exactly sure since I tried so many os's that never even hit better than 1.5MB/sec and Lubuntu the first at 10MB/sec. Now I know that I could just reinstall quite possibly but I don't want to do this cause I have already set up all of my programs that I need and want on my system and would hate to download a full day worth of stuff again (besides once I update the system again then I would be back to square 1). Plus it would be nice to know what the actual fix is that I need so in the future if I want to use another system I can and then I could know what I need to get or do. I like distro hopping sometimes every 6 months or so.  So far about the only thing I have done is changed the MTU from auto to 1492 (same speed of 700kb/sec) then I changed it too 1500 (same speed of 700kb/sec as well).  I also called my cable company and they said from their side it is running faster than it should (go figure and I can't use that speed).

Below is all of the wifi card info and alot more info than needed since this is wifi prob but just in case something wierd is conflicting I included more info. I just ran a benchmark and used a couple codes I knew.
If I am missing something please let me know but I have tried to explain this in full detail for you guys.  Thanks to any help I get much appreciated.


lsusb
Bus 001 Device 003: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]


iwconfig
wlan0     IEEE 802.11bgn  ESSID:"suddenlink.net-4A12"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:CF:F0:4A:10   
          Bit Rate:72 Mb/s (sometimes this is 150 but rare and still have 700kb/sec)   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=82/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
lo        no wireless extensions.



ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77873 (77.8 KB)  TX bytes:77873 (77.8 KB)

wlan0     Link encap:Ethernet  HWaddr 08:86:3b:77:98:86  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a86:3bff:fe77:9886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38632 errors:0 dropped:5488 overruns:0 frame:0
          TX packets:24295 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46324727 (46.3 MB)  TX bytes:2790151 (2.7 MB)


sudo lshw -C network
[sudo] password for lubuntu: 
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 08:86:3b:77:98:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.10 multicast=yes wireless=IEEE 802.11bgn


Network: (from benchmark program)

Interfaces
Network Interfaces
wlan0	40.86MiB	2.36MiB	192.168.0.10
lo	0.06MiB	0.06MiB	127.0.0.1
IP Connections
Connections
127.0.0.1:631	LISTEN	0.0.0.0:*	tcp
127.0.1.1:53		0.0.0.0:*	udp
192.168.0.10:33418	ESTABLISHED	93.152.160.101:8001	tcp
192.168.0.10:34962	ESTABLISHED	173.193.202.116:88	tcp
192.168.0.10:34968	ESTABLISHED	173.193.202.116:88	tcp
::1:631	LISTEN	:::*	tcp6
127.0.1.1:53		0.0.0.0:*	udp
0.0.0.0:68		0.0.0.0:*	udp
192.168.0.10:123		0.0.0.0:*	udp
127.0.0.1:123		0.0.0.0:*	udp
0.0.0.0:123		0.0.0.0:*	udp
0.0.0.0:12045		0.0.0.0:*	udp
:::25512		:::*	udp6
::1:123		:::*	udp6
fe80::a86:3bff:fe77:123		:::*	udp6
:::123		:::*	udp6
Routing Table
IP routing table
0.0.0.0 / 192.168.0.1	0.0.0.0	UG	wlan0
192.168.0.0 / 0.0.0.0	255.255.255.0	U	wlan0
ARP Table
ARP Table
192.168.0.1	00:1d:cf:f0:4a:15	wlan0
DNS Servers
Name servers
127.0.1.1	
Statistics
IP
34583	Total packets received
12	With invalid addresses
0	Incoming packets discarded
0	Incoming packets discarded
33766	Incoming packets delivered
22128	Requests sent out
46	Dropped because of missing route
ICMP
146	ICMP messages received
12	Input ICMP message failed.
165	ICMP messages sent
0	ICMP messages failed
ICMPMSG
TCP
299	Active connections openings
0	Bad segments received.
8	Failed connection attempts
1	Connection resets received
3	Connections established
32489	Segments received
20782	Segments send out
74	Segments retransmited
0	Bad segments received.
82	Resets sent
UDP
982	Packets received
147	Packets to unknown port received.
0	Packet receive errors
1135	Packets sent
UDPLITE
TCPEXT
137	TCP sockets finished time wait in fast timer
311	Delayed acks sent
1311	Packets directly queued to recvmsg prequeue.
121094	Bytes directly in process context from backlog
2988599	Bytes directly received in process context from prequeue
25473	Packet headers predicted
2089	Packets header predicted and directly queued to user
1002	Acknowledgments not containing data payload received
258	Predicted acknowledgments
1	Connections reset due to early user close
25	Other TCP timeouts
6	Connections reset due to unexpected data
1	Connections reset due to early user close
3	Connections aborted due to timeout


and last but no least modules:

Kernel Modules
Loaded Modules
xt_limit	Xtables: rate-limit match
xt_tcpudp	Xtables: TCP, UDP and UDP-Lite match
xt_LOG	Xtables: IPv4/IPv6 packet logging
ipt_MASQUERADE	Xtables: automatic-address SNAT
xt_DSCP	Xtables: DSCP/TOS field modification
ipt_REJECT	Xtables: packet "rejection" target for IPv4
nf_conntrack_irc	IRC (DCC) connection tracking helper
nf_conntrack_ftp	ftp connection tracking helper
xt_state	ip[6]_tables connection tracking state match module
iptable_nat	
nf_nat	
nf_conntrack_ipv4	
nf_conntrack	
nf_defrag_ipv4	
iptable_mangle	iptables mangle table
iptable_filter	iptables filter table
ip_tables	IPv4 packet filter
x_tables	{ip,ip6,arp,eb}_tables backend module
bnep	Bluetooth BNEP ver 1.3
rfcomm	Bluetooth RFCOMM ver 1.11
bluetooth	Bluetooth Core ver 2.16
snd_hda_codec_analog	Analog Devices HD-audio codec
snd_hda_intel	Intel HDA driver
snd_hda_codec	HDA codec core
nouveau	nVidia Riva/TNT/GeForce
snd_hwdep	Hardware dependent layer
snd_pcm	Midlevel PCM code for ALSA.
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
r8712u	rtl871x wireless lan driver
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
kvm_amd	
ttm	TTM memory manager subsystem (for DRM device)
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
kvm	
drm_kms_helper	DRM KMS helper
drm	DRM shared core routines
snd	Advanced Linux Sound Architecture driver for soundcards.
soundcore	Core sound module
snd_page_alloc	Memory allocator for ALSA system.
serio_raw	Raw serio driver
k8temp	AMD K8 core temperature monitor
nv_tco	TCO timer driver for NV chipsets
i2c_algo_bit	I2C-Bus bit-banging algorithm
ppdev	
mxm_wmi	MXM WMI Driver
i2c_nforce2	nForce2/3/4/5xx SMBus driver
video	ACPI Video Driver
mac_hid	
parport_pc	PC-style parallel port driver
wmi	ACPI-WMI Mapping Driver
lp	
parport	
hid_generic	HID generic driver
usbhid	USB HID core driver
hid	
uas	
usb_storage	USB Mass Storage driver for Linux
sata_nv	low-level driver for NVIDIA nForce SATA controller
pata_amd	low-level driver for AMD and Nvidia PATA IDE
floppy	


Also even though it is one of those preset routers I can't change nothin in here is some of its stats:

TX Power Level:High

B/G/N Mixed BG    Protection:enabled    Beacon Interval:110   DTIM Interval:1   RTS Threshold 2347   Fragment Threshold 2346   Frame Burst:not enabled
WMM Power Save Mode:enabled

80211N Specific Settings: Channel Bandwidth 20MHZ    Guard Interval: 800ns   MCS: Auto


forgot to include that I knew my speeds from testmy.net just to assure you all and also tried downloading various things. even torrents never went over 1mb/sec basically

Sorry about the clutter. If this ain't one of the most detailed first writes you've seen on here, I don't know what is. lol
Thanks guy's

---

### Post by TechAlchemist on 2012-12-19
Please post the results from:

```

dmesg | grep 819

```

See also:

[http://ubuntuforums.org/showthread.php?t=1705004]("http://ubuntuforums.org/showthread.php?t=1705004")

---

### Post by slixz85 on 2012-12-19
> **TechAlchemist said:**
> Please post the results from:

```

dmesg | grep 819

```

See also:

[http://ubuntuforums.org/showthread.php?t=1705004]("http://ubuntuforums.org/showthread.php?t=1705004")

[    0.000000] Memory: 978196k/1014848k available (5962k kernel code, 36192k reserved, 2931k data, 756k init, 101448k highmem)
[    0.181927] pci 0000:00:10.1: [10de:026c] type 00 class 0x040300
[    0.181942] pci 0000:00:10.1: reg 10: [mem 0xd2340000-0xd2343fff]
[    0.181998] pci 0000:00:10.1: PME# supported from D3hot D3cold

---

### Post by TechAlchemist on 2012-12-19
It seems like you aren't using the right drivers for that adapter.

You can try just switching to the correct firmware:
```

sudo modprobe r8192u_usb

```

as I think ubuntu should come with this firmware now.

If you have no success with that, try:
```

modprobe -l | grep r81*

```

and post the results before you try to build from source.

```

sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

```

as per [http://ubuntuforums.org/showthread.php?t=1705004#post10553443](http://ubuntuforums.org/showthread.php?t=1705004#post10553443).

You may need to uninstall and/or blacklist your other firmware.

EDIT: It looks like that driver is outdated and only works for the 2.6 kernel.  You may need to get a new one and build from source from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true#2282](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true#2282) (scroll to RTL8188SU and use one of the linux links).

Or you can skip the web interface and get it directly from one of their FTP links:

```

curl -O ftp://WebUser:Lc9FuH5r@209.222.7.36/cn/wlan/RTL819xSU_usb_linux_v2.6.6.0.20120405.zip

```

---

