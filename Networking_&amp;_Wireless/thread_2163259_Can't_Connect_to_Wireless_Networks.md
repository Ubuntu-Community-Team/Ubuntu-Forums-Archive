---
title: "Can't Connect to Wireless Networks"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by dinodxr on 2013-07-17
**First of all, hi guys**! i'm new to Ubuntu, used to be a Windows / Mac user for ages. So.. i wanted to try** Ubuntu 12.04 **(i tried also 13.04 i was curious) on an old laptop that i have before installing ubuntu as my primary OS in my desktop. i have a *_Toshiba Satellite M70-191_*, it runs ubuntu just fine but i can't connect to any of the available wireless networks (free or locked ones) i searched for a driver (probably* Intel 915GM*) but nothin'. i also saw here in the forums that other users experience problems when trying to connect to a wifi network. Any kind of help or advice? :popcorn:

---

### Post by papibe on 2013-07-17
Hi dinodxr. Welcome to the forums ):P

Could you open a terminal run this commands and paste its results back?
```
sudo lshw -C network

lspci -nnk | grep -iA2 net

ifconfig

route -n
```
Regards.

---

### Post by dinodxr on 2013-07-17
dinodxr@dinodxr-M70:~$ [COLOR=#ff0000]_**sudo lshw -C network**_[/COLOR]
[sudo] password for dinodxr: 
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:de:11:96
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.5 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:5000(size=256) memory:bc006000-bc0060ff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:11:b5:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:bc007000-bc007fff

dinodxr@dinodxr-M70:~$ [COLOR=#ff0000]_**lspci -nnk | grep -iA2 net**_[/COLOR]
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: 8139too
--
06:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Device [8086:2741]
    Kernel driver in use: ipw2200



dinodxr@dinodxr-M70:~$ [COLOR=#ff0000]_**ifconfig**_[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:de:11:96  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fede:1196/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24948232 (24.9 MB)  TX bytes:1950058 (1.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40895 (40.8 KB)  TX bytes:40895 (40.8 KB)


dinodxr@dinodxr-M70:~$ [COLOR=#ff0000]**_route -n_**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

---

### Post by dinodxr on 2013-07-17
i run the commands, as you said, but didn't had my wifi on. (also sorry for my bad english, italian here)

---

### Post by papibe on 2013-07-17
Thanks.

Your wireless interface is disable.

I have a Toshiba laptop and the button on the keyboard that turns on and off the wireless interface actually works. With that in mind, check if you can enable it from a hardware button, or a custom keyboard shortcut.

Let us know how it goes.
Regards.

---

### Post by dinodxr on 2013-07-17
ok, i found that switch. i got a red light and the network at the status bar shows me some wifi networks. but still can't get on anyone, even mine.

---

### Post by papibe on 2013-07-17
Glad you are making progress.

Try unplugging your ethernet cable and try to connect your own network. What error do you get?

Regards.

---

### Post by dinodxr on 2013-07-17
an error doesn't pop up, it just doesn't connect to any wifi network, even mine. it asks for my password i type and then nothing.

---

### Post by Jhon smith on 2013-07-19
Hi dinodxr, Install ubuntu 12.04 again & driver install in your laptop.  

sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
sudo reboot
create a the file /etc/modprobe.d/ath9k.conf and add the following line to it and reboot
options ath9k nohwcrypt=1

---

### Post by praseodym on 2013-07-19
> **Jhon smith said:**
> Hi dinodxr, Install ubuntu 12.04 again & driver install in your laptop.  

sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
sudo reboot
create a the file /etc/modprobe.d/ath9k.conf and add the following line to it and reboot
options ath9k nohwcrypt=1

This will not help, because of

a) 12.04, the backports are for lucid (and they contain older drivers)

b) he uses an Intel device, not Atheros

Unfortunately, the ipw2200 device driver is not further developed. Please show the outputs of
```

lsmod
rfkill list
iwconfig
dmesg | grep ipw
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by dinodxr on 2013-07-19
[COLOR=#ff8c00]**_lsmod_**[/COLOR]
Module                  Size  Used by
michael_mic            12541  4 
arc4                   12474  2 
lib80211_crypt_tkip    17276  1 
lib80211_crypt_ccmp    12790  1 
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
parport_pc             32115  0 
ppdev                  12850  0 
snd_intel8x0           33463  2 
snd_ac97_codec        106118  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
ipw2200               146213  0 
snd_timer              28932  2 snd_pcm,snd_seq
i915                  479235  2 
libipw                 46733  1 ipw2200
joydev                 17394  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         47459  1 i915
drm                   240443  3 i915,drm_kms_helper
snd                    62675  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39855  0 
cfg80211              181041  2 ipw2200,libipw
soundcore              14636  1 snd
psmouse                91381  0 
yenta_socket           27465  0 
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
pcmcia_rsrc            18368  1 yenta_socket
tifm_7xx1              12938  0 
lib80211               14041  4 lib80211_crypt_tkip,lib80211_crypt_ccmp,ipw2200,libipw
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13317  1 i915
lpc_ich                16993  0 
tifm_core              15069  1 tifm_7xx1
serio_raw              13032  0 
microcode              18396  0 
video                  19117  1 i915
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
8139too                23312  0 
firewire_ohci          36110  0 
8139cp                 26760  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci

[COLOR=#ff8c00]**_rfkill list_**[/COLOR]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

[COLOR=#ff8c00]**_iwconfig_**[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"GaurosEimai"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1C:DF:86:C3:59   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:24  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:6


[COLOR=#ff8c00]**_dmesg | grep ipw_**[/COLOR]
[   10.610264] libipw: 802.11 data/management/control stack, git-1.1.13
[   10.610269] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   10.793644] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   10.793650] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   10.793791] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.017818] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

[COLOR=#ff8c00]**_cat /etc/udev/rules.d/70-persistent-net.rules_**[/COLOR]
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:de:11:96", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:02.0 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:6f:11:b5:8a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

---

### Post by praseodym on 2013-07-19
Which encryption do you use? Try pure WPA2-AES (CCMP). Check you router manual

---

### Post by dinodxr on 2013-07-19
why change encryption? i connect just fine with my macbook and iphone in my wifi router.

---

### Post by dinodxr on 2013-07-19
and even without any active security in my router, still ubuntu can't connect.

---

### Post by praseodym on 2013-07-19
Your other devices do not use an Ahteros chip. They are known to be "special"

---

### Post by dinodxr on 2013-07-19
who has atheros? you are not helping dude.

---

### Post by dinodxr on 2013-07-19
you are not helping guys, just tellin' me to run commands in terminal (commands that none of you explain me what they do), i told you i'm a new user here but if can't have wifi on laptop running ubuntu 12.04 and an intel 2200 card then maybe i'll switch again to mac.

---

### Post by dinodxr on 2013-07-19
240views on this thread and only four people care to help me with my problem. (?!) also the first admin disappeared.

---

### Post by praseodym on 2013-07-19
As I mentioned here [http://ubuntuforums.org/showthread.php?t=2163259&p=12737085#post12737085](http://ubuntuforums.org/showthread.php?t=2163259&p=12737085#post12737085) I am aware you are NOT using an Atheros chip. Confusion in #15

On which channel does you router send? Check

```
iwlist chan
```
how many channels are available. Set the channel to fixed mode if only 1-11 are shown.

Edit: Encryption to pure WPA2-AES, not mixed WPA/WPA2

---

