---
title: "not able to connect the wireless network..."
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by tubunter on 2013-06-26
hello, 

just installed ubuntu 12.04 on my acer aspire 1520 laptop, installed ndiswrapper and wireless card driver. it recognize the card but i'm not able to connect any network:

```
user@user-Aspire-1520:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@user-Aspire-1520:~$ 

```


```
user@user-Aspire-1520:~$  iwconfig wlan0 essid Alice-00000001
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```


could anyone hep me,please?

thanks

---

### Post by Hadaka on 2013-06-26
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list
```
thanks.

---

### Post by tubunter on 2013-06-26
```
user@user-Aspire-1520:~$ lspci -nnk | grep -iA3 net
00:0a.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
    Subsystem: AMBIT Microsystem Corp. T60N871 802.11g Mini PCI Wireless Adapter [1468:0305]
    Kernel driver in use: ndiswrapper
00:0b.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
--
00:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:006e]
    Kernel driver in use: r8169
    Kernel modules: r8169
user@user-Aspire-1520:~$ lsmod
Module                  Size  Used by
cdc_ether              13544  0 
usbnet                 26253  1 cdc_ether
vesafb                 13846  1 
nvidia               8117631  26 
snd_via82xx            29741  2 
joydev                 17694  0 
snd_via82xx_modem      18843  0 
gameport               19730  1 snd_via82xx
snd_ac97_codec        134870  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12767  1 snd_ac97_codec
snd_pcm                97523  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
acer_wmi               32845  0 
sparse_keymap          13891  1 acer_wmi
snd_mpu401_uart        14170  1 snd_via82xx
snd_seq_midi           13325  0 
snd_rawmidi            30750  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
i2c_viapro             13154  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 47562  0 
bnep                   18240  2 
parport_pc             32867  0 
pcmcia                 49390  0 
ppdev                  17114  0 
bluetooth             211812  10 rfcomm,bnep
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53053  0 
psmouse               102075  0 
via_ircc               27333  0 
snd_page_alloc         18573  3 snd_via82xx,snd_via82xx_modem,snd_pcm
serio_raw              13216  0 
soundcore              15092  1 snd
k8temp                 13065  0 
edac_mce_amd           23548  0 
yenta_socket           32181  0 
pcmcia_rsrc            18431  1 yenta_socket
pcmcia_core            22615  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 37278  0 
wmi                    19257  1 acer_wmi
irda                  201416  1 via_ircc
video                  19598  1 acer_wmi
mac_hid                13254  0 
crc_ccitt              12708  1 irda
ndiswrapper           283370  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
pata_via               13702  2 
firewire_ohci          41034  0 
r8169                  62766  0 
firewire_core          64697  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
user@user-Aspire-1520:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
user@user-Aspire-1520:~$ 
```

---

### Post by Hadaka on 2013-06-26
Thanks,please Copy and paste the following..
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo rfkill unblock all
```
then re-post 
```
rfkill list all
```
thanks.

---

### Post by tubunter on 2013-06-26
```
user@user-Aspire-1520:~$ echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for user: 
blacklist acer_wmi
user@user-Aspire-1520:~$ sudo rfkill unblock all
user@user-Aspire-1520:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
user@user-Aspire-1520:~$ 

```

---

### Post by Hadaka on 2013-06-26
Thanks...try again please
do..
```
sudo rfkill unblock all
```
then boot..
and post..
```
rfkill list all
```
thanks.

---

### Post by chili555 on 2013-06-26
> **tubunter said:**
> ```
user@user-Aspire-1520:~$ echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for user: 
blacklist acer_wmi
user@user-Aspire-1520:~$ sudo rfkill unblock all
user@user-Aspire-1520:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
user@user-Aspire-1520:~$ 

```Hadaka left out a step; he's busy and goes fast!!```
*sudo modprobe -r acer-wmi*
sudo rfkill unblock all
rfkill list all
```We now return you to your regularly scheduled guru.

---

### Post by tubunter on 2013-06-26
the last command line returns nothing...

---

### Post by tubunter on 2013-06-26
Ok! it just runs fine!

what did you do!?!?...

---

### Post by Hadaka on 2013-06-26
ok...please post the output of..
```
lsmod | grep -i "acer_wmi"
rfkill list all
sudo modprobe -r ndiswrapper
sudo modprobe -v ndiswrapper
dmesg | grep ndis
```
thanks.

---

### Post by tubunter on 2013-06-26
```
user@user-Aspire-1520:~$ lsmod | grep -i "acer_wmi"
user@user-Aspire-1520:~$ rfkill list all
user@user-Aspire-1520:~$ sudo modprobe -r ndiswrapper
[sudo] password for user: 
user@user-Aspire-1520:~$ sudo modprobe -v ndiswrapper
user@user-Aspire-1520:~$ dmesg | grep ndis
[   27.917312] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[   28.129235] ndiswrapper: driver ipn2220 (INPROCOMM,02/24/2005,3.07.02.2005) loaded
[   28.241885] ndiswrapper: using IRQ 21
[   28.493404] usbcore: registered new interface driver ndiswrapper
[   30.721167] ndiswrapper (iw_set_ap_address:682): setting AP mac address failed (C0010015)
[   41.044722] ndiswrapper (iw_set_freq:441): setting configuration failed (C0010015)
[   86.013625] ndiswrapper (iw_set_ap_address:682): setting AP mac address failed (C0010015)
[   94.076536] ndiswrapper (iw_set_freq:441): setting configuration failed (C0010015)
[   94.078940] ndiswrapper (iw_set_ap_address:682): setting AP mac address failed (C0010015)
[ 1321.636245] ndiswrapper: device wlan0 removed
[ 1321.638245] usbcore: deregistering interface driver ndiswrapper
[ 1321.724547] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[ 1321.765109] ndiswrapper: driver ipn2220 (INPROCOMM,02/24/2005,3.07.02.2005) loaded
[ 1321.799540] ndiswrapper: using IRQ 21
[ 1322.051986] usbcore: registered new interface driver ndiswrapper
[ 1322.055060] ndiswrapper (iw_set_ap_address:682): setting AP mac address failed (C0010015)
[ 1322.182885] ndiswrapper (iw_set_ap_address:682): setting AP mac address failed (C0010015)
[ 1322.224322] ndiswrapper (iw_set_ap_address:682): setting AP mac address failed (C0010015)
[ 1333.155477] ndiswrapper (iw_set_freq:441): setting configuration failed (C0010015)
user@user-Aspire-1520:~$
```

---

### Post by Hadaka on 2013-06-26
ok...well..good news and bad news
the good news is..your softblock if gone !
bad news is ..looks like your ndiswrapper might be hosed..
so...first let's make sure things are up to date..
please do..
```
sudo apt-get update
sudo apt-get upgrade
```
when thats done...do
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
disconnect your ethernet cable and boot.
*if you still have no wireless...i would suggest
unloading the ndiswrapper 
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
```
and check if it is in /etc/modules
```
cat /etc/modules
```
*IF it is there then do..
```
sudo gedit /etc/modules
```
**REMOVE  ndiswrapper
save and close gedit...
then..go here -->[http://ubuntuforums.org/showthread.php?t=2148714](http://ubuntuforums.org/showthread.php?t=2148714)
post #4 and reload the ndiswrapper AND the windows xp file.
when done..then do..
```
sudo modprobe ndiswrapper
```
good luck !

---

