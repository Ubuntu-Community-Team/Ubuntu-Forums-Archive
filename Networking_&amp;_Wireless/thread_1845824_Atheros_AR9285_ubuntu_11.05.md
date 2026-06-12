---
title: "Atheros AR9285 ubuntu 11.05"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by 118118 on 2011-09-17
hi, i am completely new to linux. here are some print outs

i'm trying to  connect wirelessly to the internet but no access points are shown.

sudo lshw - C network

> *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: f4:ec:38:d0:40:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fbff0000-fbffffffnm-tool

> NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:25:22:C9:3E:1C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        F4:EC:38:grin:0:40:CF

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


lspci -nn | grep -e 0280 -e 0200

> 03:00.0 Network controller [0280]: Atheros Communications Inc.  AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev  01)lsub

> Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubiwconfig

> Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
luke@luke-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
rfkill list all

> 1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sudo iwlist scan

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
lsmod | grep ath

> No command 'ath' found, did you mean:
 Command 'tth' from package 'tth' (multiverse)
 Command 'ash' from package 'ash' (universe)
 Command 'atd' from package 'at' (main)
 Command 'atc' from package 'bsdgames' (universe)
 Command 'atp' from package 'atp' (universe)
 Command 'at' from package 'at' (main)
 Command 'atq' from package 'at' (main)
ath: command not foundgmseg | grep ath

> [    0.804486] device-mapper: multipath: version 1.2.0 loaded
[    0.804490] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.220888] ath9k 0000:03:00.0: PCI INT A -> Link[LNEB] -> GSI 18 (level, low) -> IRQ 18
[    7.220896] ath9k 0000:03:00.0: setting latency timer to 64
[    7.270246] ath: EEPROM regdomain: 0x809c
[    7.270247] ath: EEPROM indicates we should expect a country code
[    7.270249] ath: doing EEPROM country->regdmn map search
[    7.270250] ath: country maps to regdmn code: 0x52
[    7.270251] ath: Country alpha2 being used: CN
[    7.270253] ath: Regpair used: 0x52
[    7.619412] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    7.619924] Registered led device: ath9k-phy0::radio
[    7.619939] Registered led device: ath9k-phy0::assoc
[    7.619953] Registered led device: ath9k-phy0::tx
[    7.619966] Registered led device: ath9k-phy0::rx
[  622.680413] ath9k 0000:03:00.0: PCI INT A disabled
[  622.680443] ath9k: Driver unloaded
[  659.784789] ath9k 0000:03:00.0: PCI INT A -> Link[LNEB] -> GSI 18 (level, low) -> IRQ 18
[  659.784800] ath9k 0000:03:00.0: setting latency timer to 64
[  659.833943] ath: EEPROM regdomain: 0x809c
[  659.833944] ath: EEPROM indicates we should expect a country code
[  659.833946] ath: doing EEPROM country->regdmn map search
[  659.833947] ath: country maps to regdmn code: 0x52
[  659.833949] ath: Country alpha2 being used: CN
[  659.833950] ath: Regpair used: 0x52
[  659.835514] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[  659.836279] Registered led device: ath9k-phy1::radio
[  659.836299] Registered led device: ath9k-phy1::assoc
[  659.836318] Registered led device: ath9k-phy1::tx
[  659.836339] Registered led device: ath9k-phy1::rx
it's my parents' router or whatever so i would prefer to not  mess with it. i only have a wireless card on this computer... thanks a  lot for any help :smile:

---

