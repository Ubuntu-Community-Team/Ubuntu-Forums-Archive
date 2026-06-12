---
title: "No wireless on Dell Inspiron 1545 in Ubuntu 11.04"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by l88 on 2011-05-01
I am unable to connect to my wireless internet on my Dell Inspiron 1545 since I updated from ubuntu 10.04 to 11.04.

The wireless driver for my computer is BCM4312. 
No wireless networks are showing up and I have attempted the following:
- Turning on the wireless hardware switch (Fn+F2)
- Removing bcmwl-kernel-source which comes back as E: Unable to locate package bcmwl-sta-common
- Installing b43-fwcutter in the terminal which says
E: Unable to locate package bcmwl
E: Unable to locate package bcmwl-sta-kernel-source
- When I search for it in synaptic package manager it shows that it is already downloaded
- I have searched for additional drivers which comes back empty and says "no proprietary drivers are in use on this system" 

Any help would be greatly appreciated!

---

### Post by northd_tech on 2011-05-02
Well, assuming that you have a Broadcom 4312 wireless, could you post the results of the following terminal commands:

```
lsmod

cat /etc/modprobe.d/blacklist.conf
```NOTE:  that 2nd command might not be the correct thing under Ubuntu 11.04 (I'm still quite attached to Lucid Lynx 10.04.2 **LTS**, so the 'new' syntax/file structure might be different than what I'm currently using).

---

### Post by l88 on 2011-05-02
desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
joydev                 17322  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
dell_wmi               12601  0 
snd_timer              28659  2 snd_pcm,snd_seq
sparse_keymap          13666  1 dell_wmi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  1 dell_laptop
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
psmouse                73312  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  450944  3 
usb_storage            43946  0 
uas                    17676  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
ahci                   21591  2 
ssb                    45942  0 
sky2                   49172  0 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by northd_tech on 2011-05-02
> **l88 said:**
> desktop:~$ lsmod
Module                  Size  Used by
**ssb**                    45942  0 

cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

[COLOR=Red]# replaced by b43 and ssb.
blacklist bcm43xx[/COLOR]


Well, it looks like you've got the "ssb" module loaded, but I believe that it usually accompanies the "b43" module.  Let's try the following terminal command (and post the results or any error messages that you get):

```
sudo modprobe b43
```Make sure your ethernet cable is unplugged and wait a few minutes and see if you see any wireless connections.  You might need to right click on the Network Manager icon near the clock and "Enable Networking" and "Enable Wireless" with the checkmarks first.

If you still can't get wireless, you might try System > Hardware Drivers  and see if you can "Activate" either the "b43" or "STA" Broadcom driver.  If it gives you error message(s), could you post those here too?  From what I remember, the older versions of Ubuntu gave me a choice between the "b43" and the "STA" drivers (and both worked fine for my "4328" broadcom), and I seem to remember it being a mutually-exclusive "either or" thing under Hardware Drivers but that was a long time ago.

If still no wireless, can you post the output of the following terminal commands:

```
lsmod | grep b43
dmesg | grep b43
dmesg | grep wl
dmesg | grep ssb
ifconfig

```I suspect that you might be having the "b43 firmware" problem, but you definitely need more than just that "ssb" module loaded for wireless.

Your /etc/modprobe.d/blacklist.conf "blacklist" file looks mostly identical to mine (I have a working Broadcom "4328" using the Broadcom "STA" driver that has the same lines that I highlighted in [COLOR=Red]red[/COLOR] above), so I don't see anything preventing your wireless modules from loading there.

This recent pinned thread is nearing 20 pages now, but looking at the first post, "Sef" also has a Broadcom 4312 and posted 2 fixes (your 4312 should also work with the functionally-very-similar Broadcom 4311 setup as I recall):

**Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal)**
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by northd_tech on 2011-05-02
> **l88 said:**
> 
No wireless networks are showing up and I have attempted the following:
- Turning on the wireless hardware switch (Fn+F2)
- Removing bcmwl-kernel-source which comes back as E: Unable to locate package bcmwl-sta-common
- Installing b43-fwcutter in the terminal which says
E: Unable to locate package bcmwl
E: Unable to locate package bcmwl-sta-kernel-source
- When I search for it in synaptic package manager it shows that it is already downloaded
- I have searched for additional drivers which comes back empty and says "no proprietary drivers are in use on this system" 

Just as a thought- did you have a working cabled ethernet connection when you tried to make those changes with the Synaptic Package manager?  It looks like your Ubuntu couldn't see the repositories for some reason.

