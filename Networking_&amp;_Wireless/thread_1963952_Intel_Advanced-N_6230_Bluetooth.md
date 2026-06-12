---
title: "Intel Advanced-N 6230 Bluetooth"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by Avertine on 2012-04-23
PC: HP Mini 210 with Intel Centrino Advanced-N 6230 N/bluetooth, Ubuntu 11.10 x64.
Network: Asus RT-N56U dual band N router.

Issue: Bluetooth and WIFI don't seem to work together with the iwlagn driver. The Mini 210 doesn't have a hardware bluetooth switch, only a WIFI/wireless switch. I haven't been able to enable bluetooth in the least, but WIFI does work on both 2.4GHz and 5GHz band. A peculiarity, upon first booth with the card, my bluetooth mouse asked the 6230 for access to a "service" three times which I accepted. The mouse doesn't work in Ubuntu (yet).

My intentions are to use both 2.4GHz WIFI and a bluetooth mouse simultaneously. I was told elsewhere that this isn't possible with Ubuntu and refused to believe it. The card is not bad as everything functions normally in Windows 7. The bluetooth appears to be "Hard blocked" under rfkill, as seen below.

I have followed this article which explains my problem quite well: [http://askubuntu.com/questions/69234/centrino-advanced-n-6230-and-bluetooth-wireless-problems-with-dell-xps-15z](http://askubuntu.com/questions/69234/centrino-advanced-n-6230-and-bluetooth-wireless-problems-with-dell-xps-15z)

And have found no solution as of yet.

Thanks for the help!

Some info:

#cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux MINI210 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```#lspci -nnk | grep -iA2 net
```
 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3660]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5201]
    Kernel driver in use: iwlagn

```#iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"HAL 5GHz"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: F4:6D:04:6D:A5:7A   
          Bit Rate=300 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:56  Invalid misc:1   Missed beacon:0

```#rfkill list all
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```#lsmod
```

Module                  Size  Used by
iwlagn                314257  0 
snd_seq_dummy          12798  0 
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
joydev                 17693  0 
binfmt_misc            17540  1 
uvcvideo               72711  0 
arc4                   12529  2 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  3 
snd_hda_codec         104931  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
btusb                  18600  2 
serio_raw              13166  0 
bluetooth             166112  23 bnep,rfcomm,btusb
mac80211              462046  1 iwlagn
snd_seq                61896  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
i915                  571251  3 
snd                    68266  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  2 iwlagn,mac80211
wmi                    19256  1 hp_wmi
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  2 ums_realtek
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 

```

---

### Post by Avertine on 2012-04-24
Is there any more information needed? Any ideas?

Thanks again!

---

### Post by Avertine on 2012-05-20
Quoting user56060 from the link above:

> I had a similar problem where I couldn't turn  on wifi or bluetooth after disabling bluetooth, or wifi after disabling  wifi, and that fn+f2 had no effect in ubuntu. With the help of the  person above, and some other forums, this fixed the problem:
```
sudo modprobe iwlagn power_level=5 sudo modprobe btusb reset=1 sudo rfkill unblock all 
```After that, fn+f2 works, bluetooth can be disabled without disabling wifi, and wifi can be re-enabled after it is disabled.

Wifi worked out of the box for me, but enabling bluetooth disables wifi until the next restart. I upgraded to Ubuntu 12.04 x64 and the issue is the same as described above. Is there any way to get both wifi and bluetooth working under Ubuntu with these cards?

Thanks for the help!

---

### Post by henaoelkin on 2012-09-05
I have a dell xps 15z with intel centrino advanced-n 6230 and the problem with ubuntu 12.04 is the same. I follow this recomendations: 

[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z#Wireless_connection](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z#Wireless_connection)

but i dont have changes.

could any one help us?

---

