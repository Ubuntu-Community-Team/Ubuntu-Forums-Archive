---
title: "Wireless bandwidth halved when using Ubuntu 11.10"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by starfleetjustin on 2012-03-20
Greetings,

I've only seen one thread about this topic (which had no answers), and I couldn't find any other threads about it ...

**In Ubuntu 11.10, on my Toshiba laptop (I can provide the specifics about the wireless card if needed, but I'm pretty sure I'm using the latest driver), my bandwidth is approximately half of what it is in Windows 7.**

My average bandwidth is 15-16mbps in Windows, and it peaks at 6mbps in Ubuntu (tested over a week or more with proven test sites, so I know it's not a bad hop or a poor server).

This is still excellent performance, but I'd love to know where that other 10mbps went. %)

I've followed various steps I've found around the net, but nothing has resolved this issue.

Thank you for any help, and forgive me if this has been posted elsewhere or if I forgot any pertinent info.

---

### Post by wildmanne39 on 2012-03-20
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
lsusb
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by starfleetjustin on 2012-03-20
Awesome, thanks so much for your help! Here are the outputs in order of what you requested:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Dartagnan 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 i686 i386 GNU/Linux

```

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
	Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fc50]
	Kernel driver in use: atl1c

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Athos"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 68:7F:74:87:96:FD   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1873   Missed beacon:0

```

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52460  1 
binfmt_misc            17292  1 
arc4                   12473  2 
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                63474  0 
serio_raw              12990  0 
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13658  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8192ce             127361  0 
rtlwifi               107538  1 rtl8192ce
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac80211              393421  2 rtl8192ce,rtlwifi
cfg80211              172427  2 rtlwifi,mac80211
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  3 
libahci                25761  1 ahci
i915                  509554  3 
wmi                    18744  0 
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
atl1c                  36638  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

```

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 001 Device 004: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 001 Device 005: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36

```

---

### Post by wildmanne39 on 2012-03-20
Hi, if you are getting that kind of speed with this driver you are doing good, about six weeks ago people were having very slow speeds with this driver.

I have read that the issue is resolved in 12.04 that comes out in April.

You can try this:

Set your wireless settings to match the two screenshots.

---

### Post by MasterGamerJK on 2012-03-21
One of the best wifi cards out there: 

[http://hakshop.myshopify.com/collections/frontpage/products/black-usb-wifi-adapter-with-5dbi-antenna-realtek-8187l-chipset](http://hakshop.myshopify.com/collections/frontpage/products/black-usb-wifi-adapter-with-5dbi-antenna-realtek-8187l-chipset)

You can event change the country code to double the transmission power.....if you don't mind disobeying the FCC :P

---

### Post by starfleetjustin on 2012-03-21
I'll keep that in mind, MasterGamer! Thanks for the link.

I tried those settings, wildmanne, and it didn't restore my bandwidth.

I also initially had super slow speeds until one of the various tweaks I found fixed it, so I'll just be happy with what I've got until the next release of Ubuntu.

Thanks again for your help.

---

### Post by TBABill on 2012-03-21
I have seen similar claims of slow wireless speed that are specific to 11.10 in the forum and at derivative forums, such as Mint. I experienced the exact same thing on my Atheros AR9287 so I tried Mint 12 Gnome, same results. However, it was a bit better in Mint 12 KDE, but it still reverted back to the slow speeds periodically. From there I decided to try another derivative of Ubuntu, Ultimate Edition 3.2. Amazing wireless speed! I wish I knew what they did to resolve the issue because all 3 distros have the same base system and kernel. UE even includes Unity.
 
12.04 does not suffer from the issue either. It's very strange and I have yet to pinpoint the root cause of it, but it's not a driver issue because it affects users across different brands of hardware and different drivers. Default configurations on each distro with different results on the same hardware, yet UE blazes to nearly 500Kbps beyond what my ISP claims my service level is. My service is 12Mbps down/1Mbps up and I get 12.4-12.5 down and 1.5 up with UE, while stuck with 1-2Mbps down / 500Kbps up with Ubuntu and Mint. Occasionally Mint KDE got up to 7-8Mbps down, but that was very inconsistent. I did not try Kubuntu to compare.
 
Hopefully someone will come along with similar experiences and a fix they can publicize soon.

---

