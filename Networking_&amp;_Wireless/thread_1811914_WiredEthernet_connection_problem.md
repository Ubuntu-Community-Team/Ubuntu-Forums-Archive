---
title: "Wired/Ethernet connection problem"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by ccleary777 on 2011-07-25
Hi, I have  installed Ubuntu 11.04 using Wubi through Windows 7. It seems to be  working but it will not connect to my wired internet connection. It tells me there is no wired connection, when there is. I used sysinfo and its not showing any network adapter or controller. I have a board with nvidia nforce go 430, could it be a driver issue. It  works fine in windows though. Tried using a wireless adapter and all is working. But why doesn't the wired ethernet connection work.

Any clues?

Thank you

---

### Post by wildmanne39 on 2011-07-25
Hi, run these commands in a terminal please
```
sudo lshw -C network
```
```
lsmod
```
```
lspci -nn
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ccleary777 on 2011-07-26
```
chris@ubuntu:~$ sudo lshw -C network
[sudo] password for chris: 
chris@ubuntu:~$ lsmod     
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
arc4                   12473  0 
rt2500usb              22621  0 
rt2x00usb              19693  1 rt2500usb
rt2x00lib              39075  2 rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
binfmt_misc            13213  1 
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
nvidia               9766978  40 
tda18271               57528  1 
saa7134_alsa           18130  0 
tda10048               18374  1 
saa7134_dvb            33269  0 
videobuf_dvb           13867  1 saa7134_dvb
dvb_core               90587  1 videobuf_dvb
tda8290                22227  0 
tea5767                13114  0 
tuner                  26802  1 
rc_winfast             12454  0 
saa7134               149236  2 saa7134_dvb,saa7134_alsa
ir_nec_decoder         12490  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 saa7134_alsa,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rc_core                25760  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_winfast,saa7134,ir_nec_decoder
v4l2_common            16757  2 tuner,saa7134
snd_timer              28659  2 snd_pcm,snd_seq
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  3 tuner,saa7134,v4l2_common
snd                    55295  12 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        18747  3 saa7134_dvb,saa7134_alsa,saa7134
psmouse                73312  0 
videobuf_core          25193  3 videobuf_dvb,saa7134,videobuf_dma_sg
joydev                 17322  0 
tveeprom               17009  1 saa7134
soundcore              12600  1 snd
parport_pc             32111  1 
serio_raw              12990  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
nv_tco                 13331  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
hid_microsoft          12745  0 
usbhid                 41704  0 
hid                    77084  2 hid_microsoft,usbhid
floppy                 60032  0 
pata_amd               13762  0 
forcedeth              58190  0 
sata_nv                23176  1 
chris@ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a2)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.2 Multimedia audio controller [0401]: nVidia Corporation MCP51 AC97 Audio Controller [10de:026b] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9400 GT] [10de:0641] (rev a1)
04:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
chris@ubuntu:~$ rfkill list all
chris@ubuntu:~$

```Thanks.

---

### Post by wildmanne39 on 2011-07-26
Hi, was there no output for the command? If not can you run it again and give it a minute to process.
```
sudo lshw -C network
```
Thank you

---

### Post by ccleary777 on 2011-07-26
Hiya,

Without my wireless adapter (just my ethernet cable) it produces >CPUID > PCI(sysfs) > SCSI and then nothing.

With my wireless adapter and ethernet plugged in :
```
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:0d:0b:76:3f:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2500usb driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.77 link=yes multicast=yes wireless=IEEE 802.11bg

