---
title: "Speedtouch 121g No Wifi After 10.04 upgrade."
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by Robskii on 2010-04-29
Firstly I literally know nothing about how to fix Ubuntu, so any help is greatly appreciated. 

I upgraded from 9.10 to 10.04 via the upgrade manager and as soon as i loaded up into 10.04 the WiFi wouldn't connect and doesn't even give me a list of WiFi networks around my area. (Meaning the wireless card hasn't been loaded I guess?) 

I did notice during the upgrade it came up with an error about the network manager but it didn't stay up for very long.

---

### Post by Robskii on 2010-04-30
Just a little info...

> Computer HP Pavillion ac6305.uk

> robskii@Robskii:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)


> robskii@Robskii:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
>>> Bus 001 Device 004: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle <<<(My wireless dongle)
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 002: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> robskii@Robskii:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:90:06:00:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


> robskii@Robskii:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

robskii@Robskii:~$ lsmod
Module                  Size  Used by
nfnetlink_queue         6820  1 
nfnetlink               3266  2 nfnetlink_queue
binfmt_misc             6587  1 
nf_conntrack_ipv4      10672  3 
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ipt_REJECT              1928  1 
xt_tcpudp               2011  2 
iptable_filter          2271  1 
ip_tables               9991  1 iptable_filter
xt_iprange              1357  0 
xt_state                1098  3 
nf_conntrack           61583  2 nf_conntrack_ipv4,xt_state
xt_mark                  711  6 
xt_NFQUEUE              1832  3 
x_tables               14299  7 ipt_REJECT,xt_tcpudp,ip_tables,xt_iprange,xt_state,xt_mark,xt_NFQUEUE
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
p54usb                 10876  0 
p54common              24921  1 p54usb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_rawmidi            19056  1 snd_seq_midi
led_class               2864  1 p54common
nvidia               9932176  28 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
font                    7557  1 fbcon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
agpgart                31724  1 nvidia
mac80211              204922  2 p54usb,p54common
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
soundcore               6620  1 snd
cfg80211              126485  2 p54common,mac80211
vgastate                8961  1 vga16fb
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
psmouse                63245  0 
serio_raw               3978  0 
k8temp                  3024  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
ohci1394               26950  0 
usb_storage            39425  0 
xor                    15028  1 dm_raid45
forcedeth              49556  0 
pata_amd                8766  0 
ieee1394               81181  1 ohci1394
sata_nv                19440  2 


>  robskii@Robskii:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


>  robskii@Robskii:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS

robskii@Robskii:~$ uname -mr
2.6.32-21-generic i686 

>  robskii@Robskii:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
 

---

### Post by Topher88 on 2010-04-30
I'm having this same problem.  I went to install the propriety driver for my Broadcom STA card, but this time it said that the installation failed.  This didn't happen when I upgraded from Jaunty to Karmic...  In fact I don't think I've ever had a problem installing the propriety drivers for my card.

If anyone can help out here, that would be greatly appreciated.  My model is HP dv6 1230us.

---

### Post by pdc on 2010-04-30
here is a diagnostic script that is used on the OpenSuse forum;

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

run it;

it analyses your wireless and advises solutions .........

and if that isn't enough, you can post back the results to this forum

---

### Post by Robskii on 2010-05-01
Okay I used the script and got this output file.

