---
title: "HP NX9420 replaced Modem/LAN board - LAN still not working - now what?"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by Malmberg on 2013-03-15
Gents,
I have a HPNX9420 with a new 12.04 installation, where the WiFi lan is working perfect - but not the wired, no blinking LEDs, so I assumed the board was fried.
I stumbled over a spare-one, that arrived today - and I swapped the board - still no blinking LEDs :-(
So what shall the absolutely Newbie do now???

Any suggestions will be appreciated :-)

---

### Post by Hadaka on 2013-03-15
mesed up code tag..please see next post.

---

### Post by Hadaka on 2013-03-15
Hi, sorry about that.. please post the
output of..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
thanks.

---

### Post by Malmberg on 2013-03-16
> **Hadaka said:**
> Hi, sorry about that.. please post the
output of..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
thanks.

Hi Hadaka,

Here we go:
> sbm@HP:~$ lspci -nn | egrep '0200|0280'
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
sbm@HP:~$ lsmod
Module                  Size  Used by
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189585  10 rfcomm,bnep
binfmt_misc            17293  1 
tpm_infineon           17297  0 
wl                   2906598  0 
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365556  1 kvm_intel
joydev                 17394  0 
ppdev                  12850  0 
snd_hda_codec_analog    75324  1 
hp_wmi                 13653  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_intel          33029  1 
snd_hda_codec         116477  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
pcmcia                 39855  0 
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
microcode              18396  0 
parport_pc             32115  1 
hp_accel               25729  0 
snd_rawmidi            25426  1 snd_seq_midi
lis3lv02d              19270  1 hp_accel
input_polldev          13649  1 lis3lv02d
tpm_tis                18279  0 
video                  19117  0 
tifm_7xx1              12938  0 
tifm_core              15069  1 tifm_7xx1
wmi                    18745  1 hp_wmi
lib80211               14041  1 wl
yenta_socket           27465  0 
pcmcia_rsrc            18368  1 yenta_socket
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14476  1 snd_seq_midi
arc4                   12474  2 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13078  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                64717  0 
lpc_ich                16993  0 
snd                    62675  11 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                832167  3 
psmouse                91022  0 
iwlegacy               88317  1 iwl3945
ttm                    76326  1 radeon
drm_kms_helper         47459  1 radeon
mac80211              475546  2 iwl3945,iwlegacy
drm                   240232  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13317  1 radeon
serio_raw              13032  0 
cfg80211              181041  4 wl,iwl3945,iwlegacy,mac80211
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lp                     17456  0 
parport                40931  3 ppdev,parport_pc,lp
firewire_ohci          36110  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
sbm@HP:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by Malmberg on 2013-03-16
Has done a bit research :-)
The on-board NIC is a Broadcom NetXtreme Gigabit Ethernet PCI Express = BCM5753M

Is that a problem???

---

### Post by Malmberg on 2013-03-16
Hi Hadaka,
I made a new thread regarding this, with this title:
How to install BCM5753M driver / Ubuntu 12.04
That describes my issue a bit better! - right?
Cheeres

---

### Post by Hadaka on 2013-03-16
Hi, lets start by getting rid of the driver you tried
for your wireless and maybe the ethernet (hardwire)
will come alive.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
the driver you loaded is for broadcom wireless,
not ethernet..so give that a try and see what happens
thanks.

---

### Post by Malmberg on 2013-03-17
> **Hadaka said:**
> Hi, lets start by getting rid of the driver you tried
for your wireless and maybe the ethernet (hardwire)
will come alive.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
the driver you loaded is for broadcom wireless,
not ethernet..so give that a try and see what happens
thanks.

Done - nothing changed!
Thanks

---

### Post by Malmberg on 2013-03-18
Hadaka, 
I have in the meantime updated the BIOS - not that it changed anything :-)

---

### Post by Hadaka on 2013-03-18
Hi, your lan card..ethernet is not even showing up
in the outputs. Since your load is new and you changed
the card ,you might want to consider reloading ubuntu
and see if the new load "sees" the card on installation.
If that doesnt work, I would also suggest only using ONE
thread to continue troubleshooting.Having 2 different threads
is very confusing to the people trying to help you. We have no
idea what commands you have entered or what has been tried.
So please continue working with Parseodym and let him know
if you decide to reload. link to other thread...........
[http://ubuntuforums.org/showthread.php?t=2126239&](http://ubuntuforums.org/showthread.php?t=2126239&)

please mark this thread SOLVED rather than having them
merged,which only adds to the confusion.
thanks.

---

### Post by Malmberg on 2013-03-18
> **Hadaka said:**
> Hi, your lan card..ethernet is not even showing up
in the outputs. Since your load is new and you changed
the card ,you might want to consider reloading ubuntu
and see if the new load "sees" the card on installation.
If that doesnt work, I would also suggest only using ONE
thread to continue troubleshooting.Having 2 different threads
is very confusing to the people trying to help you. We have no
idea what commands you have entered or what has been tried.
So please continue working with Parseodym and let him know
if you decide to reload. link to other thread...........
[http://ubuntuforums.org/showthread.php?t=2126239&](http://ubuntuforums.org/showthread.php?t=2126239&)

please mark this thread SOLVED rather than having them
merged,which only adds to the confusion.
thanks.

Hi Hadaka,
OK - thank you so much for your help!
It was not on purpose I did start 2 threads - I’m just to new to this :-)
and, I understand that its confusing!
I think that I just will let this go - and only use the (sooooo slooow) wifi connection!
Again - thanks for your effort
Cheers Steen

---

