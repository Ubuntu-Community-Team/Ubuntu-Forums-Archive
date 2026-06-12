---
title: "Wireless connection drops on &quot;heavy duty&quot;"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by yyann on 2010-07-20
Hello everyone and thanks for checking in on my problem. This has been annoying me for weeks - ever since I updated to Lucid Lynx. As I was using the upgrade to check out other distributions, I happened to find out it happens with Ubuntu 10.04 (32-bit), Kubuntu (32-bit) and Ubuntu (64-bit, my current system).

So what happens? Whenever I use the internet connection "at the limit" - say, I am downloading a file from a server or streaming a video on YouTube - the connection simply drops. Ubuntu broadcasts a message that the connection has been lost and in order to turn it on again, I need to deactivate wireless in the network manager and turn it on again. I've been checking out the forums and found replies saying it had something to do with the high bandwidth usage that is set somewhere. I just don't know where to set it. 

Maybe you have an idea? 

Here are the desired outputs. :)

**1. Machine and brand:**```

FujitsuSiemens Lifebook E8210, Intel CentrinoDuo 2,0 GHz, 4,0 GiB DDR-RAM.
```**2. Wireless Brand, Model and Chipset:**
```
yann@yyann:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
08:03.1 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
08:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
08:03.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
08:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
yann@yyann:~$ lsusb
Bus 005 Device 002: ID 0c24:000f Taiyo Yuden Bluetooth Driver (V2.0+EDR)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**3. Interface**
```

yann@yyann:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"F*ck you, Google!"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:BC:30:68   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

