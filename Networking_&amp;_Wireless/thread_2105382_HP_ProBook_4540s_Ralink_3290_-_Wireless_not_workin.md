---
title: "HP ProBook 4540s Ralink 3290 - Wireless not working after updates"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by mosu90 on 2013-01-15
Hy guys, i have  a problem with this wireless card drivers.

I use Ubuntu 12.04 LTS.

Wireless worked pretty well (except known disconnects caused by rt2800pci driver) until ubuntu updated last week.

After that, wireless dissapeared from Network Manager. I ran lsmod and i saw rt2800pci was not loaded anymore. 

Then i installed rt3290sta which almost works, but the problem is it causes complete freeze when i open NetBeans (don't know why NetBeans cause this freeze, but i am sure the 3290sta causes it, i experienced exactly same behaviour on previus ubuntu installation after i installed custom wireless drivers).

Because of this freezes i told me that i should return to rt2800pci driver. 

I removed rt3290sta using depmod -v, i blacklisted it, removed rt2800pci from blacklist, i added them with depmod rt2800pci, added them to /etc/modules so they are loaded at startup, they appear when i use lsmod but there is no network interface.

What i found is that running "lspci -nnk | grep -iA2 net" find my network adapter but with no driver "attached"

I will post soon the results of lspci, lsmod, depmod -l etc.

lsmod:
```
rndis_host             13560  0 
cdc_ether              13312  1 rndis_host
usbnet                 25214  2 rndis_host,cdc_ether
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
wmi                    18744  1 hp_wmi
rt2x00lib              48875  3 rt2800pci,rt2800lib,rt2x00pci
i915                  419297  4 
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
mac_hid                13077  0 
radeon                737926  0 
jmb38x_ms              17406  0 
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178877  2 rt2x00lib,mac80211
uvcvideo               67203  0 
ttm                    65344  1 radeon
videodev               86588  1 uvcvideo
eeprom_93cx6           12687  1 rt2800pci
drm_kms_helper         45466  2 i915,radeon
drm                   197641  7 i915,radeon,ttm,drm_kms_helper
mei                    36570  0 
i2c_algo_bit           13199  2 i915,radeon
psmouse                86520  0 
serio_raw              13027  0 
memstick               15857  1 jmb38x_ms
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci

```

lspci
```

doru@doru-HP-ProBook-4540s:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7500M/7600M Series]
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
04:00.0 Network controller: Ralink corp. Device 3290
04:00.1 Bluetooth: Ralink corp. Device 3298
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```

nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        02:62:62:37:6C:05

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.206
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B4:B5:2F:77:E3:A0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

lspci -nnk | grep -iA2 net
```
04:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
	Subsystem: Hewlett-Packard Company Device [103c:18ec]
04:00.1 Bluetooth [0d11]: Ralink corp. Device [1814:3298]
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:17f6]
	Kernel driver in use: r8169

```

iwlist scan
```
lo        Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n35
```
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) successful.
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) complete.
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) started...
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> dhclient started with pid 3247
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Beginning IP6 addrconf.
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) complete.
Jan 16 16:47:32 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): DHCPv4 state changed nbi -> preinit
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): DHCPv4 state changed preinit -> bound
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info>   address 192.168.42.206
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info>   prefix 24 (255.255.255.0)
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info>   gateway 192.168.42.129
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info>   hostname 'doru-HP-ProBook-4540s'
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info>   nameserver '192.168.42.129'
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan 16 16:47:35 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) started...
Jan 16 16:47:36 doru-HP-ProBook-4540s NetworkManager[838]: <info> DNS: starting dnsmasq...
Jan 16 16:47:36 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): writing resolv.conf to /sbin/resolvconf
Jan 16 16:47:36 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 16 16:47:36 doru-HP-ProBook-4540s NetworkManager[838]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Jan 16 16:47:36 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) successful, device activated.
Jan 16 16:47:36 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) complete.
Jan 16 16:47:53 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): IP6 addrconf timed out or failed.
Jan 16 16:47:53 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 16 16:47:53 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 16 16:47:53 doru-HP-ProBook-4540s NetworkManager[838]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 16 17:12:21 doru-HP-ProBook-4540s NetworkManager[838]: <info> (usb0): DHCPv4 state changed bound -> renew
Jan 16 17:12:21 doru-HP-ProBook-4540s NetworkManager[838]: <info>   address 192.168.42.206
Jan 16 17:12:21 doru-HP-ProBook-4540s NetworkManager[838]: <info>   prefix 24 (255.255.255.0)
Jan 16 17:12:21 doru-HP-ProBook-4540s NetworkManager[838]: <info>   gateway 192.168.42.129
Jan 16 17:12:21 doru-HP-ProBook-4540s NetworkManager[838]: <info>   hostname 'doru-HP-ProBook-4540s'
Jan 16 17:12:21 doru-HP-ProBook-4540s NetworkManager[838]: <info>   nameserver '192.168.42.129'

```

---

### Post by novikov on 2013-01-27
I just bought this notebook -- and the "ralink" driver doesn't work at all for me...:(

//  I'm not very strong in Linux so I tried something that was easy for me  -- tried ubuntu13.04, ubuntu 12.04, debian wheezy and squeeze. All of  them didn't recognized the hardware.

---

### Post by novikov on 2013-01-28
mosu90, did it work out of the box before the update?

---

### Post by novikov on 2013-02-10
OK, I found a working solution.

To get the wifi (hp 4540s + ralink 3290) working under ubuntu 13.04 (in-development), copy the firmware from the git repository to /lib/firmware/.  Here's the exact instruction:

[http://askubuntu.com/questions/240553/how-do-i-install-ra3290-bin-wireless-driver-into-lib-firmware](http://askubuntu.com/questions/240553/how-do-i-install-ra3290-bin-wireless-driver-into-lib-firmware)

---

### Post by Mike Donovan on 2013-03-24
Replace the Wireless/Bluetooth module (easy fix)

HP ProBook 4540s icore5 running Windows7 x64, Debian AMD64 and Backtrack 5r3 AMD64.

I was able to load the firmware and compile the module from RaLink and got it all running. 
Then found out the module did not support Monitor Mode. 
I took the wireless network Mini PCI card out of my old Laptop and installed it into the HP 4540s. 
Everything is working perfectly on all 3 operating systems. The HP 4540s antenna works fine with the Atheros adapter.
When you install the parts just be careful with ESD, make sure your hands & tools are grounded.
The whole thing took 20minutes. 
You could also get one from newegg for about $25 if you dont have a spare. 

Disable Bluetooth since it wont be there anymore.

Mike

---

