---
title: "Unable to connect with Ralink 3060 (it sees networks, but  can't connect)"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by emiliobi on 2012-01-06
Hello everyone,
On my desktop I have problems using wi-fi.
I tried several solution but none of them seemed to work.
Here are some results from terminal:

emiliobi@emiliobi-H55-HD:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 10:9A:DD:85:F8:9B
                    Protocol:802.11b/g/n
                    ESSID:"Airport Extreme Villa Bianca"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:65/100  Signal level:-64 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

emiliobi@emiliobi-H55-HD:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:06.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

Thanks in advance for any possible solutions!

---

### Post by emiliobi on 2012-01-06
By the way, I'm on Ubuntu 11.10 

Thanks again!

---

### Post by wildmanne39 on 2012-01-06
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

### Post by emiliobi on 2012-01-06
```
Hello! Thanks for the prompt answer!


emiliobi@emiliobi-H55-HD:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux emiliobi-H55-HD 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

emiliobi@emiliobi-H55-HD:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  03)
    Subsystem: Biostar Microtech Int'l Corp Device [1565:2309]
    Kernel driver in use: r8169
--
05:06.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
    Subsystem: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
    Kernel driver in use: rt2860


emiliobi@emiliobi-H55-HD:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 10:9A:DD:85:F8:9B   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-68 dBm  Noise level:-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


emiliobi@emiliobi-H55-HD:~$ rfkill list all
emiliobi@emiliobi-H55-HD:~$ 

emiliobi@emiliobi-H55-HD:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
vesafb                 13809  1 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
fglrx                2928969  171 
rt3562sta             990799  1 
psmouse                73882  0 
serio_raw              13166  0 
intel_ips              18089  0 
ppdev                  17113  0 
parport_pc             36962  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
hid_apple              13375  0 
usbhid                 47198  0 
hid                    95463  2 hid_apple,usbhid
r8169                  52788  0 
pata_via               13670  0 

```

---

### Post by wildmanne39 on 2012-01-06
Hi, did you compile or install more then one driver?
Please show:
```
lsmod | grep -e rt2 -e rt3
```
Thanks

---

### Post by emiliobi on 2012-01-06
Maybe, I'm not sure..

```

emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             990799  1 
emiliobi@emiliobi-H55-HD:~$ 

```

---

### Post by wildmanne39 on 2012-01-06
Hi, run these commands please:
```
sudo rmmod -f rt3562sta
```
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
Add a single line:
```
options rt2800pci nohwcrypt=1
```
Proofread carefully, save and close gedit.
Then:
```
sudo modprobe rt2800pci
```
Reboot

---

### Post by emiliobi on 2012-01-06
Hi again,
tried everystep,
had some problem reebooting (it freezed two times), but now wireless
says "connected" but just wired connection work.

By the way I had another issue:
```

emiliobi@emiliobi-H55-HD:~$ sudo rmmod -f rt3562sta
[sudo] password for emiliobi: 
ERROR: Removing 'rt3562sta': Resource temporarily unavailable
emiliobi@emiliobi-H55-HD:~$ 

```

So before I can run this command I had to disable wireless

---

### Post by wildmanne39 on 2012-01-06
Hi, please post the output of these commands again now that you have run the previous commands.
```
lsmod | grep -e rt2 -e rt3
``` 
```
rfkill list all
```
```
iwconfig
```

---

### Post by emiliobi on 2012-01-06
Hi

```
emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             990799  1 

emiliobi@emiliobi-H55-HD:~$ rfkill list all
emiliobi@emiliobi-H55-HD:~$ 

emiliobi@emiliobi-H55-HD:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 10:9A:DD:85:F8:9B   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level:-60 dBm  Noise level:-60 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

---

### Post by emiliobi on 2012-01-06
Thanks again :)

---

### Post by wildmanne39 on 2012-01-06
Hi, you still have a driver that is wrong we are going to blacklist it. 
```
echo "blacklist rt3562sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Post the outcome of:
```
cat /etc/modprobe.d/rt2800pci.conf
```
```
nm-tool
```
```
sudo apt-get install rfkill
```
then run:
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod
```
```
ndiswrapper -l
```
Please make sure you copy and paste all commands for accuracy.
Thanks

---

### Post by emiliobi on 2012-01-07
Hi again,


```

emiliobi@emiliobi-H55-HD:~$ cat /etc/modprobe.d/rt2800pci.conf
options rt2800pci nohwcrypt=1


```

```

emiliobi@emiliobi-H55-HD:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:30:67:8F:77:DC

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        00:1F:1F:D9:41:B7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Airport Extreme Villa Bianca: Infra, 10:9A:DD:85:F8:9B, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2

```

```

emiliobi@emiliobi-H55-HD:~$ sudo apt-get install rfkill
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
rfkill è già alla versione più recente.
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.


```

Translation: rfkill most recent version
0 updated, 0 installed, 0 to remove, 0 not updated

```

emiliobi@emiliobi-H55-HD:~$ rfkill list all
emiliobi@emiliobi-H55-HD:~$ 

```

```

emiliobi@emiliobi-H55-HD:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 10:9A:DD:85:F8:9B
                    Protocol:802.11b/g/n
                    ESSID:"Airport Extreme Villa Bianca"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:65/100  Signal level:-64 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```

```

emiliobi@emiliobi-H55-HD:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
vesafb                 13809  1 
binfmt_misc            17540  1 
hid_apple              13375  0 
usbhid                 47198  0 
hid                    95463  2 hid_apple,usbhid
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  17113  0 
rt3562sta             990799  1 
snd_rawmidi            30547  1 snd_seq_midi
parport_pc             36962  1 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
fglrx                2928969  98 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              18089  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
r8169                  52788  0 
pata_via               13670  0 


```

```

emiliobi@emiliobi-H55-HD:~$ ndiswrapper -l
Il programma "ndiswrapper" non è attualmente installato.  È possibile installarlo digitando:
sudo apt-get install ndiswrapper-common


```

Translation: "ndiswrapper actually is not installed. It's possible to install it with:
sudo apt-get install ndiswrapper-common


Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, please post the output of:
```
cat /etc/modprobe.d/blacklist.conf
```
```
sudo cat /var/log/syslog | grep -e rt3 -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by emiliobi on 2012-01-07
Hello!

