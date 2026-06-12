---
title: "wireless - firmware missing"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by bushwhack77 on 2012-01-13
Hello - I've read and tried a few of the other posts about this issue, but, still have no luck with my wireless connection. I just installed the latest Ubuntu onto this old Dell Latitude D600 laptop, have gone through all of the updates/reboots and my wireless connection still says "device not ready (firmware missing)".

I've done the additional drivers search, but, no luck. Hoping one of people with a larger brain than mine might lend a hand! :)

Oh, this is a Broadcom wireless chipset in this thing - BCM4306  [14e4:4320 rev 03]

Thanks!

---

### Post by MFletcher99 on 2012-01-14
I'm having the same issue and could really use some help. My wireless chipset is the same. BCM4306.

---

### Post by wildmanne39 on 2012-01-14
Hi bushwhack77, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by MFletcher99 on 2012-01-14
Could you help me as well?

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux angel-HP-Compaq-nx6110-PU545US-ABA 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

``````
02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Kernel driver in use: b43-pci-bridge
--
02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Hewlett-Packard Company NX6110/NC6120 [103c:099c]
    Kernel driver in use: b44

``````
lo        no wireless extensions.

eth0      no wireless extensions.

``````
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

``````
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505108  2 
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
binfmt_misc            17292  1 
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31443  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
ssb                    50682  1 b44
crc_itu_t              12627  1 firewire_core

```

---

### Post by wildmanne39 on 2012-01-14
Hi MFletcher99, this should get you going.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Also it says the hardware switch is off you need to find the keys that turn it on or the switch.
Thanks

---

### Post by MFletcher99 on 2012-01-14
There is a button for my wireless but when I press it the led doesn't come on so I'm guessing it's not working. I have no clue what to do now. 

But thanks for helping with the code and stuff.

---

### Post by wildmanne39 on 2012-01-14
Hi, please run:
```
rfkill list all
sudo rfkill unblock all
```
Thanks

---

### Post by MFletcher99 on 2012-01-14
```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by wildmanne39 on 2012-01-14
Hi, the block is gone, if it still will not connect please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep b43

```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n75
```

What is the name of the network you want to connect too?
Thanks

---

### Post by kvalenza on 2012-01-15
Coincidentally, I am having the exact same problem. I have a Dell Latitude D600 with a Broadcom 570X g Integrated controller. I also have a dual boot with Windows. After lots of trial and error, I got it to work perfectly in Windows, but when I loaded Ubuntu, it did not detect any wireless network. At first it said the there was no firmware. Now it says nothing at all about anything wireless when I click the wireless icon.   (I installed then uninstalled NDIS wrapper. I also did the b43 commands you suggested above. Nothing has worked.)

Here are the results of an earlier terminal command you suggested:

user@user-Latitude-D600:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux user-Latitude-D600 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
user@user-Latitude-D600:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
	Subsystem: Dell Latitude D400 [1028:865d]
	Kernel driver in use: tg3
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
	Kernel modules: ssb
user@user-Latitude-D600:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@user-Latitude-D600:~$ rfkill list all
user@user-Latitude-D600:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                925193  2 
dcdbas                 14098  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39822  0 
psmouse                73673  0 
soundcore              12600  1 snd
ttm                    65224  1 radeon
serio_raw              12990  0 
drm_kms_helper         32889  1 radeon
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
yenta_socket           27428  0 
drm                   192194  4 radeon,ttm,drm_kms_helper
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18908  0 
binfmt_misc            17292  1 
parport_pc             32114  1 
i2c_algo_bit           13199  1 radeon
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   132972  0 
user@user-Latitude-D600:~$

---

### Post by carl4926 on 2012-01-15
@kvalenza

You need to uninstall the broadcom propriety driver and install the b43

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by wildmanne39 on 2012-01-15
Hi, reinstall the driver and firmware by adding one extra command:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
then
```
sudo modprobe b43
```
see if it comes on if not post the out put of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by MFletcher99 on 2012-01-15
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:14:C2:D6:B2:36

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         24.95.52.238
    Prefix:          22 (255.255.252.0)
    Gateway:         24.95.52.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62


