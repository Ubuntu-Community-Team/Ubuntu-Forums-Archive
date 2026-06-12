---
title: "Slow wireless with USB Adapter RTL8187 - Please help"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Gizim on 2010-08-29
Ditching Windows for the last time but this seems to be a issue wireless seems fine for a bit but then the connection slows to around 20kbps or worse. Any ideas what it could be? Using 10.04.1 it says it has a 48mb connection and i have 4 bars.

Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

adam@mario:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:05:6E:BA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"wrb3109"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c9da2e67
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000777726233313039
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101B0000000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 070C55532001021B0307140A021B
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B000103104700100000000000000001100000259C056EBA102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30311042000A4A3933343030343538361054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084

---

### Post by Gizim on 2010-08-29
Also the wireless works fine under Windows and all the computers in the house are on wireless nobody else is having issues.

---

### Post by MaindotC on 2010-08-29
Look for a report in your syslog right around the time you notice a chance in speed.

---

### Post by Gizim on 2010-08-29
> **strAlan said:**
> Look for a report in your syslog right around the time you notice a chance in speed.

Only thing i see under the daemon is 

Aug 29 21:15:16 mario wpa_supplicant[1315]: WPA: Group rekeying completed with 00:25:9c:05:6e:ba [GTK=TKIP]
Aug 29 21:15:16 mario NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Aug 29 21:15:16 mario NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed

This is a complete reconnect

Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) starting connection 'Auto wrb3109'
Aug 29 21:18:03 mario NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 29 21:18:03 mario NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto wrb3109' has security, and secrets exist.  No new secrets needed.
Aug 29 21:18:03 mario NetworkManager: <info>  Config: added 'ssid' value 'wrb3109'
Aug 29 21:18:03 mario NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 29 21:18:03 mario NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 29 21:18:03 mario NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 29 21:18:03 mario NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 29 21:18:03 mario NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 29 21:18:03 mario NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 29 21:18:03 mario NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 29 21:18:03 mario NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 29 21:18:03 mario NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 29 21:18:03 mario wpa_supplicant[1315]: Failed to initiate AP scan.
Aug 29 21:18:04 mario wpa_supplicant[1315]: WPS-AP-AVAILABLE 
Aug 29 21:18:04 mario wpa_supplicant[1315]: Trying to associate with 00:25:9c:05:6e:ba (SSID='wrb3109' freq=2437 MHz)
Aug 29 21:18:04 mario NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 29 21:18:04 mario wpa_supplicant[1315]: WPS-AP-AVAILABLE 
Aug 29 21:18:04 mario wpa_supplicant[1315]: Associated with 00:25:9c:05:6e:ba
Aug 29 21:18:04 mario NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 29 21:18:04 mario NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 29 21:18:05 mario wpa_supplicant[1315]: WPA: Key negotiation completed with 00:25:9c:05:6e:ba [PTK=CCMP GTK=TKIP]
Aug 29 21:18:05 mario wpa_supplicant[1315]: CTRL-EVENT-CONNECTED - Connection to 00:25:9c:05:6e:ba completed (reauth) [id=0 id_str=]
Aug 29 21:18:05 mario NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 29 21:18:05 mario NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wrb3109'.
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 29 21:18:05 mario NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 29 21:18:05 mario NetworkManager: <info>  dhclient started with pid 11852
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 29 21:18:05 mario NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 29 21:18:05 mario dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 29 21:18:05 mario dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 29 21:18:05 mario dhclient: All rights reserved.
Aug 29 21:18:05 mario dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 29 21:18:05 mario dhclient: 
Aug 29 21:18:05 mario NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 29 21:18:05 mario dhclient: Listening on LPF/wlan0/00:1a:ef:0b:ae:16
Aug 29 21:18:05 mario dhclient: Sending on   LPF/wlan0/00:1a:ef:0b:ae:16
Aug 29 21:18:05 mario dhclient: Sending on   Socket/fallback
Aug 29 21:18:07 mario dhclient: DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
Aug 29 21:18:08 mario dhclient: DHCPACK of 192.168.1.106 from 192.168.1.1
Aug 29 21:18:08 mario NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Aug 29 21:18:08 mario NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 29 21:18:08 mario NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 29 21:18:08 mario NetworkManager: <info>    address 192.168.1.106
Aug 29 21:18:08 mario NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 29 21:18:08 mario NetworkManager: <info>    gateway 192.168.1.1
Aug 29 21:18:08 mario NetworkManager: <info>    nameserver '68.87.68.166'
Aug 29 21:18:08 mario NetworkManager: <info>    nameserver '68.87.74.166'
Aug 29 21:18:08 mario NetworkManager: <info>    domain name 'hsd1.tn.comcast.net.'
Aug 29 21:18:08 mario NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 29 21:18:08 mario NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 29 21:18:08 mario dhclient: bound to 192.168.1.106 -- renewal in 37955 seconds.
Aug 29 21:18:08 mario NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 29 21:18:09 mario NetworkManager: <info>  Clearing nscd hosts cache.
Aug 29 21:18:09 mario NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Aug 29 21:18:09 mario NetworkManager: <info>  Clearing nscd hosts cache.
Aug 29 21:18:09 mario NetworkManager: <info>  Policy set 'Auto wrb3109' (wlan0) as default for routing and DNS.
Aug 29 21:18:09 mario NetworkManager: <info>  Activation (wlan0) successful, device activated.
Aug 29 21:18:09 mario NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 29 21:18:12 mario ntpdate[11916]: adjust time server 91.189.94.4 offset -0.014567 sec
Aug 29 21:18:16 mario wpa_supplicant[1315]: WPA: Group rekeying completed with 00:25:9c:05:6e:ba [GTK=TKIP]
Aug 29 21:18:16 mario NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Aug 29 21:18:16 mario NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed

---

### Post by Gizim on 2010-08-30
BUMP for justice

---

### Post by Gizim on 2010-08-30
Really nobody?

---

### Post by MaindotC on 2010-08-31
Those logs are a little difficult to extract something definite.  I was hoping to see something like [ERROR] or something that would jump out.  You may have difficulty finding answers here because it seems like an issue with the driver.  I'm not saying it definitely is the driver, and please don't tell the developers that, but something happened (and I'm assuming you don't know what or when or what triggered all this) and either the hardware device suffered damage, or there was a configuration changed in the driver.  How that configuration may have happened is something I don't know.

Perhaps I can't help you further but I can guide you to where you may get better support.  You could try contacting the devlopers of your wireless driver.  Usually they have a website and mailing list, or even an irc channel where you can ask questions real-time (assuming they're not idle in the channel).  If you haven't already, you can also try following the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  I believe if you follow the steps you will eventually arrive at the point where the driver needs to be recompiled or reconfigured, which is precisely why I advise you contact the developers, so it may not be of any higher degree of help but it's something.

If I can think of anything else I'll let you know.  If you do find a resolution, please post it here.

---

### Post by Gizim on 2010-08-31
> **strAlan said:**
> Those logs are a little difficult to extract something definite.  I was hoping to see something like [ERROR] or something that would jump out.  You may have difficulty finding answers here because it seems like an issue with the driver.  I'm not saying it definitely is the driver, and please don't tell the developers that, but something happened (and I'm assuming you don't know what or when or what triggered all this) and either the hardware device suffered damage, or there was a configuration changed in the driver.  How that configuration may have happened is something I don't know.

Perhaps I can't help you further but I can guide you to where you may get better support.  You could try contacting the devlopers of your wireless driver.  Usually they have a website and mailing list, or even an irc channel where you can ask questions real-time (assuming they're not idle in the channel).  If you haven't already, you can also try following the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  I believe if you follow the steps you will eventually arrive at the point where the driver needs to be recompiled or reconfigured, which is precisely why I advise you contact the developers, so it may not be of any higher degree of help but it's something.

If I can think of anything else I'll let you know.  If you do find a resolution, please post it here.

From my searches it seems a lot of people are having this same issue with the RTL8187 wireless but I have yet to find a solution.. if I can't find one looks like it's have to Windows for me.

---

### Post by MaindotC on 2010-08-31
I think paying $25 for a wireless adapter would be a much better solution than running an operating system that will encounter more problems that you can't handle.  I know that doesn't really SOLVE the problem - it's like using a CAT5 cable to connect a machine that is having a wireless problem, but is getting a different wireless adapter an issue?  Perhaps you have another machine with an extra adapter, or I have a couple extras that are fully supported that I could send you.  There's a [list of Ubuntu Hardware Compatability List](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).  It's the same way with Windows (they also have a supported hardware list) so I'd rather advise you to stick with a more secure, stable o/s.

---

### Post by Gizim on 2010-08-31
> **strAlan said:**
> I think paying $25 for a wireless adapter would be a much better solution than running an operating system that will encounter more problems that you can't handle.  I know that doesn't really SOLVE the problem - it's like using a CAT5 cable to connect a machine that is having a wireless problem, but is getting a different wireless adapter an issue?  Perhaps you have another machine with an extra adapter, or I have a couple extras that are fully supported that I could send you.  There's a [list of Ubuntu Hardware Compatability List](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).  It's the same way with Windows (they also have a supported hardware list) so I'd rather advise you to stick with a more secure, stable o/s.

I bought this
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022)
Already paid the $25

---

### Post by MaindotC on 2010-08-31
Like just now or that's what you've been trying to use all this time?

---

### Post by Gizim on 2010-08-31
> **strAlan said:**
> Like just now or that's what you've been trying to use all this time?

The whole time, it's a desktop in a area that I have no option but to use wireless.

---

### Post by MaindotC on 2010-08-31
Ok, well if you're not sure what to do, aside from what I've already suggested, it seems these are your options:

Contact Rosewill for support.  I doubt they will help you, or that you will even get through to a representative who can help you, but it is their product and although they say not every Linux distrubtion can possibly be supported they may have help or troubleshooting procedures for Ubuntu (or even Debian is fine).

Return it to Newegg and purchase a supported card from the compatability list.  I'm assuming you're outside the warranty period/return date or you'd do this already.