```

emiliobi@emiliobi-H55-HD:~$ cat /etc/modprobe.d/blacklist.conf
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

blacklist rt2800pci

blacklist rt3562sta


```
```

emiliobi@emiliobi-H55-HD:~$ sudo cat /var/log/syslog | grep -e rt3 -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
[sudo] password for emiliobi: 
Jan  7 08:37:44 emiliobi-H55-HD kernel: [ 2081.446608] ===> rt28xx_close
Jan  7 08:37:44 emiliobi-H55-HD kernel: [ 2081.451848] <=== rt28xx_close
Jan  7 08:37:44 emiliobi-H55-HD kernel: [ 2082.207224] rt28xx_get_wireless_stats --->
Jan  7 08:37:46 emiliobi-H55-HD kernel: [ 2084.296757] <==== rt28xx_init, Status=0
Jan  7 08:37:48 emiliobi-H55-HD kernel: [ 2086.260602] rt28xx_get_wireless_stats --->
Jan  7 08:37:48 emiliobi-H55-HD kernel: [ 2086.260604] <--- rt28xx_get_wireless_stats
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.472125] ===> rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.477444] <=== rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.511531] <==== rt28xx_init, Status=0
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.926697] ===> rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.931945] <=== rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.966100] <==== rt28xx_init, Status=0
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2087.317680] ===> rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2087.322893] <=== rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2087.357114] <==== rt28xx_init, Status=0
Jan  7 12:01:05 emiliobi-H55-HD NetworkManager[872]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 22:29:14 emiliobi-H55-HD NetworkManager[850]: <info> monitoring kernel firmware directory '/lib/firmware'.


```Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, the driver we need is blacklisted let's fix that.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Then remove ```
blacklist rt2800pci
```
Then close gedit, save and reboot.

Then if it does not come on:
```
sudo modprobe rt2800pci
```
Thanks

---

### Post by emiliobi on 2012-01-07
Hi,
I had to force reebot with reset button twice, I'm scared I made something wrong in the past..

I tried to remove "blacklist rt2800 pci" as you said

It didn't work :(

Then I tried also "sudo modprobe rt2800pci", before this step I couldn't see wireless connection, but this didn't work too.

Thanks!

---

### Post by wildmanne39 on 2012-01-07
Hi, > I tried to remove "blacklist rt2800 pci" as you said what happened exactly?
Thanks

---

### Post by emiliobi on 2012-01-07
Hi,

I removed it, but then as I tried to reboot I had to force it with reset button.
I just checked, the file is gone :) 

Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, okay
```
sudo cat /var/log/syslog | grep -e rt3 -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
```
```
lsmod | grep -e rt2 -e r3
```

Please post all the information and do not edit.

I am looking to see if unblacklisting the driver changed the information like it was suppose too.
Thanks

---

### Post by emiliobi on 2012-01-07
Hi

```

emiliobi@emiliobi-H55-HD:~$ sudo cat /var/log/syslog | grep -e rt3 -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
[sudo] password for emiliobi: 
Jan  7 08:37:44 emiliobi-H55-HD kernel: [ 2081.446608] ===> rt28xx_close
Jan  7 08:37:44 emiliobi-H55-HD kernel: [ 2081.451848] <=== rt28xx_close
Jan  7 08:37:44 emiliobi-H55-HD kernel: [ 2082.207224] rt28xx_get_wireless_stats --->
Jan  7 08:37:46 emiliobi-H55-HD kernel: [ 2084.296757] <==== rt28xx_init, Status=0
Jan  7 08:37:48 emiliobi-H55-HD kernel: [ 2086.260602] rt28xx_get_wireless_stats --->
Jan  7 08:37:48 emiliobi-H55-HD kernel: [ 2086.260604] <--- rt28xx_get_wireless_stats
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.472125] ===> rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.477444] <=== rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.511531] <==== rt28xx_init, Status=0
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.926697] ===> rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.931945] <=== rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2086.966100] <==== rt28xx_init, Status=0
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2087.317680] ===> rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2087.322893] <=== rt28xx_close
Jan  7 08:37:49 emiliobi-H55-HD kernel: [ 2087.357114] <==== rt28xx_init, Status=0
Jan  7 12:01:05 emiliobi-H55-HD NetworkManager[872]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 22:29:14 emiliobi-H55-HD NetworkManager[850]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 22:47:29 emiliobi-H55-HD NetworkManager[852]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 22:49:05 emiliobi-H55-HD kernel: [  110.817796] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  7 22:49:05 emiliobi-H55-HD kernel: [  110.863177] Registered led device: rt2800pci-phy0::radio
Jan  7 22:49:05 emiliobi-H55-HD kernel: [  110.863193] Registered led device: rt2800pci-phy0::assoc
Jan  7 22:49:05 emiliobi-H55-HD kernel: [  110.863206] Registered led device: rt2800pci-phy0::quality
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:06.0/net/wlan0, iface: wlan0)
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:06.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): now managed
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): bringing up device.
Jan  7 22:49:05 emiliobi-H55-HD kernel: [  110.927774] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): preparing device.
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  7 22:49:05 emiliobi-H55-HD kernel: [  110.954210] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 22:49:05 emiliobi-H55-HD dbus[838]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  7 22:49:05 emiliobi-H55-HD dbus[838]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> wpa_supplicant started
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  7 22:49:05 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan  7 22:49:23 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jan  7 22:49:23 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan  7 22:49:23 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): taking down device.
Jan  7 22:49:25 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): bringing up device.
Jan  7 22:49:25 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): bringing up device.
Jan  7 22:49:25 emiliobi-H55-HD kernel: [  130.825753] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 22:49:25 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  7 22:49:25 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  7 22:49:25 emiliobi-H55-HD NetworkManager[852]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan  7 22:51:02 emiliobi-H55-HD NetworkManager[870]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 22:52:09 emiliobi-H55-HD kernel: [   81.156972] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  7 22:52:09 emiliobi-H55-HD kernel: [   81.194001] Registered led device: rt2800pci-phy0::radio
Jan  7 22:52:09 emiliobi-H55-HD kernel: [   81.194019] Registered led device: rt2800pci-phy0::assoc
Jan  7 22:52:09 emiliobi-H55-HD kernel: [   81.194032] Registered led device: rt2800pci-phy0::quality
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:06.0/net/wlan0, iface: wlan0)
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:06.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): now managed
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 22:52:09 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): bringing up device.
Jan  7 22:52:10 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): preparing device.
Jan  7 22:52:10 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  7 22:52:10 emiliobi-H55-HD dbus[841]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  7 22:52:10 emiliobi-H55-HD kernel: [   81.263462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 22:52:10 emiliobi-H55-HD dbus[841]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  7 22:52:10 emiliobi-H55-HD NetworkManager[870]: <info> wpa_supplicant started
Jan  7 22:52:10 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  7 22:52:10 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  7 22:52:10 emiliobi-H55-HD NetworkManager[870]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan  8 00:19:47 emiliobi-H55-HD NetworkManager[840]: <info> monitoring kernel firmware directory '/lib/firmware'.


```

```

emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e r3
emiliobi@emiliobi-H55-HD:~$ 


```


Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, please try this one more time now that the 3562 driver is not loaded.
```
sudo modprobe rt2800pci
``` if that does not work please post:
```
modinfo rt2800pci
```
Thanks

---

### Post by emiliobi on 2012-01-07
Hi,

it doesn't work,

```

emiliobi@emiliobi-H55-HD:~$ modinfo rt2800pci
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     677D1338C62142695060FD2
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-14-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


```

Thanks!

---

### Post by wildmanne39 on 2012-01-07
Hi, I have asked a friend to take a look.
Thanks

---

### Post by emiliobi on 2012-01-07
Hi, thank you for your time :)

---

### Post by chili555 on 2012-01-07
You never did get rt3562sta to not load and rt2800pci to load correctly. Let's start there:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If rt2800pci is in there, remove it. Add:```
blacklist rt3562sta
```Proofread carefully, save and close gedit. Reboot and show us:```
lsmod | grep -e rt2 -e rt3
```If rt2800pci is loaded and not rt3562sta, then run:```
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by emiliobi on 2012-01-07
Hi, everytime I try to modify blacklist.conf I can't shut down or reboot, I have to press reset button. (Is that a coincidence?)


```

blacklist rt3562sta

```

was already in blacklist.conf

```

emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e rt3
emiliobi@emiliobi-H55-HD:~$ 

```

```

emiliobi@emiliobi-H55-HD:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

```

emiliobi@emiliobi-H55-HD:~$ sudo iwlist wlan0 scan
[sudo] password for emiliobi: 
wlan0     Interface doesn't support scanning.

```

---

### Post by emiliobi on 2012-01-07
Thanks!

---

### Post by chili555 on 2012-01-07
Please do:```
sudo modprobe rt2800pci
iwconfig
dmesg | grep rt2
```

---

### Post by emiliobi on 2012-01-08
Hi 

```

emiliobi@emiliobi-H55-HD:~$ sudo modprobe rt2800pci
[sudo] password for emiliobi: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.


```After this command wireless connection appear in the available connections, but it can't see my wifi network.

```

emiliobi@emiliobi-H55-HD:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


``````

emiliobi@emiliobi-H55-HD:~$ dmesg | grep rt2
[  261.582693] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  261.627941] Registered led device: rt2800pci-phy0::radio
[  261.627956] Registered led device: rt2800pci-phy0::assoc
[  261.627970] Registered led device: rt2800pci-phy0::quality
[  261.693344] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware


