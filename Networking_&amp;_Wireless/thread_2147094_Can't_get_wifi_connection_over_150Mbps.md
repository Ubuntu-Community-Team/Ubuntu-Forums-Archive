---
title: "Can't get wifi connection over 150Mbps"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by diegosolo on 2013-05-20
[FONT=arial][COLOR=#333333]I'm trying to connect to my new router at a speed of 300Mbps. My new wireless router accepts 300Mbps in 2.4Mhz and 450Mbps in 5Mhz. I'm testing right next to the router and I get 150Mbps top.[/COLOR]
[COLOR=#333333]I'm pretty aware of what 150/300/450Mbps means in real life, but the thing is that connecting to 150Mbps won't give anything above 8MBps when transfering files over the network.[/COLOR]
[COLOR=#333333]I tested all the same in Windows 7 and I can get links of 300Mbps (fluctuating, but very stable at that speed), whit 22MBps for file transfers.[/COLOR]
[COLOR=#333333]Is there something I can do? Thank you!

Adding info requested by "varunendra" (thank you!!!):[/COLOR][/FONT]


[B]uname -mr
[/B]```
3.5.0-28-generic i686
```
[B]
lsb_release -d
[/B]```
Description:    Ubuntu 12.10
```
[B]
lspci -nnk | grep -iA2 net
[/B]```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
    Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3624]
    Kernel driver in use: r8169
```
[B]
lsmod
[/B]```
Module                  Size  Used by
ipt_MASQUERADE         12664  0 
xt_state               12515  0 
ipt_REJECT             12486  0 
xt_tcpudp              12532  0 
nf_nat_h323            12810  0 
nf_conntrack_h323      51811  1 nf_nat_h323
nf_nat_pptp            12537  0 
nf_conntrack_pptp      13554  1 nf_nat_pptp
nf_conntrack_proto_gre    13581  1 nf_conntrack_pptp
nf_nat_proto_gre       12672  1 nf_nat_pptp
nf_nat_tftp            12421  0 
nf_conntrack_tftp      12818  1 nf_nat_tftp
nf_nat_sip             16946  0 
nf_conntrack_sip       24511  1 nf_nat_sip
nf_nat_irc             12543  0 
nf_conntrack_irc       13113  1 nf_nat_irc
nf_nat_ftp             12549  0 
nf_conntrack_ftp       13107  1 nf_nat_ftp
iptable_nat            12978  0 
nf_nat                 20317  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      14081  3 iptable_nat,nf_nat
nf_conntrack           66308  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
snd_hrtimer            12649  1 
vesafb                 13478  1 
coretemp               13169  0 
arc4                   12474  2 
joydev                 17162  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
dm_multipath           22403  0 
iptable_filter         12707  1 
scsi_dh                14214  1 dm_multipath
xt_owner               12451  12 
ip_tables              17792  2 iptable_nat,iptable_filter
x_tables               21936  8 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,iptable_filter,xt_owner,ip_tables
snd_hda_codec_hdmi     31457  1 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
ir_lirc_codec          12740  0 
lirc_dev               18671  1 ir_lirc_codec
microcode              18210  0 
ir_mce_kbd_decoder     12636  0 
ir_sanyo_decoder       12466  0 
snd_hda_codec_idt      59762  1 
ir_sony_decoder        12463  0 
ir_jvc_decoder         12460  0 
psmouse                84878  0 
serio_raw              13032  0 
ir_rc6_decoder         12460  0 
ir_rc5_decoder         12460  0 
ir_nec_decoder         12460  0 
lpc_ich                16926  0 
fglrx                2917043  243 
snd_hda_intel          32516  5 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_seq_midi           13133  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  17987  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
rc_rc6_mce             12455  0 
snd_seq                51281  3 snd_seq_midi,snd_seq_midi_event
ene_ir                 17908  0 
jmb38x_ms              17178  0 
rc_core                21267  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
rfcomm                 37277  12 
snd_timer              24412  3 snd_hrtimer,snd_pcm,snd_seq
memstick               15843  1 jmb38x_ms
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             31969  0 
bnep                   17708  2 
iwlwifi               348525  0 
wmi                    18591  1 hp_wmi
snd                    62146  21 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18895  0 
bluetooth             183270  22 btusb,rfcomm,bnep
ppdev                  12818  0 
mac80211              461261  1 iwlwifi
hp_accel               25729  0 
lis3lv02d              19230  1 hp_accel
input_polldev          13649  1 lis3lv02d
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
cfg80211              175574  2 iwlwifi,mac80211
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
binfmt_misc            17261  1 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
ahci                   25497  3 
libahci                25938  1 ahci
r8169                  55977  0 
firewire_ohci          35522  0 
sdhci_pci              18156  0 
sdhci                  27831  1 sdhci_pci
firewire_core          57493  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
dm_raid45              75358  0 
xor                    26091  1 dm_raid45
dm_mirror              21666  0 
dm_region_hash         16013  1 dm_mirror
dm_log                 18138  3 dm_raid45,dm_mirror,dm_region_hash
```
[B]
iwconfig
[/B]```
wlan0     IEEE 802.11abgn  ESSID:"Diegosolo5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: A0:F3:C1:8F:93:6C   
          Bit Rate=150 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:269  Invalid misc:1714   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```
[B]
ifconfig
[/B]```
eth0      Link encap:Ethernet  HWaddr 00:26:9e:10:af:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:792325 (792.3 KB)  TX bytes:792325 (792.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:82:f1:3a  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe82:f13a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2302128 errors:0 dropped:144 overruns:0 frame:0
          TX packets:680971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3308302832 (3.3 GB)  TX bytes:69550481 (69.5 MB)
```

PS: sorry about the font. I got that after an error in the submission.

---

### Post by varunendra on 2013-05-20
Hi, and Welcome to the forums diegosolo! :)

Let us take a look at what device and driver you are using, then see if we can do anything to improve the speed.

Please open a terminal (Ctrl + Alt + T), run the following commands (one at a time, you may copy-paste to avoid typos), and post back their outputs here :
```
uname -mr
lsb_release -d
lspci -nnk | grep -iA2 net
lsmod
iwconfig
ifconfig
```


**PS:**
Please use default fonts unless necessary. It is more readable :)

---

### Post by Sketchworks on 2013-05-20
same deal heres my output...sketch@TimelineX:~$ uname -mr3.8.0-21-generic x86_64
sketch@TimelineX:~$ lsb_release -d
Description:	Ubuntu 13.04
sketch@TimelineX:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:040e]
	Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 35)
	Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1101]
	Kernel driver in use: iwlwifi