yann@yyann:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:17:42:21:3e:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:11659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11659 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:1482242 (1.4 MB)  TX bytes:1482242 (1.4 MB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:19:d2:53:b0:15  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::219:d2ff:fe53:b015/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:42947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32030 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:48678245 (48.6 MB)  TX bytes:6352836 (6.3 MB)

```**4. Modules**
```

yann@yyann:~$ lsmod
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  1 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
rfcomm                 40393  4 
sco                     9617  2 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34806  16 rfcomm,bnep
vboxnetadp              5235  0 
vboxnetflt             12242  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
vboxdrv              1768311  2 vboxnetadp,vboxnetflt
joydev                 11072  0 
snd_hda_codec_realtek   279040  1 
pcmcia                 35580  0 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
arc4                    1473  2 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
iwl3945                79436  0 
iwlcore               124955  1 iwl3945
snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                740390  3 
ppdev                   6375  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           22901  4 
rsrc_nonstatic          9830  1 yenta_socket
mac80211              238448  2 iwl3945,iwlcore
btusb                  12969  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
ttm                    60847  1 radeon
drm_kms_helper         30742  1 radeon
irda                  205699  0 
crc_ccitt               1675  1 irda
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
parport_pc             29958  1 
psmouse                64576  0 
serio_raw               4918  0 
video                  20623  0 
output                  2503  1 video
cfg80211              148546  3 iwl3945,iwlcore,mac80211
drm                   199204  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
fujitsu_laptop         12753  0 
led_class               3764  4 iwl3945,iwlcore,sdhci,fujitsu_laptop
snd                    71106  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              29095  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usb_storage            49833  1 
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
sky2                   48803  0 

```**5. Kernel:**```


yann@yyann:~$ dmesg | grep wlan0
[   16.574043] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.653024] wlan0: deauthenticating from 00:1f:33:bc:30:68 by local choice (reason=3)
[   51.654666] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[   51.850129] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 2)
[   52.052530] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 3)
[   52.250074] wlan0: direct probe to AP 00:1f:33:bc:30:68 timed out
[   64.279223] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[   64.282075] wlan0: direct probe responded
[   64.282082] wlan0: authenticate with AP 00:1f:33:bc:30:68 (try 1)
[   64.284033] wlan0: authenticated
[   64.284061] wlan0: associate with AP 00:1f:33:bc:30:68 (try 1)
[   64.286876] wlan0: RX AssocResp from 00:1f:33:bc:30:68 (capab=0x411 status=0 aid=1)
[   64.286881] wlan0: associated
[   64.289089] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.380042] wlan0: no IPv6 routers present
[ 3054.081122] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3064.383154] wlan0: deauthenticating from 00:1f:33:bc:30:68 by local choice (reason=3)
[ 3064.383306] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[ 3064.386781] wlan0: direct probe responded
[ 3064.386788] wlan0: authenticate with AP 00:1f:33:bc:30:68 (try 1)
[ 3064.388601] wlan0: authenticated
[ 3064.388635] wlan0: associate with AP 00:1f:33:bc:30:68 (try 1)
[ 3064.391322] wlan0: RX AssocResp from 00:1f:33:bc:30:68 (capab=0x411 status=0 aid=1)
[ 3064.391329] wlan0: associated
[ 3064.393837] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3075.162520] wlan0: no IPv6 routers present
[ 3387.411763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3397.716094] wlan0: deauthenticating from 00:1f:33:bc:30:68 by local choice (reason=3)
[ 3397.716156] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[ 3397.719770] wlan0: direct probe responded
[ 3397.719778] wlan0: authenticate with AP 00:1f:33:bc:30:68 (try 1)
[ 3397.721599] wlan0: authenticated
[ 3397.721640] wlan0: associate with AP 00:1f:33:bc:30:68 (try 1)
[ 3397.724311] wlan0: RX AssocResp from 00:1f:33:bc:30:68 (capab=0x411 status=0 aid=1)
[ 3397.724319] wlan0: associated
[ 3397.726688] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3408.150016] wlan0: no IPv6 routers present
[ 3424.180064] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[ 3424.390062] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 2)
[ 3424.580071] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 3)
[ 3424.780035] wlan0: direct probe to AP 00:1f:33:bc:30:68 timed out
[ 3502.771602] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3502.807287] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[ 3503.000977] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 2)
[ 3503.003844] wlan0: direct probe responded
[ 3503.003850] wlan0: authenticate with AP 00:1f:33:bc:30:68 (try 1)
[ 3503.005673] wlan0: authenticated
[ 3503.005703] wlan0: associate with AP 00:1f:33:bc:30:68 (try 1)
[ 3503.007988] wlan0: RX AssocResp from 00:1f:33:bc:30:68 (capab=0x411 status=12 aid=0)
[ 3503.007993] wlan0: AP denied association (code=12)
[ 3503.008011] wlan0: deauthenticating from 00:1f:33:bc:30:68 by local choice (reason=3)
[ 3510.485718] wlan0: deauthenticating from 00:1f:33:bc:30:68 by local choice (reason=3)
[ 3510.486196] wlan0: direct probe to AP 00:1f:33:bc:30:68 (try 1)
[ 3510.489586] wlan0: direct probe responded
[ 3510.489591] wlan0: authenticate with AP 00:1f:33:bc:30:68 (try 1)
[ 3510.491670] wlan0: authenticated
[ 3510.491696] wlan0: associate with AP 00:1f:33:bc:30:68 (try 1)
[ 3510.494350] wlan0: RX AssocResp from 00:1f:33:bc:30:68 (capab=0x411 status=0 aid=1)
[ 3510.494355] wlan0: associated
[ 3510.496386] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3520.590037] wlan0: no IPv6 routers present
```[B]

6. Network configuration

[/B]```
yann@yyann:~$ sudo lshw -C network
[sudo] password for yann: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:21:3e:9b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0100000-f0103fff ioport:3000(size=256) memory:d8000000-d801ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:53:b0:15
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:d8600000-d8600fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```**7. Network scan**
```
yann@yyann:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:BC:30:68
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"F*ck you, Google!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002cbb527a183
                    Extra: Last beacon: 2150ms ago
                    IE: Unknown: 0011462A636B20796F752C20476F6F676C6521
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```**8. Ubuntu-Version / Kernel / Network restart**

```
yann@yyann:~$ lsb_release -d
Description:    Ubuntu 10.04 LTS
yann@yyann:~$ uname -mr
2.6.32-23-generic x86_64
yann@yyann:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```
Big thank you everyone!

Best wishes,
Yann.

---

### Post by yyann on 2010-07-23
Dear - is this just me or does no-one have a clue? 

What I failed to say is: I did not experience this problem back in Karmic Koala 9.10 or in Jaunty Jackalope 9.04.

Regards,
Yann.

---

### Post by mini-snapper on 2010-08-04
I have the same thing (and it was OK on previous UNR versions). I have an acer aspire one running 10.04 UNE and an oldish Netgear router. I found the problem is related to WPA security. My router doesn't do WPA2 and unbuntu says the connection is mixed WPA/WPA2. I find copying files from another machine on my local network is the best way to reproduce it.
Anyway, long story short, borrows a later model router from a friend that supports WPA2, and it's fine.
Don't know what the fix is without a router upgrade though, but that's where the problem lies I'm sure.

---

### Post by SaintDanBert on 2010-08-07
You are using the Intel 3965 wireless card.  That means that you are using the **iwlagn** driver. Are you seeing any signs that your driver crashes?

I have the intel 4965 wireless card and use **iwlagn**.
My driver crashes and thus my wirelss connection stops.

I've posted my syslog entries that I think are the crash logs, but so far I've not had any helpers step forward.

~~~ 0;-Dan

---

### Post by mini-snapper on 2010-08-09
The old aspire one zg5 uses the ath5k driver, i don't see any sign of dirver crash. dmesg reports the deauthenticated by user chioice (reason 3) messgae as shown by yyan's first post. interestingly the wireless network actually gets taken out, so other machines temporarily drop their connections too! router doesn't report any issues though which is odd. I know it's a cop out, but i've ordered a new router (been looking for an excuse for a while!), but would be interested to know why 9.04 & 9.10 worked fine and 10.04 doesn't.

---

### Post by msandoz on 2010-08-10
I'm having similar problems with the built-in network card on the new lenovo w510. i see signal and networks; i can sometimes connect. Most of the time though, I cannot connect. i have the latest kubuntu 64 installed.

even when connecting, after a while it drops and cannot get the connection back.

the network uses WPA enterprise/PEAP/mschapv2...

---

### Post by wmcbecker on 2010-08-11
Same here exactly, Yyan, no problem with Jaunty or Karmic.  Now, with Lucid, wireless drops when I try to view any streaming video, some streaming audio or try to download a larger file.  It will not connect again until I reboot.  

I too, looked around for some type of max bandwidth setting but have found none. 

I'm using a Thinkpad T60, cisco router.

Would really appreciate help with this if anyone knows anything.

---

### Post by wmcbecker on 2010-08-11
...just one more thing.  Regarding the suggestion that an upgrade to a newer router may hold the answer.  In my case, I have the brand new wireless N LinkSys router using WPA & WPA2 security and yet have the same exact problem described by Yyan.

---

### Post by SaintDanBert on 2010-08-11
> **msandoz said:**
> 
I'm having similar problems with the built-in network card on the new lenovo w510.
...


I think that Lenovo uses Intel wifi hardware.  Take a look in **/var/log/syslog** or **/var/log/messages** for something like this:
```