```

Thanks

---

### Post by chili555 on 2012-01-08
> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareFascinating...

Let's be sure no other driver is loaded:```
lsmod | grep -e rt2 -e rt3
```Let's be sure we have the firmware:```
md5sum /lib/firmware/rt2860.bin
```> but it can't see my wifi network.Does it see any?```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by emiliobi on 2012-01-08
Hi

```

emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e rt3
emiliobi@emiliobi-H55-HD:~$ 


```

```

emiliobi@emiliobi-H55-HD:~$ md5sum /lib/firmware/rt2860.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin


```

```

emiliobi@emiliobi-H55-HD:~$ sudo iwlist wlan0 scan
[sudo] password for emiliobi: 
wlan0     Interface doesn't support scanning.


```

Thanks.

---

### Post by chili555 on 2012-01-08
> emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e rt3
emiliobi@emiliobi-H55-HD:~$So neither rt2800pci *NOR* rt3562sta are loaded??? What _is_ driving your device? Please post:```
sudo lshw -C network
lsmod
```

---

### Post by emiliobi on 2012-01-08
Hi

> 
So neither rt2800pci *NOR* rt3562sta are loaded??? What _is_ driving your device? Please post:
I really don't know... what I did was try to solve with this post I found on the net:

```

http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/

``````

http://askubuntu.com/questions/84959/ralink-rt3060-driver-not-working

```For sometimes it worked on 11.04 with the first method, then I updated and everything ended to work...

```

emiliobi@emiliobi-H55-HD:~$ sudo lshw -C network
[sudo] password for emiliobi: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 00:30:67:8f:77:dc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:e800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbee0000-fbefffff
  *-network UNCLAIMED
       description: Network controller
       product: RT3060 Wireless 802.11n 1T/1R
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
       resources: memory:fbff0000-fbffffff


``````

emiliobi@emiliobi-H55-HD:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
vesafb                 13809  1 
binfmt_misc            17540  1 
hid_apple              13375  0 
usbhid                 47198  0 
hid                    95463  2 hid_apple,usbhid
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
ppdev                  17113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
parport_pc             36962  1 
fglrx                2928969  102 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
intel_ips              18089  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
r8169                  52788  0 
pata_via               13670  0 


```Thanks!

---

### Post by chili555 on 2012-01-08
That was written for Ubuntu 10.04 and it was the proper procedure at the time. The in-kernel driver rt2800pci has undergone quite a bit of development and is (mostly) working in 11.10. Let's try to figure out why it isn't loading automatically. Please post:```
cat /etc/modprobe.d/blacklist.conf.save
cat /etc/modprobe.d/blacklist.conf
```We'll try to fix up your warning and tidy up your blacklists.

Now do:```
sudo modprobe rt2800pci
sudo iwlist wlan0 scan
```Thanks.

---

### Post by emiliobi on 2012-01-08
Hi

```

emiliobi@emiliobi-H55-HD:~$ cat /etc/modprobe.d/blacklist.conf.save
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

blacklist rt20


``````

emiliobi@emiliobi-H55-HD:~$ cat /etc/modprobe.d/blacklist.conf
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



blacklist rt3562sta


``````

emiliobi@emiliobi-H55-HD:~$ sudo modprobe rt2800pci
[sudo] password for emiliobi: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.


``````

emiliobi@emiliobi-H55-HD:~$ sudo iwlist wlan0 scan
wlan0     No scan results


```Thanks

---

### Post by chili555 on 2012-01-09
The 'save' file has nothing in it we need to save, so let's get rid of our warning:```
sudo rm /etc/modprobe.d/blacklist.conf.save
```Before we get out the scalpel and do major surgery, let's have a look at:```
sudo modprobe rt2800pci
dmesg | grep -e rt2 -e wlan
```

---

### Post by emiliobi on 2012-01-09
Hi

```

emiliobi@emiliobi-H55-HD:~$ sudo rm /etc/modprobe.d/blacklist.conf.save
[sudo] password for emiliobi: 
emiliobi@emiliobi-H55-HD:~$

```

```

emiliobi@emiliobi-H55-HD:~$ sudo modprobe rt2800pci
emiliobi@emiliobi-H55-HD:~$

```

```

emiliobi@emiliobi-H55-HD:~$ dmesg | grep -e rt2 -e wlan
[  226.110758] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  226.154743] Registered led device: rt2800pci-phy0::radio
[  226.154757] Registered led device: rt2800pci-phy0::assoc
[  226.154771] Registered led device: rt2800pci-phy0::quality
[  226.221108] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  226.245558] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```


Thanks

---

### Post by chili555 on 2012-01-09
I noticed this: [http://lists.debian.org/debian-kernel/2011/02/msg00460.html](http://lists.debian.org/debian-kernel/2011/02/msg00460.html)> rt2800pci/ rt2800usb are fine, but the firmware images shipped as 
rt2860.bin (v11) and rt2870.bin (v12) in firmware-ralink appear to be 
too old for reliable operations, especially for rt30x0 (>> v17/ v19 
required) and rt35xx. Using the the plain versions shipped in 
firmware-ralink I notice the same problems, scanning works, even auth 
succeeds, but there is no actual traffic passing through.Attached is a zipped copy of the firmware. Download it to your desktop. Right-click it and select 'Extract Here.' Now, in a terminal, do:```
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.bak
cd Desktop/RT2860_Firmware_V26
sudo cp rt2860.bin /lib/firmware
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
dmesg | grep rt2
```Have we gotten rid of the MCU error? Have we connected?

---

### Post by emiliobi on 2012-01-09
Hi, after the procedure a menu with the hardware logo appeared on top panel, I clicked on it  and a window opened (I attach a screen-shot), saying (translation):
"Proprietary drivers do not have public source code that Ubuntu developers can freely modify. Security updates and corrections only depend on the manufacturer. Ubuntu can not change or improve these drivers."

Wi-fi still not working..
What I have to do? Activate the driver or not?

Many thanks!

---

### Post by emiliobi on 2012-01-09
Hi, missing something important!

```

emiliobi@emiliobi-H55-HD:~$ dmesg | grep rt2
[  226.110758] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  226.154743] Registered led device: rt2800pci-phy0::radio
[  226.154757] Registered led device: rt2800pci-phy0::assoc
[  226.154771] Registered led device: rt2800pci-phy0::quality
[  226.221108] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[ 7039.590060] rt2800pci 0000:05:06.0: PCI INT A disabled
[ 7053.355681] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7053.358363] Registered led device: rt2800pci-phy0::radio
[ 7053.358381] Registered led device: rt2800pci-phy0::assoc
[ 7053.358398] Registered led device: rt2800pci-phy0::quality
[ 7053.366697] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
[ 7123.278639] rt2800pci 0000:05:06.0: PCI INT A disabled
[ 7131.143600] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7131.146582] Registered led device: rt2800pci-phy0::radio
[ 7131.146822] Registered led device: rt2800pci-phy0::assoc
[ 7131.147079] Registered led device: rt2800pci-phy0::quality


