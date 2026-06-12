---
title: "Hey guys! =]"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by walla321123 on 2011-05-16
Hey guys! I got a problem with some pages on the internet, I'm running Ubuntu 11.04 (never used Ubuntu before)and when I first installed Ubuntu 11.04 It didn't find the wireless card (Im on a laptop, Hp). 

Anyway, fixed that, but now some pages load super slow, like hotmail, facebook (dont even open most of the times) while others like youtube and google run really fast. I checked the internet speed at speedtest.net and it was good. What might be the problem? 

I am thankful for the help guys because I intend to keep going with Ubuntu, what should i write in the terminal for you to better get a clue of the problem? 

Thanks in advance! =]

---

### Post by linuxman94 on 2011-05-16
Could you give the results of these commands?

```
ifconfig
iwconfig
sudo lshw (just the part abut networking)
lspci (again, just the networking part)

```

---

### Post by s.fox on 2011-05-16
Threads merged and moved to [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by linuxman94 on 2011-05-16
Can you remove the duplicate part in the original post?

---

### Post by s.fox on 2011-05-16
> **linuxman94 said:**
> Can you remove the duplicate part in the original post?

I see no duplicate part... :-\"

---

### Post by walla321123 on 2011-05-16
a@a-pc:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:81:4b:ef:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17

---

### Post by walla321123 on 2011-05-16
a@a-pc:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:81:4b:ef:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:21:00:bc:dd:04  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::221:ff:febc:dd04/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:9186 errors:0 dropped:0 overruns:0 frame:2274 
          TX packets:7274 errors:17 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:12762472 (12.7 MB)  TX bytes:864620 (864.6 KB) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5360 (5.3 KB)  TX bytes:5360 (5.3 KB) 

a@a-pc:~$

---

### Post by josephmills on 2011-05-16
could we also see a ```
lspci -nn
```and```
sudo lshw -C network
```thanks

---

### Post by walla321123 on 2011-05-16
a@a-pc:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:201  Noise level:199 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 

______________________________________________________________



 *-network 
                description: Wireless interface 
                product: BCM4312 802.11b/g LP-PHY 
                vendor: Broadcom Corporation 
                physical id: 0 
                bus info: pci@0000:02:00.0 
                logical name: eth1 
                version: 01 
                serial: 00:21:00:bc:dd:04 
                width: 64 bits 
                clock: 33MHz 
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.101 latency=0 multicast=yes wireless=IEEE 802.11bg 
                resources: irq:17 memory:98700000-98703fff 
        *-pci:2 
             description: PCI bridge 
             product: 82801I (ICH9 Family) PCI Express Port 3 
             vendor: Intel Corporation 
             physical id: 1c.2 
             bus info: pci@0000:00:1c.2 
             version: 03 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:42 ioport:5000(size=8192) memory:94000000-97ffffff i

______________________________________________________________


02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) 
85:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller

---

### Post by josephmills on 2011-05-16
could we see a ```
dmesg | grep wl
``` thanks

---

### Post by walla321123 on 2011-05-16
a@a-pc:~$ dmesg | grep wl
[    0.000000] DMI: Hewlett-Packard HP Compaq 6730s/30E8, BIOS 68PZU Ver. F.0A 02/20/2009
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: 68PZU Ver. F.0A; Product Version: F.0A
[   16.163383] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.648778] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.648789] wl 0000:02:00.0: setting latency timer to 64
a@a-pc:~$

---

### Post by josephmills on 2011-05-16
how about a ```
lsmod
``` and a ```
lspci -vnn | grep 14e4 
``` and a ```
rfkill list 
``` thanks

---

### Post by walla321123 on 2011-05-16
a@a-pc:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_analog    75442  1 
rfcomm                 38125  8 
snd_hda_intel          24140  2 
sco                    17779  2 
binfmt_misc            13213  1 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
uvcvideo               66851  0 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450944  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17203  0 
videodev               75143  1 uvcvideo
wl                   2642531  0 
btusb                  18160  2 
psmouse                73312  0 
snd_timer              28659  2 snd_pcm,snd_seq
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  2 lib80211_crypt_tkip,wl
drm                   180037  4 i915,drm_kms_helper
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
input_polldev          13735  1 lis3lv02d
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 
a@a-pc:~$ 

_________________________________________________


a@a-pc:~$ lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
a@a-pc:~$ 


___________________________________________________


a@a-pc:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
a@a-pc:~$

---

### Post by josephmills on 2011-05-16
please see post number 44http://ubuntuforums.org/showthread.php?t=1748245&page=5    let us know if you have any trouble

---

### Post by walla321123 on 2011-05-16
Thank you Joseph, I will check it now.

---

### Post by walla321123 on 2011-05-16
hmm dident work, When i took away the "type in bcm into the search bar then click on the green box's and mark for removal"

and put in the " broadcom-sta-source + broadcom-sta-common" which i need for my 14e4:4315 modle number, it didn't even find a wirless network, so i changed it back. My internet works on wifi, it's just super slow can't do anything except google stuff. Facebook and this forum works great when the ethernet cable is in but not on wifi.

Thanks anyway mate

---

### Post by josephmills on 2011-05-16
> **walla321123 said:**
> hmm dident work, When i took away the "type in bcm into the search bar then click on the green box's and mark for removal"

and put in the " broadcom-sta-source + broadcom-sta-common" which i need for my 14e4:4315 modle number, it didn't even find a wirless network, so i changed it back. My internet works on wifi, it's just super slow can't do anything except google stuff. Facebook and this forum works great when the ethernet cable is in but not on wifi.

Thanks anyway mateafter you installed the b43 sta did you shut down and restart? also are you just using the b43fwcutter ?  
thanks I am also trying to get a better grip on this myself happy to hear that you got your wireless working :D

---