If Synaptic (SPM) tells you that a package is already installed, there should be a "Mark for reinstallation" option that you might want to force.  SPM is usually quite good about notifying you about conflicts and needed package dependencies (but perhaps this isn't the case under Ubuntu 11.xx).

EDIT:  If you have internet access from another computer (or from cabled ethernet), you could download the Broadcom Linux STA driver directly from Broadcom's website:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

There are very specific instructions in the README.txt file, and there are different drivers for 32-bit and 64-bit.  You might not want to try compiling your own wireless modules just yet though.  You still might want to grab the appropriate STA driver from there as a Plan D or E sometime down the road, though.

---

### Post by edwin.donaldson on 2011-05-02
Same situation as I88... followed steps up to #4... here's my details
Dell Inspiron 1501, Broadcom 4311, Ubuntu 11.04

 lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  2 b43,b44


dmesg | grep b43
[   19.975932] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[ 3931.031393] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 3931.162428] Registered led device: b43-phy0::tx
[ 3931.162505] Registered led device: b43-phy0::rx
[ 3931.162578] Registered led device: b43-phy0::radio


dmesg | grep wl
[   18.713098] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.620171] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.620180] wl 0000:05:00.0: setting latency timer to 64


dmesg | grep ssb
[   20.004282] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   20.004296] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   20.004304] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   20.004312] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   20.050118] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   20.084171] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   20.084182] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   20.084190] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   20.137494] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   20.161152] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:b0:91:b0
[ 2977.000235] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[ 2977.000247] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[ 3948.000137] b44 ssb1:0: eth0: Link is down


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b0:91:b0  
          inet6 addr: fe80::21d:9ff:feb0:91b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1683898 (1.6 MB)  TX bytes:288264 (288.2 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:306268 (306.2 KB)  TX bytes:306268 (306.2 KB)

Can you help?

---

### Post by northd_tech on 2011-05-02
> **edwin.donaldson said:**
> Same situation as I88... followed steps up to #4... here's my details
Dell Inspiron 1501, Broadcom 4311, Ubuntu 11.04

 lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  2 b43,b44

dmesg | grep b43
[   19.975932] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[ 3931.031393] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 3931.162428] Registered led device: b43-phy0::tx
[ 3931.162505] Registered led device: b43-phy0::rx
[ 3931.162578] Registered led device: b43-phy0::radio

dmesg | grep wl
[   18.713098] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.620171] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.620180] wl 0000:05:00.0: setting latency timer to 64

Can you help?
It looks like you've got both the "b43" stuff and the "STA" driver loaded, Edwin.  With a Broadcom 4311, I don't believe that you will gain anything by using the 802.11n-capable "STA" driver.  These modules are probably conflicting Edwin, so let's try getting rid of the "STA" module.

Can you post the results of the following terminal commands, Edwin?
```
lsmod | grep wl

sudo rmmod wl

ifconfig

iwconfig
```

You might need to disconnect your ethernet cable first and right click on the Network Manager to "Enable Networking" and "Enable Wireless" with the checkmarks then testing to see if your wireless works any better, and try the "ifconfig" and "iwconfig" commands again.

---

### Post by nm_geo on 2011-05-02
> **northd_tech said:**
> It looks like you've got both the "b43" stuff and the "STA" driver loaded, Edwin.  With a Broadcom 4311, I don't believe that you will gain anything by using the 802.11n-capable "STA" driver.  These modules are probably conflicting Edwin, so let's try getting rid of the "STA" module.

Can you post the results of the following terminal commands, Edwin?
```
lsmod | grep wl

sudo rmmod wl

ifconfig

iwconfig
```You might need to disconnect your ethernet cable first and right click on the Network Manager to "Enable Networking" and "Enable Wireless" with the checkmarks then testing to see if your wireless works any better, and try the "ifconfig" and "iwconfig" commands again.

