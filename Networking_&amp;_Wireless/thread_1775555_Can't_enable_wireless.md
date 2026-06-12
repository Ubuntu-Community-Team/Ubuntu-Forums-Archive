---
title: "Can't enable wireless"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by davoudi on 2011-06-04
Hi,

 I just recently installed Ubuntu on my friend's computer (Compaq Persario X6000). Everything works like a charm except wireless networking. There is a button for activating wireless but I can't enable wireless by pressing it. Here is the output of sudo lshw -C Network

> 
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:71:dd:4c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.189 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:c8206000-c8207fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:b8:95:1e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


Any help is very much appreciated.

---

### Post by Bucky Ball on 2011-06-04
Have you gotten online with a cable and gotten updates?

Do that then check System>Administration>Additional Drivers. Anything there? Most Broadcom cards should work *almost* 'out of the box' these days (but you generally need to get online with a cable to achieve this). ;)

---

### Post by Jamie_Dolan on 2011-06-04
I needed a broadcom wireless proprietary driver for mine when my wireless wouldn't work, but as soon as I connected to the internet through an ethernet connection I updated my drivers with Additional Drivers and it generated the driver I needed

---

### Post by davoudi on 2011-06-04
> **Bucky Ball said:**
> Have you gotten online with a cable and gotten updates?

Do that then check System>Administration>Additional Drivers. Anything there? Most Broadcom cards should work *almost* 'out of the box' these days (but you generally need to get online with a cable to achieve this). ;)
Yes. Wire network works well and I did an update as well. I used additional driver after update but it couldn't detect anything. I recently installed Ubuntu on my machine which is a top of the line and it just sat on machine perfectly so I was wondering how I could resolve my problem on the other machine.

---

### Post by garvinrick4 on 2011-06-05
Open Synaptics and type in b43 in upper right search:

 b43-fwcutter
firmware-b43-installer

Install those 2 in Synaptic's. Right click on and choose install and hit apply arrow.
Make sure nothing else b43 installed.
After installed reboot should work, if not look in additional drivers or proprietary drivers
according to version and enable. Click on thumbnail

---

### Post by davoudi on 2011-06-05
> **garvinrick4 said:**
> Open Synaptics and type in b43 in upper right search:

 b43-fwcutter
firmware-b43-installer

Install those 2 in Synaptic's. Right click on and choose install and hit apply arrow.
Make sure nothing else b43 installed.
After installed reboot should work, if not look in additional drivers or proprietary drivers
according to version and enable. Click on thumbnail

Bravo!

---

### Post by ruseriousb511 on 2011-08-21
This will not work for me, I have tried 3-4 different trouble shooting techniques and NOTHING works. Anything else you can think of that would help ? I cant get my wifi working and I need it BAD. Please let me know.

---

### Post by bkratz on 2011-08-21
> **ruseriousb511 said:**
> This will not work for me, I have tried 3-4 different trouble shooting techniques and NOTHING works. Anything else you can think of that would help ? I cant get my wifi working and I need it BAD. Please let me know.



Do you have the same card? This is the information that would help everyone help you.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by ruseriousb511 on 2011-08-21
I have broadcomm 4306, thats what I see when I run the cpu info command.

---

### Post by bkratz on 2011-08-21
> **ruseriousb511 said:**
> I have broadcomm 4306, thats what I see when I run the cpu info command.



But which version is it (there are more than one). Post

```
lspci -nn | grep 0280
```

---

### Post by ruseriousb511 on 2011-08-21
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

this is what i get with the command you gave me, on the same notebook as the initial poster.

---

### Post by praseodym on 2011-08-21
This card works with the b43 driver. Did you install the firmware files? With Natty you need both, until Maverick you only need b43-fwcutter. Reboot your sytem after installation and show:

```
lsmod
dmesg | grep b43
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by ruseriousb511 on 2011-08-21
here are the results of the commands :
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
arc4                   12473  2 
ttm                    65184  1 radeon
hp_wmi                 13418  0 
b43                   296610  0 
sparse_keymap          13666  1 hp_wmi
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 b43
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
cfg80211              156212  2 b43,mac80211
tifm_7xx1              12898  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
video                  18951  0 
tifm_core              15040  1 tifm_7xx1
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
8139too                23208  0 
ssb                    45942  1 b43
8139cp                 22497  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ dmesg | grep b43
[    1.604123] b43-pci-bridge 0000:0b:03.0: enabling device (0000 -> 0002)
[    1.604138] b43-pci-bridge 0000:0b:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.410433] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   15.521534] Registered led device: b43-phy0::tx
[   15.521694] Registered led device: b43-phy0::rx
[   15.521838] Registered led device: b43-phy0::radio
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo iwlist scan
[sudo] password for ruseriousb5: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$

---

### Post by bkratz on 2011-08-21
One important thing

0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: hp-wifi: Wireless LAN
[COLOR="Red"]Soft blocked: yes
Hard blocked: yes[/COLOR]
2: hp-bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: yes

Hard block is usually a switch turned off, or the inability to read the switch


worth trying

sudo rfkill unblock all

and then doing a

rfkill list all

againv and post results

---

### Post by ruseriousb511 on 2011-08-21
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo rfkill unblock all
[sudo] password for ruseriousb5: 
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$  sudo rfkill unblock all
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo rfkill list all
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$

---

### Post by ruseriousb511 on 2011-08-21
why is it still hard blocked ?

---

### Post by bkratz on 2011-08-21
Have to find the thread but it appears that hp-wifi sometimes has problems correctly determining if the switch is on or not. Be back shortly.

---

### Post by ruseriousb511 on 2011-08-21
good luck and I truly appreciate your time and effort to help

---

### Post by praseodym on 2011-08-21
You can add a module parameter for the module hp_wmi:

```
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp_wmi.conf
```
Reboot your system and:

```
sudo rfkill unblock all
```
Control:

```
rfkill list
iwconfig
sudo iwlist scan
dmesg | grep wmi
```

---

### Post by bkratz on 2011-08-21
> **ruseriousb511 said:**
> good luck and I truly appreciate your time and effort to help



Post 8 is the one I was looking for, if not we have one more option to try.

[http://ubuntuforums.org/showthread.php?t=1680039](http://ubuntuforums.org/showthread.php?t=1680039)

---

### Post by ruseriousb511 on 2011-08-21
just to make sure : enter the first command and then restart notebook then directly enter the other two commands one at a time : correct ?

---

### Post by ruseriousb511 on 2011-08-21
well here it is :

ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo rfkill unblock all
[sudo] password for ruseriousb5: 
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ dmesg | grep wmi
[    0.248816] wmi: Mapper loaded
[   15.062788] hp_wmi: Unknown parameter `wireless'
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$

---

### Post by ruseriousb511 on 2011-08-21
I notice its still hard blocked but I also notice that the new wireless parameter loaded as well. Is that good bad or both ?

---

### Post by ruseriousb511 on 2011-08-21
That did it !!!!!!!!!!!!

thank you sooooooooo much !!!!!!!

:D:):P

---

### Post by bkratz on 2011-08-21
> **ruseriousb511 said:**
> That did it !!!!!!!!!!!!

thank you sooooooooo much !!!!!!!

:D:):P


congratulations (finally!)! getting it to work. Enjoy

---