kernel: [ 6516.552204] iwlagn 0000:03:00.0: queue number out of range: 0, must be 7 to 14

kernel: [ 6516.552210] ------------[ cut here ]------------

kernel: [ 6516.552249] WARNING: at /build/buildd/linux-2.6.32/net/m
ac80211/agg-tx.c:150 ___ieee80211_stop_tx_ba_session+0x89/0x90 [mac80211]()

kernel: [ 6516.552256] Hardware name: 7764CTO

kernel: [ 6516.552260] Modules linked in: aes_i586 aes_generic nls_
iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm sco bridge stp bnep l2cap snd_hda_codec_analog fbcon tileblit font bitblit softcursor vga16fb vgastate mmc_block snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm pcmcia arc4 thinkpad_acpi 
snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlagn iwlcore snd_timer snd_seq_device mac80211 yenta_socket rsrc_nonstatic i915 ppdev tpm_tis sdhci_pci tpm snd
 drm_kms_helper nvram parport_pc psmouse sdhci tpm_bios led_class pcmcia_core cfg80211 btusb bluetooth soundcore drm i2c_algo_bit video output serio_raw intel_agp snd_page_alloc agpgart lp parport ohci1394 ahci ieee1394 e1000e

kernel: [ 6516.552417] Pid: 10, comm: events/1 Not tainted 2.6.32-2
4-generic-pae #39-Ubuntu

kernel: [ 6516.552423] Call Trace:
kernel: [ 6516.552441]  [<c0154192>] warn_slowpath_common+0x72/0xa0
kernel: [ 6516.552464]  [<f89c6f39>] ? __ieee80211_stop_tx_ba_session+0x89/0x90 [mac80211]
...

```

~~~ 0;-Dan

---

### Post by mini-snapper on 2010-08-17
> **wmcbecker said:**
> ...just one more thing.  Regarding the suggestion that an upgrade to a newer router may hold the answer.  In my case, I have the brand new wireless N LinkSys router using WPA & WPA2 security and yet have the same exact problem described by Yyan.

Do you know whether you use AES or TKIP encryption? I was coming round to the idea that it's a combination of driver (in may case ath5k), and TKIP. If I use a USB wireless dongle in the same machine, all is fine!

---

### Post by MSwal2846 on 2010-08-20
I have this same issues and am lobbying people to go to this bug report and add their information:

[https://bugs.launchpad.net/ubuntu/+bug/583210/](https://bugs.launchpad.net/ubuntu/+bug/583210/)

I do not believe this to be a router issue.

---

### Post by joao.taborda on 2011-01-30
i've got the same problem in an acer aspire one...

is there any fix?.. i've been looking for this everywhere and it looks many people have the problem, but no solution found yet :-/

---

### Post by MSwal2846 on 2011-01-30
Hi,

I followed the directions documented in this post:  

[http://ubuntuforums.org/showthread.php?t=1203594&highlight=mswal2846&page=6](http://ubuntuforums.org/showthread.php?t=1203594&highlight=mswal2846&page=6) 

and they worked perfectly for me.  The only draw back is that whenever there is a major kernel update, I need to redo the steps, but the wireless connection is perfect afterward.

Good luck....

---

