---
title: "HP ProBook 4525s Wireless Not Available"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by The Card Cheat on 2011-11-09
Hey,

Hopefully this thread is not considered too dead, I am having a similar issue to those here but not identical, but it seemed this thing has been fleshed out here pretty solidly so far so I shouldn't make a new thread. I read through and I believe this is a new variant of the problem.

I got a new laptop for work and I have not been able to get wireless to activate at all with 11.10. There is a hard switch (but it isn't a "switch", it is a button that always has the amber/ochre coloration indicating it is off). I never pressed the switch either way before I discovered I couldn't find my home wireless, as I have only moved to use wireless in the last week, I am wired at work. I have an Ubuntu install alone, Windows in virtualbox (I was hoping I could be slick and activate it in Windows then catch it in Ubuntu, but I guess since the host OS does not use it the virtualbox can not even see it). I have tried everything I have seen online and the stuff in here that is relevant I think, but I did not want to go further and mess something up without some guidance.

The computer is a HP ProBook 4525s, I can not seem to find the identity of the wireless card anywhere, the only place it even shows up is in rfkill.

cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Walnut 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 98:4b:e1:4f:5a:37
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=10.1.10.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:d0020000-d003ffff
```
nm-tool
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 98:4b:e1:4f:5a:37
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=10.1.10.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:d0020000-d003ffff

```
rfkill list all
```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
```
lsmod | grep -e laptop -e wmi
```
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
wmi                    19256  1 hp_wmi
```
lspci -nn | grep 0280
```
nothing
```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
sudo iwlist scan
Code:
lo        no wireless extensions.

eth0      no wireless extensions.
```
lsmod | grep b43
```
b43                   341198  0 
ssb                    52752  1 b43
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
lspci -nn
Code:
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:01.0 PCI bridge [0604]: Hewlett-Packard Company Device [103c:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4) [1022:9608]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
```

I tried to do the ```
sudo rfkill unblock all
``` fix many times both disabling/enabling network manager, restarting, etc. and it has never helped. Devices still show up as hard blocked. I also tried blacklisting hp-wmi but if I do this nothing shows up in rfkill or the list of devices and the wireless functionality is still not there. I also tried enabling LAN/WLAN switching in the BIOS then tricking the wireless card into turning on by unplugging the wired after it was connected.

Help would be mucho appreciated, I use this laptop for development for work and not being able to use it remotely (anywhere but the office) is hampering what I could be getting done.

---

### Post by wildmanne39 on 2011-11-09
Hi, I see you decided to start your own thread, that other thread was not to old, you can post in it as long as it has had activity within the last 12 months.

I am not sure that I can help, your card is either turned off in the bios, not seated properly which I do not think is possible in a laptop or it is bad, I say that because it should have shown up with the commands you ran even being hard blocked.

If this is an old laptop it could be a different type of card and we can see it with different commands so we will try them, please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
sudo pccardctl ident
```
```
lsusb
```
Thank you

---

### Post by The Card Cheat on 2011-11-09
Thanks. The idea that it might be bad has been a fear, I am more adept at Windows than Linux, but this just was not looking right. I have been through the BIOS once to look for weird stuff but I will again. Do you know if there is an ultimate boot CD type thing that would allow me to see devices outside Linux without another OS? I guess I can also try a puppy linux or something off my usb just to see as well. I did read someone else claiming they absolutely needed HP Wireless Assistant in Windows to activate it then boot back into Linux but I have a hard time seeing how that base of a functionality would solely be in their Windows assistant.

lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:142c]
	Kernel driver in use: r8169

```
sudo pccardctl ident
```
no output
```
lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05c8:040d Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

```

Thanks

---

### Post by The Card Cheat on 2011-11-09
I can't believe that I am saying this but it was indeed in the BIOS. There was an option for "Bluetooth/WiFi combo device". I can only assume the last time I went through the BIOS I just saw Bluetooth and thought nothing of it. The fact that this was disabled by default is ridiculous, but I did miss it. I came here for an answer though and your thoughts made me re-check my own so thanks a ton.

---

### Post by wildmanne39 on 2011-11-10
Hi, your welcome! I am glad I could help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

