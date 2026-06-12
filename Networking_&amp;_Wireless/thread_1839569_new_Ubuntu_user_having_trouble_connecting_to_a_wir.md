---
title: "new Ubuntu user having trouble connecting to a wireless network."
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by joehootenanny on 2011-09-05
Hi guys.  

I just installed Ubuntu 11 on my notebook.  It is a Compaq Presario CQ60-215DX.  When I had Windows I had no trouble connecting to a network.  I replaced Windows with Ubuntu.  I have installed all available updates and installed all recommended drivers in the Additional Drivers app.  When I disconnect my Ethernet cable I click on the wireless icon in the upper right. "Enable Wireless" is grayed out and cannot be selected.  When I got to Network Connections there are no WiFi networks available.  My iPod and PS3 have no trouble seeing my network and my neighbors' networks.

Any help that you guys could provide would be much appreciated.

---

### Post by garvinrick4 on 2011-09-05
open a terminal and run this. 
```
lspci
```
Now post results here, only really need network cards (one is ethernet and one wireless)

---

### Post by joehootenanny on 2011-09-05
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01




Thanks for offering your help, Garvinrick4.  I'm not sure exactly what you need so here is everything.

---

### Post by garvinrick4 on 2011-09-05
Post the output of
> lsmod
So users can see output.
There are alot of good users with better skill sets using that card and driver than I. Post the output for them and you will get help. I will keep an eye on this and contact someone
for you if not helped soon.

---

### Post by joehootenanny on 2011-09-05
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
binfmt_misc            13213  1 
joydev                 17322  0 
nvidia               9766978  46 
arc4                   12473  2 
ath5k                 144534  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
cfg80211              156212  3 ath5k,ath,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18951  0 
k10temp                12951  0 
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
shpchp                 32345  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
pata_amd               13762  0 
forcedeth              58190  0 
ahci                   21591  2 
libahci                25548  1 ahci

---

### Post by garvinrick4 on 2011-09-05
Does:
```
sudo modprobe ath5k
```Get it going for you. Let me know.

---

### Post by garvinrick4 on 2011-09-05
Need a user that is efficient with ath5k driver to help this new user please.

EDIT:
Joehootenanny,
 You have not replied so I will take it you are in running order.

#Wildmanne39, thank you for looking in on this thread for me.

---

### Post by wildmanne39 on 2011-09-06
Hi, it looks like the driver is loaded, please run these commands and post the results here.
```
sudo lshw -C network
```
```
nm-tool
```
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
Thank you

---

### Post by joehootenanny on 2011-09-06
okay just ran those commands






matt@conan:~$ sudo modprobe ath5k
[sudo] password for matt: 
matt@conan:~$ sudo modprobe ath5k
matt@conan:~$ sudo 1shw -C network
sudo: 1shw: command not found
matt@conan:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:76:0A:83

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.116.2.50
    DNS:             24.116.2.34
    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:24:2B:AA:D8:FC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


matt@conan:~$ cat /etc/1sb-release; uname -a
cat: /etc/1sb-release: No such file or directory
Linux conan 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
matt@conan:~$ lspci -nn | grep -e 0280 -e 0200
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
matt@conan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
matt@conan:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by praseodym on 2011-09-06
Hello,

unload the following module:

```
sudo modprobe -rf hp_wmi
sudo rfkill unblock all
sudo service network-manager restart
```
Check:

```
iwconfig
rfkill list
sudo iwlist scan
```
If it works for you you should prevent the modul from being loaded in future:

```
echo "blacklist hp_wmi" | sudo tee /etc/modprobe.d/blacklist-hp_wmi.conf
```

---

### Post by joehootenanny on 2011-09-06
I still cannot get connected to my wireless network


```
matt@conan:~$ sudo modprobe -rf hp_wmi
[sudo] password for matt: 
matt@conan:~$ sudo rfkill unblock all
matt@conan:~$ sudo service network-manager restart
network-manager start/running, process 1870
matt@conan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
matt@conan:~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
matt@conan:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

matt@conan:~$ echo "black list hp_wmi" | sudo tee /etc/modprobe.d/blacklist-hp_wmi.conf
black list hp_wmi
matt@conan:~$ 

```

---

### Post by wildmanne39 on 2011-09-06
Hi it says you are hard blocked try to turn your wireless on with fn f2, it may be any of the f buttons or there may be a switch on you computer to turn it on, then run this command again.
```
rfkill list all
```

Thank you

---

### Post by joehootenanny on 2011-09-06
Your right I do have a button on my notebook for turning WiFi on and off.  It does not seem to make a difference though when I use it.  i still cannot enable WiFi. 

Here are the results before and after I pressed the button. 

```
matt@conan:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
matt@conan:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

---

### Post by joehootenanny on 2011-09-06
> **joehootenanny said:**
> Your right I do have a button on my notebook for turning WiFi on and off.  It does not seem to make a difference though when I use it.  i still cannot enable WiFi. 

Scratch that.  I can put a check mark next to "Enable Wireless" but it still does not see any available networks.

---

### Post by wildmanne39 on 2011-09-06
Hi try the previous commands like this.
```
sudo modprobe -rf hp-wmi
sudo rfkill unblock all
sudo service network-manager restart
```
Thank you

---

### Post by praseodym on 2011-09-06
Typo, no blank:

> ```
echo "black list hp_wmi" | sudo tee /etc/modprobe.d/blacklist-hp_wmi.conf
black list hp_wmi
```
take the blank out via

```
gksudo gedit /etc/modprobe.d/blacklist-hp_wmi.conf
```
save, exit, and reboot.

---