```

Thanks

---

### Post by chili555 on 2012-01-09
Please let me see:```
ls -al /lib/firmware | grep rt28
md5sum /lib/firmware/rt2860.bin
```


-------
note to chili:
$ md5sum /home/chili/Desktop/Forum/RT2860_Firmware_V26/rt2860.bin
66332d7636ee78db31b056aa0e44b097

---

### Post by emiliobi on 2012-01-09
Hi,

```

emiliobi@emiliobi-H55-HD:~$ ls -al /lib/firmware | grep rt28
-rw-r--r--  1 root root    8192 2012-01-09 17:46 rt2860.bak
-rw-r--r--  1 root root    8192 2011-08-23 15:23 rt2870.bin
lrwxrwxrwx  1 root root      10 2011-08-23 15:23 rt3070.bin -> rt2870.bin
lrwxrwxrwx  1 root root      10 2011-08-23 15:23 rt3090.bin -> rt2860.bin


```

```

emiliobi@emiliobi-H55-HD:~$ md5sum /lib/firmware/rt2860.bin
md5sum: /lib/firmware/rt2860.bin: File o directory non esistente


```

Something went wrong on the previous procedure?
Thanks

---

### Post by chili555 on 2012-01-09
> Something went wrong on the previous procedure?Yes, indeed. Let's retrace our steps. Is the file on your desktop?```
ls Desktop/RT2860_Firmware_V26
```You should see:```
LICENSE.ralink-firmware.txt  rt2860.bin
```Now, let's copy the .bin file over:```
sudo cp Desktop/RT2860_Firmware_V26/rt2860.bin /lib/firmware
```Now see if it actually arrived:```
ls -al /lib/firmware | grep rt28
```Is the rt2860.bin file there? Which version?```
md5sum /lib/firmware/rt2860.bin
```If it's 66332d7636ee78db31b056aa0e44b097, then it is there and the right version and so we try again:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
dmesg | grep rt2
```> "Proprietary drivers do not have public source code that Ubuntu developers can freely modify. Security updates and corrections only depend on the manufacturer. Ubuntu can not change or improve these drivers."Ignore for now.

---

### Post by emiliobi on 2012-01-09
Hi,

```

emiliobi@emiliobi-H55-HD:~$ sudo cp '/home/emiliobi/RT2860_Firmware_V26/rt2860.bin' /lib/firmware
[sudo] password for emiliobi: 


```

(I put the file in home directory since desktop was under other folders, I think is the italian version, can it be?)
```

emiliobi@emiliobi-H55-HD:~$ ls -al /lib/firmware | grep rt28
-rw-r--r--  1 root root    8192 2012-01-09 17:46 rt2860.bak
-rw-r--r--  1 root root    8192 2012-01-09 18:54 rt2860.bin
-rw-r--r--  1 root root    8192 2011-08-23 15:23 rt2870.bin
lrwxrwxrwx  1 root root      10 2011-08-23 15:23 rt3070.bin -> rt2870.bin
lrwxrwxrwx  1 root root      10 2011-08-23 15:23 rt3090.bin -> rt2860.bin


```

```

emiliobi@emiliobi-H55-HD:~$ md5sum /lib/firmware/rt2860.bin
66332d7636ee78db31b056aa0e44b097  /lib/firmware/rt2860.bin


```

```

emiliobi@emiliobi-H55-HD:~$ sudo modprobe -r rt2800pci


```

```

emiliobi@emiliobi-H55-HD:~$ sudo modprobe rt2800pci


```

```

emiliobi@emiliobi-H55-HD:~$ dmesg | grep rt2
[  226.110758] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  226.154743] Registered led device: rt2800pci-phy0::radio
[  226.154757] Registered led device: rt2800pci-phy0::assoc
[  226.154771] Registered led device: rt2800pci-phy0::quality
[  226.221108] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[ 7039.590060] rt2800pci 0000:05:06.0: PCI INT A disabled
[ 7053.355681] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7053.358363] Registered led device: rt2800pci-phy0::radio
[ 7053.358381] Registered led device: rt2800pci-phy0::assoc
[ 7053.358398] Registered led device: rt2800pci-phy0::quality
[ 7053.366697] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
[ 7123.278639] rt2800pci 0000:05:06.0: PCI INT A disabled
[ 7131.143600] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7131.146582] Registered led device: rt2800pci-phy0::radio
[ 7131.146822] Registered led device: rt2800pci-phy0::assoc
[ 7131.147079] Registered led device: rt2800pci-phy0::quality
[11400.325300] rt2800pci 0000:05:06.0: PCI INT A disabled
[11437.750152] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[11437.752619] Registered led device: rt2800pci-phy0::radio
[11437.752637] Registered led device: rt2800pci-phy0::assoc
[11437.752651] Registered led device: rt2800pci-phy0::quality


```

---

### Post by emiliobi on 2012-01-09
Hi,

I didn't mentioned that I'm on 64 bit

Thanks again

---

### Post by wildmanne39 on 2012-01-09
Hi, I see the surgeon is operating, no wonder I got stuck.
Thanks

---

### Post by emiliobi on 2012-01-09
Thank you both for your time guys!

I really made some mess...I should have contact you before!

---

### Post by wildmanne39 on 2012-01-09
Hi, don't give up if anyone can get you through this it is chili.
Thanks

---

### Post by chili555 on 2012-01-09
> [11400.325300] rt2800pci 0000:05:06.0: PCI INT A disabled
[11437.750152] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[11437.752619] Registered led device: rt2800pci-phy0::radio
[11437.752637] Registered led device: rt2800pci-phy0::assoc
[11437.752651] Registered led device: rt2800pci-phy0::qualityThis looks pretty solid. Now does it scan?```
sudo iwlist wlan0 scan
```If there is no result, let's see if the newer firmware works better with rt3562sta:```
sudo modprobe -r rt2800pci
sudo modprobe rt3562sta
sudo iwlist ra0 scan
```

---

### Post by emiliobi on 2012-01-09
Hi

```

emiliobi@emiliobi-H55-HD:~$ sudo iwlist wlan0 scan
[sudo] password for emiliobi: 
wlan0     No scan results


```

```

emiliobi@emiliobi-H55-HD:~$ sudo modprobe -r rt2800pci
emiliobi@emiliobi-H55-HD:~$

```

```

emiliobi@emiliobi-H55-HD:~$ sudo modprobe rt3562sta
emiliobi@emiliobi-H55-HD:~$

```

```

emiliobi@emiliobi-H55-HD:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 10:9A:DD:85:F8:9B
                    Protocol:802.11b/g/n
                    ESSID:"Airport Extreme Villa Bianca"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:60/100  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```

It sees the network but it won't connect :(

Thanks

---

### Post by emiliobi on 2012-01-09
Hi,

do I have to reebot?

Thanks

---

### Post by wildmanne39 on 2012-01-09
Hi, no.
thanks

---

### Post by chili555 on 2012-01-09
I wonder if it won't connect because there are spaces in the name of the SSID? Can this be changed? Are there any clues here?```
sudo cat /var/log/syslog | grep -e ra0 -e etwork | tail -n25
```

---

### Post by emiliobi on 2012-01-09
Hi

nope :( I just checked and to be sure I tried on the  Teminal in an other computer:

```

  	 	 	 	 	 	   Last login: Mon Jan  9 23:21:38 on ttys000
 host569:~ emiliobiancardi$ sudo ln -s /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport
 host569:~ emiliobiancardi$ airport -I
      agrCtlRSSI: -65
      agrExtRSSI: 0
     agrCtlNoise: -96
     agrExtNoise: 0
           state: running
         op mode: station  
      lastTxRate: 130
         maxRate: 130
 lastAssocStatus: 0
     802.11 auth: open
       link auth: wpa2-psk
           BSSID: 10:9a:dd:85:f8:9b
            SSID: Airport Extreme Villa Bianca
             MCS: 15
         channel: 1
 host569:~ emiliobiancardi$  
  

