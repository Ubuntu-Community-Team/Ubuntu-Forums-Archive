---
title: "Dell Inspiron 1520 Wireless &amp; Wired not working on Ubuntu 13.04 64-Bit"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by DazzyB on 2013-06-14
Hello all,

I'm new here (and to Linux) and I need help...

I have installed the 64-Bit version of Ubuntu (13.04) on my Dell Inspiron 1520 and I love it!  But, for some odd reason, my WiFi and Ethernet connections are not working at all.  The very strange thing is that the Ethernet connection does work when booting from the Live CD version! (but not Wifi still).

When I installed Ubuntu, I did check the option to download all the updates and other third party software, but still no network support after booting from the hard disk.

I have searched these forums and Google and have found lots of posts regarding fixing this issue on my model of laptop, but none apply to 13.04.  I have still tried the fixes suggested but still can not get either network interface working.

Please could someone offer me some assistance - I really don't know where else to turn now!

Thank you very much in advance! 

Dazzy :)

---

### Post by praseodym on 2013-06-14
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -r
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by DazzyB on 2013-06-15
> **praseodym said:**
> Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -r
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/network/interfaces
cat /etc/resolv.conf
```

Hi Praseodym!  Here are the results...

**tcc@tcc-laptop:~$ uname -r**
**3.8.0-25-generic**
**tcc@tcc-laptop:~$ lspci -nnk | grep -iA2 net**
**03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)**
**	Subsystem: Dell Device [1028:01f1]**
**03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)**
**--**
**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)**
**	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]**
**	Kernel driver in use: wl**
**tcc@tcc-laptop:~$ lsusb**
**Bus 005 Device 002: ID 0fe6:9700 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter**
**Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub**
**Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub**
**Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**tcc@tcc-laptop:~$ lsmod**
**Module                  Size  Used by**
**gpio_ich               13476  0 **
**snd_hda_codec_idt      70256  1 **
**joydev                 17377  0 **
**coretemp               13355  0 **
**dell_wmi               12681  0 **
**sparse_keymap          13890  1 dell_wmi**
**snd_hda_intel          39619  3 **
**snd_hda_codec         136453  2 snd_hda_codec_idt,snd_hda_intel**
**snd_hwdep              13602  1 snd_hda_codec**
**ssb                    79171  1 **
**snd_pcm                97451  2 snd_hda_codec,snd_hda_intel**
**snd_page_alloc         18710  2 snd_pcm,snd_hda_intel**
**dell_laptop            17369  0 **
**snd_seq_midi           13324  0 **
**snd_seq_midi_event     14899  1 snd_seq_midi**
**dcdbas                 14397  1 dell_laptop**
**wl                   3226093  1 **
**snd_rawmidi            30180  1 snd_seq_midi**
**microcode              22881  0 **
**snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi**
**r852                   18241  0 **
**sm_common              16860  1 r852**
**nand                   58949  2 r852,sm_common**
**snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi**
**snd_timer              29425  2 snd_pcm,snd_seq**
**nand_ecc               13273  1 nand**
**nand_bch               13147  1 nand**
**dm9601                 13413  0 **
**lib80211               14352  1 wl**
**bch                    17434  1 nand_bch**
**r592                   18019  0 **
**usbnet                 31879  1 dm9601**
**nand_ids               12723  1 nand**
**psmouse                95870  0 **
**snd                    68876  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device**
**mtd                    45202  2 nand,sm_common**
**memstick               16554  1 r592**
**serio_raw              13215  0 **
**cfg80211              510937  1 wl**
**lpc_ich                17061  0 **
**soundcore              12680  1 snd**
**i915                  600396  3 **
**drm_kms_helper         49394  1 i915**
**mac_hid                13205  0 **
**drm                   286028  4 i915,drm_kms_helper**
**parport_pc             28152  0 **
**ppdev                  17073  0 **
**i2c_algo_bit           13413  1 i915**
**bnep                   18036  2 **
**rfcomm                 42641  0 **
**wmi                    19070  1 dell_wmi**
**bluetooth             228619  10 bnep,rfcomm**
**video                  19390  1 i915**
**lp                     17759  0 **
**parport                46345  3 lp,ppdev,parport_pc**
**firewire_ohci          40103  0 **
**sdhci_pci              18590  0 **
**sdhci                  32522  1 sdhci_pci**
**firewire_core          64508  1 firewire_ohci**
**ahci                   25731  2 **
**libahci                31364  1 ahci**
**crc_itu_t              12707  1 firewire_core**
**tcc@tcc-laptop:~$ ifconfig -a**
**eth2      Link encap:Ethernet  HWaddr 00:e0:4c:53:44:58  **
**          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0**
**          inet6 addr: fe80::2e0:4cff:fe53:4458/64 Scope:Link**
**          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1**
**          RX packets:92420 errors:536 dropped:126 overruns:122 frame:654**
**          TX packets:88553 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:1000 **
**          RX bytes:127245218 (127.2 MB)  TX bytes:6735840 (6.7 MB)**

**lo        Link encap:Local Loopback  **
**          inet addr:127.0.0.1  Mask:255.0.0.0**
**          inet6 addr: ::1/128 Scope:Host**
**          UP LOOPBACK RUNNING  MTU:65536  Metric:1**
**          RX packets:573 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:0 **
**          RX bytes:57991 (57.9 KB)  TX bytes:57991 (57.9 KB)**

**tcc@tcc-laptop:~$ **
**tcc@tcc-laptop:~$ clear**

**tcc@tcc-laptop:~$ uname -r**
**3.8.0-25-generic**
**tcc@tcc-laptop:~$ lspci -nnk | grep -iA2 net**
**03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)**
**	Subsystem: Dell Device [1028:01f1]**
**03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)**
**--**
**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)**
**	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]**
**	Kernel driver in use: wl**
**tcc@tcc-laptop:~$ lsusb**
**Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub**
**Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub**
**Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**
**tcc@tcc-laptop:~$ lsmod**
**Module                  Size  Used by**
**gpio_ich               13476  0 **
**snd_hda_codec_idt      70256  1 **
**joydev                 17377  0 **
**coretemp               13355  0 **
**dell_wmi               12681  0 **
**sparse_keymap          13890  1 dell_wmi**
**snd_hda_intel          39619  3 **
**snd_hda_codec         136453  2 snd_hda_codec_idt,snd_hda_intel**
**snd_hwdep              13602  1 snd_hda_codec**
**ssb                    79171  1 **
**snd_pcm                97451  2 snd_hda_codec,snd_hda_intel**
**snd_page_alloc         18710  2 snd_pcm,snd_hda_intel**
**dell_laptop            17369  0 **
**snd_seq_midi           13324  0 **
**snd_seq_midi_event     14899  1 snd_seq_midi**
**dcdbas                 14397  1 dell_laptop**
**wl                   3226093  1 **
**snd_rawmidi            30180  1 snd_seq_midi**
**microcode              22881  0 **
**snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi**
**r852                   18241  0 **
**sm_common              16860  1 r852**
**nand                   58949  2 r852,sm_common**
**snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi**
**snd_timer              29425  2 snd_pcm,snd_seq**
**nand_ecc               13273  1 nand**
**nand_bch               13147  1 nand**
**dm9601                 13413  0 **
**lib80211               14352  1 wl**
**bch                    17434  1 nand_bch**
**r592                   18019  0 **
**usbnet                 31879  1 dm9601**
**nand_ids               12723  1 nand**
**psmouse                95870  0 **
**snd                    68876  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device**
**mtd                    45202  2 nand,sm_common**
**memstick               16554  1 r592**
**serio_raw              13215  0 **
**cfg80211              510937  1 wl**
**lpc_ich                17061  0 **
**soundcore              12680  1 snd**
**i915                  600396  3 **
**drm_kms_helper         49394  1 i915**
**mac_hid                13205  0 **
**drm                   286028  4 i915,drm_kms_helper**
**parport_pc             28152  0 **
**ppdev                  17073  0 **
**i2c_algo_bit           13413  1 i915**
**bnep                   18036  2 **
**rfcomm                 42641  0 **
**wmi                    19070  1 dell_wmi**
**bluetooth             228619  10 bnep,rfcomm**
**video                  19390  1 i915**
**lp                     17759  0 **
**parport                46345  3 lp,ppdev,parport_pc**
**firewire_ohci          40103  0 **
**sdhci_pci              18590  0 **
**sdhci                  32522  1 sdhci_pci**
**firewire_core          64508  1 firewire_ohci**
**ahci                   25731  2 **
**libahci                31364  1 ahci**
**crc_itu_t              12707  1 firewire_core**
**tcc@tcc-laptop:~$ ifconfig -a**
**lo        Link encap:Local Loopback  **
**          inet addr:127.0.0.1  Mask:255.0.0.0**
**          inet6 addr: ::1/128 Scope:Host**
**          UP LOOPBACK RUNNING  MTU:65536  Metric:1**
**          RX packets:605 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:605 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:0 **
**          RX bytes:60263 (60.2 KB)  TX bytes:60263 (60.2 KB)**

**tcc@tcc-laptop:~$ iwconfig**
**lo        no wireless extensions.**

**tcc@tcc-laptop:~$ rfkill list**
**tcc@tcc-laptop:~$ cat /etc/network/interfaces**
**# interfaces(5) file used by ifup(8) and ifdown(8)**
**auto lo**
**iface lo inet loopback**
**tcc@tcc-laptop:~$ cat /etc/resolv.conf**
**# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)**
**#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN**

Dazzy :)

---

### Post by DazzyB on 2013-06-15
> **ahallubuntu said:**
> You probably have a Broadcom wireless card and the driver must be properly installed.  Being wired in temporarily to an ethernet connection will help get your wireless running.

Start by opening a terminal (Ctrl Alt t) and typing these commands:

```
sudo lshw -C network
rfkill list all
```

What are the results?  This can help us verify for sure that you have a Broadcom wireless card and also which one.

If you have a Broadcom card (BCMxxxx) you can google for "Ubuntu BCMxxxx" (where "BCMxxxx" is the card you actually have for example BCM4313).  If you actually have that card, you can try this:

[http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working](http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working)

which was for 12.04 but may work for 13.04 as well.

Hi Ahallubuntu!  Here's the results you asked for too...

**tcc@tcc-laptop:~$ sudo lshw -C network**
**[sudo] password for tcc: **
**  *-network               **
**       description: Network controller**
**       product: BCM4311 802.11b/g WLAN**
**       vendor: Broadcom Corporation**
**       physical id: 0**
**       bus info: pci@0000:0c:00.0**
**       version: 01**
**       width: 32 bits**
**       clock: 33MHz**
**       capabilities: pm msi pciexpress bus_master cap_list**
**       configuration: driver=wl latency=0**
**       resources: irq:17 memory:fe8fc000-fe8fffff**
**  *-network UNCLAIMED**
**       description: Ethernet controller**
**       product: BCM4401-B0 100Base-TX**
**       vendor: Broadcom Corporation**
**       physical id: 0**
**       bus info: pci@0000:03:00.0**
**       version: 02**
**       width: 32 bits**
**       clock: 33MHz**
**       capabilities: pm bus_master cap_list**
**       configuration: latency=64**
**       resources: memory:fe5fe000-fe5fffff**
**tcc@tcc-laptop:~$ rfkill list all**
**tcc@tcc-laptop:~$ **

I will try your link suggestion and let you know what happens :)

Dazzy.

---

### Post by DazzyB on 2013-06-15
> **ahallubuntu said:**
> You probably have a Broadcom wireless card and the driver must be properly installed.  Being wired in temporarily to an ethernet connection will help get your wireless running.

Start by opening a terminal (Ctrl Alt t) and typing these commands:

```
sudo lshw -C network
rfkill list all
```

What are the results?  This can help us verify for sure that you have a Broadcom wireless card and also which one.

If you have a Broadcom card (BCMxxxx) you can google for "Ubuntu BCMxxxx" (where "BCMxxxx" is the card you actually have for example BCM4313).  If you actually have that card, you can try this:

[http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working](http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working)

which was for 12.04 but may work for 13.04 as well.

I have a USB to Ethernet adapter which works ok so I used that to get an Internet connection on the ubuntu laptop and then tried your suggestion.  Didn't work sadly :(

---

### Post by praseodym on 2013-06-15
Install the following package via double-click:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Then uninstall the STA driver via:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```Reboot.

---

### Post by DazzyB on 2013-06-16
> **praseodym said:**
> Install the following package via double-click:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Then uninstall the STA driver via:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```Reboot.

Awesome, it worked!!!!!!! Thank you! :)

---

### Post by ajar on 2013-07-04
Thank you from me as well. I got it working! (Ubuntu 13.04 32 bit)

---

