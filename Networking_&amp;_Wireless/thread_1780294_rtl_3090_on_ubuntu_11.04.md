---
title: "rtl 3090 on ubuntu 11.04"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by micho119 on 2011-06-11
Hi all,

i recently installed ubuntu 11.04 on my hp g62-b31ee laptop
the wireless is not working (but it actually detect the wireless network)
i couldn't find the wlan0 by using ifconfig in terminal

i've downloaded this package :
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb)

it gave "bad" message but it had been installed.

can anyway tell what should i do?
thanks

---

### Post by chili555 on 2011-06-11
What 'bad message?' I downloaded and installed this perfectly well. Let's do some diagnostics. Please open a terminal and run and post:```
modinfo rt3090sta
lspci -nn
iwconfig
lsmod
```We'll get it fixed up!

---

### Post by micho119 on 2011-06-11
hi chili, and thank you for the quick response,
actually, i've seen the wlan0 on ifconfig when i reset the laptop.

and it sees the network and keep asking for the password even though i put it million times and it won't connect.

what should i do?

---

### Post by micho119 on 2011-06-11
the bad message said :
the package is of bad quality
the installation of a package which violates the quality standards isn't allowed. THIs could cause serious problems on your computer. Please contact the person or organization who provided this package and include details beneath.

the deatils are :
Linitan Check result for /media/04FA6426FA6415EB/Linux/rt....etc
E: rt3090-dkms: arch-independent-package-contains-binary-or-object usr/src

---

### Post by chili555 on 2011-06-11
Here is what I got:> $ sudo dpkg -i rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb 
[sudo] password for chili: 
Selecting previously deselected package rt3090-dkms.
(Reading database ... 165258 files and directories currently installed.)
Unpacking rt3090-dkms (from rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb) ...
Setting up rt3090-dkms (1:2.4.0.4-0ubuntu0~ppa0) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
Please provide the data requested in post #2.

---

### Post by micho119 on 2011-06-11
Hi Chili,

I've did so and it shows exactly what you wrote.
but still nothing, it is just keep asking for my password, it is on WPA2-PSK mode.
my router is TP-Link TD-W8101G

---

### Post by micho119 on 2011-06-11
and it is encrypted using TKIP,
should i change this?
should i put a static ip?

---

### Post by chili555 on 2011-06-11
Please post the data requested in post #2.

---

### Post by micho119 on 2011-06-11
michel@ubuntu:~$ modinfo rt3090sta
filename:       /lib/modules/2.6.38-8-generic/updates/dkms/rt3090sta.ko
license:        GPL
version:        2.4.0.4
srcversion:     9A7B078F56A0351E1A34B06
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
michel@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
michel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
michel@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  0 
binfmt_misc            13213  1 
sco                    17779  0 
bnep                   17785  0 
l2cap                  48656  4 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
rt2860sta             494649  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rt2800pci              18159  0 
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
btusb                  18160  0 
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 uvcvideo
drm                   180037  4 i915,drm_kms_helper
bluetooth              65565  5 rfcomm,sco,bnep,l2cap,btusb
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
psmouse                73312  0 
cfg80211              156212  2 rt2x00lib,mac80211
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
eeprom_93cx6           12653  1 rt2800pci
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  1 
libahci                25548  1 ahci
r8169                  42534  0 
michel@ubuntu:~$

---

### Post by micho119 on 2011-06-11
here it is..

---

### Post by micho119 on 2011-06-12
this has been solved.. i am now wireless.. 
thank you.. :)

---

### Post by chili555 on 2011-06-12
Man, oh man! Look at all those drivers fighting each other for control of your wireless! rt3090sta isn't even one of them. Yikes!!!> $ lsmod
Module Size Used by
rt2860sta 494649 0
rt2800pci 18159 0
rt2800lib 43824 1 rt2800pci
crc_ccitt 12595 2 rt2860sta,rt2800lib
rt2x00pci 13986 1 rt2800pci
rt2x00lib 39075 3 rt2800pci,rt2800lib,rt2x00pci
mac80211 257001 3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211 156212 2 rt2x00lib,mac80211Let's blaclist a few of them and see if your wireless starts to behave. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines at the end:```
blacklist rt2860sta
blacklist rt2800pci
blacklist rt2x00pci
```Proofread carefully, save and close gedit. Next, do:```
sudo su
echo rt3090sta >> /etc/modules
exit
```Reboot and tell us if your wireless is working as expected.

---

### Post by micho119 on 2011-06-12
thank you man, it worked perfectly,
can i do the same with kubuntu 11.04? and on 64bit?

---

### Post by micho119 on 2011-06-12
and what do you really prefer? because i found KDE on kubuntu is much top style than ubuntu?

---

### Post by chili555 on 2011-06-12
> **micho119 said:**
> thank you man, it worked perfectly,
can i do the same with kubuntu 11.04? and on 64bit?I'm pretty sure you can. Actually, I doubt you really needed to install rt3090. I think blacklisting rt2800pci and rt2x00pci and letting rt2860sta do the job would work just fine.> and what do you really prefer? because i found KDE on kubuntu is much top style than ubuntu?I keep coming back to Gnome. It's probably just an old dog-new tricks thing. I like and use what I like because I'm familiar with it after all these years.

---

### Post by micho119 on 2011-06-12
but they are pretty the same? i mean same packages, same console?
and what about suse?

---

### Post by chili555 on 2011-06-12
> **micho119 said:**
> but they are pretty the same? i mean same packages, same console?
and what about suse?They're pretty much the same. The buttons and icons are a bit different and where they are is a bit different. Gnome is a bit more CPU and GPU hungry, but, unless you have an older computer with less memory, that's not much of an issue. You can install them both and select which one you want at the login screen. Once you've figured out which you like the most, remove the other. 

There are a few applications that are specific to one or the other, but you can run them on the other. For instance, I love the CD and DVD burning program K3b; it's a KDE application. When I installed it, Synaptic told me I also needed several KDE library files. I installed them and it runs fine. I think if you like the look and feel of KDE, then there isn't the slightest reason not to have it. That's one of the beautiful things about Linux. You are free to do it your way. In fact, with a little programming knowledge, you could even design and install your own windowing manager! Imagine that, MWM!

I prefer Ubuntu to Suse for the same reasons I stated above. I like what I am familiar with. I have tried Suse a few times over the years and it's nice, but I can't find the things I need that I know easily in Ubuntu. It's not bad or wrong; for me it's just different. I think they have live CDs; try it and see.

---

### Post by micho119 on 2011-06-12
thank you for this explanation, :)
i've read also about linux mint which is based on ubuntu with more clearer theme.
i think i should do a lot of test before i decide which one i will work with.
thank you again man, you help me a lot.

---

