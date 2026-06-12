---
title: "wireless on x201 fails shortly after boot"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by gregnorc on 2010-05-01
Hi, I just got Ubuntu 10.04 running on my new Lenovo X201 (had to disable KMS, originally it had been unable to boot to the GUI due to some issues with the integrated graphics

Everything is working now, except wifi. When I boot up, I can ping sites and stuff... very briefly. Then wireless fails... any pings just hang and I eventually get no response. Other hosts on the network run fine... my roomate is surfing right now via the wireless (we're using WPA2), and the xbox is connected via ehternet and it gets a connection fine as well, so I don't think it's an issue with the router or modem.

I'm not sure exactly what card I have, Thinkwiki seems to indicate both the card models for this laptop use the same driver:
[http://www.thinkwiki.org/wiki/Category:X201](http://www.thinkwiki.org/wiki/Category:X201)

Below is the output from lspci:
```
sigma@wopr:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

The output from iwconfig:
```
sigma@wopr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"fleshlight"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:21:29:92:5D:CB   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/100  Signal level=-84 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Output for lsmod:
```
sigma@wopr:~$ lsmod
Module                  Size  Used by
michael_mic             2164  8 
arc4                    1473  4 
aesni_intel            12337  153 
cryptd                  8116  1 aesni_intel
aes_x86_64              7912  1 aesni_intel
aes_generic            27607  2 aesni_intel,aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
dm_crypt               13043  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
thinkpad_acpi          79335  0 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_dummy           1782  0 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
led_class               3732  1 thinkpad_acpi
nvram                   7639  1 thinkpad_acpi
psmouse                64608  0 
serio_raw               4918  0 
r8192se_pci           486547  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i915                  317872  0 
drm_kms_helper         30742  1 i915
ahci                   37646  2 
intel_agp              29225  2 i915
drm                   198770  2 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
e1000e                136205  0 

```

dmesg output (unplugged the ethernet cord and pinged google.com, then ran dmesg):
```
[ 2839.787201] FW Scan long time without stop, stop hw scan
[ 2839.788212] <-----------rtl8192se_check_hw_scan()
[ 2959.573227] ----------->rtl8192se_check_hw_scan()
[ 2959.573231] FW Scan long time without stop, stop hw scan
[ 2959.574240] <-----------rtl8192se_check_hw_scan()
[ 3079.359436] ----------->rtl8192se_check_hw_scan()
[ 3079.359440] FW Scan long time without stop, stop hw scan
[ 3079.360450] <-----------rtl8192se_check_hw_scan()
[ 3199.143454] ----------->rtl8192se_check_hw_scan()
[ 3199.143458] FW Scan long time without stop, stop hw scan
[ 3199.144466] <-----------rtl8192se_check_hw_scan()
[ 3318.935426] ----------->rtl8192se_check_hw_scan()
[ 3318.935430] FW Scan long time without stop, stop hw scan
[ 3318.936439] <-----------rtl8192se_check_hw_scan()
[ 3438.712810] ----------->rtl8192se_check_hw_scan()
[ 3438.712814] FW Scan long time without stop, stop hw scan
[ 3438.713823] <-----------rtl8192se_check_hw_scan()
[ 3558.496441] ----------->rtl8192se_check_hw_scan()
[ 3558.496446] FW Scan long time without stop, stop hw scan
[ 3558.497455] <-----------rtl8192se_check_hw_scan()
[ 3678.281313] ----------->rtl8192se_check_hw_scan()
[ 3678.281318] FW Scan long time without stop, stop hw scan
[ 3678.282331] <-----------rtl8192se_check_hw_scan()
[ 3798.066251] ----------->rtl8192se_check_hw_scan()
[ 3798.066255] FW Scan long time without stop, stop hw scan
[ 3798.067265] <-----------rtl8192se_check_hw_scan()
[ 3850.094338] e1000e: eth0 NIC Link is Down

```

(That was snipped significantly, can post more if needed)

If anyone has any ideas what could be wrong, I'd appreciate any feedback!

---

### Post by gregnorc on 2010-05-02
I now cannot connect to any networks at all... I can see them, I can attempt to join, but the connection fails.

I'm trying to find drivers to update but with no luck, I found this page but the links for my chipset (rtl8191SE-VA2) don't work:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2262](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2262)

---

