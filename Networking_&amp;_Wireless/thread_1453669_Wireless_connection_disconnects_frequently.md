---
title: "Wireless connection disconnects frequently"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by Vistz on 2010-04-13
I upgraded to Karmic the other day and my Wireless Internet has been disconnecting every hour or so. I had the same problem on Intrepid but I managed to fix it somehow. After disconnecting, it will reconnect after a few seconds.

---

### Post by 2hot6ft2 on 2010-04-13
I've been rubbing my crystal ball until it looks more like an egg, but I still can't see what wifi adapter you have.:-k

How about you tell us?
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.
:lolflag:

---

### Post by Vistz on 2010-04-14
Here is what I got

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by leorolla on 2010-04-15
```
sudo lshw -C network
lsmod
```

---

### Post by Vistz on 2010-04-21
I typed both commands in and I got a description of my network and a list of modules. Am I supposed to be looking for something specific?


*Edit
Should I enable the karmic backports?

---

### Post by leorolla on 2010-04-22
You should post the outpout of these commands to help us figure out what goes on in your computer.

---

### Post by Vistz on 2010-04-22
sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:ecfff000-ecffffff

```

lsmod
```
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_idt      59876  1 
pcmcia                 36808  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
dell_wmi                2564  0 
snd_seq_dummy           2656  0 
iwl3945                71164  0 
iwlcore               113920  1 iwl3945
mac80211              210508  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56500  0 
iptable_filter          3100  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
serio_raw               5280  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              130632  3 iwl3945,iwlcore,mac80211
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      8964  0 
parport                35340  2 ppdev,lp
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usbhid                 38208  0 
video                  19380  0 
output                  2780  1 video
tg3                   109600  0 
intel_agp              27676  0 
agpgart                34988  1 intel_agp

```

---

### Post by leorolla on 2010-04-22
Is it a fresh install or did you do some fixes on it that you don't remember?

Did you try Lucid?

I also found this and this:
[http://www.ubuntuforums.org/showthread.php?t=1359647](http://www.ubuntuforums.org/showthread.php?t=1359647)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Vistz on 2010-04-22
I originally had Intrepid on my laptop. Then I upgrade to Jaunty and then Karmic. I plan on upgrading to Lucid next week. In the mean time, should I install the backports on karmic?

---

### Post by Rocket J Squirrel on 2010-04-22
I have a different wireless adaptor on my laptop. In karmic I got flaky connections, often for no more than a few dozen minutes at a time, with a continually falling signal strength meter. I'm not saying that my setup is like yours, but I put in some patches and got things working. I also enabled backports and it did its juu-juu and I've now got dead-solid dependable wireless connectivity.

---

### Post by Vistz on 2010-04-22
> **Rocket J Squirrel said:**
> I have a different wireless adaptor on my laptop. In karmic I got flaky connections, often for no more than a few dozen minutes at a time, with a continually falling signal strength meter. I'm not saying that my setup is like yours, but I put in some patches and got things working. I also enabled backports and it did its juu-juu and I've now got dead-solid dependable wireless connectivity.

Yep. The backports seem to have done the trick.

---

### Post by computerfox on 2012-08-18
I'm on Ubuntu Server and this happens all the time to me.  Does anyone have any suggestions, besides going to an ethernet connection?

---

### Post by wildmanne39 on 2012-08-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