Contact the developers of the [rtl8187]("http://rtl-wifi.sourceforge.net/wiki/Main_Page") driver.  According to [this Backtrack post](http://backtrack.offensive-security.com/index.php/HCL:Wireless#Rosewill_RNX-G1.28W.29) that's the driver (and chipset) it should be using.

---

### Post by Gizim on 2010-08-31
> **strAlan said:**
> Ok, well if you're not sure what to do, aside from what I've already suggested, it seems these are your options:

Contact Rosewill for support.  I doubt they will help you, or that you will even get through to a representative who can help you, but it is their product and although they say not every Linux distrubtion can possibly be supported they may have help or troubleshooting procedures for Ubuntu (or even Debian is fine).

Return it to Newegg and purchase a supported card from the compatability list.  I'm assuming you're outside the warranty period/return date or you'd do this already.

Contact the developers of the [rtl8187]("http://rtl-wifi.sourceforge.net/wiki/Main_Page") driver.  According to [this Backtrack post](http://backtrack.offensive-security.com/index.php/HCL:Wireless#Rosewill_RNX-G1.28W.29) that's the driver (and chipset) it should be using.

Man that sucks, it seems that wireless and Ubuntu just do not mix at all in any form. Looking at the Wireless compatible list I can't find a USB adapter that works %100 for 10.04

---

### Post by MaindotC on 2010-08-31
Well, look at the dates of the wiki entries - 2007, 2008...a lot of kernel revisions and upgrades have been released since then.  Do something positive for the community and go to the rtl8187 forum or mailing list and get a resolution and post it here, or update the wiki.  I know it may take time, and you probably need to be connected yesterday not in a week, but you have the power to affect several users and better their experience by helping coordinate a resolution.  I tried to do that, but it doesn't seem that anything I say is of any benefit to your situation, and that's perfectly fine because I know at least I tried.  You have the card, so why don't you try contacting their forum or maybe first installing the driver from source - perhaps it will conform better to your machine if you compile the driver directly on it.

---

### Post by giich on 2012-01-02
Guys, sorry for digging the old topic, but it seems that problem is still here on Ubuntu 11.10. And i got solution! :popcorn:

So the problem is:

RTL 81817b working slow (120 kilobytes per second max) after few seconds after u turn it on. 

The funny thing that first 10 seconds it can download at good speed (1,5 megabytes per second). 

I didnt found why this happens, so i had to choose more radical way - disable build in driver and run my TrendNet 424-UB through ndiswrapper.

Here is what you got to do:

Step 1. Installing ndiswrapper. 
```
sudo apt-get install ndisgtk
```Step 2. Getting drivers. Its better if you pick driver from manufacturer site, in this case - realtek.com. I picked the driver for windows xp. That's 3 files and the main is net8187b.inf

The driver which i used can also be downloaded here - [http://depositfiles.com/files/kuxj9yxcl](http://depositfiles.com/files/kuxj9yxcl) 

If the link is broken, just reply here, i'm subscribed to this thread.


 ```
sudo ndiswrapper -i /path-where-you-unpacked-driver/net8187b.inf
```Step 3. Running ndsiwrapper
 ```
Sudo depmod -a
``` ```
sudo modprobe ndiswrapper
```And now we make autostart:
 ```
sudo ndiswrapper -m
``` ```
sudo gedit /etc/modules
```add string
ndiswrapper

and save the file.

Step 4. Disabling old drivers
RTL8187 driver is located at /lib/modules/3.0.014-generic (or whatever you version is)/kernel/driver/net/wireless/RTL818x/rtl8187/rtl8187.ko

I've just renamed file to rtl8187.old.ko. You need to be sudo to do this:

 ```
sudo nautilus
```and then find your driver and rename it. 

Step 5. 
 ```
sudo reboot
``` (or just use reboot button)

I got my net working fine now at 1,5 megabytes per second. If that will not work for you, you can rename driver back, remove ndiswrapper and reboot.

I picked this instruction from here:
[http://forum.ubuntu.ru/index.php?topic=57020.0](http://forum.ubuntu.ru/index.php?topic=57020.0)
But it's on russian language.

---

### Post by ridhisundar on 2012-01-18
I have same problem of Internet slowness.

 > lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Acer Incorporated [ALI] Aspire 5920G [1025:0121]
    Kernel modules: tg3> root@Ridhi-Aspire:~# lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  12 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
r8712u                189049  0 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
btusb                  18600  2 
r592                   18144  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
psmouse                73882  0 
memstick               16569  1 r592
bluetooth             166112  23 bnep,rfcomm,btusb
mtd                    33181  2 sm_common,nand
serio_raw              13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  566827  4 
snd_timer              29991  2 snd_pcm,snd_seq
wmi                    19256  1 acer_wmi
drm_kms_helper         42558  1 i915
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   236290  5 i915,drm_kms_helper
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
root@Ridhi-Aspire:~#> root@Ridhi-Aspire:~# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Ridhi-Aspire 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux



Please advise...

---

### Post by giich on 2012-01-19
Have you tried ndiswrapper?

But u need to find your own driver, cause your chipset is not RTL8187 AFAIK.

---