```

```

emiliobi@emiliobi-H55-HD:~$ sudo cat /var/log/syslog | grep -e ra0 -e etwork | tail -n25
[sudo] password for emiliobi: 
Jan  9 23:10:11 emiliobi-H55-HD kernel: [26481.992768] Set_NetworkType_Proc::(NetworkType=1)
Jan  9 23:10:11 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: scanning -> associating
Jan  9 23:10:12 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: associating -> 4-way handshake
Jan  9 23:10:16 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: 4-way handshake -> disconnected
Jan  9 23:10:16 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: disconnected -> scanning
Jan  9 23:10:18 emiliobi-H55-HD kernel: [26488.316040] ===>Set_NetworkType_Proc::(INFRA)
Jan  9 23:10:18 emiliobi-H55-HD kernel: [26488.316042] Set_NetworkType_Proc::(NetworkType=1)
Jan  9 23:10:18 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: scanning -> associating
Jan  9 23:10:18 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: associating -> 4-way handshake
Jan  9 23:10:20 emiliobi-H55-HD NetworkManager[938]: <warn> Activation (ra0/wireless): association took too long.
Jan  9 23:10:20 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  9 23:10:20 emiliobi-H55-HD NetworkManager[938]: <warn> Activation (ra0/wireless): asking for new secrets
Jan  9 23:10:20 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): supplicant interface state: 4-way handshake -> disconnected
Jan  9 23:10:20 emiliobi-H55-HD NetworkManager[938]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <warn> No agents were available for this request.
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <warn> Activation (ra0) failed for access point (Airport Extreme Villa Bianca)
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <info> Marking connection 'Auto Airport Extreme Villa Bianca' invalid.
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <warn> Activation (ra0) failed.
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <info> (ra0): deactivating device (reason 'none') [0]
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jan  9 23:12:20 emiliobi-H55-HD NetworkManager[938]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jan  9 23:12:20 emiliobi-H55-HD kernel: [26610.453189] ===>Set_NetworkType_Proc::(INFRA)
Jan  9 23:12:20 emiliobi-H55-HD kernel: [26610.453190] Set_NetworkType_Proc::(NetworkType=1)


```

Thanks

---

### Post by emiliobi on 2012-01-09
the second code is the one from ubuntu of course :)

---

### Post by emiliobi on 2012-01-09
Hi,
do you mean that the name will influence the stability of the connection?

I didn't understand sorry

But one time it worked with the long name, i will try with another router and different name.

Thanks

---

### Post by emiliobi on 2012-01-09
Hi,

I tried with the iPhone's wifi hotspot: it connects for 1 o 2 seconds but then it disappear.

Thanks

---

### Post by emiliobi on 2012-01-09
Here the code:
```

emiliobi@emiliobi-H55-HD:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 10:9A:DD:85:F8:9B
                    Protocol:802.11b/g/n
                    ESSID:"Airport Extreme Villa Bianca"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-42 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 72:EA:D6:0E:4B:38
                    Protocol:802.11g
                    ESSID:"iPhone di Emilio Biancardi"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:100/100  Signal level:-46 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK



```

Thanks

---

### Post by emiliobi on 2012-01-09
Hello Guys, sorry for disturbing you again, I'm having other issues...
I'm stucked :(
I was trying to change compiz config preferences and the dock on the left disappeared now I reeboted and I still can't see it..
And I can't open Terminal too...even with alt+f2..nor other application..

Since I already backed-up all the files before (not many programs, I can install them in an hour) can it be a good idea to re-install with a fresh dvd?

Let me know what do you think

Really many thanks

---

### Post by wildmanne39 on 2012-01-09
Hi, we are suppose to stick to the topic but here is a link to fix the launcher and wait on chili555 before reinstalling please.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thanks

---

### Post by emiliobi on 2012-01-09
Hi,
Sorry to go off-topic
I will wait for chili555.
You guys make Ubuntu special!

Thanks

---

### Post by chili555 on 2012-01-09
So, is your compiz, etc. working now? When you compiled rt3562sta, did you make the change in os/linux/config.mk to instruct the driver to use Network Manager?

---

### Post by emiliobi on 2012-01-10
HI
> 
 When you compiled rt3562sta, did you make the change in os/linux/config.mk to instruct the driver to use Network Manager? 	


Yes I remember that. Something like "has wpa supplicant" to set as yes instead of no.

 I'm not out of the previous situation, I'm scared that modification made in Natty are affecting Oneiric now.  (More than one, that was the very first time I installed Ubuntu, you can imagine how messy I could have been...) 

I will try again the solution provided by wildmanne39.

If nothing work You think re-install 32bit (instead of 64bit) version will be better also for network driver, etc.?

Again, many thanks!

---

### Post by chili555 on 2012-01-10
I am not yet to the re-install point. Do you know you can dual-boot the 32-bit version, that is, install it along-side the 64-bit?> Something like "has wpa supplicant" to set as yes instead of no.
...as well as Network Manager=y. Do you have the file on your Desktop or Downloads or somewhere? Can you check the file?

---

### Post by emiliobi on 2012-01-10
Hi

> 
Do you know you can dual-boot the 32-bit version, that is, install it along-side the 64-bit?


I didn't know :)

I checked the file:
```

# Support ATE function
HAS_ATE=n

# Support QA ATE function
HAS_QA_SUPPORT=n

# Support XLINK mode
HAS_XLINK=n


# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

#Support Net interface block while Tx-Sw queue full
HAS_BLOCK_NET_IF=n

#Support DFS function
HAS_DFS_SUPPORT=n

#Support Carrier-Sense function
HAS_CS_SUPPORT=n


# Support for Multiple Cards
HAS_MC_SUPPORT=n

#Support for PCI-MSI
HAS_MSI_SUPPORT=n


#Support for IEEE802.11e DLS
HAS_QOS_DLS_SUPPORT=n

#Support for EXT_CHANNEL
HAS_EXT_BUILD_CHANNEL_LIST=n


#Support for Net-SNMP
HAS_SNMP_SUPPORT=n

#Support features of 802.11n Draft3
HAS_DOT11N_DRAFT3_SUPPORT=y

#Support features of Single SKU. 
HAS_SINGLE_SKU_SUPPORT=n

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=y


HAS_KTHREAD_SUPPORT=n


#Support statistics count
HAS_STATS_COUNT=y


#Client support WDS function
HAS_CLIENT_WDS_SUPPORT=n

#Support for Bridge Fast Path & Bridge Fast Path function open to other module
HAS_BGFP_SUPPORT=n
HAS_BGFP_OPEN_SUPPORT=n

#Support MAC80211 LINUX-only function
HAS_CFG80211_SUPPORT=n

#Support RFKILL hardware block/unblock LINUX-only function
HAS_RFKILL_HW_SUPPORT=y


#Support Restore Credential back to profile
HAS_CREDENTIAL_STORE_SUPPORT=y

#Support to show the MAC address without bring up interface. 
HAS_PRE_ASSIGN_MAC_ADDR=y

HAS_RESOURCE_PRE_ALLOC=y

HAS_BT_COEXISTENCE_SUPPORT=y
#################################################

CC := $(CROSS_COMPILE)gcc
LD := $(CROSS_COMPILE)ld

