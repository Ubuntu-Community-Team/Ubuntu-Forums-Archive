---
title: "Toshiba Satellite WiFi struggles"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by sungod84 on 2011-09-14
Hello
     I have been scouring these forums and others alike to find a solution to my problem and have come up with nothing seemed to fit. I am hoping that I can get some help here. I will post as much info as possible. If the solution exists somewhere else I am happy if you would kindly point the way. I was unsuccessful. I also currently have the realtek RTL819x WiFi driver insatlled. Thank You in advance! :)


Toshiba Satellite L745

output of lspci:

sungod84@SunGod84:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)

output of lsmod:
sungod84@SunGod84:~$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  831 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     31291  1 
snd_hda_codec_conexant    60606  1 
r8192ce_pci           466060  0 
arc4                   12473  2 
rtl8192ce              66006  0 
rtl8192c_common        64264  1 rtl8192ce
rtlwifi                84167  1 rtl8192ce
mac80211              259567  2 rtl8192ce,rtlwifi
snd_hda_intel          32188  2 
snd_hda_codec         107780  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                88146  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              155552  2 rtlwifi,mac80211
snd_seq_midi           13132  0 
snd_rawmidi            25172  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                59337  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28484  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61415  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13666  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
joydev                 17322  0 
psmouse                59039  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
i915                  451068  3 
drm_kms_helper         40745  1 i915
ahci                   21591  2 
drm                   184164  4 i915,drm_kms_helper
atl1c                  35753  0 
i2c_algo_bit           13184  1 i915
libahci                25548  1 ahci
video                  18951  1 i915

output of lsusb:
sungod84@SunGod84:~$ lsusb
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b289 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

output of ifconfig: 
sungod84@SunGod84:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:69:a1:67  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9a:8fff:fe69:a167/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1520 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1041404 (1.0 MB)  TX bytes:180758 (180.7 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52401 (52.4 KB)  TX bytes:52401 (52.4 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:47:7d:ad  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe47:7dad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21994240 (21.9 MB)  TX bytes:2560809 (2.5 MB)

output of iwconfig:
sungod84@SunGod84:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SunGod84"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: E0:91:F5:CA:C5:88   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

vboxnet0  no wireless extensions.

---

### Post by sungod84 on 2011-09-15
After posting this I went to a wired connection out of frustration. I tried my wifi one more time and now I am no longer even able to connect to my home network. From slow loading pages to no connection. Help will now be even more appreciated

---

