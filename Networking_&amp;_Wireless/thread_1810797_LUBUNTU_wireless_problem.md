---
title: "LUBUNTU wireless problem"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by noober on 2011-07-23
Computer is a Compaq presario v2000, runs fine with windows 7 32 bit.  And before that I had Ubuntu on it.  I have tried everything I remember that got wireless working with Ubuntu.  Also the hardware switch for the wireless does not work while running lubuntu.  Any ideas? Help please

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in a terminal please
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```

---

### Post by noober on 2011-07-23
Nothing happened when I did that.:(

---

### Post by nm_geo on 2011-07-23
He would like to see any result you get in the terminal.  Those are diagnostic commands that will help wildmanne figure out how to help.  So post the results .

---

### Post by noober on 2011-07-23
> **nm_geo said:**
> He would like to see any result you get in the terminal.  Those are diagnostic commands that will help wildmanne figure out how to help.  So post the results .

Seriously nothing happened. Lubuntu icon bottom left > run > right?  Terminal in unbuntu run in lubuntu? No report was generated:confused:

---

### Post by wildmanne39 on 2011-07-23
Hi, was this the terminal that opened or just a little window? If it was just a little window try this ctrl+alt+t to open the terminal.

---

### Post by noober on 2011-07-23
> **wildmanne39 said:**
> Hi, was this the terminal that opened or just a little window? If it was just a little window try this ctrl+alt+t to open the terminal.

Yeah my bad, I figured it was the same thing. Thank for helping.


compaq@Mace:~$ lspci -nn | grep 0280
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
compaq@Mace:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

compaq@Mace:~$ rfkill list All
Bogus list argument 'All'.
compaq@Mace:~$ rfkill list All
Bogus list argument 'All'.
compaq@Mace:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
compaq@Mace:~$

---

### Post by nm_geo on 2011-07-23
I am curious .. run this one please..

```
cat /etc/lsb-release; uname -a

```

---

### Post by wildmanne39 on 2011-07-23
Hi, this should get your wireless working.

Open your package manager and type in bcm and make sure that the there are no drivers installed for the broadcom card then install b43fwcutter,firmware-b43-installer,bcmwl-kernel-source.
Then restart your computer and see if you have wireless internet.

---

### Post by noober on 2011-07-23
> **nm_geo said:**
> I am curious .. run this one please..

```
cat /etc/lsb-release; uname -a

```

compaq@Mace:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux Mace 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux
compaq@Mace:~$

---

### Post by nm_geo on 2011-07-23
okay have you tired the STA (wl) driver?

---

### Post by noober on 2011-07-23
> **wildmanne39 said:**
> Hi, this should get your wireless working.

Open your package manager and type in bcm and make sure that the there are no drivers installed for the broadcom card then install b43fwcutter,firmware-b43-installer,bcmwl-kernel-source.
Then restart your computer and see if you have wireless internet.

Did not work.  

What is the STA driver I can not find it under the packet manager.

---

### Post by nm_geo on 2011-07-23
> **noober said:**
> Did not work.  

What is the STA driver I can not find it under the packet manager.

I believe it is ,bcmwl-kernel-source.. I would remove that package..
And reboot..
Then we will see

---

### Post by noober on 2011-07-23
Still nothing. :confused:

---

### Post by nm_geo on 2011-07-23
Ok you tried reboot?

let us see

```
sudo lshw -C network
``````
lsmod
``````
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```Just copy and paste in terminal  that last one if not easy to retype

---

### Post by noober on 2011-07-23
How bad is it?


compaq@Mace:~$ sudo lshw -c network
[sudo] password for compaq: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:2c:90:56
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.30 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:c0204000-c0205fff
compaq@Mace:~$ lsmod
Module                  Size  Used by
ndiswrapper           192828  0 
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  67 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
snd_atiixp_modem       18624  0 
snd_atiixp             19400  1 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
hp_wmi                 13418  0 
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
tifm_7xx1              12898  0 
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  10 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
shpchp                 32345  0 
k8temp                 12872  0 
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
firewire_ohci          31504  0 
8139too                23208  0 
sdhci_pci              13623  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
video                  18951  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
i2c_algo_bit           13184  1 radeon
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ati_agp                13202  0 
pata_atiixp            12968  2 
compaq@Mace:~$ cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
blacklist bcm43xx
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
alias wlan0 ndiswrapper
compaq@Mace:~$

---

### Post by nm_geo on 2011-07-23
Wow I need chili555 aspirins .. 
We have lots of conflicts .. and blacklist problems..
Let start here.

```
sudo apt-get autoremove ndiswrapper
```

---

### Post by nm_geo on 2011-07-23
Wow I need chili555 aspirins .. 
We have lots of conflicts .. and blacklist problems..
Let start here.

```
sudo apt-get autoremove ndiswrapper
```

Then do
 ```