```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

```
43 -e firmware -e wpa -e wlan -e etork | tail -n75
Jan 14 15:56:50 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.522958] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 15:56:51 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[533]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 16:22:20 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [ 1540.453265] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
Jan 14 16:22:20 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [ 1542.789974] b43-pci-bridge 0000:02:04.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jan 14 16:22:20 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [ 1542.789997] b43-pci-bridge 0000:02:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0000000)
Jan 14 16:22:20 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [ 1542.790005] b43-pci-bridge 0000:02:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
Jan 14 16:22:20 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [ 1542.790014] b43-pci-bridge 0000:02:04.0: restoring config space at offset 0x1 (was 0x0, writing 0x6)
Jan 14 16:22:20 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [ 1542.829524] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 16:23:19 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[533]: <info> kernel firmware directory '/lib/firmware' changed
Jan 14 16:39:17 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.522596] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 16:39:18 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[519]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 17:13:25 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.513876] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 17:13:26 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[530]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 20:15:53 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.491297] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 20:15:54 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[539]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 20:39:47 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.539779] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 20:39:48 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[521]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 14 21:03:30 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.499319] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 14 21:03:31 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[503]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 15 11:57:03 angel-HP-Compaq-nx6110-PU545US-ABA kernel: [    1.515068] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 15 11:57:04 angel-HP-Compaq-nx6110-PU545US-ABA NetworkManager[549]: <info> monitoring kernel firmware directory '/lib/firmware'.

```

The network I want to connect to is called "ABee"

---

### Post by kvalenza on 2012-01-15
> **wildmanne39 said:**
> Hi, reinstall the driver and firmware by adding one extra command:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
then
```
sudo modprobe b43
```
see if it comes on if not post the out put of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

Not much luck. The first time I did it, it showed all of the wireless connections, and it said that I was connected, but I was not.

Then I rebooted the computer, and NO wireless connectios appeared. So I went through the process again, and this time it actually worked. But when I rebooted the computer, again, no wireless connections appeared. I went through it a third time after rebooting, and again, they appeared but I could not connect.  Here is the output you asked for:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by wildmanne39 on 2012-01-15
Hi kvalenza, this command should make it work at boot then we have to find out why it will not connect.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Then reboot with wired connection out and you can not have an usb adapter for internet connected either or it will conflict.

If it does not connect please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep b43
rfkill list all
iwconfig
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n75
```
show all the output from the commands please do not edit.
Thanks

---

### Post by kvalenza on 2012-01-15
> **wildmanne39 said:**
> Hi kvalenza, this command should make it work at boot then we have to find out why it will not connect.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Then reboot with wired connection out and you can not have an usb adapter for internet connected either or it will conflict.