WFLAGS := -DAGGREGATION_SUPPORT -DPIGGYBACK_SUPPORT -DWMM_SUPPORT  -DLINUX -Wall -Wstrict-prototypes -Wno-trigraphs 
WFLAGS += -DSYSTEM_LOG_SUPPORT -DLED_CONTROL_SUPPORT -DPROFILE_STORE -DPRE_ASSIGN_MAC_ADDR



ifeq ($(HAS_RESOURCE_PRE_ALLOC),y)
WFLAGS += -DRESOURCE_PRE_ALLOC
endif

ifeq ($(HAS_KTHREAD_SUPPORT),y)
WFLAGS += -DKTHREAD_SUPPORT
endif

ifeq ($(HAS_RTMP_FLASH_SUPPORT),y)
WFLAGS += -DRTMP_FLASH_SUPPORT
endif


#################################################

# config for STA mode

ifeq ($(RT28xx_MODE),STA)
WFLAGS += -DCONFIG_STA_SUPPORT -DDBG

ifeq ($(HAS_XLINK),y)
WFLAGS += -DXLINK_SUPPORT
endif


ifeq ($(HAS_WPA_SUPPLICANT),y)
WFLAGS += -DWPA_SUPPLICANT_SUPPORT
ifeq ($(HAS_NATIVE_WPA_SUPPLICANT_SUPPORT),y)
WFLAGS += -DNATIVE_WPA_SUPPLICANT_SUPPORT
endif
endif




ifeq ($(HAS_ATE),y)
WFLAGS += -DRALINK_ATE
WFLAGS += -DCONFIG_RT2880_ATE_CMD_NEW
ifeq ($(HAS_QA_SUPPORT),y)
WFLAGS += -DRALINK_QA
endif
endif


ifeq ($(HAS_SNMP_SUPPORT),y)
WFLAGS += -DSNMP_SUPPORT
endif

ifeq ($(HAS_QOS_DLS_SUPPORT),y)
WFLAGS += -DQOS_DLS_SUPPORT
endif

ifeq ($(HAS_DOT11_N_SUPPORT),y)
WFLAGS += -DDOT11_N_SUPPORT
ifeq ($(HAS_DOT11N_DRAFT3_SUPPORT),y)
WFLAGS += -DDOT11N_DRAFT3
endif
endif


ifeq ($(HAS_CS_SUPPORT),y)
WFLAGS += -DCARRIER_DETECTION_SUPPORT
endif

ifeq ($(HAS_STATS_COUNT),y)
WFLAGS += -DSTATS_COUNT_SUPPORT
endif

ifeq ($(HAS_CFG80211_SUPPORT),y)
WFLAGS += -DRT_CFG80211_SUPPORT
ifeq ($(HAS_RFKILL_HW_SUPPORT),y)
WFLAGS += -DRFKILL_HW_SUPPORT
endif
endif

ifeq ($(OSABL),YES)
WFLAGS += -DOS_ABL_SUPPORT
endif



ifeq ($(HAS_PROFILE_STORE_SUPPORT),y)
WFLAGS += -DPROFILE_STORE
endif

ifeq ($(HAS_CREDENTIAL_STORE_SUPPORT),y)
WFLAGS += -DCREDENTIAL_STORE
endif

ifeq ($(HAS_PRE_ASSIGN_MAC_ADDR),y)
WFLAGS += -DPRE_ASSIGN_MAC_ADDR
endif

endif
# endif of ifeq ($(RT28xx_MODE),STA)

#################################################

#################################################

#
# Common compiler flag
#






ifeq ($(HAS_EXT_BUILD_CHANNEL_LIST),y)
WFLAGS += -DEXT_BUILD_CHANNEL_LIST
endif

ifeq ($(HAS_IDS_SUPPORT),y)
WFLAGS += -DIDS_SUPPORT
endif


ifeq ($(OSABL),YES)
WFLAGS += -DEXPORT_SYMTAB
endif

ifeq ($(HAS_CLIENT_WDS_SUPPORT),y)
WFLAGS += -DCLIENT_WDS
endif

ifeq ($(HAS_BGFP_SUPPORT),y)
WFLAGS += -DBG_FT_SUPPORT
endif

ifeq ($(HAS_BGFP_OPEN_SUPPORT),y)
WFLAGS += -DBG_FT_OPEN_SUPPORT
endif


#################################################
# ChipSet specific definitions.
#
ifeq ($(CHIPSET),2860)
WFLAGS +=-DRTMP_MAC_PCI -DRTMP_PCI_SUPPORT -DRT2860 -DRT28xx -DA_BAND_SUPPORT
CHIPSET_DAT = 2860
ifeq ($(HAS_DFS_SUPPORT),y)
WFLAGS += -DDFS_SOFTWARE_SUPPORT
endif
endif

ifeq ($(CHIPSET),3090)
WFLAGS +=-DRTMP_MAC_PCI -DRT30xx -DRT3090  -DRTMP_PCI_SUPPORT -DRTMP_RF_RW_SUPPORT -DRTMP_EFUSE_SUPPORT
CHIPSET_DAT = 2860
endif

ifeq ($(CHIPSET),2870)
WFLAGS +=-DRTMP_MAC_USB -DRTMP_USB_SUPPORT -DRT2870 -DRT28xx -DRTMP_TIMER_TASK_SUPPORT -DA_BAND_SUPPORT
CHIPSET_DAT = 2870
ifeq ($(HAS_DFS_SUPPORT),y)
WFLAGS += -DDFS_SOFTWARE_SUPPORT
endif

endif

ifeq ($(CHIPSET),2070)
WFLAGS +=-DRTMP_MAC_USB -DRT30xx -DRT3070 -DRT2070 -DRTMP_USB_SUPPORT -DRTMP_TIMER_TASK_SUPPORT -DRTMP_RF_RW_SUPPORT -DRTMP_EFUSE_SUPPORT
CHIPSET_DAT = 2870
endif

ifeq ($(CHIPSET),3070)
WFLAGS +=-DRTMP_MAC_USB -DRT30xx -DRT3070 -DRTMP_USB_SUPPORT -DRTMP_TIMER_TASK_SUPPORT -DRTMP_RF_RW_SUPPORT -DRTMP_EFUSE_SUPPORT
CHIPSET_DAT = 2870

```

I give a view of my desktop now...(in the attached screenshot)

Thanks!

---

### Post by chili555 on 2012-01-10
Your config.mk file looks fine. You've done all you can reasonably do with rt3562sta. I suggest you reboot, if you haven't already, which will unload rt3562sta, since it's blacklisted. Next I suggest you try compat-wireless. Here is an explanation: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659143)  See post #16.

If compat-wireless doesn't solve it for us, I'd suggest 32-bit. You might download, burn and boot the 32-bit live CD, it is quite possible that rt2800pci will work out of the box.

rt2x00 is a tricky suite of drivers and under active development. I wish there was an easy answer.

---

### Post by UltimateCat on 2012-01-10
> **emiliobi said:**
> Hi

```
emiliobi@emiliobi-H55-HD:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             990799  1 

emiliobi@emiliobi-H55-HD:~$ rfkill list all
emiliobi@emiliobi-H55-HD:~$ 

emiliobi@emiliobi-H55-HD:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 10:9A:DD:85:F8:9B   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level:-60 dBm  Noise level:-60 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

I have the exact same thing going on. Only I have Ubuntu 10.04.
I'm just a newbie but I found on a website that says drivers don't work unless you install the firmware.
[www.ralinktech.com](www.ralinktech.com)   ( Rt73_Linux_STA_Drv )
Do you think this (firmware) could be why we can't get online?(Because we either did or didn't install this firmware?)
Hope this helps.

---

### Post by emiliobi on 2012-01-10
Hi,

I will try compat-wireless, then as you said I will go for 32bit. 