sketch@TimelineX:~$ lsmod
Module                  Size  Used by
btusb                  22474  0 
parport_pc             28152  0 
pci_stub               12622  1 
ppdev                  17073  0 
vboxpci                23194  0 
vboxnetadp             25670  0 
bnep                   18036  2 
rfcomm                 42641  4 
bluetooth             228619  11 bnep,btusb,rfcomm
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
arc4                   12615  2 
uvcvideo               80847  0 
iwldvm                241834  0 
snd_hda_intel          39619  3 
videobuf2_vmalloc      13056  1 uvcvideo
mac80211              606457  1 iwldvm
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
ums_realtek            17949  0 
videobuf2_core         40513  1 uvcvideo
snd_hwdep              13602  1 snd_hda_codec
usb_storage            57204  1 ums_realtek
videodev              129260  2 uvcvideo,videobuf2_core
kvm_intel             132891  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm                   443165  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
snd_rawmidi            30180  1 snd_seq_midi
joydev                 17377  0 
aesni_intel            55399  1 
aes_x86_64             17255  1 aesni_intel
iwlwifi               173477  1 iwldvm
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  600351  7 
snd_timer              29425  2 snd_pcm,snd_seq
acer_wmi               32467  0 
sparse_keymap          13890  1 acer_wmi
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
drm_kms_helper         49394  1 i915
drm                   286313  3 i915,drm_kms_helper
mei                    41158  0 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           13413  1 i915
wmi                    19070  1 acer_wmi
psmouse                95870  0 
coretemp               13355  0 
intel_ips              17978  0 
soundcore              12680  1 snd
serio_raw              13215  0 
lpc_ich                17061  0 
lp                     17759  0 
video                  19390  2 i915,acer_wmi
parport                46345  3 lp,ppdev,parport_pc
mac_hid                13205  0 
microcode              22881  0 
ahci                   25731  2 
libahci                31364  1 ahci
atl1c                  41071  0 
sketch@TimelineX:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"JJWZP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:B8:D7:CC:D5   
          Bit Rate=117 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:833  Invalid misc:207   Missed beacon:0


