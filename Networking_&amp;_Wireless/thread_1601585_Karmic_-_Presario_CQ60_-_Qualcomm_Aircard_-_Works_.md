---
title: "Karmic - Presario CQ60 - Qualcomm Aircard - Works here on WinXP, but not on Ubuntu."
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by Sean Moran on 2010-10-20
Alas, the wifi provider for this hotel has been troubled for almost a week now, and my girlfriend finally became so tired of my frowns and scowls and overall bad form in the way of kindness and good manners that she dragged me down to Rayong Town today on the bus insisting that I get myself an aircard, to save her from having to put up with more of my offline misery.
We went straight to the Star Computer Hotel and the Hardware House International (where I tend to like the people as professional and not cheapest, but fair prices for good service), and after an hour of watching Somchai fiddle with all my newly installed Win XP drivers to try to get the aircard to work, I found a nice little number for 1,390 baht, that proclaims to be Linux friendly. I believe it's some sort of Qualcomm derivative, although the brand on the box is AlNet. I've listed the model from the installation guide below.
Yes, and it's working acceptibly on the unfortunate installation of WinXP I've got infesting my /dev/sda1 but I'm still offline back in Ubuntu.
It would really make my night/week/month if anybody might notice something wrong in the way I've been trying to follow the instructions. Please forgive me for not searching around much, because the online time is currently unknown except that it is bound to be extremely shortlived until I purchase a Happy-DTAC refill, and I have typed this all out in gEdit beforehand, because I don't know how much time is left on the inaugural SIMM card. I have saved the Comprehensive ndiswrapper Troubleshooting Guide as well as the HOWTO post a wireless issue thingo, and done the usual scan in typical frustrated geek mode. 
At least it taught me how to disable my onboard Atheros pci card with the /etc/modprobe.d/blacklist method, so I have now disabled the standard laptop's wifi facilities to avoid conflicts, but there's still a piece of this jigsaw that I haven't managed to wangle yet, and I know it will be something so simple once I work out what it is that I am not doing correctly.
Please help if you can see where I'm going wrong. I hope to put another 100 baht credit on the SIMM card tomorrow and login again to see if there might be some way to get myself redeemed from this Stuck-in-IE nightmare with this new Aircard Modem which has instructions for Ubuntu and Fedora, but it just doesn't work for me, out of the box.
<============================================================================>
Here is the data I have taken down so far - 
(NB: The characters "" = null/nothing for this text.)
SIMM Card Account: Happy DTAC, Thailand.
APN: [www.dtac.co.th]("http://www.dtac.co.th") <same as WinXP settings that work>
Aircard Modem Name: Alnet 3.5G USB HSDPA Modem (some kind of Qualcomm thing)
Model No.: UW622BL-T
I have installed Windows Wireless Drivers and:
bsmdm.inf
bsser.inf
to suit Win32 AND Vista64, just to be sure. For each: Hardware Present: NO
<all the .inf drivers that came with the Aircard>
Configure Network: "Could not find a network configuration tool"
---o0o---
I then booted back to WinXP and manually downloaded around a dozen .deb files to install GNOME-PPP, which I copied across to the var/cache/apt/archives directory and managed to install GNOME-PPP in a rather 'roundabout way ...
GNOME PPP:
Username: ""
Password: ""
Remember password OFF
Phone number: *99# <according to the Happy-DTAC setting which works on WinXP>
Connect: "Modem not responding"
Log:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
 
Setup:
Modem:
Device: /dev/ttyUSB0 Detect: "No modem was found on your system"
Type: Analog Modem
Speed: 460800
Phone Line: Tone
Volume: High
Phone numbers... *99#
Init Strings...
Init 2 ATQ0 V1 E1 SO=0 &C1 &D2 +FCLASS=0
Init 3 AT+CGDCONT=1,"IP",""DTAC" 
<Aircard instructions were ..."IP",""CMNET" but I took a chance on DTAC after CMNET failed repeatedly. Note extra quote in original instructions that I figured best to omit after a few trials...> 
Init 4 - Init 9 ""
Dial prefix: ""
Dial Attempts: 1
Wait for dialtone ON
Networking:
IP: Dynamic IP address
DNS: Automatic DNS
 
Options:
Desktop Integration:
On Connection:
Minimize OFF
Dock in notofication area OFF
Connection:
Auto Reconnect ON
Abort if line busy OFF
Abort if no dialtone ON
Check carrier line ON
Check default route ON
Ignore terminal strings ON
Send custom reply OFF
Idle time: 0 disabled
 
---o0o---
This is quite a long-shot and I don't know how much time is left on the credit for this SIMM card that came with the Aircard, but would anyone have any clues as to how I might replicate the working Windows XP Aircard Modem success with Ubuntu? I'm working with Karmic right now because the good old Karmic installation has the extra packages like Windows Wireless Drivers and such things that I would find it difficult to restore if I was to try on Maverick without some kind of online connection.
Also, it's a Compaq Presario CQ60 laptop, around 12 months old, if that might provide any answers. As mentioned above, the Atheros PCI card has been temporarily blacklisted to avoid conflicts.
Much appreciate your expertise and time to anyone who can fathom this one out. Thanks.
 