### Post by wildmanne39 on 2011-09-17
Hi, I posted commands for you to run in this thread.
[http://ubuntuforums.org/showthread.php?t=1836867&page=4](http://ubuntuforums.org/showthread.php?t=1836867&page=4)
run them then post the results in this thread.
Thank you

---

### Post by 118118 on 2011-09-18
[LEFT]i reinstalled ubuntu last night and this morning .briefly had a connection but it was very slow. i have replied in that thread you linked to[/LEFT]

---

### Post by praseodym on 2011-09-18
Shut off the power management and reload the driver with a module parameter:

```
sudo iwconfig wlan0 power off
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart
```
If it works make it permanent:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

---

### Post by 118118 on 2011-09-18
no luck.

---

### Post by wildmanne39 on 2011-09-18
Hi, we need to work in just one thread it is to confusing to me trying to work in both I do not know if you are answering me or the other person.

Please let work just in this one and post the results of these commands here.
```
lspci -nn | grep -e 0280 -e 0200 
```
```
sudo iwlist scan
```
Thank you

---

### Post by 118118 on 2011-09-18
hi. no problem.


the first command's output was as follows ```
lspci -nn | grep -e 0280 -e 0200
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```the second ```
... wlan0 no  scan results
```:)

sorry about the edit.

---

### Post by wildmanne39 on 2011-09-18
Hi, wow it is making it hard for us, try the first command this way just copy and past all commands it is easier that way.
```
lspci -nn
```
Thank you

---

### Post by 118118 on 2011-09-18
```
lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 LPC Bridge [10de:03e2] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0d.0 VGA compatible controller [0300]: nVidia Corporation C61 [GeForce 7025 / nForce 630a] [10de:03d6] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:08.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```

thank you

---

### Post by wildmanne39 on 2011-09-18
Hi, please post the results of this command here:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by 118118 on 2011-09-18
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
snd_hda_codec_via      56765  1 
binfmt_misc            13213  1 
arc4                   12473  2 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nouveau               621970  2 
snd_timer              28659  2 snd_pcm,snd_seq
ttm                    65184  1 nouveau
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
ppdev                  12849  0 
parport_pc             32111  1 
snd                    55295  16 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
k10temp                12951  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 nouveau
serio_raw              12990  0 
video                  18951  1 nouveau
i2c_nforce2            12906  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sata_nv                23176  2 
crc_itu_t              12627  1 firewire_core
forcedeth              58190  0 
pata_amd               13762  0 

```

---

### Post by wildmanne39 on 2011-09-18
There is a problem where some people never get this adapter to work but most do, I have a couple of thoughts.
1. Is your network hidden?
2. I still think you need make sure your router is set to wpa2 only.
```
dmesg | egrep 'rt2|firm|radio|switch'
```
post the results of this command please.

Your card is not scanning for networks.
Thank you

---

### Post by 118118 on 2011-09-19
1. no it's not hidden
2. i can give it a shot
```

[    7.761293] Registered led device: ath9k-phy0::radio
[    8.417318] Console: switching to colour frame buffer device 160x50
[   94.144141] Registered led device: ath9k-phy0::radio
```

---

### Post by wildmanne39 on 2011-09-19
Hi, try this command please with out your wired connection.
```
sudo rfkill unblock all
```
Thank you

---

### Post by 118118 on 2011-09-19
nothing changes.

---

### Post by wildmanne39 on 2011-09-19
Hi, post the results of these commands please:
```
ndiswrapper -l
```
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
```
cat /etc/network/interfaces
```
Thank you

---

### Post by 118118 on 2011-09-19
```
luke@luke-desktop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
``````
 luke@luke-desktop:~$ sudo gedit /etc/modprobe.d/ath9k.conf
[sudo] password for luke: 

(gedit:5417): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.MJEE2V': No such file or directory

(gedit:5417): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5417): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G4BS1V': No such file or directory

(gedit:5417): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```document was blank
```

luke@luke-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by wildmanne39 on 2011-09-19
Hi, let do this please:
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thank you

---

### Post by 118118 on 2011-09-19
hi - still no networks show up.

---

### Post by wildmanne39 on 2011-09-19
Hi, try this command again please:
```
lsmod | grep ath
```
```
dmesg | grep firmware
```
```
ls /lib/firmware/ath9k
```
and post the results here.
Thank you

---

### Post by 118118 on 2011-09-19
```
luke@luke-desktop:~$ lsmod | grep ath
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
```

```

luke@luke-desktop:~$ dmesg | grep firmware

```
```
luke@luke-desktop:~$ ls /lib/firmware/ath9k
ls: cannot access /lib/firmware/ath9k: No such file or directory
luke@luke-desktop:~$ 
```

btw is just found a cd that was bundled with this desktop with "for wireless n adapter only" written on it. don't know if that's relevant at all.

---

### Post by wildmanne39 on 2011-09-19
Hi, no it is not. I am going to ask a friend to help us.
Thank you

---

### Post by praseodym on 2011-09-19
Please show

```
uname -a
iwlist chan
```
This is a downgraded card with this chipset, it only works in the 2.4 GHz range, only works in a small-range with bad radio reception.

---

### Post by 118118 on 2011-09-19
```
luke@luke-desktop:~$ uname -a
Linux luke-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
luke@luke-desktop:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
luke@luke-desktop:~$ 


```oh - you mean my wireless hardware is poor quality?

---

### Post by wildmanne39 on 2011-09-19
Hi, so you need to change your router to one of the channels listed and see if you can connect, also the encryption should be changed to wpa2 if is is not already.
Thank you

---

### Post by praseodym on 2011-09-19
In notebooks there are often downgraded cards implemented, as you see, only the 2.4 GHz channels are available, so you have to change the channel to one of these, as wildmanne39 wrote before.

The driver ath9k is not the problem, it can also handle the 5 GHz channels

---

### Post by wildmanne39 on 2011-09-19
Hi, thank you praseodym your knowledge is great, and I learned something I did not know about that card but it explains some of the trouble we have been having, plus the client was not wanting to change any settings in the router.
Thanks again

---

### Post by 118118 on 2011-09-20
hi, thanks for the help! i've just got to find the password for the router now.

---

### Post by 118118 on 2011-09-20
i typed iwcan list in my computer which does have a wireless connection and got the following

> wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.437 GHz (Channel 6)is that relevant to whether this will work? might it just be that the card is so shitty that the signal cannot be picked up at this range... i have a airport extreme - that might help? though again i'd have to find the password to the router...

---

### Post by 118118 on 2011-09-20
ok - so i'm about to reset my wireless router... can i just check that 
a) there's no way to back it up without the admin password already anyway
b) you will be able to assist me here if i can't get wifi to work anywhere in the house then?


thanks :)

---

### Post by wildmanne39 on 2011-09-20
Hi, yes that is relevant please post the complete results of:
```
nm-tool
```
```
sudo iwlist scan
```
I am not sure what you mean by back up your router?
Thank you

---

### Post by 118118 on 2011-09-26
kk.
i am unable to access the router for a few days still. thanks!!

---

### Post by 118118 on 2011-10-06
hi,

just to let you know that this appears to be solved now :D
thanks!

---

### Post by wildmanne39 on 2011-10-06
Hi, I am glad it is fixed.

---

### Post by 118118 on 2011-10-14
hi sorry to ask but my internet is very slow - might that be due to a low signal strength, despite it apparently running at a 65.0 Mbps speed?

---

### Post by praseodym on 2011-10-14
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan
lsmod
```

---

### Post by 118118 on 2011-11-25
hi,

have recently moved home and do not have internet connection on the desktop still. there is a wireless connection available to my netbook that works fine in the same room. here's the output of those commands [for the desktop].

```
luke@luke-desktop:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Atheros Communications Inc. Device [168c:30a1]
    Kernel driver in use: ath9k
luke@luke-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
luke@luke-desktop:~$ sudo iwlist scan
[sudo] password for luke: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

luke@luke-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
udf                    83795  0 
ses                    17137  0 
enclosure              14656  1 ses
usb_storage            43946  0 
uas                    17676  0 
snd_hda_codec_via      56765  1 
snd_usb_audio          91410  0 
binfmt_misc            13213  1 
arc4                   12473  2 
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
ath9k                 103633  0 
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
nouveau               621970  2 
snd_pcm                80244  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
mac80211              257001  1 ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
ttm                    65184  1 nouveau
ath9k_common           13611  1 ath9k
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_hw              300328  2 ath9k,ath9k_common
drm_kms_helper         40745  1 nouveau
ath                    19141  2 ath9k,ath9k_hw
ppdev                  12849  0 
cfg80211              156212  3 ath9k,mac80211,ath
drm                   180037  4 nouveau,ttm,drm_kms_helper
snd                    55295  15 snd_hda_codec_via,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
parport_pc             32111  1 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 nouveau
serio_raw              12990  0 
video                  18951  1 nouveau
i2c_nforce2            12906  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
k10temp                12951  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
usbhid                 41704  0 
hid                    77084  1 usbhid
crc_itu_t              12627  2 udf,firewire_core
pata_amd               13762  0 
forcedeth              58190  0 
sata_nv                23176  2 
luke@luke-desktop:~$ 

```


thank you very much for any assistance.

---

### Post by praseodym on 2011-11-25
Try to upgrade the driver:

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```

Reboot and check again. Additionally you can shut off the hardware encryption:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by 118118 on 2011-11-25
i don't have internet access sol can't update the driver..?

will try the other thing now.

---

### Post by praseodym on 2011-11-25
Which kernel is that? Please show:

> uname -a

---

### Post by 118118 on 2011-11-25
i tried those commands and no luck

---

### Post by 118118 on 2011-11-25
> **praseodym said:**
> Which kernel is that? Please show:
```
Linux luke-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
```

:)

---

### Post by 118118 on 2011-11-26
hi,

no more help with this :guitar: ??

---

### Post by praseodym on 2011-11-27
Ok, install the latest kernel, headers, and drivers:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-12-generic_2.6.38-12.51_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-12-generic_2.6.38-12.51_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-12-generic_2.6.38-12.51_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-12-generic_2.6.38-12.51_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-12_2.6.38-12.51_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-12_2.6.38-12.51_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-2.6.39-natty-generic_2.6.38.12.27_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-2.6.39-natty-generic_2.6.38.12.27_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/universe/l/linux-backports-modules-2.6.38/linux-backports-modules-cw-2.6.39-2.6.38-12-generic_2.6.38-12.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux-backports-modules-2.6.38/linux-backports-modules-cw-2.6.39-2.6.38-12-generic_2.6.38-12.8_i386.deb)

Save the files in "Downloads", install them by

```
sudo dpkg -i ~/Downloads/*.deb
```
and reboot.

---

### Post by 118118 on 2011-11-27
cool. thanks!


will let you know...

---

### Post by 118118 on 2011-11-27
since doing this, i have the error message after bootup, in the top right of the screen

"Intall Problem: the configuration for GNOME power manager have been been installed correctly. Please contact your adminstrator".

Also, my password is not logging me in!



:popcorn:
edit it's not an authentication problem.

---

### Post by 118118 on 2011-11-27
oh and i rebooted the computer through the same terminal that i used to install the .deb packages [from a flash drive - which i "safely removed" before using on the desktop that i am trying to fix].

---

### Post by praseodym on 2011-11-27
Hold the SHIFT-button during boot-up and choose an earlier kernel

---

### Post by 118118 on 2011-11-28
> **praseodym said:**
> Hold the SHIFT-button during boot-up and choose an earlier kernel
hi,

this did not do anything - i got the same new fancy screen and error message.
BTW i only had about 40 MBs of space left on the drive. I am sorry for not mentioning this, though hopefully nothing has been lost!

---

### Post by praseodym on 2011-11-28
This is pretty bad, maybe swapping didnt work, so the installation went bad.

Boot via Live-CD, the hard disk is then automatically mounted to "/media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers", check that. After that mount anything you need in the Live-system:

```
sudo mount -o bind /dev /media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers/dev 
sudo mount -o bind /sys /media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers/sys
sudo mount -t proc /proc /media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers/proc
sudo cp /proc/mounts /media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers/etc/mtab 
sudo cp /etc/resolv.conf /media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers/etc/resolv.conf 
```
After that change to the installed system:
```
sudo chroot /media/[COLOR="Red"]very[/COLOR]long[COLOR="Red"]folder[/COLOR]name[COLOR="Red"]with[/COLOR]numbers /bin/bash 
```
and repair it/clean up:
```
apt-get autoremove
apt-get autoclean
apt-get clean
update-initramfs -u
```
If you have any internet connection with Live-CD update your system ([COLOR="Lime"]Recommended! Try a cable![/COLOR]):
```
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get clean
exit [COLOR="Cyan"]#now you are back in the live system[/COLOR]
```
Reboot the regular system.

Remark: If you have a /boot-partition you need to mount it, too. If so, please show with regular Live-CD without doing anything else (or if you are unsure)
```
sudo fdisk -l
```

---

### Post by wildmanne39 on 2011-11-28
Hi, also you say that you only have 40 mbs of disk space free, if root is felled up it will not boot, you will need to free up some space.

---

### Post by 118118 on 2011-11-29
i am trying to boot from a flash drive atm but nothing is happening quickly...


please may i ask - my priority now is to save the files that are on my ubuntu disc. i would try to go into windows [it's dual boot] and access them but ubuntu starts [and fails] to load automatically when the computer is restarted, rather than giving me the option of which OS to load. how can i force the computer to let me choose on startup - esp that is if this live-usb is not going to work..?

i mean if i do that then i am happy to just reformat the ubuntu partition...

:popcorn::popcorn:

---

### Post by praseodym on 2011-11-29
With Live-CD you should see the windows partitions in the file manager

---

### Post by 118118 on 2011-11-29
sorry to be so demanding but... i don't have startupmanager installed and don't have an internet connection yet. i had been using a terminal command so that when i rebooted it started in windows. but i've lost the command... any help??

---

### Post by praseodym on 2011-11-29
Here

[http://de.archive.ubuntu.com/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.13-5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/s/startupmanager/startupmanager_1.9.13-5_all.deb)

---

### Post by 118118 on 2011-11-29
hi,

lots of dependency problems here...
[http://ziga.hamsworld.net/2010/03/26/reboot-to-windows-shortcut-for-ubuntu-9-10-grub-2/](http://ziga.hamsworld.net/2010/03/26/reboot-to-windows-shortcut-for-ubuntu-9-10-grub-2/) i am trying to follow this [as i did before] but i get an error message half way through when typing sudo update-grub
because i'm running ubuntu from usb?

what alternatives do i have to load windows?

---

### Post by 118118 on 2011-11-29
i am in the process of transferring a load of files to the windows partition. once that's done, can i just reinstall from the USB to sort out the issue with the kernel upgrade?

---

### Post by praseodym on 2011-11-29
Yes, if you are overwriting the old Linux partition(s)

---

### Post by 118118 on 2011-11-30
ok... i am reinstalling ubuntu. how might i get the wireless connection to work?


BTW i am also struggling to share a wireless connection with this pc via ethernet [http://ubuntuforums.org/showthread.php?p=11500669#post11500669](http://ubuntuforums.org/showthread.php?p=11500669#post11500669)

---

### Post by praseodym on 2011-11-30
Deactivate the hardware encryption as described and reboot after the installation. You may want to update the system via cable first, if possible

---

### Post by 118118 on 2011-12-03
i can't see any posts here mentioning hardware encryption!

thanks.

---

### Post by praseodym on 2011-12-03
#38 in this thread

---

### Post by 118118 on 2011-12-03
did those commands...

---

