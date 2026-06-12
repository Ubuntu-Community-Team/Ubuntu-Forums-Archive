---
title: "Ubuntu 11.10 installed and wireless NOT working"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by MSKAN98 on 2012-02-19
I am new to Ubuntu and installed 11.10 version today to get a feel and can connect to internet by wired network. When I checked System Settings --> Network, I didn't see my Wireless connection name listed under Wireless. What should I do to check I have the updated drivers installed for my wireless card(Dell D620 laptop with Dell Wireless 1390 WLAN Mini-card) and make my wireless work again. I have dual OS and wireless is working fine with Windows XP.

---

### Post by wildmanne39 on 2012-02-19
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by MSKAN98 on 2012-02-20
[SIZE=3][FONT=Batang]cat /etc/lsb-release; uname -a[/FONT][/SIZE]
[SIZE=3][FONT=Batang][DISTRIB_ID=Ubuntu[/FONT][/SIZE]
[SIZE=3][FONT=Batang]DISTRIB_RELEASE=11.10[/FONT][/SIZE]
[SIZE=3][FONT=Batang]DISTRIB_CODENAME=oneiric[/FONT][/SIZE]
[SIZE=3][FONT=Batang]DISTRIB_DESCRIPTION="Ubuntu 11.10"[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux ][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]lspci -nnk | grep -iA2 net[/FONT][/SIZE]
[SIZE=3][FONT=Batang][09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Subsystem: Dell Latitude D620 [1028:01c2][/FONT][/SIZE]
[SIZE=3][FONT=Batang]Kernel driver in use: tg3[/FONT][/SIZE]
[SIZE=3][FONT=Batang]--[/FONT][/SIZE]
[SIZE=3][FONT=Batang]0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007][/FONT][/SIZE]
[SIZE=3][FONT=Batang]Kernel modules: wl, ssb ][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]iwconfig[/FONT][/SIZE]
[SIZE=3][FONT=Batang][lo no wireless extensions.[/FONT][/SIZE]
[SIZE=3][FONT=Batang]eth0 no wireless extensions.[/FONT][/SIZE]
[SIZE=3][FONT=Batang]][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]rfkill list all[/FONT][/SIZE]
[SIZE=3][FONT=Batang][[/FONT][/SIZE]
[SIZE=3][FONT=Batang]0: dell-wifi: Wireless LAN[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Soft blocked: no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Hard blocked: no[/FONT][/SIZE]
[SIZE=3][FONT=Batang]][/FONT][/SIZE]
 
 
[SIZE=3][FONT=Batang]lsmod[/FONT][/SIZE]
[SIZE=3][FONT=Batang][[/FONT][/SIZE]
[SIZE=3][FONT=Batang]Module Size Used by[/FONT][/SIZE]
[SIZE=3][FONT=Batang]rfcomm 38408 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]bnep 17923 2[/FONT][/SIZE]
[SIZE=3][FONT=Batang]bluetooth 148839 10 rfcomm,bnep[/FONT][/SIZE]
[SIZE=3][FONT=Batang]parport_pc 32114 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]ppdev 12849 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]binfmt_misc 17292 1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_hda_codec_idt 60049 1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]joydev 17393 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_hda_intel 24262 2[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_hda_codec 91859 2 snd_hda_codec_idt,snd_hda_intel[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_hwdep 13276 1 snd_hda_codec[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_pcm 80435 2 snd_hda_intel,snd_hda_codec[/FONT][/SIZE]
[SIZE=3][FONT=Batang]wl 2646601 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]dell_laptop 13519 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]dcdbas 14098 1 dell_laptop[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_seq_midi 13132 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_rawmidi 25241 1 snd_seq_midi[/FONT][/SIZE]
[SIZE=3][FONT=Batang]pcmcia 39822 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_seq_midi_event 14475 1 snd_seq_midi[/FONT][/SIZE]
[SIZE=3][FONT=Batang]psmouse 73673 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]serio_raw 12990 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event[/FONT][/SIZE]
[SIZE=3][FONT=Batang]i915 509519 3[/FONT][/SIZE]
[SIZE=3][FONT=Batang]yenta_socket 27428 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]pcmcia_rsrc 18367 1 yenta_socket[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_timer 28932 2 snd_pcm,snd_seq[/FONT][/SIZE]
[SIZE=3][FONT=Batang]pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/SIZE]
[SIZE=3][FONT=Batang]drm_kms_helper 32889 1 i915[/FONT][/SIZE]
[SIZE=3][FONT=Batang]lib80211 14570 1 wl[/FONT][/SIZE]
[SIZE=3][FONT=Batang]drm 192194 4 i915,drm_kms_helper[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd 55902 13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/SIZE]
[SIZE=3][FONT=Batang]i2c_algo_bit 13199 1 i915[/FONT][/SIZE]
[SIZE=3][FONT=Batang]soundcore 12600 1 snd[/FONT][/SIZE]
[SIZE=3][FONT=Batang]video 18908 1 i915[/FONT][/SIZE]
[SIZE=3][FONT=Batang]snd_page_alloc 14115 2 snd_hda_intel,snd_pcm[/FONT][/SIZE]
[SIZE=3][FONT=Batang]lp 17455 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]parport 40930 3 parport_pc,ppdev,lp[/FONT][/SIZE]
[SIZE=3][FONT=Batang]usbhid 41905 0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]hid 77367 1 usbhid[/FONT][/SIZE]
[SIZE=3][FONT=Batang]tg3 132972][/FONT][/SIZE]

