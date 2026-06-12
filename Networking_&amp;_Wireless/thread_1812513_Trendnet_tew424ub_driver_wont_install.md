---
title: "Trendnet tew424ub driver wont install"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by v460816 on 2011-07-26
I have a computer with 2 internal harddrives installed. One (40gb) has windows 7 the other(20gb) has Linux 11.04. My wireless adapter trendnet tew424uv 0457:0163 works with win7. I cannot get it to work with Linux.. I have tried using ndiswrapper terminal and GUI forms. The GUI freezes the os while the terminal just displays the comands(-I, -m etc) I downloaded the drivers from the trendnet website. please help me!!!

---

### Post by bkratz on 2011-07-26
> **v460816 said:**
> I have a computer with 2 internal harddrives installed. One (40gb) has windows 7 the other(20gb) has Linux 11.04. My wireless adapter trendnet tew424uv 0457:0163 works with win7. I cannot get it to work with Linux.. I have tried using ndiswrapper terminal and GUI forms. The GUI freezes the os while the terminal just displays the comands(-I, -m etc) I downloaded the drivers from the trendnet website. please help me!!!




since you are using ndiswrapper see post 35 here for help.

[http://ubuntuforums.org/showthread.php?p=9487338](http://ubuntuforums.org/showthread.php?p=9487338)

---

### Post by v460816 on 2011-07-27
Yup still didn't work... It said installed sis163.inf but the device still will not activate..

---

### Post by wildmanne39 on 2011-07-28
Hi, please run these commands in a terminal
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by v460816 on 2011-07-28
#{root@vincent-desktop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:13:d4:44:31:75
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000  driverversion=7.3.21-k8-NAPI firmware=N/A latency=0 link=no mingnt=255  multicast=yes port=twisted pair
       resources: irq:18 memory:fe9e0000-fe9fffff ioport:cf80(size=32)
  *-network
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: c
       bus info: pci@0000:03:0c.0
       logical name: wlan0
       version: 11
       serial: 00:40:05:90:43:17
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=adm8211  driverversion=2.6.38-8-generic firmware=N/A latency=64 link=no  maxlatency=128 mingnt=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:20 ioport:d400(size=256) memory:feaff400-feaff7ff memory:feaa0000-feabffff
root@vincent-desktop:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82875P/E7210 Memory Controller Hub [8086:2578] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82875P Processor to AGP Controller [8086:2579] (rev 02)
00:03.0 PCI bridge [0604]: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge [8086:257b] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface [8086:257e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER  (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G400/G450 [102b:0525] (rev 82)
02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]
03:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8  [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
03:04.0 RAID bus controller [0104]: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 37:cool: [105a:3373] (rev 02)
03:0c.0 Network controller [0280]: ADMtek ADM8211 802.11b Wireless Interface [1317:8201] (rev 11)
root@vincent-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Power Management:eek:ff
          
root@vincent-desktop:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@vincent-desktop:~# lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
mga                    36074  2 
drm                   180037  3 mga
vesafb                 13449  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
adm8211                30923  0 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 adm8211
binfmt_misc            13213  1 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
eeprom_93cx6           12653  1 adm8211
usbhid                 41704  0 
cfg80211              156212  2 adm8211,mac80211
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,sn  d_seq,snd_timer,snd_seq_device
usb_storage            43946  2 
matrox_w1              12753  0 
hid                    77084  1 usbhid
wire                   26760  1 matrox_w1
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
uas                    17676  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sata_promise           17855  0 
crc_itu_t              12627  1 firewire_core
e1000                 101089  0 
floppy                 60032  0 
root@vincent-desktop:~#
}



this everythin it gave me

---

### Post by wildmanne39 on 2011-07-28
Hi, please run these commands and post the output here.
```
dmesg | grep adm8211
```
```
dmesg | grep firmware
```
```
dmesg | grep wlan0
```
```
lsmod | grep adm8211
```
and post the results here.
Thank you

---

### Post by v460816 on 2011-07-28
vincent@vincent-desktop:~$ sudo -s
[sudo] password for vincent: 
root@vincent-desktop:~# dmesg | grep adm8211
[   14.983929] adm8211 0000:03:0c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   14.990372] 0000:03:0c.0 (adm8211): Channel range: 1 - 11
[   14.990377] 0000:03:0c.0 (adm8211): RFtype=1 BBPtype=1 Specific BBP=0 Transceiver=0
root@vincent-desktop:~# dmesg | grep firmware
root@vincent-desktop:~# dmesg | grep wlan0
[   23.716240] ADDRCONF(NETDEV_UP): wlan0: link is not ready
root@vincent-desktop:~# lsmod | grep adm8211
adm8211                30923  0 
mac80211              257001  1 adm8211
eeprom_93cx6           12653  1 adm8211
cfg80211              156212  2 adm8211,mac80211
root@vincent-desktop:~#

---

### Post by lkjoel on 2011-07-28
@v460816
Try these links: [http://ubuntuforums.org/showthread.php?p=3213248](http://ubuntuforums.org/showthread.php?p=3213248)
and
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_%28ndiswrapper%29")

---

### Post by wildmanne39 on 2011-07-28
@ lkjoel thank you for the link I appreciate it.

@v460816
In 11.04 that adapter is suppose to work out of the box.

What version of ubuntu are you using? in 10.10 you can enable the backports repositories in synaptic and then you should be able to install the firmware for your card.

---

### Post by wildmanne39 on 2011-07-28
Hi, also try 
```
sudo ifconfig wlan0 down
```
```
sudo modprobe -r adm8211
```
```
sudo modprobe adm8211
```
```
sudo ifconfig wlan0 up

```
please unplug your wired connection then run those commands and see if your wireless comes on.
Thank you

---

### Post by lkjoel on 2011-07-28
If the above technique does not work, could you post us the output of these commands?
```
sudo /etc/init.d/network* restart
!!
``````
sudo /etc/init.d/network-manager restart
``````
sudo  /etc/init.d/network-interface restart
``````
sudo  /etc/init.d/network-interface-security restart
```

---

### Post by v460816 on 2011-07-28
Will try tomorrow...

---

### Post by v460816 on 2011-07-29
Ok now the windows wireless drivers tool recognizes that the device is plugged in... Now how do I have it find and connect to wireless internets in range? Thank you for your patience I'm a newbie with Linux ;)

---

### Post by wildmanne39 on 2011-07-29
Hi, run these commands please now that you can see the connections.
```
sudo iwlist scan
```
```
iwconfig
```
```
rfkill list all

```
```
lsmod | grep adm8211
```
and post the output here.
Thank you

---

### Post by v460816 on 2011-07-29
```
root@vincent-desktop:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

root@vincent-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@vincent-desktop:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@vincent-desktop:~# lsmod | grep adm8211
adm8211                30923  0 
mac80211              257001  1 adm8211
eeprom_93cx6           12653  1 adm8211
cfg80211              156212  2 adm8211,mac80211
root@vincent-desktop:~# 

```

---

### Post by wildmanne39 on 2011-07-29
Hi, according to the information you posted it still does not see any wireless connections.

What do you mean by this?
> Ok now the windows wireless drivers tool recognizes that the device is plugged in.
That it is recognized in windows? if so that does not help us on ubuntu.

If that is not what you meant please explain.

Also you never told me are you using 10.10 or 11.04 ubuntu?
Thank you

---

