---
title: "Ralink RT3070STA won't install :(    (help me chili555)"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by m-momr on 2011-07-23
Hi, been reading alot here and i think my main problem is that the drivers from ralink think i have an other card. This is why

The adapter is the Rokland N3
I have opened my device and there is a RT3070L chip on it.

lsusb:
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

at the end of make it gives me alot of output about rt5370sta

```
/home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:8543: warning: the frame size of 1040 bytes is larger than 1024 bytes
  LD [M]  /home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  LD [M]  /home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic'
cp -f /home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko /tftpboot

```

in the Makefile it says:
```
CHIPSET = 5370
```
if i try to change it to 3070 it won't compile.

Any help would be greatly appreciated

EDIT:

```
root@administrator-thor:/home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO# make install
make -C /home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-30-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.35-30-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-30-generic
make[1]: Leaving directory `/home/marius/Downloads/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'

```

even make install gives info about installing rt5370sta.ko 

where other guides i see here gives output about install rt3070sta.ko

i am really confused :|

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in a terminal please
```
lsmod
```
```
iwconfig
```
```
rfkill list All
```
and post the results here.
Thank you

---

### Post by pedal2metal on 2011-07-23
Hi, 


Regarding your issue, I got rid of that error by doing this:

cd to the directory where the uncompressed driver files are, then edit os/linux/usb_main_dev.c
add one line &#8220;MODULE_LICENSE(&#8220;GPL&#8221;);&#8221; 

(you may add it below the "MODULE_DESCRIPTION..." line)

That was it for me.

---

### Post by m-momr on 2011-07-23
I have blacklisted:

blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt2870sta

so I have to modprobe rt2870sta to show you the output of iwconfig, which then is:

```
root@administrator-thor:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"linky2-5"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: C0:C1:C0:0B:07:BE   
          Bit Rate=120 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

virbr0    no wireless extensions.

wlan1     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:-81 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@administrator-thor:~# 
```

also the rt2870sta for my card, but only on 802.11g and not 802.11n.

lsmod:
```
Module                  Size  Used by
rt2870sta             446110  1 
crc_ccitt               1699  1 rt2870sta
cryptd                  8140  0 
aes_x86_64              7936  3 
aes_generic            27631  1 aes_x86_64
ip6table_filter         1719  0 
ip6_tables             20633  1 ip6table_filter
xt_conntrack            2830  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_conexant    37695  1 
binfmt_misc             7984  1 
rfcomm                 40787  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
ipt_MASQUERADE          1919  3 
iptable_nat             4593  1 
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13143  5 iptable_nat,nf_nat
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
xt_state                1386  1 
nf_conntrack           75238  6 xt_conntrack,ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2440  2 
xt_tcpudp               2627  5 
iptable_filter          1778  1 
ip_tables              19171  2 iptable_nat,iptable_filter
x_tables               24423  10 ip6table_filter,ip6_tables,xt_conntrack,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,ip_tables
bridge                 79700  0 
stp                     2195  1 bridge
kvm_intel              49183  0 
kvm                   299465  1 kvm_intel
joydev                 11395  0 
usbhid                 42030  0 
hid                    84710  1 usbhid
snd_hda_intel          26147  2 
snd_hda_codec         100919  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
arc4                    1497  2 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
btusb                  12961  2 
snd_rawmidi            22207  1 snd_seq_midi
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
iwlagn                202800  0 
pcmcia                 40944  0 
i915                  335073  4 
thinkpad_acpi          78535  0 
iwlcore               146875  1 iwlagn
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                10022  0 
tpm                    16019  1 tpm_tis
tpm_bios                6426  1 tpm
drm_kms_helper         32836  1 i915
uvcvideo               62411  0 
drm                   206198  4 i915,drm_kms_helper
nvram                   7990  1 thinkpad_acpi
mac80211              267099  2 iwlagn,iwlcore
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
snd                    64277  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
psmouse                62080  0 
r852                   11348  0 
sm_common               4441  1 r852
nand                   38430  2 r852,sm_common
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
cfg80211              170581  3 iwlagn,iwlcore,mac80211
yenta_socket           24279  0 
pcmcia_rsrc            10357  1 yenta_socket
serio_raw               4910  0 
mtd                    21479  2 sm_common,nand
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
intel_agp              32334  2 i915
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
sdhci_pci               8115  0 
ahci                   22370  3 
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
e1000e                151819  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  2 thinkpad_acpi,sdhci
libahci                26148  1 ahci
```

```
root@administrator-thor:~# rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
root@administrator-thor:~# 