If it does not connect please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep b43
rfkill list all
iwconfig
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n75
```
show all the output from the commands please do not edit.
Thanks

This time the wireless icon showed up, but every time I clicked my wireless network (keith1) nothing happened and I did not connect. A message kept coming up saying "Wireless disconnected." Then when I clicked disconnect wireless a window came up saying "Wireless disconnected. You are now offline.

I have Windows in a dual boot and the wireless does work. However, it took a full day of lots of reading online forums to get it to work in Windows, which really puzzled me. But now it works fine. I guess I assumed erroneously that I would not have the same problem with Ubuntu because the problem was in the Windows configuration.  I am wondering if I should switch to Mepis on this computer.  Anyway, he is what you asked for from the terminal:

user@user-Latitude-D600:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:0F:1F:B3:15:29

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:0B:7D:0B:83:59

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Keith-Wireless1: Infra, 00:26:F2:8D:AA:87, Freq 2452 MHz, Rate 54 Mb/s, Strength 97 WPA
    linksys:         Infra, 00:1D:7E:4E:23:BF, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    Sweet Rose:      Infra, 00:24:C9:82:17:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    orwin:           Infra, 1C:BD:B9:FF:F3:64, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    2WIRE517:        Infra, 00:26:50:F5:A7:A1, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    Marc_and_Beth:   Infra, 00:13:F7:A4:2D:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2


user@user-Latitude-D600:~$ sudo iwlist scan
[sudo] password for user: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:8D:AA:87
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Keith-Wireless1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000156f81d80
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000F4B656974682D576972656C65737331
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409071B00000000000000000000000000000000000000
                    IE: Unknown: 3D1609071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000026F28DAA871021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: 00:13:F7:A4:2D:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Marc_and_Beth"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001990281a180
                    Extra: Last beacon: 720ms ago
                    IE: Unknown: 000D4D6172635F616E645F42657468
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340600070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A6C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160600010000000F000000000000000000000000000000
                    IE: Unknown: DD720050F204104A0001101044000102103B000103104700103CFCC90F0042337B8137F2C50569CB1410210009534D432C20496E632E1023000B534D435747425231342D4E102400024131104200046E6F6E651054000800060050F20400011011000B534D435747425231342D4E100800020004
          Cell 03 - Address: 00:26:50:F5:A7:A1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"2WIRE517"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013aa2e181
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 00083257495245353137
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 00:1D:7E:4E:23:BF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001accdda4189
                    Extra: Last beacon: 968ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000

user@user-Latitude-D600:~$ lsmod | grep b43
b43                   318816  0 
ssb                    50682  1 b43
mac80211              393459  1 b43
cfg80211              172392  2 b43,mac80211
user@user-Latitude-D600:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
user@user-Latitude-D600:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
user@user-Latitude-D600:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n75
Jan 15 20:49:09 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 15 20:49:10 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 15 20:49:12 user-Latitude-D600 wpa_supplicant[960]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Jan 15 20:49:12 user-Latitude-D600 wpa_supplicant[960]: CTRL-EVENT-DISCONNECTED bssid=00:26:f2:8d:aa:87 reason=2
Jan 15 20:49:12 user-Latitude-D600 kernel: [   65.924669] wlan0: deauthenticated from 00:26:f2:8d:aa:87 (Reason: 2)
Jan 15 20:49:12 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan 15 20:49:12 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 15 20:49:13 user-Latitude-D600 wpa_supplicant[960]: Trying to authenticate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:13 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 15 20:49:13 user-Latitude-D600 wpa_supplicant[960]: Trying to associate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:13 user-Latitude-D600 kernel: [   67.424280] wlan0: authenticate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:13 user-Latitude-D600 kernel: [   67.425678] wlan0: authenticated
Jan 15 20:49:13 user-Latitude-D600 kernel: [   67.426664] wlan0: associate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:13 user-Latitude-D600 kernel: [   67.429219] wlan0: RX ReassocResp from 00:26:f2:8d:aa:87 (capab=0x431 status=0 aid=2)
Jan 15 20:49:13 user-Latitude-D600 kernel: [   67.429225] wlan0: associated
Jan 15 20:49:13 user-Latitude-D600 wpa_supplicant[960]: Associated with 00:26:f2:8d:aa:87
Jan 15 20:49:13 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 15 20:49:13 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 15 20:49:14 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 15 20:49:16 user-Latitude-D600 kernel: [   70.434024] wlan0: deauthenticated from 00:26:f2:8d:aa:87 (Reason: 2)
Jan 15 20:49:16 user-Latitude-D600 wpa_supplicant[960]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Jan 15 20:49:16 user-Latitude-D600 wpa_supplicant[960]: CTRL-EVENT-DISCONNECTED bssid=00:26:f2:8d:aa:87 reason=2
Jan 15 20:49:16 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan 15 20:49:16 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 15 20:49:18 user-Latitude-D600 wpa_supplicant[960]: Trying to authenticate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:18 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 15 20:49:18 user-Latitude-D600 wpa_supplicant[960]: Trying to associate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:18 user-Latitude-D600 kernel: [   71.934089] wlan0: authenticate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:18 user-Latitude-D600 kernel: [   71.935521] wlan0: authenticated
Jan 15 20:49:18 user-Latitude-D600 kernel: [   71.936377] wlan0: associate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:18 user-Latitude-D600 kernel: [   71.939204] wlan0: RX ReassocResp from 00:26:f2:8d:aa:87 (capab=0x431 status=0 aid=2)
Jan 15 20:49:18 user-Latitude-D600 kernel: [   71.939210] wlan0: associated
Jan 15 20:49:18 user-Latitude-D600 wpa_supplicant[960]: Associated with 00:26:f2:8d:aa:87
Jan 15 20:49:18 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 15 20:49:18 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 15 20:49:18 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 15 20:49:21 user-Latitude-D600 kernel: [   75.004686] wlan0: deauthenticated from 00:26:f2:8d:aa:87 (Reason: 2)
Jan 15 20:49:21 user-Latitude-D600 wpa_supplicant[960]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Jan 15 20:49:21 user-Latitude-D600 wpa_supplicant[960]: CTRL-EVENT-DISCONNECTED bssid=00:26:f2:8d:aa:87 reason=2
Jan 15 20:49:21 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan 15 20:49:21 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 15 20:49:22 user-Latitude-D600 wpa_supplicant[960]: Trying to authenticate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:22 user-Latitude-D600 wpa_supplicant[960]: Trying to associate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:22 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 15 20:49:22 user-Latitude-D600 kernel: [   76.512283] wlan0: authenticate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:22 user-Latitude-D600 kernel: [   76.513695] wlan0: authenticated
Jan 15 20:49:22 user-Latitude-D600 kernel: [   76.514421] wlan0: associate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:22 user-Latitude-D600 kernel: [   76.516960] wlan0: RX ReassocResp from 00:26:f2:8d:aa:87 (capab=0x431 status=0 aid=2)
Jan 15 20:49:22 user-Latitude-D600 kernel: [   76.516966] wlan0: associated
Jan 15 20:49:22 user-Latitude-D600 wpa_supplicant[960]: Associated with 00:26:f2:8d:aa:87
Jan 15 20:49:22 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 15 20:49:22 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 15 20:49:23 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 15 20:49:25 user-Latitude-D600 kernel: [   79.523712] wlan0: deauthenticated from 00:26:f2:8d:aa:87 (Reason: 2)
Jan 15 20:49:25 user-Latitude-D600 wpa_supplicant[960]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Jan 15 20:49:25 user-Latitude-D600 wpa_supplicant[960]: CTRL-EVENT-DISCONNECTED bssid=00:26:f2:8d:aa:87 reason=2
Jan 15 20:49:25 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan 15 20:49:25 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 15 20:49:27 user-Latitude-D600 wpa_supplicant[960]: Trying to authenticate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:27 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 15 20:49:27 user-Latitude-D600 wpa_supplicant[960]: Trying to associate with 00:26:f2:8d:aa:87 (SSID='Keith-Wireless1' freq=2452 MHz)
Jan 15 20:49:27 user-Latitude-D600 kernel: [   81.044286] wlan0: authenticate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:27 user-Latitude-D600 kernel: [   81.045677] wlan0: authenticated
Jan 15 20:49:27 user-Latitude-D600 kernel: [   81.046717] wlan0: associate with 00:26:f2:8d:aa:87 (try 1)
Jan 15 20:49:27 user-Latitude-D600 kernel: [   81.049299] wlan0: RX ReassocResp from 00:26:f2:8d:aa:87 (capab=0x431 status=0 aid=2)
Jan 15 20:49:27 user-Latitude-D600 kernel: [   81.049305] wlan0: associated
Jan 15 20:49:27 user-Latitude-D600 wpa_supplicant[960]: Associated with 00:26:f2:8d:aa:87
Jan 15 20:49:27 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 15 20:49:27 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 15 20:49:28 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 15 20:49:28 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Jan 15 20:49:28 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Jan 15 20:49:28 user-Latitude-D600 kernel: [   82.221949] wlan0: deauthenticating from 00:26:f2:8d:aa:87 by local choice (reason=3)
Jan 15 20:49:28 user-Latitude-D600 wpa_supplicant[960]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jan 15 20:49:28 user-Latitude-D600 NetworkManager[553]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
user@user-Latitude-D600:~$

---

### Post by wildmanne39 on 2012-01-15
Hi, please take the dash out of your SSID and that should help, also wpa2 works better then wpa, wep or mixed mode for encryption.
Thanks

---

### Post by kvalenza on 2012-01-16
I have no idea why it didn't work yesterday, but after doing everything that was suggested 24 hours ago (and it still didn't work then), my wireless is working perfectly today.

Thanks for your help! :-)

---

### Post by wildmanne39 on 2012-01-16
Hi, it could have just needed rebooting after what we tried.

Did you change the name of your network by taking out the dash? Just asking so I will be able to help the next person better.
Thanks

---

### Post by over_my_head on 2012-01-17
my computer is giving me the same problem

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux warkitten-HP-Pavilion-dv6700-Notebook-PC 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
```

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137c]
	Kernel driver in use: b43-pci-bridge
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30cc]
	Kernel driver in use: r8169
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
```


```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```

Module                  Size  Used by
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
arc4                   12473  2 
binfmt_misc            17292  1 
snd_rawmidi            25241  1 snd_seq_midi
b43                   318816  0 
mac80211              393459  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
r592                   17808  0 
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
cfg80211              172392  2 b43,mac80211
memstick               15857  1 r592
mtd                    35852  2 sm_common,nand
i915                  505159  3 
psmouse                73673  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ahci                   21634  2 
libahci                25727  1 ahci
ssb                    50682  1 b43
r8169                  43104  0 
```