```

collectNWData.sh V0.6.3.5-1 (Rev: 1.223, Build: 2010/04/27 18:11:56 UTC)
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux Robskii 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
==================================================================================================================
*** cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Robskii
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xa000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1856 (1.8 KB)  TX bytes:1856 (1.8 KB)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
==================================================================================================================
*** lspci
==================================================================================================================
*** lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 002: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| agpgart         | binfmt_misc     | bitblit         | cfg80211        | dm_raid45        |
| fbcon           | font            | forcedeth       | i2c_nforce2     | ieee1394         |
| k8temp          | led_class       | lp              | mac80211        | nf_conntrack_ipv4 |
| nfnetlink       | nfnetlink_queue | ohci1394        | p54common       | p54usb           |
| pata_amd        | ppdev           | sata_nv         | serio_raw       | snd_hda_codec    |
| snd_hda_codec_realtek| snd_hda_intel   | snd_hwdep       | snd_rawmidi     | snd_seq_device   |
| snd_seq_dummy   | snd_seq_midi    | snd_seq_oss     | softcursor      | tileblit         |
| usb_storage     | vga16fb         | vgastate        | xor             | xt_iprange       |
| xt_mark         | xt_NFQUEUE      | xt_state        | xt_tcpudp       |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
==================================================================================================================
*** Actual date for bias of following greps
17:30:16 2010-05-01
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
/var/log/messages:Apr 30 00:13:00 Robskii kernel: [   17.021565] Registered led device: p54-phy0::radio
/var/log/messages:Apr 30 01:10:36 Robskii kernel: [ 3473.755609] Registered led device: p54-phy1::radio
/var/log/messages:Apr 30 03:09:44 Robskii kernel: [10622.361126] Registered led device: p54-phy2::radio
/var/log/messages.1:Apr 23 14:26:32 Robskii kernel: [   22.219880] Registered led device: p54-phy0::radio
/var/log/messages.1:Apr 25 16:17:19 Robskii kernel: [   22.064954] Registered led device: p54-phy0::radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May  1 17:23:32 Robskii kernel: [   17.046678] usb 1-3.4: firmware: requesting isl3887usb
May  1 17:23:32 Robskii kernel: [   17.686119] usb 1-3.4: firmware: requesting isl3887usb_bare
Apr 25 16:17:18 Robskii kernel: [   20.844737] usb 1-3.1: firmware: requesting isl3887usb
Apr 25 16:17:18 Robskii kernel: [   20.901227] phy0: p54 detected a LM87 firmware
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.31-17-generic       | 2.6.31-19-generic       | 2.6.31-20-generic       | 2.6.32-21-generic        |
| 3com                    | acenic                  | adaptec                 | advansys                 |
| agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw          | ar9170-1.fw              |
| ar9170-2.fw             | ar9170.fw               | ath3k-1.fw              | atmel_at76c502_3com.bin  |
| atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin     | atmel_at76c504_2958.bin  |
| atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin      | atmsar11.fw              |
| av7110                  | bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw      |
| bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                    |
| cxgb3                   | dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw |
| dvb-usb-dib0700-1.20.fw | e100                    | ea                      | edgeport                 |
| emi26                   | emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf   |
| i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw         |
| ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw       |
| iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                   |
| keyspan                 | keyspan_pda             | korg                    | libertas                 |
| matrox                  | mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw               |
| mwl8k                   | myricom                 | NPE-B                   | NPE-C                    |
| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |
| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| RTL8192SE               | sb16                    | scripts                 | slicoss                  |
| sun                     | sxg                     | tehuti                  | ti_3410.fw               |
| ti_5052.fw              | tigon                   | tr_smctr.bin            | ttusb-budget             |
| usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw |
| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw       |
| v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw       |
| v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | vicam                    |
| whiteheat.fw            | whiteheat_loader.fw     | yam                     | yamaha                   |
| zd1201-ap.fw            | zd1201.fw               | zd1211                  |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
No WLANs found
==================================================================================================================
*** NWElizaStates
DI:0 AP:0 NI:1 cNI:1 NDIS:0 NIWL:0 IP6:0 WLW:0 RTDT:debian 

```

From the looks of it it's found my usb dongle. (which I already know) but any ideas on how to install it, no idea why it's uninatalled in 10.04 and not 9.10.

---

### Post by pdc on 2010-05-01
the script doesn't advance things with usb device

[http://ubuntuforums.org/showthread.php?t=1057828](http://ubuntuforums.org/showthread.php?t=1057828)

post #4 suggests ndiswrapper

in this thread

[http://www.linuxforums.org/forum/ubuntu-help/139755-ubuntu-speedtouch-121g-ndiswrapper-help.html](http://www.linuxforums.org/forum/ubuntu-help/139755-ubuntu-speedtouch-121g-ndiswrapper-help.html)

post #4 also ........ you may need some of the detail from this?

for your own research if you google on 

> ubuntu 06b9:0121          you will see lots of stuff ........ 06b9:0121 is the unique ID for your device

*some would sa*y spend $10 and buy one that is more user friendly but I am sure you will persevere

---

### Post by framplinux on 2010-05-01
> **pdc said:**
> the script doesn't advance things with usb device

Unfortunately you are right. The script is still struggling with USB WLAN devices. I'll update the script to check for the string 'wireless' for USB devices so CND0120E will not appear any more - at least for this card:-)

---

### Post by framplinux on 2010-05-01
Fixed :) Thx to pdc he detected this script issue .

---

### Post by Robskii on 2010-05-05
Well I fixed the issue by going back to 9.10 as a fresh install and installing the windows drivers with ndiswrapper before the upgrade. Still had the error about network manager until restarting after the upgrade when all seemed to work.

---

### Post by OpPoSiTe on 2010-05-07
Hey Robskii.

Had the same problem with exactly the same ST121g,
the ```
sudo apt-get install linux-firmware-nonfree
``` solved the problem.

Hope i helps.

---

### Post by kmacphail on 2010-05-11
Thank you so much OpPoSiTe that did the trick for me.  I don't actually use ubuntu on my desktop just a backend for XBMC in the loving room so I was rather frustrated when I lost my internet connection (I am not clued up on of which Ubuntu packages are in the repos as I'm a Gentoo user)

---

