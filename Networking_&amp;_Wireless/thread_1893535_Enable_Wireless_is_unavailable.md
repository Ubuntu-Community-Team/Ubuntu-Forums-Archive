---
title: "Enable Wireless is unavailable"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by ElibusSlyde on 2011-12-10
Hi all,

When I first installed Ubuntu 11.10, Enable Wireless was located  directly above Enable Networking. It was greyed out and inaccessible. I installed Broadcom STA Wireless Driver from Additional Drivers<System Settings, and now Enable Wireless has been removed from the menu.

This is what I get when check the device with wired connection.

```
benjamin@Blah:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:9c:bf:85
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.73 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:f9bfe000-f9bfffff

```
This is what I get when I check the wireless device without a wired connection.

```
benjamin@Blah:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:9c:bf:85
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:f9bfe000-f9bfffff

```
This is what I get when I check connections without a wired connection

```
benjamin@Blah:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```


Any idea how I can get the wireless working? I can change over to Windows XP and it works without issue.

---

### Post by ElibusSlyde on 2011-12-10
In case this is helpful, the laptop I am having this issue with is a Dell Vostro 1500

---

### Post by TBABill on 2011-12-10
The STA driver is broken for the BCM4311 in Ubuntu 11.04 and 11.10. Open a terminal and ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Once that's finished, just ```
sudo modprobe b43
```Wait a few moments and try to connect.

---

### Post by TBABill on 2011-12-10
Before you do the above steps, could you open a terminal and paste back here the output of ```
lsmod
```I would like to see if you have a 2-driver conflict, but if you do the above first we won't ever know.

---

### Post by bkratz on 2011-12-10
> **ElibusSlyde said:**
> In case this is helpful, the laptop I am having this issue with is a Dell Vostro 1500



TBABILL's instructions are correct, but you might also have blacklist issues since you previously tried the STA driver. See the last half of this document regarding this.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by ElibusSlyde on 2011-12-10
lsmod results

Thanks a ton for the help. I'll check out the Blacklist issue, as well

```

lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
nvidia              10390874  48 
b44                    31443  0 
ssb                    50682  1 b44
snd_hda_intel          24262  4 
joydev                 17393  0 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
dell_laptop            13519  0 
wl                   2646601  0 
psmouse                73673  0 
snd_hwdep              13276  1 snd_hda_codec
dcdbas                 14098  1 dell_laptop
r852                   17901  0 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
sm_common              16737  1 r852
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
r592                   17808  0 
nand_ecc               13070  1 nand
memstick               15857  1 r592
mtd                    35852  2 sm_common,nand
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 dell_wmi
lib80211               14570  1 wl
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

```

---

### Post by TBABill on 2011-12-10
Ok, no conflicts in your lsmod, which just lists active modules (drivers). If you need to blacklist the wl module, which is the driver STA, just edit the file, as root, /etc/modprobe.d/blacklist.conf and add the following to the end: ```
blacklist wl
``` then save the file. Once that's done, just ```
sudo modprobe -r wl b43
``` and then ```
sudo modprobe b43
``` Wait a few moments, connect and enjoy :)

---

### Post by ElibusSlyde on 2011-12-11
OK, so I've done that, and it worked great. I now have the enable wireless option again. The problem is that the Broadcom STA driver is no longer active and I can't view/setup my wireless connection because it says device not ready (firmware missing).

Activating the STA driver is what set the other error in motion, should I reactivate it or is there something else I should do?


Thanks again for all the help.

---

### Post by bkratz on 2011-12-11
> **ElibusSlyde said:**
> OK, so I've done that, and it worked great. I now have the enable wireless option again. The problem is that the Broadcom STA driver is no longer active and I can't view/setup my wireless connection because it says device not ready (firmware missing).

Activating the STA driver is what set the other error in motion, should I reactivate it or is there something else I should do?


Thanks again for all the help.


No, you don't want to activate the STA driver. You should be using b43 now. don't quite understand the posting 

```
so I've done that, and it worked great.
```

Are you able to connect now?

---

### Post by ElibusSlyde on 2011-12-11
No, I'm not able to connect. When I bring up the menu "Wireless Enabled is selected, but the "Wireless Networks" is grayed out and says "Device not ready (firmware missing)". 

In Additional Drivers, the Broadcom STA driver is not activated.

---

### Post by westie457 on 2011-12-11
Open Software Centre and search for bcm. In the list that shows remove all of them that have a check mark against them except for the 2 b43 packages you were asked to install.

After that has been done reboot your system. All should be well.

---

### Post by ElibusSlyde on 2011-12-11
Ok, I was able to get it to work. I input 
```

sudo apt-get install b43-fwcutter firmware-b43-installer

```
(from [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)) and restarted. After restarting, the "enable wireless" was once again missing, so I input
```

sudo modprobe -r wl b43

```
and
```

sudo modprobe b43

```

After doing so, I was able to view available networks and connect without issue. Currently, I am drinking coffee on my deck with my laptop keep my legs warm against the cold. Thanks a ton everyone.

---

### Post by bkratz on 2011-12-11
Good to hear you finally got it! Enjoy, and please go to the thread tools and mark as solved in case it helps someone else.

---

