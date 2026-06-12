---
title: "Intel 3945 wireless not working"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by oscarivera9 on 2013-02-12
I've read everywhere and I can't seem to find a solution to this.  I've got a Fujitsu Lifebook N6420 with an Intel 3945 wireless card that will not connect.
If anyone has any ideas I'd love to hear them.

---

### Post by praseodym on 2013-02-12
Hi,

please show:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by oscarivera9 on 2013-02-12
> **praseodym said:**
> Hi,

please show:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

```
oscarivera9@mint-LifeBook-N6420 ~ $ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 21)
    Subsystem: Fujitsu Limited. Device [10cf:1300]
    Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1000]
    Kernel modules: iwl3945
08:03.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
``````
oscarivera9@mint-LifeBook-N6420 ~ $ lsmod
Module                  Size  Used by
arc4                   12529  2 
joydev                 17457  0 
coretemp               13400  0 
rtl8187                56912  0 
input_polldev          13896  0 
eeprom_93cx6           13302  1 rtl8187
pcmcia                 48964  0 
parport_pc             32688  0 
bnep                   18140  2 
ppdev                  17073  0 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
r852                   18281  0 
sm_common              16817  1 r852
nand                   54706  2 r852,sm_common
nand_ids               12723  1 nand
microcode              22803  0 
mtd                    44905  2 sm_common,nand
nand_bch               13147  1 nand
bch                    17399  1 nand_bch
lpc_ich                17061  0 
psmouse                95552  0 
nand_ecc               13230  1 nand
r592                   18019  0 
snd_hda_codec_realtek    77876  1 
memstick               16554  1 r592
yenta_socket           31817  0 
pcmcia_rsrc            18288  1 yenta_socket
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13215  0 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
iwl3945                65159  0 
iwlegacy              100331  1 iwl3945
mac80211              539908  3 rtl8187,iwl3945,iwlegacy
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19335  0 
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              206566  4 rtl8187,iwl3945,iwlegacy,mac80211
radeon                895653  3 
ttm                    83595  1 radeon
mac_hid                13205  0 
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon
fujitsu_laptop         18947  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
tg3                   148780  0
``````
oscarivera9@mint-LifeBook-N6420 ~ $ iwconfig
wlan1     IEEE 802.11bg  ESSID:"NETGEAR68"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 2C:B0:5D:38:7A:C1   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3635  Invalid misc:74   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.
``````
oscarivera9@mint-LifeBook-N6420 ~ $ rfkill list
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````
oscarivera9@mint-LifeBook-N6420 ~ $ sudo iwlist scan
[sudo] password for oscarivera9: 
wlan1     Scan completed :
          Cell 01 - Address: 2C:B0:5D:38:7A:C1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR68"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006d613a29183
                    Extra: Last beacon: 424ms ago
                    IE: Unknown: 00094E4554474541523638
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010219B5326A7FB4B06BC6F07D741C0EC991021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:13:10:36:14:3A
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"iHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f1aae6c64
                    Extra: Last beacon: 2492ms ago
                    IE: Unknown: 000569486F6D65
                    IE: Unknown: 010882848B96A4B0C8EC
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C9298E0
                    IE: Unknown: DD06001018020305
          Cell 03 - Address: 00:7F:28:D6:E1:15
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"CRFXP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fe56c9255
                    Extra: Last beacon: 988ms ago
                    IE: Unknown: 00054352465850
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B
          Cell 04 - Address: 84:1B:5E:7C:E1:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"o13oilstop"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000042b10ca85
                    Extra: Last beacon: 3356ms ago
                    IE: Unknown: 000A6F31336F696C73746F70
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```I'm using the same laptop right now that has the problem because I thought it would be easier to do it this way so I could copy everything from the terminal onto here.  This means that I'm using a wireless USB device to connect to the internet so you may see that show up in the results.  Also, I'm primarily a Ubuntu user and this laptop is the only PC that I have without Ubuntu; instead it has Linux Mint but I suppose that pretty much everything should be the same as if I were using Ubuntu since Mint is like Ubuntu's offspring.

---

### Post by praseodym on 2013-02-12
Does not look bad, though. Deactivate IPv6 ("Ignore") in the network-manager-applet. Please show additionally:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dmesg | grep iwl
```
Did you deactivate the MAC-address filter in your router? Try also a fixed channel, e.g. 6.

---

### Post by oscarivera9 on 2013-02-12
> **praseodym said:**
> Does not look bad, though. Deactivate IPv6 ("Ignore") in the network-manager-applet. Please show additionally:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dmesg | grep iwl
```Did you deactivate the MAC-address filter in your router? Try also a fixed channel, e.g. 6.

So, here's the info you requested:


