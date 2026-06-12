---
title: "Wireless Network found, but won't connect."
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by Captain Alex on 2010-08-10
I'm having trouble connecting to my wireless network. I'm currently using NetworkManager, but I was having trouble without too. 

I can detect the network fine, it asks for the wireless password, and I enter it. But then I can't get past the "Attempting to join wireless network" It stays there for a few minutes and then asks me for password again, so I enter it again. But it still hangs, then it just gets stuck in a loop of asking for the password.

Here are some basic terminal commands I entered.

lspci

```
captain@The-Ship-Of-Capn-Alex:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 05)
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

```

lsusb
```
captain@The-Ship-Of-Capn-Alex:~$ lsusb
Bus 004 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ping [www.google.com](www.google.com)
```
ping: unknown host www.google.com
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8901  0 
fat                    47767  1 vfat
usb_storage            39425  0 
nls_utf8                1069  1 
isofs                  29250  1 
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6587  1 
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
arc4                    1153  2 
snd_mpu401_uart         5617  1 snd_via82xx
fbcon                  35102  72 
tileblit                2031  1 fbcon
snd_seq_dummy           1338  0 
font                    7557  1 fbcon
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
rt73usb                22434  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
crc_itu_t               1371  1 rt73usb
vga16fb                11385  0 
i2c_viapro              5573  0 
rt2x00usb               9703  1 rt73usb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              27509  2 rt73usb,rt2x00usb
nouveau               467048  2 
led_class               2864  1 rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
via_ircc               21745  0 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
mac80211              204922  2 rt2x00usb,rt2x00lib
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  186556  1 via_ircc
psmouse                63245  0 
drm                   162471  4 nouveau,ttm,drm_kms_helper
snd                    54148  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
joydev                  8708  0 
via_agp                 5310  1 
i2c_algo_bit            5028  1 nouveau
crc_ccitt               1339  1 irda
cfg80211              126485  2 rt2x00lib,mac80211
soundcore               6620  1 snd
ppdev                   5259  0 
agpgart                31724  3 ttm,drm,via_agp
lp                      7028  0 
parport_pc             25962  1 
shpchp                 28820  0 
parport                32635  3 ppdev,lp,parport_pc
8139too                18545  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
8139cp                 16186  0 
pata_via                7272  3 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp
floppy                 53016  0
```

Thank you for any help I receive.

---

### Post by uncfan_2563 on 2010-08-10
Yeah same thing is happening to me. Try install wicd maybe?

---

### Post by Captain Alex on 2010-08-10
Did that work for you?

---

### Post by uncfan_2563 on 2010-08-10
Well. No but dunno, might work for you

---

### Post by Captain Alex on 2010-08-10
What is it and where can I get it? Also, maybe if i get a WPAsupplicant? But I don't know anything about them, I was just reading about them somewhere.

---

### Post by Yeshua1964 on 2010-08-10
I have the same problem.  Actually my network manager disappeared.  I tried, but all that did was tell me my network password was wrong.  The fix I am using is to log in as a guest, then it reads the network manager and I am allowed to use the network with the same password that was being rejected.  Then I just switch back to my regular account and all is fine.  If anyone knows how to fix this, I would be forever in your debt.  Ok, that might be a bit much...but you get the point.

---

### Post by dineshs on 2010-08-10
If nothing works try to update the system.The following link may help
[http://ubuntuforums.org/showthread.php?t=1549395](http://ubuntuforums.org/showthread.php?t=1549395)
Yeshua,
[http://ubuntuforums.org/showthread.php?t=1545744](http://ubuntuforums.org/showthread.php?t=1545744)
[http://ubuntuforums.org/showthread.php?p=9636750#post9636750](http://ubuntuforums.org/showthread.php?p=9636750#post9636750)

---

### Post by speedotorpedo on 2010-08-10
I am having the same problems and the links in the last post don't help. I would appreciate any help available. I have looked for the issue on other sites but to no avail.

---

### Post by Captain Alex on 2010-08-11
How interesting....

I actually just tried to boot ubuntu from the CD. When I did that, it asked me for a keyring when connecting to my wireless. I entered the same password for my wireless for the keyring. And it worked from the CD.

I rebooted and after ubuntu loaded my wireless worked just fine... It automatically connected and I am now online.

When I had originally encountered the keyring I had just clicked close/cancel.

If anyone else had a problem similar to mine I suggest making sure you enter a keyring, preferably the same as the wireless password

---

### Post by Captain Alex on 2010-08-11
Also, thank you everyone who assisted me. :) Your help was greatly appreciated.

---

### Post by freshminted on 2012-05-07
Despite trying all the suggestions my own move from wired  to wireless modem router has been an absolute failure. ADSL - found, All port lights OK, but no internet EVER.
Let me explain;
On my current hard wired system running Ubuntu 11.10, my Thompson Speed touch is linked to a Vonage Port adaptor for their VOIP system. This works wonderfully well. But when I try to set up a replacement TP-Link W901G (without using the Vonage/Voip), and try hard wired, all lights are on but I get no internet connection.
I have variously tried using a different laptop - same result. Changing all the cables - same result. Using the Vonage port adaptor: same result.

Now not having a wireless connection isn't the end of the world, but it would be really rather nice to be able to use my laptop properly and not as a desktop!

---