sketch@TimelineX:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:6a:8a:3e:f1:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:206256 (206.2 KB)  TX bytes:206256 (206.2 KB)


wlan0     Link encap:Ethernet  HWaddr 00:24:d7:00:45:d0  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d7ff:fe00:45d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16592491 (16.5 MB)  TX bytes:32191654 (32.1 MB)

---

### Post by varunendra on 2013-05-20
Oh, sorry, I forgot to include the more important comment in my 'PS', "Please use 'Code' tags to post command outputs. It preserves their formatting and makes them look less scary.." :D
Please follow the "Code Tags example" link in my signature to see how to use it. (oh, and then edit your above post to wrap the code part within 'Code' tags, it's really scaring me.. ;))

Anyway, the important stuff -
> **Sketchworks said:**
> 
sketch@TimelineX:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 35)
	Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1101]
	Kernel driver in use: **[COLOR="#800000"]iwlwifi[/COLOR]**

Everything looks normal to me, except that this driver (iwlwifi) is often reported to have problem with N-channel (if I remember correctly). Not only this one, most of the linux wireless drivers I know of have difficulty with N-channel. Disheartening, I know, but this is what I have gathered so far, and I wish I'm wrong.

Unless someone else can offer a better suggestion, please try -
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi swcrypto=1
```
Does it make any difference? This is a temporary change and will be lost at reboot. We can make it permanent if it helps.

**PS:**
Don't forget to edit the previous post to wrap the output in 'Code' tags, you'll like it ! :)

**EDIT:**
Just realized that I am answering two different users at the same time.
However, since both of you are using the same driver (even though different kernel and OS versions), and have same complaints, what I suggested above is all I have to suggest. But please, do post if it makes any difference or not, as maybe someone else would be able to offer a better help if that doesn't help.

Oh, and the 'Code' tags part also goes the same for both of you :P

---

### Post by diegosolo on 2013-05-21
Sorry, but nothing has changed. I'm still stuck at 150Mbps. But thank you anyway!

---

### Post by varunendra on 2013-05-21
Already suspected that :(

However, there is one more thing in 'Your' output that can be altered hoping for a miracle -
> **diegosolo said:**
> 
[B]iwconfig
[/B]```
wlan0     IEEE 802.11abgn  ESSID:"Diegosolo5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: A0:F3:C1:8F:93:6C   
          Bit Rate=150 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:269  Invalid misc:1714   Missed beacon:0
