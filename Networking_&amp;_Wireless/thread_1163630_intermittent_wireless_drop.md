---
title: "intermittent wireless drop"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by fjohnson on 2009-05-18
Hello,
 
I am new to Ubuntu, having just installed 9.0.4 (2.6.28-11-generic) on an HP G60-230US with an Atheros wireless adapter (AR928X). After I defined the wireless network, it connected to my wireless network, but the signal pickup was weak - about 50% at 30 feet, and only 85% at 5 feet - and the connection dropped after a period of activity. After the connection drops, it auto connects again after a minute or two ... cycle repeats until I get tired of it and revert to Vista. Under Vista the signal strength is almost 100% and I've never had any drops.
 
 My wireless lan is set to WPA2-PSK, no-broadcast of the ssid, and auto channel.

I've checked some of the forums posts about intermittent connection problems, but the config of my system doesn't ever seem to completely match up with what was in the problem and/or resolution. I was tempted to try the windows driver work-around (ndiswrapper?), but thought I'd ask for advice first. Anyone have any ideas?

Some data I collected is below (sorry if too much info, and someone please tell me if I've just published my hidden ssid and password for the whole world to see).

Thanks in advance.
[U][B]

/etc/network/interfaces[/B][/U]
auto lo
iface lo inet loopback


_**iwconfig output**_
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11abgn  Mode:Managed  Frequency:2.417 GHz  
          Access Point: 00:11:22:8E:06:91   Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
         Power Management:off
          Link Quality=42/100  Signal level:-89 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.


_**lshw -C network output**_
         *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:24:2b:ad:84:84
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.6 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn


_**iwlist scan output**_
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:11:22:8E:06:91
                    ESSID:""
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=46/100  Signal level:-86 dBm  Noise level=-116 dBm
                    Encryption key:on
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD2C0050F204104A0001101044000101105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000103
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000caaed5b180
                    Extra: Last beacon: 20ms ago
pan0      Interface doesn't support scanning.


_**lsmod output**_
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
aes_i586               15744  3 
aes_generic            35880  1 aes_i586
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
ath9k                 263224  0 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
mac80211              217208  1 ath9k
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               38032  1 mac80211
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
iTCO_wdt               19108  0 
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_vendor_support    11652  1 iTCO_wdt
led_class              12036  1 ath9k
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
video                  25360  0 
output                 11008  1 video
r8169                  40836  0 
mii                    13312  1 r8169
usb_storage            82880  1 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


_**lspci output**_
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by fjohnson on 2009-05-21
Older posts with this type of problem have suggested trying Ndiswrapper, but that doesn't list 9.0.4 as a supported rev.

Also, the old post suggest trying supplicant, but that seems to be built-in (in some fashion) to 9.0.4.

Anyone have any ideas of things to try?

---

### Post by wristbandsnow on 2009-05-22
hi friends these are information mostly useful for me. Thanks for sharing us. If they are all doing after problem is not solved.. What are doing that situation. If you have any suggestion then share with us. I wait for a positive response. Thanks

---

### Post by t0mppa on 2009-05-22
Looks like it's a temporary setback for the ath9k, see [here]("http://ubuntuforums.org/showpost.php?p=7227423&postcount=182") for more info.

Anyway, you can go ahead and try NDISWrapper, it does work on 9.04. Just have to find those windows drivers though. And another option is to try the Madwifi (ath_pci) driver that you can download from [here]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz"), although I'm not 100% sure if it supports your chip.

---

### Post by adhika_rexuss on 2009-05-22
I had the same problem with my Ubuntu 8.10 previously.
Then I just found out that by setting my router to broadcast only G signal it fixed the intermitten drop issue.

Now everything looks OK with me.
So my suggestion is set your router signal to the ones that you will be using only.

---