```

---

### Post by pedal2metal on 2011-07-23
The above will let you compile without the license error. Regarding your confusion as of the 5370 instead of the 3070 references, that's exactly why I am here too...same confusion, I am also trying to install my 3070 usb chipset drivers properly.

---

### Post by m-momr on 2011-07-23
guess i am looking for a way to tell the compiler/force it to use 3070 and not 5370

---

### Post by wildmanne39 on 2011-07-23
Hi, I believe you can use the rt2800usb driver but the rt2870sta needs to be black listed, and you would have to get rid of the drivers you complied. I do not think you will have n speed with the rt2800 usb driver though. I am going to ask chili555 to take a look but I do not think he is on right now.

---

### Post by chili555 on 2011-07-23
For the information of all you driver genies, the driver rt2870sta claims your device, as does rt2800usb and rt5370sta:> ID [COLOR="Red"]148f:3070[/COLOR] Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter```
$ modinfo rt5370sta | grep 3070
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
``````
$ modinfo rt2870sta | grep 3070
description:    RT2870/RT3070 Wireless Lan Linux Driver
firmware:       rt3070.bin
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Unless you have some evidence that rt2870sta is not doing the job and rt5370sta will do the job, I think you are asking for trouble by compiling *another* driver.

I think your problem is two wireless cards:> wlan0     IEEE 802.11abgn  ESSID:"linky2-5"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: C0:C1:C0:0B:07:BE   
          Bit Rate=120 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

virbr0    no wireless extensions.

wlan1     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:-81 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Network Manager connects one and quits for the day.

What are you trying to accomplish with two cards?

Sorry I was away; Mrs. Chili made me get dressed up and go out for steak.

---

### Post by chili555 on 2011-07-23
> **pedal2metal said:**
> The above will let you compile without the license error. Regarding your confusion as of the 5370 instead of the 3070 references, that's exactly why I am here too...same confusion, I am also trying to install my 3070 usb chipset drivers properly.What's stamped on the chip and what lsusb says often are no clue as to the driver. The usb.id such as 148f:3070 tells all. Most of the time, the device in my example is claimed by rt2870sta and rt2800usb. When rt2800usb is blacklisted, they work perfectly. Compiling a Ralink driver never helps, because the conflict remains. However, many here report that compiling a newer version of rt2870sta gets N speeds.

Here and on the Mint forum, I bet I type 'blacklist rt2800usb' six or eight times a *week*!

---

### Post by m-momr on 2011-07-23
I got the new card to improve range at my school, there are some places where it's hard to connect, and stay connected.

My card works with rt2870sta, but its acting a little wierd.
It can't find my network on channel 13, and it won't connect to N networks.

other people on the forums get a rt3070sta.ko from the make.
I get a rt5370sta.ko, why? where is that defined?

EDIT: thanks for taking the time to reply :)

---

### Post by chili555 on 2011-07-23
> other people on the forums get a rt3070sta.ko from the make.rt3070sta is old in Ubuntu terms; it was merged into rt2870sta:```
$ modinfo rt2870sta 
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
[COLOR="Red"]description:    RT2870/RT3070 Wireless Lan Linux Driver[/COLOR]
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin

```I guess you could find the old RT3070 package laying around somewhere, but why? rt2870sta in the default kernel is slightly better and rt5370sta is a bit better yet.> I get a rt5370sta.ko, why? where is that defined?It's defined somewhere in the file you downloaded and compiled. It could be called anything; what's relevant is the usb.ids it claims.

Did you get rt5370sta to compile correctly? Have you tried it?```
sudo ifconfig wlan1 down
sudo rmmod -f rt2870sta
sudo modprobe rt5370sta
sudo ifconfig wlan1 up
```Network Manager will still have trouble with two cards. You might have better luck if you blacklisted the driver for the internal card, or at least:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
```I will be very surprised if you get better results from a USB device than an Intel iwlagn. I learn something new every day...

---

### Post by m-momr on 2011-07-23
Ok, WOW, i have no idea why it works now.
Thanks a lot :D

All i did was reboot, build the latest driver , make, make install, and "modprobe rt5370sta"

now it works at 72mbit/s.
I still dont understand why it won't go to 150mbit/s like my intel at 2.5 ghz N.

Right now i am one floor&20 meters away from my accesspoint, and the intel has 54/100 signal quality, and my usb unit has 100/100.

Thanks again.

---

### Post by wildmanne39 on 2011-07-23
Hi, I am glad chili555 was able to get your problems sorted out,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