```Here are the other commands with the wireless adapter and the ethernet plugged in

```
chris@ubuntu:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
arc4                   12473  2 
rt2500usb              22621  0 
rt2x00usb              19693  1 rt2500usb
rt2x00lib              39075  2 rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
nvidia               9766978  40 
tda18271               57528  1 
tda10048               18374  1 
saa7134_alsa           18130  0 
saa7134_dvb            33269  0 
videobuf_dvb           13867  1 saa7134_dvb
dvb_core               90587  1 videobuf_dvb
tda8290                22227  0 
tea5767                13114  0 
tuner                  26802  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 saa7134_alsa,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rc_winfast             12454  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
saa7134               149236  2 saa7134_dvb,saa7134_alsa
ppdev                  12849  0 
ir_nec_decoder         12490  0 
joydev                 17322  0 
parport_pc             32111  1 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
rc_core                25760  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_winfast,ir_nec_decoder,saa7134
k8temp                 12872  0 
snd                    55295  12 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
v4l2_common            16757  2 tuner,saa7134
videodev               75143  3 tuner,saa7134,v4l2_common
videobuf_dma_sg        18747  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          25193  3 videobuf_dvb,saa7134,videobuf_dma_sg
soundcore              12600  1 snd
tveeprom               17009  1 saa7134
nv_tco                 13331  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
hid_microsoft          12745  0 
usbhid                 41704  0 
hid                    77084  2 hid_microsoft,usbhid
sata_nv                23176  1 
forcedeth              58190  0 
pata_amd               13762  0 
floppy                 60032  0 
chris@ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a2)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.2 Multimedia audio controller [0401]: nVidia Corporation MCP51 AC97 Audio Controller [10de:026b] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9400 GT] [10de:0641] (rev a1)
04:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
chris@ubuntu:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
chris@ubuntu:~$ 

