---
title: "Wireless Issue, Dell Vostro"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by am0nrahx on 2012-06-28
I'm running Ubuntu 12.04 LTS on a Dell Vostro 1720, can't seem to get the wireless to work. 

The Additional Drivers application tells me Broadcom STA, but when activated, it doesn't work. The onboard NIC works fine but just can't seem to get the WLAN to work.

Any insight is appreciated.

---

### Post by wildmanne39 on 2012-06-29
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by am0nrahx on 2012-06-29
**cat /etc/lsb-release; uname -a**
> 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux TROLLIBURR 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 i686 i386 GNU/Linux**lspci -nnk | grep -iA2 net**
> 08:00.0 Ethernet controller [0200]:  Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit  Ethernet controller [10ec:8168] (rev 03)
        Subsystem: Dell Device [1028:02c0]
        Kernel driver in use: r8169
--
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
        Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
        Kernel driver in use: wl
**nm-tool** 

> NetworkManager Tool
 
State: connected (global)
 
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        0C:60:76:36:0B:86
 
  Capabilities:
 
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
 
  Wireless Access Points 
 
 
- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:D9:13:ED
 
  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s
 
  Wired Properties
    Carrier:         on
 
  IPv4 Settings:
    Address:         192.168.2.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
 
    DNS:             192.168.2.1
**iwconfig**
> lo        no wireless extensions.
 
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
 
eth0      no wireless extensions.
[B]
rfkill list all[/B]
> 0: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
**lsmod**
> Module                  Size  Used by
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nvidia              10958194  43 
lib80211_crypt_tkip    17240  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
psmouse                87213  0 
snd                    62064  15  snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
wl                   2646601  0 
binfmt_misc            17292  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
video                  19068  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
mmc_block              22618  2 
firewire_ohci          40180  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
r8169                  56321  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


---

### Post by madvinegar on 2012-06-29
Your rfkill list shows that your dell-wifi is both hard blocked and soft blocked.

Open terminal and write:

```
sudo rfkill unblock all
```

Also, check that your wifi switch is on.

Then post here again the results of ```
sudo rfkill list all
``` to check that it has been unblocked.

---

### Post by am0nrahx on 2012-06-29
rfkill unblock all resulted with Yes listed for both.

---

### Post by wildmanne39 on 2012-06-29
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

If still does not connect post the output of:
```
rfkill list all
```

For the hard block there should be a key or button to turn it on.
Thanks

---

### Post by am0nrahx on 2012-06-30
it appears to be working correctly now. Thank you for all your help!

---

### Post by wildmanne39 on 2012-06-30
Hi, I am glad you have it working. please use thread tools at the top of the page to mark the thread solved.
Thanks

---

