---
title: "Re-installed 12.04.1 and now wireless &quot;device not ready&quot;, worked before"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by veroslav on 2012-09-24
Hi,

I had Ubuntu 12.04 (64-bit) installed and working perfectly (wireless included) on my desktop. Then I decided I needed Windows 7 back and re-installed it from the recovery disks.

Now I would like to re-install Ubuntu as well. I downloaded 12.04.1 and booted from the live USB.

Unfortunately, in the live session, I am unable to find any wireless networks to connect to, and I am greeted with the following message in the network manager:

```
Wireless Networks
    Device not ready
```I've tried disabling and re-enabling both the network and wireless from the NM but to no avail. Also tried restarting the live session: no difference. The wireless works in Windows 7. As I said, this used to work in my original Ubuntu 12.04 installation, I didn't even needed to connect through ethernet and download the drivers, it just worked!

Below are some outputs that may be relevant for debugging:

```
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:2a9c]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Lite-On Communications Inc Device [11ad:6632]
    Kernel driver in use: rt2800pci

*-network DISABLED
                description: Wireless interface
                product: RT3090 Wireless 802.11n 1T/1R PCIe
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 00
                serial: 70:f1:a1:93:ad:75
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-29-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:fbff0000-fbffffff
```Can anybody help me?

Thank you in advance.

---

### Post by veroslav on 2012-09-24
UPDATE: Well, while I was in the live session, I plugged in the Ethernet cable and suddenly the wireless came alive! I could see and connect to my router that was listed in the available connections! :)

So I decided to make an install but after I did that, the wireless again is not working :(
I get the same error as before ("Device not ready") in the Network Manager. Not even connecting the Ethernet cable fixes it this time around.

Anybody who could help me, please?

Below is the output of lsmod, I am willing to provide more details if necessary. Just want to get it to work! :(

```
user@user-desktop:~$ lsmod
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
vesafb                 13844  1 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nvidia              12336440  40 
lp                     17799  0 
snd_hda_codec_realtek   224173  1 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
wmi                    19256  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              51144  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
psmouse                97362  0 
i7core_edac            28102  0 
mac_hid                13253  0 
cfg80211              205544  2 rt2x00lib,mac80211
edac_core              53746  3 i7core_edac
eeprom_93cx6           12725  1 rt2800pci
soundcore              15091  1 snd
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
firewire_ohci          41000  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_core          63558  1 firewire_ohci
r8169                  62099  0 
crc_itu_t              12707  1 firewire_core
usb_storage            49198  0 

```

---

### Post by daslinkard on 2012-09-24
What is the output of the following sudo command?
```
lspci
```

---

### Post by veroslav on 2012-09-25
Hi daslinkard,

well, after having restarted the computer a few more times, the wireless just suddenly came back! I dont understand why because I didn't make any changes between the restarts, but last time it just connected straight away to my router after the final restart.

I do recall that I had similar issues now and then in the past (wireless cutting out or being very hard to get going after a fresh install), but this was all on the older versions of Ubuntu (10.10 in particular).

The wireless has been working flawlessly until now.

Regards,
Veroslav

---

### Post by daslinkard on 2012-09-25
I'm glad it's working for you....go ahead and mark this as solved!  Any time you need anything we are here for you.

---

### Post by veroslav on 2012-09-29
Hi again!

Unfortunately, after logging in to Windows for the first time since the problem "cured" itself and logging back to Ubuntu after that, the wireless is gone again :(

It is the same problem as before: Wireless Networks: Device not ready

It seems as though Windows is messing up the wireless connection in Ubuntu. The wireless works as it should in Windows, it connects automatically to my router.

daslinkard, below is the sudo output of lspci command, as requested:

```
user@user-desktop:~$ sudo lspci
[sudo] password for user: 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
04:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```Thank you in advance for any kind of help, this is a really annoying problem.

Kind Regards,
Veroslav

---

### Post by daslinkard on 2012-09-29
Maybe you could try this workaround...

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/541620]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620")

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

---

### Post by veroslav on 2012-10-02
Hi again, daslinkard.

I did some research and it is definately the Windows that is messing up the wireless card. There exists some kind of power management option in Windows that locks the wireless card as a part of power management function.

I've disabled this option in Windows but sadly it didn't make any difference.

What helps is to wait (ca 30 min) after shutting down Windows, and THEN boot into Ubuntu. This way the wireless works in Ubuntu as well. It seems to be some kind of timeout issue, as rebooting to Ubuntu directly after shutting down Windows ALLWAYS renders the wireless "device not ready" in Ubuntu.

I appreciate more info on this issue if anybody has it, although I am starting to feel that this is more of a Windows issue , rather than Ubuntu, and as such might be more appropriate for "Others" forum or similar.

Thanks.

---

