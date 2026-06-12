---
title: "Dell Wireless 5630 (EVDO-HSPA) Mobile Broadband Mini-Card"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by maxum2400 on 2012-04-27
I have purchased a Dell Latitude E5420 laptop with the Dell Wireless 5630 broadband mini-card.  The laptop was pre-configured with Windows 7.  I replaced that OS with the ubuntu 10.10 iso from Dell.  The ubuntu OS does not recognize the 5630 mini-card.  Dell essentially told me that they could not help me since my laptop originally came with windows, and so they directed me to the ubuntu forum.

Has anyone gotten this 5630 mini-card working for a ubuntu OS?

---

### Post by wildmanne39 on 2012-04-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by maxum2400 on 2012-04-30
```

```root@adi-Latitude-E5420:~# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux adi-Latitude-E5420 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
root@adi-Latitude-E5420:~# lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0010]
    Kernel driver in use: wl
--
0a:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)
    Subsystem: Dell Device [1028:049b]
    Kernel driver in use: tg3
root@adi-Latitude-E5420:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:8 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@adi-Latitude-E5420:~# rfkill list all
root@adi-Latitude-E5420:~# lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
dm_crypt               11385  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54887  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     7736  0 
ppdev                   5556  0 
parport_pc             26058  0 
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
dell_wmi                2852  0 
dcdbas                  5402  0 
psmouse                59033  0 
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
wl                   1959533  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lib80211                5058  2 lib80211_crypt_tkip,wl
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
i915                  290938  2 
drm_kms_helper         30200  1 i915
drm                   168054  3 i915,drm_kms_helper
tg3                   123310  0 
ahci                   19013  0 
intel_agp              26360  2 i915
firewire_ohci          21106  0 
libahci                21667  3 ahci
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
output                  1883  1 video
crc_itu_t               1383  1 firewire_core
agpgart                32011  2 drm,intel_agp
root@adi-Latitude-E5420:~# 


Thanks for helping.

---

### Post by wildmanne39 on 2012-05-02
Hi, please do:
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
```
watch for errors then unplug your wired connection and reboot.
Thanks

---

### Post by maxum2400 on 2012-05-02
Hello again,

I performed the apt-get commands.  I did not get any errors.  Also, I performed the previous commands and did not notice any differences in their output from before.

Thanks.

---

### Post by wildmanne39 on 2012-05-03
Hi, please try:
```
sudo modprobe wl
```
then post the output of:
```
dmesg | grep wl
lsmod | grep wl
```
Thanks

---

### Post by maxum2400 on 2012-05-03
Hello again,

The wl module was already loaded so I unloaded and then loaded it again for no real good reason.  Therefore, the dmesg output will show the same results twice.

root@adi-Latitude-E5420:~# modprobe wl
root@adi-Latitude-E5420:~# dmesg | grep wl
[   16.640384] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.708048] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.708058] wl 0000:02:00.0: setting latency timer to 64
[  741.490793] wl 0000:02:00.0: PCI INT A disabled
[  746.252792] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  746.252814] wl 0000:02:00.0: setting latency timer to 64
root@adi-Latitude-E5420:~# lsmod | grep wl
wl                   1959533  0 
lib80211                5058  2 wl,lib80211_crypt_tkip


Thanks.

---

### Post by wildmanne39 on 2012-05-03
Hi, post the output of::
```
nm-tool
sudo iwlist scan
``` 
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etork -e radio -e switch | tail -n75
```
Thanks

---

### Post by maxum2400 on 2012-05-03
Hello,

Here is the output.  Thanks.


root@adi-Latitude-E5420:~# nm-tool

NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        44:6D:57:2D:93:69

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2653 6660:       Infra, 00:0F:CC:5A:B2:7C, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WEP
    BoLoNoRa:        Infra, 00:20:A6:83:6D:46, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BoLoNoRa_Guest:  Infra, 00:18:39:0A:08:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA
    BoLoNoRa:        Infra, 00:20:A6:83:77:C6, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        D0:67:E5:4A:AA:A8

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1

    DNS:             192.168.10.1


root@adi-Latitude-E5420:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:20:A6:83:77:C6
                    ESSID:"BoLoNoRa"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-88 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1E:C7:F0:92:69
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-40 dBm  Noise level:-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:20:A6:83:6D:46
                    ESSID:"BoLoNoRa"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-76 dBm  Noise level:-88 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:1E:C7:F0:92:69
                    ESSID:" "
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-38 dBm  Noise level:-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:18:39:0A:08:89
                    ESSID:"BoLoNoRa_Guest"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