```
Try turning the power management off -
```
sudo iwconfig wlan0 power off
```
Then check if it is correctly turned off -
```
iwconfig
```
It should show up as "off" now. Does that make any difference? I'd try to search if someone has reported a better speed (if the time allows), but for now, I'm out of ammo !

---

### Post by toothandnail on 2013-05-21
This sounds pretty much like the problem I've hit. Didn't find this before I started this thread: [http://ubuntuforums.org/showthread.php?t=2147017](http://ubuntuforums.org/showthread.php?t=2147017)

In my case, I'm limited to 150 mbps, but that is down to the router firmware. Under any of the 3.7.x kernels, I got consistent 150 mbps connects to my router. Under any of the 3.8.x kernels, I couldn't get anything better than 72.2 mbps. 

I normally use Arch, which has just moved on to the 3.9.3 kernel. My connect speed went straight back to 150 mbps, and, as of this morning (updated firmware for the WAG320N) I'm getting consistent 300 mbps connects.

Given the results I've seen, I suspect you're not going to solve the problem unless you can either go to a more recent kernel, or backdate to one of the the 3.7.x kernels.

I'm not familiar enough with Ubuntu to know how easy or possible either of those options is.....

Paul.

---

### Post by varunendra on 2013-05-21
> **toothandnail said:**
> This sounds pretty much like the problem I've hit. Didn't find this before I started this thread: [http://ubuntuforums.org/showthread.php?t=2147017](http://ubuntuforums.org/showthread.php?t=2147017)

In my case, I'm limited to 150 mbps, but that is down to the router firmware. Under any of the 3.7.x kernels, I got consistent 150 mbps connects to my router. Under any of the 3.8.x kernels, I couldn't get anything better than 72.2 mbps.
Yes, given the abnormal amount and nature of problems, the 3.8x series kernel is evidently a hell of wireless issues. We are facing the most unexpected regressions in almost all of the native wireless drivers, and at the same time, the proprietary ones are failing due to critical changes in the kernel code.

Anyway, if you wish, you can directly download the other (supported) version of kernels from kernel-ppa mainline : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Just download the .deb package of the desired kernel, and double click to install (or dpkg -i ...).

Let us know if you do and if it really helps. Reportedly, it does.

---

### Post by toothandnail on 2013-05-21
> **varunendra said:**
> Yes, given the abnormal amount and nature of problems, the 3.8x series kernel is evidently a hell of wireless issues. We are facing the most unexpected regressions in almost all of the native wireless drivers, and at the same time, the proprietary ones are failing due to critical changes in the kernel code.

Anyway, if you wish, you can directly download the other (supported) version of kernels from kernel-ppa mainline : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Just download the .deb package of the desired kernel, and double click to install (or dpkg -i ...).

Let us know if you do and if it really helps. Reportedly, it does.

:) Thanks for that. Used the link you provided, downloaded and installed the 3.9.2 kernel and installed it. Just restarted the laptop and I'm getting 300 mbps connnection to the router again.

Useful information also - I've got lots to learn about Ubunut....

Paul.

---

### Post by varunendra on 2013-05-22
> **toothandnail said:**
> Used the link you provided, downloaded and installed the 3.9.2 kernel and installed it. Just restarted the laptop and I'm getting 300 mbps connnection to the router again..

Thanks to you too, that's a great confirmation for us solution hunters! :)

I'm sure this particular kernel is going to be our most frequent suggestion for a few days..!

---

### Post by diegosolo on 2013-05-22
Sorry to ruin the party guys, but I've been trying the kernel versions thing with no good results. Seems to be a solution for some cases only. I updated to Ubuntu 13.04 with 72Mbps top connections. Upgraded manually to kernel 3.9.2 also with no luck (had to go back to 3.8 because ATI legacy drivers don't work in 3.9). In this last case, connections were back to 150Mbps. I guess its something just to try ut.

Thank you anyway for all your help!

---

### Post by varunendra on 2013-05-23
> **diegosolo said:**
> Sorry to ruin the party guys, but I've been trying the kernel versions thing with no good results.

Hmm.. that only proves to me that the driver alone is not the deciding factor for the speed, which is somewhat obvious. But since changing kernel alone was enough for toothandnail (as far as he told us) to improve the speeds, it definitely is a helping factor, if not the only one.

Did you try changing the power management on wireless from "on" to "off" ? Did you check whether it sticked or not *(iwconfig)*?
Please show us the current status of-
```
iwconfig
ifconfig
grep -iR [a-z0-9] /sys/module/iwlwifi/parameters/
sudo iwlist wlan0 scan
```

Also, it is recommended to use pure WPA2-PSK mode encryption in the router, and especially not WPA/WPA2 mixed mode.

---

### Post by diegosolo on 2013-05-23
Turning power management off didn't work. Here is the info you requested:

**iwconfig**
```
wlan0     IEEE 802.11abgn  ESSID:"Diegosolo5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: A0:F3:C1:8F:93:6C   
          Bit Rate=6 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:87   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:26:9e:10:af:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87760 (87.7 KB)  TX bytes:87760 (87.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1e:65:82:f1:3a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe82:f13a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14007447 (14.0 MB)  TX bytes:940118 (940.1 KB)

```

**grep -iR [a-z0-9] /sys/module/iwlwifi/parameters/**
```
/sys/module/iwlwifi/parameters/5ghz_disable:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/auto_agg:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:1
/sys/module/iwlwifi/parameters/bt_ch_inhibition:Y
/sys/module/iwlwifi/parameters/fw_restart:1
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/plcp_check:Y
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0

```

**sudo iwlist wlan0 scan**
```
wlan0     Scan completed :
          Cell 01 - Address: A0:F3:C1:8F:93:6C
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Diegosolo5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d5fbe435d
                    Extra: Last beacon: 274028ms ago
                    IE: Unknown: 000A446965676F736F6C6F35
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 074C4152202401112801112C01113001113401183801183C01184001186401186801186C01187001187401187801187C01188001188401188801188C011895011E99011E9D011EA1011EA5011E00
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEF011BFFFFFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF011BFFFFFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D16240D0000000000000000000000000000000000000000
                    IE: Unknown: 3416240D0000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 02 - Address: A0:F3:C1:8F:93:6C
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d703c203b
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 050400010000
                    IE: Unknown: 074C4152202401112801112C01113001113401183801183C01184001186401186801186C01187001187401187801187C01188001188401188801188C011895011E99011E9D011EA1011EA5011E00
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEF011BFFFFFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D16240D0000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: 00:23:CD:1E:C9:F0
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"QUE MALA SEGURIDAD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003debf392ea
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0012515545204D414C4120534547555249444144
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1604051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD880050F204104A0001101044000101103B00010310470010000000000000100000000023CD1EC9F01021000754502D4C494E4B10230009544C2D57523734304E10240003312E3010420003312E301054000800060050F204000110110020576972656C657373204C697465204E20526F7574657220544C2D57523734304E100800020086103C000101
          Cell 04 - Address: 00:13:33:9A:87:4A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TODOPC_WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007d39fcafa7
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000B544F444F50435F57494649
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010630412531019200612280013339A87481021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120

```

Thank you!

---

### Post by diegosolo on 2013-05-23
Oh! I forgot. I'm using WPA2-PSK security with AES encription.

---

### Post by varunendra on 2013-05-24
> **diegosolo said:**
> **iwconfig**
```
wlan0     IEEE 802.11abgn  ESSID:"Diegosolo5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: A0:F3:C1:8F:93:6C   
          **Bit Rate=[COLOR="#FF0000"]6 Mb/s[/COLOR] **  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:87   Missed beacon:0

```
6 Mb/s ?? Wasn't it supposed to be 150 Mb/s ?
How about setting it to be fixed at 150 Mb/s rather than auto (which it currently seems to be set at) -
```
sudo iwconfig wlan0 rate 150M
```
..or a slightly lower one that is supported.

Speaking of 'supported' speeds, your **iwlist scan** output doesn't show anything above 54 Mb/s, but to be honest, I am an absolute noob at understanding its output, and not sure how else to verify the supported speeds if higher ones exist.

(I'd be very grateful if someone can explain that to me regarding N-channel speeds.)

> **grep -iR [a-z0-9] /sys/module/iwlwifi/parameters/**
```
/sys/module/iwlwifi/parameters/**[COLOR="#B22222"]5ghz_disable:[/COLOR]**N
/sys/module/iwlwifi/parameters/swcrypto:0
....

```
That ^^ is a new parameter in iwlwifi driver, doesn't exist in the version on my system (12.04.2). But it seems that it is meant to disable the 5ghz channel which is supposed to provide higher speed. I'm not sure if the 2.4ghz channels can provide the 300mbps speed, so can't say if it may be worth messing with this parameter and go about doing changes in the router itself.

A quote from [this post]("http://ubuntuforums.org/showthread.php?t=2121980&p=12542911#post12542911") by bellaseem may be relevant here (not sure where he quoted it from) :
> "The fact that you have strong signal but not at least the 65mbps data rate suggests that your client is limiting itself to G mode operation for some reason. The most common reasons are:

[LIST=1]
[*]The router is not set to do N on its 2.4GHz radio.
[*]Your router or your client is configured to use WEP or TKIP (WPA1) encryption, not AES-CCMP (WPA2). WEP and TKIP, as implemented by most Wi-Fi gear, is not fast enough to keep up with N rates, so the 802.11n spec disallows using those modes with 802.11n connections. To get N rates, you have to use AES-CCMP or no encryption.
[*]Your AP (or I suppose your client) does not have QoS (802.11e, WMM) enabled. The 802.11n spec requires QoS."
[/LIST]


So make sure the last point is true in your case.

---

