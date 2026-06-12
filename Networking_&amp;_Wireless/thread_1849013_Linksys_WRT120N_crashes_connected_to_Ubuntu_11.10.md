---
title: "Linksys WRT120N crashes connected to Ubuntu 11.10"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by drkages on 2011-09-23
I have a linksys WRT120N router, which is shared between a couple users of different platforms.

When I use my hp with ubuntu 11.10 installed connected to the wireless the wireless and LAN network goes down, and forces a turn on/off of the router to get connectivity again.

I suspect the router firmware crashes.

However the problem doesn't exist if only windows users are on the system.
I also did the same task on ubuntu 11.10 inside a virtual machine and there was NO lost of connectivity.


Anyone has any idea what might the problem be and possible solutions?

thanks

---

### Post by praseodym on 2011-09-23
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan
lsmod
lsusb
```
Router-firmware is up-to-date? MAC-filter allows new clients?

Why 11.10? Its just beta since today?!

---

### Post by drkages on 2011-09-23
lspci -nnk | grep -iA2 net
Produces 
> 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:1436]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
	Kernel driver in use: iwlagn


iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ESBA-NET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:C8:38:9A   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:207  Invalid misc:52   Missed beacon:0


sudo iwlist scan
> 
Cell 05 - Address: 98:FC:11:C8:38:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:off
                    ESSID:"ESBA-NET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000005d3d5e
                    Extra: Last beacon: 319210ms ago
                    IE: Unknown: 0008455342412D4E4554
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001011041000100103B000103104700100000000000000001100098FC11C8389A102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30361042000C4A555430304C3437393934361054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000


lsmod

> 
Module                  Size  Used by
usbhid                 47198  0 
hid                    95463  1 usbhid
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
joydev                 17693  0 
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
hp_wmi                 18092  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
serio_raw              13166  0 
radeon               1015995  0 
i915                  566711  8 
ttm                    76805  1 radeon
drm_kms_helper         42558  2 radeon,i915
drm                   236330  6 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915
input_polldev          13896  1 lis3lv02d
video                  19412  1 i915
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
iwlagn                314213  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
intel_ips              18089  0 
wmi                    19256  1 hp_wmi
binfmt_misc            17540  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  3 
uas                    18027  0 
ahci                   26002  0 
libahci                26861  1 ahci
r8169                  52788  0 


lsusb
> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 004: ID 10f1:1a25 Importek 
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 03f0:231d Hewlett-Packard 


lspci (for NICs)
> 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)


I updated the firmware for the router but no difference.

Ubuntu 11.10 was hoping for better support for hybrid-graphics which kept me out from using linux as primary for a while

---

### Post by drkages on 2011-09-24
I changed the wireless from N-only to BG mixed and I haven't seen the problem yet.

Any ideas about the cause of the problem. As to why the N network would create problems but not the BG?

---

### Post by praseodym on 2011-09-24
Maybe Intel still deactivates N-mode per default. Try

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager restart
```

---

### Post by pjssilva on 2011-10-09
> **praseodym said:**
> Maybe Intel still deactivates N-mode per default. Try

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager restart
```

Interesting enough, I have exactly the same problem using exactly the same wireless card. My router is different though, it is a TP-Link TL-WR1043ND with DD-WRT firmware.

The solution for me is the opposite of the suggestion above. I have to turn off the 11n in the card (use "options iwlagn 11n_disable=1" above). By doing this my laptop connects using 11g and there isn't any problem. I can then configure the router with "Mixed N/G" mode and allow the other clients to connect with n speed.

---

### Post by mapero on 2011-10-10
Used Fedora 15 some time and had the same behavior with dd-wrt on tp-link 1043nd and intel n6200. They fixed it after some time with this kernel patch:

[https://bugzilla.redhat.com/show_bug.cgi?id=708747](https://bugzilla.redhat.com/show_bug.cgi?id=708747)

Now going back to Ubuntu 11.10 i have the same problem again. 

mapero

---

### Post by dernier_recours on 2011-10-13
Same problem here under 11.10 - 64 bits final release, with Cisco Linksys WRT120N. I experienced this issue with Fedora 15 - Gnome 3. Anybody successfully used the solution quoted here?

> **praseodym said:**
> 
```

echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager restart

```


UPDATE: it didn't work for me.

---

### Post by dernier_recours on 2011-10-13
pjssilva's solution worked for me.

> **pjssilva said:**
> Interesting enough, I have exactly the same problem using exactly the same wireless card. My router is different though, it is a TP-Link TL-WR1043ND with DD-WRT firmware.

The solution for me is the opposite of the suggestion above. I have to turn off the 11n in the card (use "options iwlagn 11n_disable=1" above). By doing this my laptop connects using 11g and there isn't any problem. I can then configure the router with "Mixed N/G" mode and allow the other clients to connect with n speed.

---

### Post by mentose457 on 2011-10-13
> **pjssilva said:**
> Interesting enough, I have exactly the same problem using exactly the same wireless card. My router is different though, it is a TP-Link TL-WR1043ND with DD-WRT firmware.

The solution for me is the opposite of the suggestion above. I have to turn off the 11n in the card (use "options iwlagn 11n_disable=1" above). By doing this my laptop connects using 11g and there isn't any problem. I can then configure the router with "Mixed N/G" mode and allow the other clients to connect with n speed.

Thanks, this also worked for me. 

Could you please expound on what you mean by 'I can then configure the router with "Mixed N/G" mode and allow the other clients to connect with n speed'.

I am wondering if the commands above disabled N mode in the router, not just on my computer. BTW, I have the same router as the OP.

Thanks

---

### Post by tetorutama on 2011-10-18
Quote:
                                                                      Originally Posted by **praseodym**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11280475#post11280475")                 
                 [I]     Code:
     echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf sudo modprobe -rf iwlagn sudo modprobe -v iwlagn sudo service network-manager restart 
[/I]

Worked for me aswell!! Big thanks for helping out with that one!

---

### Post by wilsonr0 on 2011-10-30
> **praseodym said:**
> Maybe Intel still deactivates N-mode per default. Try

```
echo "options iwlagn 11n_disable=0" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
sudo service network-manager restart
```

Hi - many thanks for this - worked for me as well... but only until a restart.

Is there a way I can make these changes persist?

I'm running 11.10 on a lenovo Thinkpad and I've been using a wired connection because of this problem for at least six months!

Thanks again,

Rob

---

### Post by praseodym on 2011-10-30
In 11.10 you better deactivate the N-Mode with "=1" in that file, there is a bug in the driver.

---

### Post by vipulbhandari82 on 2011-11-11
I contacted linksys and they say they don't support linux with their routers so they can't help. 

I have opened a bug report with Ubuntu regarding this issue. It would help if you guys subscribe to the bug. IT would make the bug's criticality important. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/850544](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/850544)

---