You were all very kind, thank you so much!

P.s. If I re-install and I have network issues I have to open another thread?

Thank you again

---

### Post by emiliobi on 2012-01-10
Hi, I think the procedure in ubuntu 10.04 it's a bit different (in this thread you will find a comment about this from chili555).

I'm trying to do what the expert said, if it doesn't work I will re-install the 32 bit.
And if wifi still doesn't work I will open a new thread :)

Thanks fot your comment!



> I have the exact same thing going on. Only I have Ubuntu 10.04.
I'm just a newbie but I found on a website that says drivers don't work unless you install the firmware.
[www.ralinktech.com]("http://www.ralinktech.com/")   ( Rt73_Linux_STA_Drv )
Do you think this (firmware) could be why we can't get online?(Because we either did or didn't install this firmware?)
Hope this helps. 	

---

### Post by chili555 on 2012-01-10
> **UltimateCat said:**
> I have the exact same thing going on. Only I have Ubuntu 10.04.
I'm just a newbie but I found on a website that says drivers don't work unless you install the firmware.
[www.ralinktech.com](www.ralinktech.com)   ( Rt73_Linux_STA_Drv )
Do you think this (firmware) could be why we can't get online?(Because we either did or didn't install this firmware?)
Hope this helps.rt3562sta doesn't require firmware. rt73usb is an entirely different animal and does require its own firmware.

On the subject of firmware, see my link and post above.

---

### Post by emiliobi on 2012-01-10
Hi,
thanks again for the help.

I re-installed (11-10,32bit), but still have problem with wifi:
```

emiliobi@Umbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




```