```

---

### Post by wildmanne39 on 2011-07-26
Hi, please run this command in a terminal
```
sudo cat /var/log/syslog | grep -e forcedeth -e 14.0
```
That is so we can see if you have any error messages about your network card.

If there are numerous repeats, we only need to see one repeat; in your case 8-10 lines, please post the results here.
Thank you

---

### Post by ccleary777 on 2011-07-27
```
Jul 27 19:18:38 ubuntu kernel: [    0.181707] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 27 19:18:38 ubuntu kernel: [    0.181716] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 27 19:18:38 ubuntu kernel: [    0.181722] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 27 19:18:38 ubuntu kernel: [    0.181751] pci 0000:00:14.0: supports D1 D2
Jul 27 19:18:38 ubuntu kernel: [    0.181752] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 27 19:18:38 ubuntu kernel: [    0.181756] pci 0000:00:14.0: PME# disabled
Jul 27 19:18:38 ubuntu kernel: [    0.214206] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jul 27 19:18:38 ubuntu kernel: [    0.214706] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
Jul 27 19:18:38 ubuntu kernel: [    0.223534] pnp 00:01: [io  0x1400-0x147f]
Jul 27 19:18:38 ubuntu kernel: [    0.223536] pnp 00:01: [io  0x1480-0x14ff]
Jul 27 19:18:38 ubuntu kernel: [    0.223628] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 27 19:18:38 ubuntu kernel: [    0.223630] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 27 19:18:38 ubuntu kernel: [    0.981176] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 27 19:18:38 ubuntu kernel: [    1.010520] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 27 19:18:38 ubuntu kernel: [    1.010527] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 27 19:18:38 ubuntu kernel: [    1.532699] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 27 19:18:38 ubuntu kernel: [    1.532702] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 27 19:18:38 ubuntu kernel: [   17.278951] type=1400 audit(1311790716.875:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=523 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   17.279284] type=1400 audit(1311790716.875:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   17.279490] type=1400 audit(1311790716.875:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   17.310400] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 27 19:18:38 ubuntu kernel: [   19.110134] type=1400 audit(1311790718.707:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=814 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.112559] type=1400 audit(1311790718.711:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.112772] type=1400 audit(1311790718.711:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=814 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.113273] type=1400 audit(1311790718.711:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=813 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.141430] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Jul 27 19:18:38 ubuntu kernel: [   19.161527] type=1400 audit(1311790718.759:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=817 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.161940] type=1400 audit(1311790718.759:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=817 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.164968] type=1400 audit(1311790718.763:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=829 comm="apparmor_parser"
Jul 27 19:18:39 ubuntu NetworkManager[842]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 27 19:18:39 ubuntu NetworkManager[842]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 27 19:18:58 ubuntu rtkit-daemon[1239]: Successfully made thread 1480 of process 1480 (n/a) owned by '1000' high priority at nice level -11.
Jul 27 19:18:58 ubuntu pulseaudio[1480]: pid.c: Daemon already running.
chris@ubuntu:~$ 

```

Is that what you were after

---

### Post by wildmanne39 on 2011-07-27
Hi, close the part I need is where network manager is try to connect and it can not, if you need to you can post all of it here and we will look through it.

---

### Post by ccleary777 on 2011-07-28
Thanks here it is

```
Jul 24 10:00:52 ubuntu kernel: [    0.891460] EISA: Detected 0 cards.
Jul 24 10:00:52 ubuntu kernel: [    1.013115] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 24 10:00:52 ubuntu kernel: [    1.013305] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 24 10:00:52 ubuntu kernel: [    1.013310] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 24 10:00:52 ubuntu kernel: [    1.536696] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 24 10:00:52 ubuntu kernel: [    1.536701] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 24 10:00:52 ubuntu kernel: [    6.821704] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 24 10:00:52 ubuntu kernel: [    8.195797] type=1400 audit(1311498049.797:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=586 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [    8.196148] type=1400 audit(1311498049.801:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=586 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [    8.196355] type=1400 audit(1311498049.801:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=586 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [    8.196706] type=1400 audit(1311498049.801:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=587 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [    8.197158] type=1400 audit(1311498049.801:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=587 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [    8.197370] type=1400 audit(1311498049.801:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=587 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [   11.296146] type=1400 audit(1311498052.901:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=917 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [   11.296489] type=1400 audit(1311498052.901:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=917 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [   11.296697] type=1400 audit(1311498052.901:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=917 comm="apparmor_parser"
Jul 24 10:00:52 ubuntu kernel: [   11.333522] type=1400 audit(1311498052.937:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=916 comm="apparmor_parser"
Jul 24 10:00:54 ubuntu NetworkManager[943]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 24 10:00:54 ubuntu NetworkManager[943]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 24 10:00:54 ubuntu NetworkManager[943]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 24 10:00:54 ubuntu NetworkManager[943]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:14.0/net/eth0
Jul 24 10:00:59 ubuntu kernel: [   18.380057] type=1400 audit(1311498059.985:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=918 comm="apparmor_parser"
Jul 24 10:00:59 ubuntu kernel: [   18.382084] type=1400 audit(1311498059.985:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=918 comm="apparmor_parser"
Jul 24 10:00:59 ubuntu kernel: [   18.383326] type=1400 audit(1311498059.985:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=918 comm="apparmor_parser"
Jul 24 10:01:12 ubuntu rtkit-daemon[1306]: Successfully made thread 1490 of process 1487 (n/a) owned by '1000' RT at priority 5.
Jul 24 17:47:46 ubuntu kernel: [    0.181710] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 24 17:47:46 ubuntu kernel: [    0.181720] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 24 17:47:46 ubuntu kernel: [    0.181725] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 24 17:47:46 ubuntu kernel: [    0.181754] pci 0000:00:14.0: supports D1 D2
Jul 24 17:47:46 ubuntu kernel: [    0.181756] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 24 17:47:46 ubuntu kernel: [    0.181759] pci 0000:00:14.0: PME# disabled
Jul 24 17:47:46 ubuntu kernel: [    0.214902] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Jul 24 17:47:46 ubuntu kernel: [    0.223532] pnp 00:01: [io  0x1400-0x147f]
Jul 24 17:47:46 ubuntu kernel: [    0.223534] pnp 00:01: [io  0x1480-0x14ff]
Jul 24 17:47:46 ubuntu kernel: [    0.223626] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 24 17:47:46 ubuntu kernel: [    0.223628] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 24 17:47:46 ubuntu kernel: [    1.033039] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 24 17:47:46 ubuntu kernel: [    1.033173] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 24 17:47:46 ubuntu kernel: [    1.033177] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 24 17:47:46 ubuntu kernel: [    1.548661] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 24 17:47:46 ubuntu kernel: [    1.548665] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 24 17:47:46 ubuntu kernel: [    6.303692] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 24 17:47:46 ubuntu kernel: [    7.040734] type=1400 audit(1311526062.641:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=595 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [    7.041056] type=1400 audit(1311526062.641:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=595 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [    7.041264] type=1400 audit(1311526062.641:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=595 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [    7.041865] type=1400 audit(1311526062.641:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=591 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [    7.042184] type=1400 audit(1311526062.641:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=591 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [    7.042391] type=1400 audit(1311526062.641:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=591 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [   10.729711] type=1400 audit(1311526066.329:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=870 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [   10.731253] type=1400 audit(1311526066.329:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=870 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [   10.731469] type=1400 audit(1311526066.329:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=870 comm="apparmor_parser"
Jul 24 17:47:46 ubuntu kernel: [   10.808100] type=1400 audit(1311526066.409:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=869 comm="apparmor_parser"
Jul 24 17:47:47 ubuntu NetworkManager[896]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 24 17:47:47 ubuntu NetworkManager[896]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 24 17:47:47 ubuntu NetworkManager[896]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 24 17:47:53 ubuntu kernel: [   17.719754] type=1400 audit(1311526073.317:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=871 comm="apparmor_parser"
Jul 24 17:47:53 ubuntu kernel: [   17.721730] type=1400 audit(1311526073.321:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=871 comm="apparmor_parser"
Jul 24 17:47:53 ubuntu kernel: [   17.722937] type=1400 audit(1311526073.321:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=871 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [    0.149065] print_constraints: dummy: 
Jul 25 20:02:04 ubuntu kernel: [    0.149095] Time: 20:01:46  Date: 07/25/11
Jul 25 20:02:04 ubuntu kernel: [    0.177705] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 25 20:02:04 ubuntu kernel: [    0.177714] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 25 20:02:04 ubuntu kernel: [    0.177720] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 25 20:02:04 ubuntu kernel: [    0.177748] pci 0000:00:14.0: supports D1 D2
Jul 25 20:02:04 ubuntu kernel: [    0.177750] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 25 20:02:04 ubuntu kernel: [    0.177753] pci 0000:00:14.0: PME# disabled
Jul 25 20:02:04 ubuntu kernel: [    0.219554] pnp 00:01: [io  0x1400-0x147f]
Jul 25 20:02:04 ubuntu kernel: [    0.219556] pnp 00:01: [io  0x1480-0x14ff]
Jul 25 20:02:04 ubuntu kernel: [    0.219648] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 25 20:02:04 ubuntu kernel: [    0.219651] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 25 20:02:04 ubuntu kernel: [    0.814606] loop: module loaded
Jul 25 20:02:04 ubuntu kernel: [    1.015163] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 25 20:02:04 ubuntu kernel: [    1.015343] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 25 20:02:04 ubuntu kernel: [    1.015348] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 25 20:02:04 ubuntu kernel: [    1.536690] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 25 20:02:04 ubuntu kernel: [    1.536694] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 25 20:02:04 ubuntu kernel: [   15.746876] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 25 20:02:04 ubuntu kernel: [   15.870501] type=1400 audit(1311620522.475:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   15.871315] type=1400 audit(1311620522.475:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   15.871524] type=1400 audit(1311620522.475:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.894021] type=1400 audit(1311620524.499:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=882 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.895306] type=1400 audit(1311620524.499:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=883 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.895650] type=1400 audit(1311620524.499:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=883 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.895855] type=1400 audit(1311620524.499:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=883 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.966079] type=1400 audit(1311620524.571:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=896 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.966482] type=1400 audit(1311620524.571:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=896 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu kernel: [   17.969968] type=1400 audit(1311620524.575:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=903 comm="apparmor_parser"
Jul 25 20:02:04 ubuntu NetworkManager[890]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 25 20:02:04 ubuntu NetworkManager[890]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 25 20:02:04 ubuntu NetworkManager[890]:    SCPlugin-Ifupdown: (141096480) ... get_connections.
Jul 25 20:02:04 ubuntu NetworkManager[890]:    SCPlugin-Ifupdown: (141096480) ... get_connections (managed=false): return empty list.
Jul 25 20:02:04 ubuntu NetworkManager[890]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 25 20:08:04 ubuntu NetworkManager[2070]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 25 20:08:04 ubuntu NetworkManager[2070]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 25 20:08:04 ubuntu NetworkManager[2070]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 19:38:04 ubuntu kernel: [    0.181420] pci 0000:00:0d.0: reg 20: [io  0xf400-0xf40f]
Jul 26 19:38:04 ubuntu kernel: [    0.181460] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
Jul 26 19:38:04 ubuntu kernel: [    0.181698] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 26 19:38:04 ubuntu kernel: [    0.181708] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 26 19:38:04 ubuntu kernel: [    0.181713] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 26 19:38:04 ubuntu kernel: [    0.181742] pci 0000:00:14.0: supports D1 D2
Jul 26 19:38:04 ubuntu kernel: [    0.181744] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 19:38:04 ubuntu kernel: [    0.181747] pci 0000:00:14.0: PME# disabled
Jul 26 19:38:04 ubuntu kernel: [    0.214102] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Jul 26 19:38:04 ubuntu kernel: [    0.214600] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
Jul 26 19:38:04 ubuntu kernel: [    0.223549] pnp 00:01: [io  0x1400-0x147f]
Jul 26 19:38:04 ubuntu kernel: [    0.223551] pnp 00:01: [io  0x1480-0x14ff]
Jul 26 19:38:04 ubuntu kernel: [    0.223643] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 26 19:38:04 ubuntu kernel: [    0.223646] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 26 19:38:04 ubuntu kernel: [    1.021236] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 19:38:04 ubuntu kernel: [    1.021400] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 19:38:04 ubuntu kernel: [    1.021405] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 19:38:04 ubuntu kernel: [    1.536683] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 26 19:38:04 ubuntu kernel: [    1.536687] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 19:38:04 ubuntu kernel: [   16.759934] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 26 19:38:04 ubuntu kernel: [   16.967452] type=1400 audit(1311705482.564:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=594 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   16.967791] type=1400 audit(1311705482.564:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=594 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   16.968031] type=1400 audit(1311705482.564:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=594 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.735448] type=1400 audit(1311705484.332:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=882 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.735777] type=1400 audit(1311705484.332:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=882 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.735988] type=1400 audit(1311705484.332:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=882 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.738970] type=1400 audit(1311705484.336:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=881 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.781902] type=1400 audit(1311705484.380:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=891 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.782298] type=1400 audit(1311705484.380:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=891 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu kernel: [   18.786331] type=1400 audit(1311705484.384:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=897 comm="apparmor_parser"
Jul 26 19:38:04 ubuntu NetworkManager[895]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 19:38:04 ubuntu NetworkManager[895]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 19:38:32 ubuntu rtkit-daemon[1236]: Successfully made thread 1470 of process 1424 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:20:50 ubuntu kernel: [    0.149066] print_constraints: dummy: 
Jul 26 21:20:50 ubuntu kernel: [    0.149097] Time: 21:20:31  Date: 07/26/11
Jul 26 21:20:50 ubuntu kernel: [    0.177707] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 26 21:20:50 ubuntu kernel: [    0.177716] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 26 21:20:50 ubuntu kernel: [    0.177722] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 26 21:20:50 ubuntu kernel: [    0.177750] pci 0000:00:14.0: supports D1 D2
Jul 26 21:20:50 ubuntu kernel: [    0.177752] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 21:20:50 ubuntu kernel: [    0.177755] pci 0000:00:14.0: PME# disabled
Jul 26 21:20:50 ubuntu kernel: [    0.219450] pnp 00:01: [io  0x1400-0x147f]
Jul 26 21:20:50 ubuntu kernel: [    0.219452] pnp 00:01: [io  0x1480-0x14ff]
Jul 26 21:20:50 ubuntu kernel: [    0.219543] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 26 21:20:50 ubuntu kernel: [    0.219545] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 26 21:20:50 ubuntu kernel: [    0.814606] loop: module loaded
Jul 26 21:20:50 ubuntu kernel: [    1.025663] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 21:20:50 ubuntu kernel: [    1.025805] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 21:20:50 ubuntu kernel: [    1.025811] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 21:20:50 ubuntu kernel: [    1.548721] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 26 21:20:50 ubuntu kernel: [    1.548727] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 21:20:50 ubuntu kernel: [   16.774533] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 26 21:20:50 ubuntu kernel: [   16.787325] type=1400 audit(1311711648.388:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   16.787663] type=1400 audit(1311711648.388:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   16.787866] type=1400 audit(1311711648.388:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.243090] type=1400 audit(1311711650.844:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=919 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.248113] type=1400 audit(1311711650.852:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=917 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.249757] type=1400 audit(1311711650.852:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=918 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.250843] type=1400 audit(1311711650.852:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=919 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.251050] type=1400 audit(1311711650.852:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=919 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.251171] type=1400 audit(1311711650.852:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=917 comm="apparmor_parser"
Jul 26 21:20:50 ubuntu kernel: [   19.264812] type=1400 audit(1311711650.868:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=923 comm="apparmor_parser"
Jul 26 21:20:51 ubuntu NetworkManager[909]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 21:20:51 ubuntu NetworkManager[909]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 21:20:55 ubuntu rtkit-daemon[1331]: Successfully made thread 1420 of process 1328 (n/a) owned by '106' RT at priority 5.
Jul 26 21:24:50 ubuntu kernel: [  258.514601] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jul 26 21:24:50 ubuntu kernel: [  258.514604] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jul 26 21:24:50 ubuntu kernel: [  258.514606] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jul 26 21:24:50 ubuntu kernel: [  258.514608] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jul 26 22:14:00 ubuntu dhclient: DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
Jul 26 22:14:00 ubuntu dhclient: DHCPNAK from 192.168.1.254
Jul 26 22:14:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 22:14:09 ubuntu dhclient: DHCPOFFER of 192.168.1.64 from 192.168.1.254
Jul 26 22:14:09 ubuntu dhclient: DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
Jul 26 22:14:09 ubuntu dhclient: DHCPNAK from 192.168.1.254
Jul 27 19:18:38 ubuntu kernel: [    0.181707] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 27 19:18:38 ubuntu kernel: [    0.181716] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 27 19:18:38 ubuntu kernel: [    0.181722] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 27 19:18:38 ubuntu kernel: [    0.181751] pci 0000:00:14.0: supports D1 D2
Jul 27 19:18:38 ubuntu kernel: [    0.181752] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 27 19:18:38 ubuntu kernel: [    0.181756] pci 0000:00:14.0: PME# disabled
Jul 27 19:18:38 ubuntu kernel: [    0.214206] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jul 27 19:18:38 ubuntu kernel: [    0.214706] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
Jul 27 19:18:38 ubuntu kernel: [    0.223534] pnp 00:01: [io  0x1400-0x147f]
Jul 27 19:18:38 ubuntu kernel: [    0.223536] pnp 00:01: [io  0x1480-0x14ff]
Jul 27 19:18:38 ubuntu kernel: [    0.223628] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 27 19:18:38 ubuntu kernel: [    0.223630] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 27 19:18:38 ubuntu kernel: [    0.981176] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 27 19:18:38 ubuntu kernel: [    1.010520] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 27 19:18:38 ubuntu kernel: [    1.010527] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 27 19:18:38 ubuntu kernel: [    1.532699] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 27 19:18:38 ubuntu kernel: [    1.532702] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 27 19:18:38 ubuntu kernel: [   17.278951] type=1400 audit(1311790716.875:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=523 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   17.279284] type=1400 audit(1311790716.875:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   17.279490] type=1400 audit(1311790716.875:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   17.310400] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 27 19:18:38 ubuntu kernel: [   19.110134] type=1400 audit(1311790718.707:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=814 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.112559] type=1400 audit(1311790718.711:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.112772] type=1400 audit(1311790718.711:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=814 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.113273] type=1400 audit(1311790718.711:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=813 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.141430] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Jul 27 19:18:38 ubuntu kernel: [   19.161527] type=1400 audit(1311790718.759:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=817 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.161940] type=1400 audit(1311790718.759:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=817 comm="apparmor_parser"
Jul 27 19:18:38 ubuntu kernel: [   19.164968] type=1400 audit(1311790718.763:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=829 comm="apparmor_parser"
Jul 27 19:18:39 ubuntu NetworkManager[842]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 27 19:18:39 ubuntu NetworkManager[842]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 27 19:18:58 ubuntu rtkit-daemon[1239]: Successfully made thread 1480 of process 1480 (n/a) owned by '1000' high priority at nice level -11.
Jul 27 19:18:58 ubuntu pulseaudio[1480]: pid.c: Daemon already running.
Jul 28 22:08:41 ubuntu kernel: [    0.181712] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
Jul 28 22:08:41 ubuntu kernel: [    0.181722] pci 0000:00:14.0: reg 10: [mem 0xfe02a000-0xfe02afff]
Jul 28 22:08:41 ubuntu kernel: [    0.181728] pci 0000:00:14.0: reg 14: [io  0xc000-0xc007]
Jul 28 22:08:41 ubuntu kernel: [    0.181756] pci 0000:00:14.0: supports D1 D2
Jul 28 22:08:41 ubuntu kernel: [    0.181758] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 28 22:08:41 ubuntu kernel: [    0.181761] pci 0000:00:14.0: PME# disabled
Jul 28 22:08:41 ubuntu kernel: [    0.214401] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Jul 28 22:08:41 ubuntu kernel: [    0.214904] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Jul 28 22:08:41 ubuntu kernel: [    0.223556] pnp 00:01: [io  0x1400-0x147f]
Jul 28 22:08:41 ubuntu kernel: [    0.223558] pnp 00:01: [io  0x1480-0x14ff]
Jul 28 22:08:41 ubuntu kernel: [    0.223651] system 00:01: [io  0x1400-0x147f] has been reserved
Jul 28 22:08:41 ubuntu kernel: [    0.223654] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul 28 22:08:41 ubuntu kernel: [    1.030595] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 28 22:08:41 ubuntu kernel: [    1.030763] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 28 22:08:41 ubuntu kernel: [    1.030769] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 28 22:08:41 ubuntu kernel: [    1.552703] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:38:cb:d8
Jul 28 22:08:41 ubuntu kernel: [    1.552706] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 28 22:08:41 ubuntu kernel: [   16.162273] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
Jul 28 22:08:41 ubuntu kernel: [   16.167951] type=1400 audit(1311887319.763:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=574 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   16.168465] type=1400 audit(1311887319.767:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=574 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   16.168665] type=1400 audit(1311887319.767:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=574 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.738036] type=1400 audit(1311887321.335:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=855 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.738367] type=1400 audit(1311887321.335:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=856 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.738710] type=1400 audit(1311887321.335:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=856 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.738921] type=1400 audit(1311887321.335:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=856 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.799588] type=1400 audit(1311887321.395:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=859 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.799984] type=1400 audit(1311887321.395:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=859 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu kernel: [   17.806348] type=1400 audit(1311887321.403:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=881 comm="apparmor_parser"
Jul 28 22:08:41 ubuntu NetworkManager[871]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 28 22:08:41 ubuntu NetworkManager[871]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
chris@ubuntu:~$ 

```

---

### Post by chili555 on 2011-07-28
>  ubuntu dhclient: DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
Jul 26 22:14:00 ubuntu dhclient: [COLOR="Red"]DHCPNAK[/COLOR] from 192.168.1.254
Jul 26 22:14:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 22:14:09 ubuntu dhclient: DHCPOFFER of 192.168.1.64 from 192.168.1.254
Jul 26 22:14:09 ubuntu dhclient: DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
Jul 26 22:14:09 ubuntu dhclient: DHCPNAK from 192.168.1.254Wild Man, you might investigate this. DHCPNAK means the server has withdrawn its offer. The client returns to the INIT state. Does ccleary777 have any specific settings in Network Manager? It ought to be blank. You might try:```
sudo ifdown eth0
sudo rmmod -f forcedeth
sudo modprobe forcedeth phy_power_down=0
sudo ifup eth0
```If it helps, you can write a .conf file.

Now we return to our regularly scheduled guru.

---

### Post by wildmanne39 on 2011-07-28
Hi, thank you chili555.

Please run the commands that chili555 listed and post here the results.
Thank you):P

---

### Post by ccleary777 on 2011-07-29
Thanks for helping guys. This is what I have, I left it for 10 mins but still the last command just produced a flashing cursor.

```
chris@ubuntu:~$ sudo ifdown eth0
[sudo] password for chris: 
RTNETLINK answers: No such process
chris@ubuntu:~$ sudo rmmod -f forcedeth
chris@ubuntu:~$ sudo modprobe forcedeth phy_power_down=0
chris@ubuntu:~$ sudo ifup eth0



```

---

### Post by wildmanne39 on 2011-07-29
Hi, run these commands please
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
cat /etc/network/interfaces
```
This will tell you what is in a file called interfaces. You should see
> auto lo
iface lo inet loopback 
Thank you

---

### Post by ccleary777 on 2011-07-29
```
chris@ubuntu:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
chris@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
chris@ubuntu:~$ 


```

Thank you.

---

### Post by wildmanne39 on 2011-07-29
Hi, you need to take out everything except what I showed in my last post by doing this
```
gksu gedit
```
then then at the top of the window click on open then browse to the filesystem etc folder and then the network folder and open the interfaces file, then delete the files that are not suppose to be there and restart ubuntu.

---

### Post by ccleary777 on 2011-07-30
Hi, 
Yep did that the interfaces file now contains only 
```
auto lo
iface lo inet loopback
```Still cant connect to the internet via ethernet, very annoying

---

### Post by lkjoel on 2011-07-30
Let's just make sure you have an enter line at the end of the interfaces file.
I don't know how important it is, but it's better to be safe than sorry ;-)
```
cat << EOF | sudo tee -a /etc/network/interfaces
auto lo
iface lo inet loopback

EOF

```
Then reboot

---

### Post by ccleary777 on 2011-08-02
Yep, made sure there is a enter line. Still no wired network :(:(

---

### Post by lkjoel on 2011-08-02
Try putting an Ubuntu LiveCD in the disk tray, rebooting into the LiveCD, and then see if you can connect to the internet.

---

### Post by ccleary777 on 2011-08-05
Just tried booting from the live cd and guess what .......

Still no wired internet.

Maybe Ubuntu just doesn't like my hardware or something.

---

### Post by wildmanne39 on 2011-08-05
Hi, I had a person with that same card and problem, he ended up reinstalling 10.10 and it fixed his problem.

I do not think you need to do that unless you are just not happy with your wireless connection, but I am out of ideas.

Also I know you are using 11.04, so you probably would not want 10.10.

I am sorry I do not have the answer for you.

---

### Post by lkjoel on 2011-08-05
> **ccleary777 said:**
> Just tried booting from the live cd and guess what .......

Still no wired internet.

Maybe Ubuntu just doesn't like my hardware or something.
It's a problem with the Ubuntu OS, so we can't really help you.

---

### Post by ccleary777 on 2011-08-06
Thanks for your help guys. I'll have to stick to wireless until some updates come along. Thanks again.

---

### Post by wildmanne39 on 2011-08-06
Hi, your welcome!

---

