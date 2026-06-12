---
title: "Enable Wireless PCI card"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by komarx6 on 2012-10-22
Hello!
I have problem with my wireless card in Lubuntu. 1 of 5 times when I turn on my laptop it's working. But other 4 times it does not.
```
lshw -C network
``` prints this: 
```
*-network **DISABLED**
       description: Wireless interface
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: rename6
       version: 01
       serial: 00:0c:41:fc:82:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.5.0-17-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:d4000000-d400ffff
```
How can I enable it?
In puppy linux it is always disabled, but when I go through complicated process of connecting to wireless network (in puppy linux it is) somehow it gets enabled. So, I'm sure it can be enabled I just don't know how.
Puppy and Lubuntu use same driver "ath5k", and modprobe ath5k does not help. Actually lsmod shows ath5k.
Any expert advices on this???

---

### Post by komarx6 on 2012-10-22
Anyone?
It's not integrated card, so it can be removed from port that is on the left side of laptop.
I can see when it's working, both lights blink. When it's not working than only one light is constantly on.
Sometimes when I start computer it starts to blink right away and I know that for this time it would work.
In puppy it does not work until I try to connect.

---

### Post by steeldriver on 2012-10-22
well since it sometimes works OK I would guess it's more likely a software or hardware block issue than a basic driver issue - what do you get if you type this in a terminal?

```
rfkill list all 
```

---

### Post by komarx6 on 2012-10-23
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
And currently it's not working.

---

### Post by chili555 on 2012-10-23
When it's not working, please run and post:```
lsmod
dmesg | grep ath
```Thanks.

---

### Post by komarx6 on 2012-10-23
My friend entered Guest Account and tried to connect to password protected network. I guess internal card was showing network that he tries to connect but than he was able select Atheros card to connect with that card, in dialog for entering password. And card started to blink. So now it working. I'll post output now, and after reboot when card should be disabled.

WORKING:
```
 lsmod
Module                  Size  Used by
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
arc4                   12473  2 
ath5k                 135205  0 
ath                    19187  1 ath5k
mac80211              461161  1 ath5k
cfg80211              175375  3 ath5k,ath,mac80211
pcmcia                 39509  0 
hostap_pci             52704  2 
hostap                105671  1 hostap_pci
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
lib80211               14040  2 hostap_pci,hostap
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_intel8x0           33106  1 
snd_ac97_codec        105616  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80163  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          69337  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
microcode              18209  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
psmouse                84843  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 37276  0 
bnep                   17707  2 
ppdev                  12817  0 
serio_raw              13031  0 
bluetooth             183228  10 rfcomm,bnep
snd                    61991  10 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14036  2 snd_intel8x0,snd_pcm
lpc_ich                16925  0 
shpchp                 32189  0 
soundcore              14599  1 snd
i915                  457161  2 
nvram                  13986  1 thinkpad_acpi
nsc_ircc               23002  0 
irda                  184929  1 nsc_ircc
crc_ccitt              12595  1 irda
parport_pc             31968  1 
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
e100                   35903  0 
crc_itu_t              12627  1 firewire_core
floppy                 55444  1 

```

```
dmesg | grep ath
[   34.539234] ath5k 0000:02:00.0: >enabling device (0000 -> 0002)
[   34.539410] ath5k 0000:02:00.0: >registered as 'phy0'
[   34.877513] ath: EEPROM regdomain: 0x10
[   34.877526] ath: EEPROM indicates we should expect a direct regpair map
[   34.877533] ath: Country alpha2 being used: CO
[   34.877537] ath: Regpair used: 0x10
[   34.993176] ath5k: phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[   34.993190] ath5k: phy0: RF5112B multiband radio found (0x36)
```

---

### Post by komarx6 on 2012-10-24
NOT WORKING:
```
lsmod
Module                  Size  Used by
arc4                   12473  2 
ath5k                 135205  0 
ath                    19187  1 ath5k
mac80211              461161  1 ath5k
cfg80211              175375  3 ath5k,ath,mac80211
snd_intel8x0           33106  1 
snd_ac97_codec        105616  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80163  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          69337  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
microcode              18209  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39509  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                84843  0 
serio_raw              13031  0 
hostap_pci             52704  2 
snd                    61991  10 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14036  2 snd_intel8x0,snd_pcm
hostap                105671  1 hostap_pci
lpc_ich                16925  0 
bnep                   17707  2 
soundcore              14599  1 snd
yenta_socket           27095  0 
lib80211               14040  2 hostap_pci,hostap
bluetooth             183228  7 bnep
pcmcia_rsrc            18191  1 yenta_socket
ppdev                  12817  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
nvram                  13986  1 thinkpad_acpi
nsc_ircc               23002  0 
irda                  184929  1 nsc_ircc
i915                  457161  2 
parport_pc             31968  1 
crc_ccitt              12595  1 irda
shpchp                 32189  0 
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
firewire_ohci          35521  0 
e100                   35903  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 55444  1 
```

```
dmesg | grep ath
[   32.694395] ath5k 0000:02:00.0: >enabling device (0000 -> 0002)
[   32.694569] ath5k 0000:02:00.0: >registered as 'phy0'
[   32.995830] ath: EEPROM regdomain: 0x10
[   32.995845] ath: EEPROM indicates we should expect a direct regpair map
[   32.995851] ath: Country alpha2 being used: CO
[   32.995855] ath: Regpair used: 0x10
[   33.107059] ath5k: phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[   33.107070] ath5k: phy0: RF5112B multiband radio found (0x36)

```

---

### Post by komarx6 on 2012-10-24
Thank you.

---

### Post by komarx6 on 2012-10-24
I've seen few times that "Connect" button is disabled when user tries to connect to password protected network, in dialog where user enters pasword. Does anyone know what could be reason for that. I have that problem when I try to connect some network.
But sometimes if I enter 5 or 13  characters, button is enabled although password has 12 characters.
That's strange.

Also I have problem with connecting with my biult-in card which does not receive enough signal, but it tries to connect and fails, and than all over again, and I can't stop it. It's anoying.

---

### Post by chili555 on 2012-10-29
> Also I have problem with connecting with my biult-in card which does not receive enough signal, but it tries to connect and fails, and than all over again, and I can't stop it. It's anoying.Let's disable the internal card and see if it helps.```
sudo su
echo "blacklist hostap" >> /etc/modprobe.d/blacklist.conf
echo "blacklist hostap_pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if things are improved.

---

### Post by komarx6 on 2012-10-29
Thank you very much.
Well it did help when it comes to the anoying thing. Internal card does not work anymore, so it stopped anoying me.
External card also worked after reboot, but it does not mean anything. I will reboot few more times and report results.

Thank you.

---

### Post by komarx6 on 2012-10-29
I have rebooted 3 times and external card worked, and I was able to connect. I don't really need internal card because this one is better. Although it's not proof, I conclude that it's fixed.
So, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you!

---

### Post by chili555 on 2012-10-29
Thank you for your kind words. Glad it's working.

---