running ```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```

gives me this output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/19.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 153612 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:014-9 (using .../b43-fwcutter_1%3a014-9_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Preparing to replace firmware-b43-installer 1:014-9 (using .../firmware-b43-installer_1%3a014-9_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:014-9) ...
Setting up firmware-b43-installer (1:014-9) ...
An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead.
Aborting.
```

any ideas?

---

### Post by wildmanne39 on 2012-01-17
Hi, please do:
```
sudo apt-get --purge remove b43-fwcutter firmware-b43-installer
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
```
sudo modprobe b43
```
see if it works.

Thank you bkratz I had missed that.
Thanks

---

### Post by bkratz on 2012-01-17
@wildmanne--I believe there is a typo in the third command

sudo modprobe b[COLOR="Red"]4[/COLOR]3

---

### Post by over_my_head on 2012-01-18
yep, it works!
Thanks!!:-)

---

### Post by wildmanne39 on 2012-01-18
Hi, over_my_head, your welcome! glad to help.

---

### Post by the_master on 2012-01-30
> **wildmanne39 said:**
> Hi, reinstall the driver and firmware by adding one extra command:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
then
```
sudo modprobe b43
```
see if it comes on if not post the out put of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

This worked for me on 11.10 with a bcm4318.  Thanks!

---