PS: Below are some output from commands I have run in accordance with the HOWTO suggestions:
<============================================================================>
$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1f:16:ea:15:63 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:26 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
wlan0 Link encap:Ethernet HWaddr 00:26:5e:38:e7:56 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
wmaster0 Link encap:UNSPEC HWaddr 00-26-5E-38-E7-56-00-00-00-00-00-00-00-00-00-00 
UP RUNNING MTU:0 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
<============================================================================>
$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
<============================================================================>
$ lsmod
Module Size Used by
usbserial 36264 0 
nls_utf8 1568 0 
isofs 31620 0 
binfmt_misc 8356 1 
ppdev 6688 0 
dm_crypt 12928 0 
joydev 10240 0 
nls_iso8859_1 3740 1 
nls_cp437 5372 1 
vfat 10716 1 
fat 51452 1 vfat
snd_hda_codec_nvhdmi 4828 1 
snd_hda_codec_conexant 20060 1 
arc4 1660 2 
ecb 2524 2 
iptable_filter 3100 0 
nvidia 9586440 38 
ip_tables 11692 1 iptable_filter
x_tables 16544 1 ip_tables
ndiswrapper 185532 0 
snd_hda_intel 27016 2 
snd_hda_codec 75708 3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep 7200 1 snd_hda_codec
snd_pcm_oss 37920 0 
snd_mixer_oss 16028 1 snd_pcm_oss
snd_pcm 75296 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
agpgart 34988 1 nvidia
psmouse 57332 0 
serio_raw 5280 0 
ath5k 124772 0 
mac80211 181140 1 ath5k
led_class 4096 1 ath5k
ath 8060 1 ath5k
cfg80211 93052 3 ath5k,mac80211,ath
snd_seq_dummy 2656 0 
shpchp 32272 0 
i2c_nforce2 6784 0 
snd_seq_oss 28576 0 
snd_seq_midi 6464 0 
snd_rawmidi 22176 1 snd_seq_midi
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 22276 2 snd_pcm,snd_seq
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 59204 16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 7264 1 snd
snd_page_alloc 9156 2 snd_hda_intel,snd_pcm
lp 8964 0 
parport 35340 2 ppdev,lp
usbhid 38208 0 
dm_raid45 84228 0 
xor 15620 1 dm_raid45
usb_storage 52768 0 
video 19380 0 
output 2780 1 video
forcedeth 54152 0 
ramzswap 8880 1 
xvmalloc 5180 1 ramzswap
lzo_decompress 2620 1 ramzswap
lzo_compress 2300 1 ramzswap
 
 
<============================================================================>
$dmesg OMITTED - it was 500 lines long for the output.
 
 
<============================================================================>
$ sudo lshw -C network
*-network 
description: Ethernet interface
product: MCP77 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1f:16:ea:15:63
capacity: 100MB/s
width: 32 bits
clock: 66MHz
capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:07:00.0
logical name: wmaster0
version: 01
serial: 00:26:5e:38:e7:56
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:23 memory:c2000000-c200ffff
 
 
 
 
<============================================================================>
$ iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wmaster0 Interface doesn't support scanning.
wlan0 No scan results
 
 
 
 
<============================================================================>
$ lsb_release -d
Description: Ubuntu 9.10
 
 
<============================================================================>
$ uname -mr
2.6.31-22-generic i686
 
<============================================================================>
$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... [ OK ] 
 
<<< Still same result: Modem not responding >>>

---

### Post by Sean Moran on 2010-10-21
What a storm in a teacup that turned out to be!  My misconception was pre-empted by the assumption that if it was too hard for people making good salaries in computer shops to work out how to setup elcheapo aircards on Linux, then it must be extremely difficult to accomplish.  

Hence all the trouble I went to yesterday morning to setup a new install of WinXP , Hence my efforts to install Windows Wireless Drivers two months ago, just in case I needed to go searching for an aircard that worked.    I even checked someone's HOWTO on the Bangkok Library site for Ubuntu 10.04 just to see if I'd gotten the APN right or not.

As it turned out, it wasn't such a big problem from the beginning.

For this Alnet 3.5G USB HSDPA Modem - Model No.: UW622BL-T it's easy as pii.

1. Forget about Windows Wireless Drivers and ndiswrapper concerns. Forget about Gnome-PPP and all the instructions in the .PDF file that comes with the product.  

2. You DO need to add "blacklist ath_pci" to the /etc/modprobe.d/blacklist.conf file if you're using the Atheros card that comes with the Compaq CQ60, and perhaps the same goes for other specifications of machine that have builtin wifi.

3. Goto System->Preferences->Network Connections and select Mobile Broadband->Add.

No need for username nor password with Happy DTAC, but the number *99# and the  APN of "www.dtac.co.th" seems imperative.  Good idea to tick the boxes to open by default and allow all users too, I reckon.

4. When the icon for the Aircard is ready ojn the desktop, right-click and select Eject.

5.   Open terminal and type:
```

sudo rmmod usbserial
sudo modprobe usbserial vendor=0x05c6 product=0x9000

```


Hopefully, aftger blacklisting any conflicting devices, adding the Mobile Broadband entry, Ejecting the device, and probing the USB serial modules as in #5, you should see the little panel icon start to whirr around and get some sort of broadband connection.

I'll double check this in a while to make sure it works the way I have mentioned it did.

It's really great to have a web browser and mouse that don't work in slow motion like WinXp was torturing me with last night.

Problem Solved.  Not sure where to add the correct prefix.

---

### Post by Sean Moran on 2010-10-21
Yeah, the config' checks out after another fresh install of Karmic.

The moral of the story is twofold:


1: Don't believe anything that the experts tell you in computer shops.

2: Don't believe the instructions they put in .PDF files for cheap perpherals.

I reckon that should make it a simple process to configure this sort of thing for any
one who can follow those two important guidelines.  Basically, you're on your own. Good luck.

---