---

### Post by Djesurun1 on 2012-02-20
Hello Ubuntu Forums!

I am having the EXACT same problem and I am a new Linux (Ubuntu) user as well. I was hoping you could help us both at the same time. I really need to get my computer on the network so I can do my homework for school...my wifes laptop is really frustrating...and uses windows not mention lol. My macbook just died on me so I have to get the bugs fixed on my linux desktop. Ok...So here are the responces to the commands you asked MSKAN to try out. Thanks again...I hope you don't mind me tagging along on your thread. I have searched the forums and tried so many different fixes but nothing has worked so far. FYI I have AT&T Uverse which i have read has had issues connecting to Linux OS. My network settings I have changed to WPA2 instead of the default WPA1 AND WPA2 setting. 

[djesurun1@djesurunlinux:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux djesurunlinux 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 athlon i386 GNU/Linux
djesurun1@djesurunlinux:~$ lspci -nnk | grep -iA2 net
02:07.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
    Subsystem: Netgear WG311T 108 Mbps Wireless PCI Adapter (rev.A2) [1385:4d00]
    Kernel driver in use: ath5k
    Kernel modules: ath5k
02:08.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
    Subsystem: ADMtek Device [1317:0574]
    Kernel driver in use: tulip
--
02:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard [1458:e000]
    Kernel driver in use: 8139too
djesurun1@djesurunlinux:~$ iw config
The program 'iw' is currently not installed.  You can install it by typing:
sudo apt-get install iw
djesurun1@djesurunlinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
djesurun1@djesurunlinux:~$ rf killlist all
rf: command not found
djesurun1@djesurunlinux:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
djesurun1@djesurunlinux:~$ lsmod
Module                  Size  Used by
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
nvidia               7098131  24 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
k8temp                 12905  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  3 ath5k,ath,mac80211
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_ali1535            12777  0 
i2c_ali1563            12850  0 
ns558                  12654  0 
binfmt_misc            17292  1 
gameport               15060  2 ns558
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
tulip                  52487  0 
sata_uli               12693  0 
pata_ali               13562  2 
8139too                23283  0 
8139cp                 22636  0 
floppy                 60310  0 
djesurun1@djesurunlinux:~$ ]

---

### Post by chili555 on 2012-02-20
Please see your other post.

---

### Post by MIRAAN Baloch on 2012-02-20
Plz Chack this?

Install usb_modeswitch using the following command:

    sudo apt-get install usb-modeswitch usb-modeswitch-data 

after installing usb_modeswitch plug your modem in. If your modem is already plugged in remove it and then plug it back in. Now use lsusb command to see if your modem is properly recognized. The output should contain a line like:

    Bus xxx Device xxx: ID 19d2:fff1 ONDA Communication S.p.A. 

Now go to System->Preferences->Network Connections. Click on Mobile Broadband Tab.

---

### Post by wildmanne39 on 2012-02-20
Hi MSKAN98, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
unplug your wired connection and reboot.
Thanks

---

### Post by MSKAN98 on 2012-02-20
Hi wildmanne39, 
Your suggestion worked like a charm and I am now connected online by wireless. Thanks.
One more off the topic question, I have a dual OS(Win XP and Ubuntu 11.10). When I boot, Win XP is the default and loads without any selection.
How can I make Ubuntu the default selection while booting?

Once again, Thanks for all the members who contributed to this thread.
-MSKAN98.

---

### Post by praseodym on 2012-02-20
Hi Djesurun1,

deactivate the hardware encryption of your wireless driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by wildmanne39 on 2012-02-20
Hi, I am glad it is working and as for the other question is should be asked in absolute beginners or general section of the forum so you can get the help you need and keep this thread for wireless issues.
Thanks

---