Should I open another thread? (since now it can't see the networks)

Thanks

---

### Post by chili555 on 2012-01-10
Nope. Please post:```
dmesg | grep rt2
md5sum /lib/firmware/rt2860.bin
```

---

### Post by emiliobi on 2012-01-10
Hi
```

emiliobi@Umbuntu:~$ dmesg | grep rt2
[    7.075450] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.148490] Registered led device: rt2800pci-phy0::radio
[    7.148509] Registered led device: rt2800pci-phy0::assoc
[    7.148528] Registered led device: rt2800pci-phy0::quality

```

Thanks!

---

### Post by emiliobi on 2012-01-10
Hi

```

emiliobi@Umbuntu:~$ md5sum /lib/firmware/rt2860.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin


```

Thanks

---

### Post by chili555 on 2012-01-10
Let's try the other firmware. Please see post #39 on page 4. You can download it to any convenient place if not Desktop.

---

### Post by emiliobi on 2012-01-10
Hi

```

emiliobi@Umbuntu:~/Scrivania/RT2860_Firmware_V26$ dmesg | grep rt2
[    7.075450] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.148490] Registered led device: rt2800pci-phy0::radio
[    7.148509] Registered led device: rt2800pci-phy0::assoc
[    7.148528] Registered led device: rt2800pci-phy0::quality
[ 2552.192215] rt2800pci 0000:05:06.0: PCI INT A disabled
[ 2560.097456] rt2800pci 0000:05:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2560.100093] Registered led device: rt2800pci-phy0::radio
[ 2560.100229] Registered led device: rt2800pci-phy0::assoc
[ 2560.100290] Registered led device: rt2800pci-phy0::quality


```

```

emiliobi@Umbuntu:~/Scrivania/RT2860_Firmware_V26$ md5sum /lib/firmware/rt2860.bin
66332d7636ee78db31b056aa0e44b097  /lib/firmware/rt2860.bin


```

Still not working 

Thanks

---

### Post by chili555 on 2012-01-12
Sorry for the delay in responding. Sometimes my real life intervenes.

I think there are seven possibilities for your card; two you have tried already. You have tried the built-in rt2800pci with both versions of the firmware.

Next, I'd suggest compat-wireless (see above). If it doesn't work right away, try the other firmware and reload the driver:```
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860_6633_.bak
sudo mv /lib/firmware/rt2860.bak /lib/firmware/rt2860.bin
```The 6633 I added is a reference to the md5sum that distinguishes the newer firmware from the older file with a 75a1xx md5sum. That puts the original firmware back in place. Now reload the driver:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
```Steps five and six involve recompiling rt3562sta and blacklisting rt2800pci; and then trying both firmwares.

Step seven involves a hammer. Please let me know if you need guidance with any of this.

---

### Post by emiliobi on 2012-01-12
Hi, 
> Sorry for the delay in responding. Sometimes my real life intervenes.Chili555 you are more than a kind person, you are super, please don't say sorry! 
I really appreciate your work and the passion  you put into it.
Now back to wifi-hammer situation:

Step 3 and 4 that you suggested didn't work :(

You said >  Steps five and six involve recompiling rt3562sta and blacklisting rt2800pci; and then trying both firmwares.How can I do that ? :)

For step 7 Instead of a hammer I'd rather buy an usb wifi dongle that will work..what do you think?

Many thanks!

---

### Post by chili555 on 2012-01-12
> How can I do that ?Just like this: [http://ubuntuforums.org/showthread.php?t=1850267](http://ubuntuforums.org/showthread.php?t=1850267)

The link for download has moved here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

Under step #8, substitute:```
sudo make install
```

I just ran 'make' myself and it builds with warnings but no errors.

You'll also need to blacklist rt2800pci:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
modprobe -r rt2800pci
exit
```

If it doesn't spring to life, we'll try both firmwares.

---

### Post by wildmanne39 on 2012-01-12
Hi, I am learning a lot also, I have been away for most of two days myself, it is good to be back and learning so much.
Thanks

---

### Post by emiliobi on 2012-01-12
Hi,

I wrote down everything
Now I try to reboot, if it makes problems I'll tell you 

```

emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make
[sudo] password for emiliobi: 
make -C tools
make[1]: ingresso nella directory "/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools"
gcc -g bin2h.c -o bin2h
make[1]: uscita dalla directory "/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools"
/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-14-generic-pae/build SUBDIRS=/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.0.0-14-generic-pae"
  CC [M]  /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information
  LD [M]  /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: uscita dalla directory "/usr/src/linux-headers-3.0.0-14-generic-pae"
cp -f /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot


``````


emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make install
make -C /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: impossibile creare la directory "/etc/Wireless": File già esistente
make[1]: ingresso nella directory "/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux"
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-14-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.0.0-14-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.0.0-14-generic-pae
make[1]: uscita dalla directory "/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux"



``````

emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo gedit /etc/modprobe.d/blacklist.conf 

(gedit:2257): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.09KL7V" non riuscita: File o directory non esistente

(gedit:2257): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente

(gedit:2257): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.EZ7F7V" non riuscita: File o directory non esistente

(gedit:2257): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente

(gedit:2257): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.2Y3N7V" non riuscita: File o directory non esistente

(gedit:2257): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente
emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo gedit /etc/modprobe.d/blacklist.conf 

(gedit:2275): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.XX2G7V" non riuscita: File o directory non esistente

(gedit:2275): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente

(gedit:2275): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.W5NP7V" non riuscita: File o directory non esistente

(gedit:2275): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente

(gedit:2275): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.EV3N7V" non riuscita: File o directory non esistente

(gedit:2275): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente


``````

emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo gedit /etc/modules 

(gedit:2283): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.3PPO7V" non riuscita: File o directory non esistente

(gedit:2283): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente

(gedit:2283): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.X2HK7V" non riuscita: File o directory non esistente

(gedit:2283): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: File o directory non esistente
emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo update-initramfs -u 
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic-pae


``````

emiliobi@Umbuntu:~/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo su
root@Umbuntu:/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
root@Umbuntu:/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# modprobe -r rt2800pci
root@Umbuntu:/home/emiliobi/Scrivania/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# exit
exit


```Thanks

---

### Post by chili555 on 2012-01-12
> (gedit:2257): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Creazione del file "/root/.local/share/recently-used.xbel.09KL7V" non riuscita: File o directory non esistenteThat's fairly harmless but easy to fix:```
sudo mkdir /root/.local/share
```So, does it work, connect, sing??

Scrivania = Desktop?? I'm alsways tempted to say, "Download these files to your scrivania."

---

### Post by chili555 on 2012-01-12
> **wildmanne39 said:**
> Hi, I am learning a lot also, I have been away for most of two days myself, it is good to be back and learning so much.
ThanksI am reminded of an old pal of mine who said, "I learned a lot doing this job: don't be here when we do the next one!" I'm starting to feel that way about rt2800xx.

---

### Post by emiliobi on 2012-01-12
Hi!

> 
Scrivania = Desktop?? I'm alsways tempted to say, "Download these files to your scrivania." 	


yes, Scrivania is the Italian for Desktop :D

```

emiliobi@Umbuntu:~$ sudo mkdir /root/.local/share
mkdir: impossibile creare la directory "/root/.local/share": File o directory non esistente
emiliobi@Umbuntu:~$ 


```

I'm lost..

---

### Post by chili555 on 2012-01-12
> emiliobi@Umbuntu:~$ sudo mkdir /root/.local/share
mkdir: impossibile creare la directory "/root/.local/share": File o directory non esistenteLet's try one level at a time. Verify that /root exists:```
sudo su
ls /root
```If there are no complaints, check for .local:```
ls /root/.local
```If it is not there, as I suspect, create it:```
mkdir /root/.local
```And now the last part:```
mkdir /root/.local/share
exit
```Post back any problema.

---

### Post by emiliobi on 2012-01-12
Hi

```

emiliobi@Umbuntu:~$ sudo su
root@Umbuntu:/home/emiliobi# ls /root
root@Umbuntu:/home/emiliobi# ls /root/.local
ls: impossibile accedere a /root/.local: File o directory non esistente
root@Umbuntu:/home/emiliobi# mkdir /root/.local
root@Umbuntu:/home/emiliobi# mkdir /root/.local/share
root@Umbuntu:/home/emiliobi# exit
exit



```

And now I have to repeat the process in post 80?

Thanks!

---

### Post by chili555 on 2012-01-12
No, just try this:```
sudo gedit /etc/modprobe.d/blacklist.conf 

```Make sure your change to *blacklist rt2800pci* is there. Add it if not; save and close gedit. Reboot. Report success. Open Chianti Classico Reserva.

---

### Post by emiliobi on 2012-01-12
Hi,

>  And now I have to repeat the process in post 80?
 

or maybe just:

```

sudo gedit /etc/modprobe.d/blacklist.conf 			 		

```

Thanks

---

### Post by emiliobi on 2012-01-12
Hi take a look:

```

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
blacklist rt2800pci
blacklist rt2x00pci
blacklist rt2800pci

```

I have to remove one right?

Thanks

>  Open Chianti Classico Reserva. 	

We make lambrusco at home :)

---

### Post by chili555 on 2012-01-12
> I have to remove one right?Not really. It's fine. You can if you are obsessive like me, but the system will work perfectly fine with two.

Secco, I assume?

---

### Post by emiliobi on 2012-01-12
Hi,

still not working...

>  Secco, I assume?     Both secco and
 amabile :)

Thanks

---

### Post by chili555 on 2012-01-12
Let's go shopping. If you'd like to get together a list of devices that are available at reasonable cost there, I'll help you decide which work out of the box in Ubuntu. rt2800pci is going to wake me up screaming; and not with joy!

Did you install 11.10?

---

### Post by ratcheer on 2012-01-12
Your blacklist should be fine. But, you can remove the double entry if you want.

All I ever have to do after running "sudo make install" is "sudo modprobe rt3562sta". A few seconds after doing that, wireless should come up.

On rare occasions, I have to right-click the Network Manager applet and select "Enable wireless network". But, that should not be necessary unless you have previously disabled it.

Sorry for butting in. I hope this helps.

Tim

PS - To verify that the driver is properly loaded, run "sudo lspci -v". The wireless section of output should look something like this:

```
06:00.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    [COLOR=Blue]Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci[/COLOR]
```

---

### Post by emiliobi on 2012-01-13
Hi

> Let's go  shopping. If you'd like to get together a list of devices that are  available at reasonable cost there, I'll help you decide which work out  of the box in Ubuntu. rt2800pci is going to wake me up screaming; and  not with joy!

Did you install 11.10?           
Yes, I already was on 11.10 64 bit, after the compiz situation I re-installed 11.10 32 bit.

> Your blacklist should be fine. But, you can remove the double entry if you want.

All I ever have to do after running "sudo make install" is "sudo  modprobe rt3562sta". A few seconds after doing that, wireless should  come up.I tried, it didn't worked, but as chili555 suggested I think I will buy another card/usb dongle.
Any suggestions are more than welcome!

Thanks a lot to everyone who helped me!

---

### Post by chili555 on 2012-01-13
> Any suggestions are more than welcome!My suggestion is above:> If you'd like to get together a list of devices that are available at reasonable cost there, I'll help you decide which work out of the box in Ubuntu.I know what I can find at Walmart and Best Buy but I have no idea what you can get there at reasonable cost. By the way, any we find with an rt2x00 chipset are unacceptable, in my opinion. That driver seems to be hit or miss in 11.10.

---

### Post by emiliobi on 2012-01-13
Hi

what do you think of D-Link DWA-552?
(cost 22.7 $)

Thanks.

---

### Post by chili555 on 2012-01-13
> **emiliobi said:**
> Hi

what do you think of D-Link DWA-552?
(cost 22.7 $)

Thanks.Good choice! Please check here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI)

> Works out of the box in Karmic Koala (9.10, AMD64), including running "N" wireless protocol and WPA/WPA2-Personal securityI believe the drop-outs mentioned have been solved in later Ubuntu versions. Any other choices?

---

### Post by emiliobi on 2012-01-13
Hi

> I believe the drop-outs mentioned have been solved in later Ubuntu versions. Any other choices?     

DWL-G520 (cost less, no wifi N about 30 $)

or the

DWA-556 (this one with N, about 90 $ )

but this cost a lot more!

(I want to stay on the atheros chip, since the F.S.F. suggest it)

Thanks!

---

### Post by emiliobi on 2012-01-13
Hi

> DWA-556 (this one with N, about 90 $ )


found one at 75 $

Thanks

---

### Post by chili555 on 2012-01-13
I like them both. I look forward to a good report.

---

### Post by emiliobi on 2012-01-18
Hi all,

```

emiliobi@Umbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Airport Extreme Villa Bianca"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:9A:DD:85:F8:9B   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:57   Missed beacon:0


```

It seems to work! Out of the box, just installed!

Many thanks again!

emiliobi

p.s.

I will celebrate with a good bottle of lambrusco tonight!

p.p.s. I will suggest everyone to avoid ralink 3060 chip!

---

### Post by chili555 on 2012-01-18
Awesome! Glad it's working.> I will celebrate with a good bottle of lambrusco tonight!Excellent! I will have to make do with Beaujolais Villages.

---

### Post by wildmanne39 on 2012-01-18
Hi, your welcome! I am glad you got one that works.

---

### Post by emiliobi on 2012-01-18
Tonight I raised my glass to you guys, but I forgot to mention which card I bought :D

That's the DWL-G520

Many many thanks again!

see you next time

---

