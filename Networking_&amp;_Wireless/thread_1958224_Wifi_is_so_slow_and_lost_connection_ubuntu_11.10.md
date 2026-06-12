---
title: "Wifi is so slow and lost connection ubuntu 11.10"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by Docmero on 2012-04-13
Hi ,
I'm a new user to Ubuntu .
I recently installed it and immediatly faced problems .
My Wifi connectin is good , however I can't log to any site and when I can (rarly and randomly ) it is soooooooooo slow .
My wifi is a USB RT73 .My wifi adapter is edimax-ew-7318usg
 tahnks .
These are the solutions I already tried after 7 hours of researching .
>>>>>>>>>><<<<<<<<<
:

Open terminal and enter the following command:

sudo -s gksu gedit /etc/modprobe.d/ath9k.conf

at the end of the file add this:

options ath9k nohwcrypt=1

Save an restart your OS.

If you still have the issue, then try instructions on step 2.

2- Second Method:

This method involves forcing iwlagn to not use n, the commands will  disable n on the device without making it a permanant change, check  first if this work for you, if you notice that the speed improved then  continue to make the change permanant. If this solution didn`t work for  you, then reboot your computer to revert the chnages.

sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1

If you notice that the wifi speed improved, then make the change permanent :

gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf

and add this line to the file:

options iwlagn 11n_disable=1

save & quit

3- Third method : You need to disactivate IPv6, to do that, open terminal and enter the following commands:

echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf echo  "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf echo  "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf  echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf

Then restart your system.

Please report if the solution discribed in this post worked for you by commenting this post. Thanks for your help.
.............................................
Code:

options iwlagn 11n_disable=1 11n_disable50=1

to
Code:

options iwlagn 11n_disable=1



sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1

Try browsing again and if there is an improvement, make this change permanent by creating an 'options' file:

gksu gedit /etc/modprobe.d/options.conf

and add the line

options iwlagn 11n_disable=1

Hope this will help.
.......................................
sudo -s

echo "options ath5k nohwcrypt=1" > /etc/modprobe.d/ath5k.conf

&#1604;&#1603;&#1585;&#1608;&#1578; ath9k

sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

..............................
Alt+F2 type gnome-terminal

then run the below command

$sudo apt-get remove &#8211;purge network-manager

uninstalled the networkmanager

$sudo apt-get install wicd

Installed the wicd for fixing the issue.


...............
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up[B]
.....................
Sudo iwconfig wlan0 power off[/B]

Thanks Guys . This post is from the Win7 .

---

### Post by praseodym on 2012-04-14
Hi,

please show the outputs of

```
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by Docmero on 2012-04-14
> **praseodym said:**
> Hi,

please show the outputs of

```
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

After trying alot of thing the problem got worse and it couldn't even connect to the network
so I installed the system from scratch again (upgraded from 11.10 to 11.10 !! ) and changed the port of the USB . Surprisingly , the problem vanished and the Internet now is stable and works well . Anyway , these are the outputs of what you asked for just in case if you notice any thing wrong to prevent the problem from happening again or the problem appear again out of no where . Thanks
_***UPDATE: The problem is back and I can't fix it :(***_
***lsusb***
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless
Adapter
Bus 002 Device 004: ID 058f:3881 Alcor Micro Corp. 
Bus 002 Device 005: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
```
***lsmod***
```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_via      71209  1 
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia              12319299  40 
snd_seq_midi           13324  0 
rt73usb                31735  0 
rt2x00usb              20830  1 rt73usb
rt2x00lib              50365  2 rt73usb,rt2x00usb
mac80211              462046  2 rt2x00usb,rt2x00lib
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_rawmidi            30547  1 snd_seq_midi
cfg80211              199630  2 rt2x00lib,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
usbhid                 47198  0 
v4l2_compat_ioctl32    17083  1 videodev
hid                    95463  1 usbhid
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            27942  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  3 i7core_edac
mxm_wmi                12979  0 
asus_atk0110           18078  0 
wmi                    19256  1 mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
ahci                   26002  0 
crc_itu_t              12707  2 rt73usb,firewire_core
libahci                26861  1 ahci
xhci_hcd               82820  0 
pata_jmicron           12747  0 
r8169                  52788  0 
```***rfkill list***
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``` **iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"tota"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: B4:82:FE:2A:97:62   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:195   Missed beacon:0
```
***sudo iwlist scan***
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: B4:82:FE:2A:97:62
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"tota"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f819b2588
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0004746F7461
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by praseodym on 2012-04-14
Deactivate the power management of the card:

```
sudo iwconfig wlan0 power off
```

---

### Post by Docmero on 2012-04-17
> **praseodym said:**
> Deactivate the power management of the card:

```
sudo iwconfig wlan0 power off
```

As I expected the problem is now back again without any obvious reason !!
I've applied  the code and it didn't work . Any other solution ?
Ubuntu was fun till this problem started !!:confused:

---

### Post by Docmero on 2012-04-18
So , No solution ? :(

---

### Post by Docmero on 2012-04-19
Now I know why ubuntu is unpopular . Thanks guys . I think I'm gonna remove it and back to windows 7 .

---

### Post by praseodym on 2012-04-20
> **Docmero said:**
> Now I know why ubuntu is unpopular . Thanks guys . I think I'm gonna remove it and back to windows 7 .

Most people have no problem with this card, its about one of your settings, I believe...

Strange is this:

```
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="Red"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="Red"]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
```
Check if you can change the router settings to WPA2-AES (CCMP) instead of TKIP.

---

### Post by tmaranets on 2012-04-20
I am not sure of this, but try installing new Wifi drivers for your computer. Possibly Ubuntu messed something up with your drivers, but I doubt it. Maybe try ethernet.

---