```
oscarivera9@mint-LifeBook-N6420 ~ $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
oscarivera9@mint-LifeBook-N6420 ~ $ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 208.67.222.222
nameserver 208.67.220.220
oscarivera9@mint-LifeBook-N6420 ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
oscarivera9@mint-LifeBook-N6420 ~ $ dmesg | grep iwl
[   19.238446] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   19.238451] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   19.305712] iwl3945 0000:05:00.0: >Error: saturation power is -1, less than minimum expected 40
[   19.305729] iwl3945 0000:05:00.0: >Tunable channels: 7 802.11bg, 10 802.11a channels
[   19.305733] iwl3945 0000:05:00.0: >Detected Intel Wireless WiFi Link 3945ABG
[   19.305888] iwl3945 0000:05:00.0: >irq 46 for MSI/MSI-X
[   19.401754] ieee80211 phy0: >Selected rate control algorithm 'iwl-3945-rs'
[   20.085060] iwl3945 0000:05:00.0: >loaded firmware version 15.32.2.9
[   20.088039] iwl3945 0000:05:00.0: >BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[   20.088046] iwl3945 0000:05:00.0: >Unable to set up bootstrap uCode: -5
[   20.089380] iwl3945 0000:05:00.0: >BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0x0, s/b 0xf802020
[   20.089383] iwl3945 0000:05:00.0: >Unable to set up bootstrap uCode: -5
[   20.090758] iwl3945 0000:05:00.0: >BSM uCode verification failed at addr 0x00003800+4 (of 900), is 0x2069, s/b 0x400000
[   20.090761] iwl3945 0000:05:00.0: >Unable to set up bootstrap uCode: -5
[   20.092131] iwl3945 0000:05:00.0: >BSM uCode verification failed at addr 0x00003800+4 (of 900), is 0xffffffff, s/b 0x400000
[   20.092136] iwl3945 0000:05:00.0: >Unable to set up bootstrap uCode: -5
[   20.093470] iwl3945 0000:05:00.0: >BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0x0, s/b 0xf802020
[   20.093473] iwl3945 0000:05:00.0: >Unable to set up bootstrap uCode: -5
[   20.093823] iwl3945 0000:05:00.0: >Unable to initialize device after 5 attempts.
```Now, you suggest that I change some settings on my router but I have a question regarding that.   Given that if I use a wireless USB dongle on the same laptop with the problem or if I use Windows 8 installed on a different partition on the same laptop, I can connect to the internet just fine, why would I want to change any settings on the router?

---

### Post by praseodym on 2013-02-13
Try to add the boot parameter

```
clocksource=acpi_pm
```
into the /etc/default/grub, e.g.
```

[COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR]="quiet splash [COLOR="Red"]clocksource=acpi_pm[/COLOR] video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap"
```
Save, close the editor and update grub:
```

sudo update-grub
```
Reboot.

---

### Post by oscarivera9 on 2013-02-15
> **praseodym said:**
> Try to add the boot parameter

```
clocksource=acpi_pm
```into the /etc/default/grub, e.g.
```

[COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR]="quiet splash [COLOR=Red]clocksource=acpi_pm[/COLOR] video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap"
```Save, close the editor and update grub:
```

sudo update-grub
```Reboot.

First of all, thanks praseodym for your help and sorry I took so long to try your suggestion, I was extremely busy with work.  Second, I tried what you said: edit /etc/default/grub, save, update grub, reboot, and everything is still the same.  The wireless card is not working.

---

### Post by steeldriver on 2013-02-15
Based on your dmesg output, it seems like it might be a firmware issue? what is your kernel version? firmware version?

```
uname -a

apt-cache policy linux-firmware
```

---

### Post by oscarivera9 on 2013-02-16
> **steeldriver said:**
> Based on your dmesg output, it seems like it might be a firmware issue? what is your kernel version? firmware version?

```
uname -a

apt-cache policy linux-firmware
```

OK, here's what you requested:

```
oscarivera9@mint-LifeBook-N6420 ~ $ uname -a
  Linux mint-LifeBook-N6420 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``````
oscarivera9@mint-LifeBook-N6420 ~ $ apt-cache policy linux-firmware
  linux-firmware:
    Installed: 1.95
    Candidate: 1.95
    Version table:
   *** 1.95 0
          500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
          100 /var/lib/dpkg/status

```

---

### Post by oscarivera9 on 2013-02-17
I can't find an answer and I thought asking here in the ubuntu forums would help, but I'm still stuck on step 1.  I am actually considering getting a usb wireless dongle that I know would be compatible.
If possible I'd rather not have to spend money getting something that I technically already have (I just can't get it to work under Linux yet it works fine with Windows).

---

### Post by ahallubuntu on 2013-02-17
~

---

### Post by mörgæs on 2013-02-19
Does this help?

[http://ubuntuforums.org/showpost.php?p=12428981&postcount=1295]("http://ubuntuforums.org/showthread.php?t=1543006&page=130")

(post 1295)

---

### Post by oscarivera9 on 2013-03-19
Thanks to everyone who tried to help me with my wireless problem.  I finally gave up and bought an external USB wi-fi dongle.  It turns out that I think there is something physically wrong with the built in wi-fi Intel 3945 that my laptop comes with.  This is a laptop that was handed down to me in an effort to see if I could fix it as it was at one point completely broken (problems with the power).  I eventually fixed it and it now runs great except for the wi-fi.  I came to the conclusion that the actual Intel 3945 Wi-Fi card is broken because eventually when I would boot into Windows I began to loose my connection whereas originally it used to run ok but with Linux Mint it never even worked.  Because it began to drop the connection even in Windows I came to the conclusion that the Wi-Fi card must be broken so I decided to just buy an external one and now everything is fine.
My problem has been solved by me replacing the faulty part so I assume that I should mark this thread as "solved".  If anyone thinks otherwise let me know, otherwise I will mark it as "solved" within two days.

Thanks again

---

