---
title: "wireless connection"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by ba912 on 2012-01-14
[FONT=Comic Sans MS]Hi, I've been trying to install a wireless card on a new home built pc running Ubuntu 11.10, followed all the trouble shooting guides I can find, pc knows the card is there, and lists the driver and seems to recognise the kernel, whatever that means! I've also used a wire connection to run additional drivers with no success, and set up the router details and key etc. Enable Networking and Enable Wireless are both checked. However, says there is no "Access point", and somewhere I saw "firmware missing".  I can't find anything else to try. [/FONT]
[FONT=Comic Sans MS]Info on terminal reads,  driver =43-pci-bridge latency =32. [/FONT]
[FONT=Comic Sans MS]Card details are IEEE802.11b/g/n WLAN Adapter.[/FONT]
[FONT=Comic Sans MS]Thanks in advance to anyone out there with some more ideas.........:confused:[/FONT]

---

### Post by wildmanne39 on 2012-01-14
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

### Post by ba912 on 2012-01-14
```
william@william-System-Product-Name-System-Product-Name:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux william-System-Product-Name-System-Product-Name 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux
william@william-System-Product-Name-System-Product-Name:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Broadcom Corporation Device [14e4:0453]
    Kernel driver in use: b43-pci-bridge
william@william-System-Product-Name-System-Product-Name:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
william@william-System-Product-Name-System-Product-Name:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
william@william-System-Product-Name-System-Product-Name:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
ppdev                  12849  0 
sparse_keymap          13658  1 asus_wmi
arc4                   12473  2 
b43                   318816  0 
mac80211              393459  1 b43
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
binfmt_misc            17292  1 
cfg80211              172392  2 b43,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_codec_realtek   254125  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
k10temp                12990  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_timer              28932  2 snd_seq,snd_pcm
fglrx                2756852  110 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
snd                    55902  14 snd_rawmidi,snd_hda_codec_realtek,snd_seq,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer,snd_seq_device
wmi                    18744  1 asus_wmi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
hid                    77367  1 usbhid
crc_itu_t              12627  1 firewire_core
ssb                    50682  1 b43
r8169                  43104  0 
ahci                   21634  3 
libahci                25727  1 ahci
pata_atiixp            12967  0 
w
```

---

### Post by ba912 on 2012-01-14
Hi, thanks for your response, hope I've followed yr directions ok!  Look forward to hearing back

---

### Post by wildmanne39 on 2012-01-14
Hi, please do this:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
unplug wired connection and reboot.
Thanks

---

### Post by ba912 on 2012-01-14
[COLOR=RoyalBlue][FONT=Comic Sans MS]Thank you so much, wireless connected :D[/FONT][/COLOR]

---

### Post by wildmanne39 on 2012-01-14
Hi, your welcome!
Enjoy

---