### Post by wildmanne39 on 2012-02-01
Hi, your welcome!

---

### Post by francium25 on 2012-06-04
Hi, my Broadcom wireless is not working like the others.

I am running Xubuntu 12.04 Precise Pangolin on my Dell Latitude D800 laptop, which previously came with Windows XP. Wireless was working fine on XP. Besides, I am not so familiar with Linux.

I have done some research on this and figured out that the correct package would be firmware-b43legacy-installer (which will automatically install b43-fwcutter).
> 02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridgeBCM4306 and Truemobile 1450, thus the b43legacy. ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access), [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)) In fact, if I attempt to install firmware-b43-installer, I get
> An unsupported BCM4301, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.I've installed, removed, and reinstalled b43-fwcutter, firmware-b43legacy-installer as well as firmware-b43-installer multiple times, but was not able to bring the wireless network up.  It complains most of the time 'device not ready (firmware missing)', and occasionally 'wireless is disabled' if I enable/disable it by selecting/de-selecting 'Enable Wireless.' All I get in the dmesg is:
> [ 2967.957530] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 2967.957537] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 2967.957541] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

I found there is a directory /lib/firmware/b43legacy (no b43 or b43-open there), which contains ucode5.fw. If I make a symbolic link of b43 to b43legacy (ln -s b43legacy b43) in /lib/firmware (definitely not the right thing to do), I get the following error messages in dmesg: > [ 4806.196082] b43-phy0 ERROR: YOUR FIRMWARE IS TOO OLD. Firmware from binary drivers older than version 4.x is unsupported. You must upgrade your firmware files.
[ 4806.196093] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

Any help is greatly appreciated. Again, I am running the latest Xubuntu.

iwlist scan: > wlan0     Interface doesn't support scanning : Network is down
iwconfig: > wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:onrfkill list all: > 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
nm-tool:> State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:0B:7D:22:01:E3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
lsmod:
> root@Latitude-D800:/lib/firmware/b43legacy# lsmod | grep b43
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43lsmod (full): > Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
b43                   342643  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39791  0 
mac80211              436455  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nouveau               708198  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87213  0 
serio_raw              13027  0 
ttm                    65344  1 nouveau
cfg80211              178679  2 b43,mac80211
drm_kms_helper         45466  1 nouveau
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
rfcomm                 38139  4 
drm                   197692  4 nouveau,ttm,drm_kms_helper
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
bcma                   25651  1 b43
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
bnep                   17830  2 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
mac_hid                13077  0 
parport_pc             32114  1 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
firewire_ohci          40180  0 
tg3                   137273  0 
ssb                    50691  1 b43
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

---

### Post by francium25 on 2012-06-05
Update - Following the instructions from ([www.linuxwireless.org/en/users/Drivers/b43](www.linuxwireless.org/en/users/Drivers/b43)) for "**Other distributions not mentioned above**" worked.

---

### Post by wildmanne39 on 2012-06-05
Hi, I am glad you got it sorted.

---

### Post by Idzi on 2012-06-05
> **wildmanne39 said:**
> Hi MFletcher99, this should get you going.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Also it says the hardware switch is off you need to find the keys that turn it on or the switch.
Thanks

Hi. Just wanted to say thanks. 
I had exactly the same problem with a Broadcom BCM4318 (on an old HP Compaq nx6110 running Ubuntu 11.04).  This bit of code to install new firmware solved the issue in one shot! 
Cheers.

---

### Post by mdjdevlin on 2012-12-16
> **carl4926 said:**
> @kvalenza

You need to uninstall the broadcom propriety driver and install the b43

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```


Thank you....you da man):P

---

