---
title: "Acer aspire 5050 network problem"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by kennedn on 2011-03-28
I have an Aspire acer 5050 laptop and have been having network problems for sometime. This only started occurring when i upgraded the Ubuntu kernal to the newest one. 

I just done a clean install of ubuntu again in the hope that it would get rid of my problem and it seemed to for the first few boots but after i reinstalled windows xp along side ubuntu i started running into the same problem again but im not sure exactly whats causing the problem though.

The only solution ive found is playing around with the wifi switch at the front of my laptop for a couple of minutes until ubuntu decided to recognize my build in wifi card which is an Atheros AR2413.

Ive looked around on a bunch of similar threads but the few that have a solution have never solved my wifi problems.

Any help would be much appreciated :)

---

### Post by PCNetSpec on 2011-03-28
Could be this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090)

---

### Post by kennedn on 2011-04-15
Sorry but that didn't seem to work, the Wifi started working again unexpectedly shortly after i posted though, but now its back to its old habits with not wanting to switch on :L

Anybody got any other ideas?

---

### Post by kennedn on 2011-04-19
bump

---

### Post by josephmills on 2011-04-19
could I please see a ```
lshw -C network
```

---

### Post by kennedn on 2011-04-19
Here's the output of your command: 

```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:f4:54:8b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:a000(size=256) memory:b0211c00-b0211cff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:bc:d1:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.2.4 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:b0200000-b020ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by josephmills on 2011-04-19
could I see a ```
dmesg | grep ath5k
``` and a ```
lsmod
``` thanks again

---

### Post by kennedn on 2011-04-19
Heres the dmesg | grep ath5k output: 

```

[   29.247783] ath5k 0000:08:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   29.247845] ath5k 0000:08:04.0: registered as 'phy0'
[   30.303007] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)

```and the lsmod:

```

Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  4 
snd_seq_midi            4588  0 
radeon                829223  3 
zd1211rw               43440  0 
snd_rawmidi            17783  1 snd_seq_midi
ath5k                 130083  0 
snd_seq_midi_event      6047  1 snd_seq_midi
mac80211              231959  2 zd1211rw,ath5k
pcmcia                 35973  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath                     8153  1 ath5k
ttm                    56633  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  4 zd1211rw,ath5k,ath,mac80211
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
drm_kms_helper         30200  1 radeon
drm                   168060  5 radeon,ttm,drm_kms_helper
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                  8767  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               8635  0 
psmouse                59033  0 
serio_raw               4022  0 
k8temp                  3228  0 
i2c_algo_bit            5168  1 radeon
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
ati_agp                 5202  0 
agpgart                32011  3 ttm,drm,ati_agp
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  1 
usbhid                 36882  0 
hid                    67742  1 usbhid
8139too                19581  0 
sdhci_pci               6633  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
sdhci                  15922  1 sdhci_pci
led_class               2633  2 ath5k,sdhci
pata_atiixp             3288  0 
sata_sil                7035  2 

```Cheers

---

### Post by josephmills on 2011-04-19
make sure that you are **pluged into router** then Could you please go to **System-->addmin-->synaptic package manager** then go to** setting-->repositories ** then make sure that all the same ones are ticked **(see pic)** then if your repositories changed a window will pop up close it then go to the **reload button (see pic)** and click it  after download is done. open you **terminal** and insert ```
sudo apt-get upgrade
```

---

### Post by kennedn on 2011-05-08
I just did a fresh install of ubuntu 10.10 again and the internet now seems to be working fine, it stopped again today but i think i found a solution, i restarted and went into my windows xp partition and i noticed that the internet switch on the front of my laptop was on so i switched it off and then it connected on windows xp, i then restarted again and switched to my ubuntu partition and its been working fine all day :L thanks to everyone who tried to help i think im going to declare this form solved as i cant see any other solutions.

---