+1 I believe Edwin has both installed.
You might have other blacklists that are created by the STA install too. Copy and Run this in terminal and paste results

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```

---

### Post by l88 on 2011-05-07
NorthD_Tech here is the returns:

~$ sudo modprobe b43

dell-desktop:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43
dell-desktop:~$ dmesg | grep b43
[    1.302892] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.302910] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[ 4118.569371] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[ 4118.720339] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 4118.856417] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9595.192144] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[ 9595.344340] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 9595.500818] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[17471.294231] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[17471.444341] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[17471.571746] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[19876.848811] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[19876.971929] Registered led device: b43-phy0::tx
[19876.971963] Registered led device: b43-phy0::rx
[19876.971997] Registered led device: b43-phy0::radio
dell-desktop:~$ dmesg | grep wl
dell-desktop:~$ dmesg | grep ssb
[    1.327219] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.327238] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.327255] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.327272] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.380366] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:42:20:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:396285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:537092363 (537.0 MB)  TX bytes:26234501 (26.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28798 (28.7 KB)  TX bytes:28798 (28.7 KB)

---

### Post by fallofshadows on 2011-05-24
This happened once you upgraded to 11.04? I have my wireless working on 10.10, and I'm currently (as in right now haha) running 11.04 from a flash drive. Needless to say, I have no net connection, and the driver I used to get it running on 10.10 doesn't appear in synaptic.

If you get it working, please let us know. For now, I'm definitely not going to upgrade. Thanks for posting this unintentional warning :D

---

### Post by silentnomore on 2011-07-23
Hi, folks.  Thanks for all the advice you've given on here, it's helped loads thus far.  I'm a total newbie to Linux, so you may have to explain everything in completely basic terms for me.  I'm completely stuck with getting the wi-fi working at the mo, so wondered if any of you guys could help, please?  My setup:

- Dell Inspiron 1545 with Dell Wireless 1397 WLAN Mini-Card
- Dual-boot Windows 7 (well-used) and Ubuntu 11.04 (clean install, no additions)
- BT Homehub wireless router

I've followed instructions I've found, hooked up the network cable to the LAN port, then ran the Synaptic Package Manager, searched for "firmware-b43-lpphy-installer", marked & installed, activated the STA driver (whatever that is) then restarted, and the wi-fi network was automatically detected.  I've entered the security password for the network and saved it fine, disconnected the network cable and restarted, and I can see the network there to connect to it, but Ubuntu won't connect.  It tries to for about a minute or two, then just stops trying with no error message to speak of.

Does anyone have any suggestions what the problem might be?  And if so, could you possibly do me the honour of explaining a solution in step-by-step layman's terms for me, please?  Like I said, I've only just popped my Linx cherry :P , and know little to nothing about Linux at all, but I am attempting to learn as much as possible ASAP.

Thanks for your advice.

---

### Post by nm_geo on 2011-07-23
copy and paste this in terminal

```
lspci -nn | grep 0280
```show results here copy and paste

```
sudo lshw -C network
``````

lsmod
```

---

### Post by wildmanne39 on 2011-07-23
Hi run these commands in a terminal please
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
and post the results here.
Thank you

---

### Post by silentnomore on 2011-07-25
Wow, thanks for the qick responses!  Ok, here are the results as requested:

[QUOTE="lspci -nn | grep 0280"]0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/QUOTE]

[QUOTE="sudo lshw -C network"]  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:0b:43:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: f0:4d:a2:81:75:fe
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)[/QUOTE]

[QUOTE="lsmod"]Module                  Size  Used by
michael_mic            12540  0 
arc4                   12473  0 
nls_utf8               12493  1 
udf                    83795  1 
crc_itu_t              12627  1 udf
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  450944  3 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17203  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
wl                   2642531  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
dell_laptop            13515  0 
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  4 i915,drm_kms_helper
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
videodev               75143  1 uvcvideo
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  4 
libahci                25548  1 ahci
sky2                   49172  0 [/QUOTE]

[QUOTE="iwconfig"]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0[/QUOTE]

[QUOTE="rfkill list All"]Error message stating "All" was an invalid parameter, or something along those lines.[/QUOTE]

Does that help make it all clearer?

---

### Post by nm_geo on 2011-07-25
```
 
rfkill list all

```
 
Not a large A...try again just copy and paste the command in the terminal (no Typo)
 
You have the STA (wl) driver installed but as you know it is not working correctly.
 
_wireless info for lshw command_
configuration: broadcast=yes [COLOR=red]driver=wl0 [/COLOR]driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 
 
_lsmod info on driver_
wl 2642531 0
 
> I've followed instructions I've found, hooked up the network cable to the LAN port, then ran the Synaptic Package Manager, searched for [COLOR=red]"firmware-b43-lpphy-installer", marked & installed [/COLOR], activated the [COLOR=red]STA driver[/COLOR] (whatever that is) then restarted
 
installed [COLOR=#ff0000]"firmware-b43-lpphy-installer"  [/COLOR][COLOR=black]that's good you need that firmware...[/COLOR]
activated the [COLOR=red]STA driver[/COLOR]  That's not good with that firmware _De-activate that bugger_
 
Install_ b43-fwcutter_  that can be done in a few ways..Synaptic search _bcm _you will see it.  
 
or
 
```
 
sudo apt-get install b43-fwcutter 

```

---

### Post by wildmanne39 on 2011-07-25
Hi, open synaptic and make sure you have firmwareb43-lpphy-installer and b43fwcutter and if you have sta driver and bcmwl-kerrnel-source uninstall them, then restart your system with out the wired internet plugged in.

These are the only to you want to have installed firmwareb43-lpphy-installer and b43fwcutter.

---

### Post by nm_geo on 2011-07-25
you got him wildmanne I was lurking Sorry.. I need to get back to work anyway.. :P

---

### Post by wildmanne39 on 2011-07-25
Hi nm_geo, I am sorry also when I start to post no one has replied but by the time I get my information together you beat my to it. I did not know I was posting after you or I would not heave done it, you are just  quick draw and I am slow.

---