lsmod
```

---

### Post by wildmanne39 on 2011-07-23
Hi, I am just going to watch this part.

---

### Post by noober on 2011-07-23
compaq@Mace:~$ sudo apt-get autoremove ndiswrapper
[sudo] password for compaq: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndiswrapper
compaq@Mace:~$ lsmod
Module                  Size  Used by
ndiswrapper           192828  0 
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  69 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
snd_atiixp_modem       18624  0 
snd_atiixp             19400  1 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
hp_wmi                 13418  0 
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
tifm_7xx1              12898  0 
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  10 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
shpchp                 32345  0 
k8temp                 12872  0 
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
firewire_ohci          31504  0 
8139too                23208  0 
sdhci_pci              13623  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
video                  18951  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
i2c_algo_bit           13184  1 radeon
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ati_agp                13202  0 
pata_atiixp            12968  2 
compaq@Mace:~$

---

### Post by nm_geo on 2011-07-23
Please reboot..
and do the 
```
lsmod
```

Also verify that under Additional Driver the STA driver is not activated or installed.

We have blacklist issue with B43 and ssb and we need them too.

```
cd /etc/modprobe.d
ls
```

They should not be added to the normal 
blacklist.conf
So we may just remove the file the STA (wl) driver created.

---

### Post by nm_geo on 2011-07-23
How did you install the ndswrapper?  It might help to know.

---

### Post by noober on 2011-07-23
> **nm_geo said:**
> How did you install the ndswrapper?  It might help to know.

through synaptic manager.  Do you think it would be worth it for me to just reinstall? So we can start from a clean slate?


compaq@Mace:~$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  66 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
snd_atiixp             19400  1 
snd_atiixp_modem       18624  0 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
joydev                 17322  0 
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
psmouse                73312  0 
tifm_7xx1              12898  0 
yenta_socket           27230  0 
snd                    55295  10 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12872  0 
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13095  0 
ndiswrapper           192828  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   180037  4 radeon,ttm,drm_kms_helper
firewire_ohci          31504  0 
sdhci_pci              13623  0 
8139too                23208  0 
i2c_algo_bit           13184  1 radeon
video                  18951  0 
firewire_core          56138  1 firewire_ohci
ati_agp                13202  0 
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  2 
compaq@Mace:~$ cd /etc/modprobe.d
compaq@Mace:/etc/modprobe.d$ ls
alsa-base.conf           blacklist-framebuffer.conf   broadcom-sta-common.conf
blacklist                blacklist-modem.conf         libpisock9.conf
blacklist-ath_pci.conf   blacklist-oss.conf           ndiswrapper.conf
blacklist.conf           blacklist-rare-network.conf  sl-modem.conf
blacklist-firewire.conf  blacklist-watchdog.conf
compaq@Mace:/etc/modprobe.d$

---

### Post by nm_geo on 2011-07-23
Remove ndiswrapper with Synaptic..
Be sure to remove that bcmwl-kernel-source too...

I think all you need is 
b43-fwcutter
firmware-b43-installer

We can get there but if you want to re-install that would be okay too.
Up to you really..

It does look like the blacklist for b43 and ssb are gone.. Maybe..

---

### Post by nm_geo on 2011-07-23
ignore that i see the blacklist file


just let me know..

---

### Post by noober on 2011-07-23
Yeah let me reinstall because I have it partitioned now but I am pretty sure I want just lubuntu.  So that way I know how for the future.  Is there a script I should run and post immediately after the install?

---

### Post by nm_geo on 2011-07-23
> **noober said:**
> Yeah let me reinstall because I have it partitioned now but I am pretty sure I want just lubuntu.  So that way I know how for the future.  Is there a script I should run and post immediately after the install?

Not really I would After new install

```
sudo apt-get update
``````
sudo apt-get upgrade
```Wait awhile LOL

Then 

```
sudo apt-get install b43-fwcutter
``````
sudo apt-get install firmware-b43-installer
```Reboot without ethernet setup wireless
I think you will have updated lubuntu and wireless..

---

### Post by noober on 2011-07-23
Works fine now thank you.

---

### Post by wildmanne39 on 2011-07-23
Hi, glad it all worked out,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by nm_geo on 2011-07-23
noober give us 
```

sudo lshw -C network
```

It will be part of a project we are planning.. :D

---

### Post by noober on 2011-07-24
> **nm_geo said:**
> noober give us 
```

sudo lshw -C network
```

It will be part of a project we are planning.. :D

Now I just have to figure the monitor out. Thanks for your help.

sudo] password for compaq: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:2c:90:56
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2.
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:c0204000-c0205fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:71:39:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-.generic firmware=410.2160 ip=192.168.1.34 link=yes multicast=yes wireles70.191.243.0=IEEE 802.11bg
compaq@Mace:~$

---

### Post by nm_geo on 2011-07-24
thanks noober .. Please mark thread Solved near Title...

---

