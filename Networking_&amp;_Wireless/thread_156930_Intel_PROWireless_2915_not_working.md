---
title: "Intel PRO/Wireless 2915 not working"
date: 2006-04-08
forum: Networking &amp; Wireless
---

### Post by prashanthgopinath on 2006-04-08
Hi,
I am new to linux and need help on setting up wireless network. I am using "Dell INSPIRON 600m" laptop with Ubuntu 5.10(Breezy). I am not able to setup the wireless network on my laptop. 
The following are the details:
Laptop: Dell Insiron600m
Wireless Card: Intel PRO/Wireless 2915
Wireless Router: AirLink 101(802.11G)

The following are output of some commands that might be of help:

**gopinath@ubuntu:~$ lspci**
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
**0000:02:03.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)**

**gopinath@ubuntu:~$ lsmod**
Module                  Size  Used by
nls_cp437               5888  1
isofs                  32824  1
udf                    75524  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  17
af_packet              20232  4
pcspkr                  3652  0
rtc                    11832  0
[B]ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211[/B]
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
b44                    19204  0
mii                     5248  1 b44
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  701
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

**gopinath@ubuntu:~$ dmesg**
.164000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[4294858.164000] Socket status: 30000006
[4294858.175000] PCI: Enabling device 0000:02:01.1 (0000 -> 0002)
[4294858.175000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294858.175000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:01be]
[4294858.295000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[4294858.295000] Socket status: 30000006
[4294858.700000] ieee80211_crypt: registered algorithm 'NULL'
[4294858.703000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294858.703000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[B][4294858.719000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294858.719000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294858.723000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294858.723000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[4294858.999000] ipw2200: Radio Frequency Kill Switch is On:
[4294858.999000] Kill switch must be turned off for wireless networking to work.
[4294860.684000] Real Time Clock Driver v1.12
[4294860.720000] input: PC Speaker
[4294943.006000] eth1: no IPv6 routers present
[/B]

Thanks in advance.

Prashanth

---

### Post by YuHoo on 2006-04-08
[QUOTE=prashanthgopinath][4294858.719000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6[/QUOTE]

You have the old drivers default in the Breezy install, these did not work for my XPS M140 either. I run through the installation of the stable in this thread: [http://ubuntuforums.org/showthread.php?t=154615&highlight=ipw2200](http://ubuntuforums.org/showthread.php?t=154615&highlight=ipw2200)

I'll repost for your convenience as well...

To install, get the newest ieee80211b drivers, if you haven't done so already, at [http://ieee80211.sourceforge.net/index.php]("http://ieee80211.sourceforge.net/index.php"). The biggest thing you need to do is not to follow their instructions. 

Untar it with and then enter its folder to make and make install
```
tar -xzvf ieee80211-1.1.13.tgz
make
make install
```
If you have any errors check below the download area where they have a fix for it.

Then get the stable releases of ipw2200, the newest versions do not work all the time. [http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/"). Make sure to get the ipw2200-1.1.0.tgz and the firmware v2.4

```
tar -xzvf ipw2200-fw-2.4.tgz
sudo cp ipw2200-fw-2.4 /lib/hotplug/firmware
```
Now your firmware is installed, all you need is the drivers.

```
tar -xzvf ipw2200-1.1.0.tgz
cd ipw2200-1.1.0
sudo make
sudo make install
```

Good luck, make sure you get the stable releases so you don't need to worry about experimental problems.

---

### Post by prashanthgopinath on 2006-04-08
Hi YuHoo,
Thanks for your reply. I am facing some issues while compiling "ieee80211-1.1.13". 
Am I missing something?

The following is the error: 
[COLOR="Red"]/wireless/ieee80211-1.1.13# make
Checking in /lib/modules/2.6.12-9-386 for ieee80211 components...
find: /lib/modules/2.6.12-9-386/build/: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-9-386/build M=/home/gopinath/Desktop/wireless/ieee80211-1.1.13 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
[/COLOR]


Prashanth

---

### Post by prashanthgopinath on 2006-04-08
I think I got the issue..... have to install the linux kernel source from the ubuntu packages. I will try that and update on the status.

Thanks,
Prashanth

---

### Post by prashanthgopinath on 2006-04-08
Hi YuHoo,
I blindly followed the steps to install the new drivers, its working fine. The only extra change I did was disabled the ipv6 as it was looking for a ipv6 router and hence was not getting an IP, i think....
 
Thanks a lot for all the help... :)

Prashanth

---

### Post by YuHoo on 2006-04-09
no problem, ipw2200 has given me about 10,000 headaches so I've gone through nearly every driver available for it. And surprise, I keep finding that stable releases are the best to use.

---