root@adi-Latitude-E5420:~# cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etork -e radio -e switch | tail -n75
May  3 16:44:32 adi-Latitude-E5420 avahi-daemon[1114]: Withdrawing address record for fe80::466d:57ff:fe2d:9369 on eth1.
May  3 17:20:30 adi-Latitude-E5420 kernel: [ 6300.383205] wl 0000:02:00.0: PCI INT A disabled
May  3 17:20:30 adi-Latitude-E5420 kernel: [ 6301.297948] SMP alternatives: switching to UP code
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874879.977319] SMP alternatives: switching to SMP code
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874880.530859] wl 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874880.530892] wl 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x93c00004)
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874880.530900] wl 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874880.530910] wl 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874880.564312] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  3 17:20:30 adi-Latitude-E5420 kernel: [1266874880.564322] wl 0000:02:00.0: setting latency timer to 64
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): now managed
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): device state change: 1 -> 2 (reason 2)
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): bringing up device.
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): preparing device.
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): deactivating device (reason: 2).
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): supplicant interface state:  starting -> ready
May  3 17:20:33 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): device state change: 2 -> 3 (reason 42)
May  3 17:20:35 adi-Latitude-E5420 avahi-daemon[1114]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::466d:57ff:fe2d:9369.
May  3 17:20:35 adi-Latitude-E5420 avahi-daemon[1114]: New relevant interface eth1.IPv6 for mDNS.
May  3 17:20:35 adi-Latitude-E5420 avahi-daemon[1114]: Registering new address record for fe80::466d:57ff:fe2d:9369 on eth1.*.
May  3 17:20:44 adi-Latitude-E5420 kernel: [    6.781079] eth1: no IPv6 routers present
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) starting connection 'Auto 2653 6660'
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): device state change: 3 -> 4 (reason 0)
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): device state change: 4 -> 5 (reason 0)
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1/wireless): access point 'Auto 2653 6660' has security, but secrets are required.
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> (eth1): device state change: 5 -> 6 (reason 0)
May  3 17:20:59 adi-Latitude-E5420 NetworkManager[1108]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  3 17:23:25 adi-Latitude-E5420 kernel: [    4.197165] Console: switching to colour frame buffer device 170x48
May  3 17:23:25 adi-Latitude-E5420 kernel: [   16.604535] wl: module license 'MIXED/Proprietary' taints kernel.
May  3 17:23:25 adi-Latitude-E5420 kernel: [   16.644569] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  3 17:23:25 adi-Latitude-E5420 kernel: [   16.644579] wl 0000:02:00.0: setting latency timer to 64
May  3 17:23:25 adi-Latitude-E5420 kernel: [   16.690190] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> monitoring kernel firmware directory '/lib/firmware'.
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1, iface: eth1)
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> WiFi enabled by radio killswitch; enabled by state file
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> WWAN enabled by radio killswitch; enabled by state file
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> WiMAX enabled by radio killswitch; enabled by state file
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <error> [1336080207.850885] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): now managed
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 1 -> 2 (reason 2)
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): bringing up device.
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): preparing device.
May  3 17:23:27 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): deactivating device (reason: 2).
May  3 17:23:28 adi-Latitude-E5420 avahi-daemon[1179]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::466d:57ff:fe2d:9369.
May  3 17:23:28 adi-Latitude-E5420 avahi-daemon[1179]: New relevant interface eth1.IPv6 for mDNS.
May  3 17:23:28 adi-Latitude-E5420 avahi-daemon[1179]: Registering new address record for fe80::466d:57ff:fe2d:9369 on eth1.*.
May  3 17:23:28 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): supplicant manager state:  down -> idle
May  3 17:23:28 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 2 -> 3 (reason 0)
May  3 17:23:28 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): supplicant interface state:  starting -> ready
May  3 17:23:38 adi-Latitude-E5420 kernel: [   30.242542] eth1: no IPv6 routers present
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) starting connection 'Auto 2653 6660'
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 3 -> 4 (reason 0)
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 4 -> 5 (reason 0)
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1/wireless): access point 'Auto 2653 6660' has security, but secrets are required.
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 5 -> 6 (reason 0)
May  3 17:25:53 adi-Latitude-E5420 NetworkManager[1180]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  3 17:25:56 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 6 -> 9 (reason 7)
May  3 17:25:56 adi-Latitude-E5420 NetworkManager[1180]: <warn> Activation (eth1) failed for access point (2653 6660)
May  3 17:25:56 adi-Latitude-E5420 NetworkManager[1180]: <warn> Activation (eth1) failed.
May  3 17:25:56 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): device state change: 9 -> 3 (reason 0)
May  3 17:25:56 adi-Latitude-E5420 NetworkManager[1180]: <info> (eth1): deactivating device (reason: 0).

---

### Post by wildmanne39 on 2012-05-04
Hi, it looks like a bug with network manager but you are using ubuntu 10.10 which is not supported anymore as of this month so very soon you will not be able to get any updates or install applications, I suggest you upgrade to a newer version then if you need help with wireles post back.
Thanks

---

### Post by maxum2400 on 2012-05-05
Hi,

Thanks for your help.  I will upgrade and see what happens.

---

### Post by wildmanne39 on 2012-05-05
Hi, your welcome!

---

### Post by maxum2400 on 2012-05-09
Hi again,

After upgrading to 12.04 LTS, I was able to connect to the 3G network.  Once I configured my mobile broadband connection settings using the network manager, it worked out of the box.

Thanks again.

---

