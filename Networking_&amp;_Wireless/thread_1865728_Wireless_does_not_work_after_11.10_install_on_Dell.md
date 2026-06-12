---
title: "Wireless does not work after 11.10 install on Dell Latitide D630"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by azpartners on 2011-10-20
Wireless did not work after 11.04 update, did fresh install of 11.10 and it did not work. Wireless card is bcm43xx. Installed proprietary STA driver, blacklisted both bcma and brcmsmac per your forum, still does not work. I have not seen any other fixes specific to 11.10.

---

### Post by wildmanne39 on 2011-10-20
Hi please post the results of:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by azpartners on 2011-10-20
azpartners@azpartners-Latitude-D630:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux azpartners-Latitude-D630 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

azpartners@azpartners-Latitude-D630:~$ lspci -nnk | grep -ia2 net
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel modules: wl, ssb

azpartners@azpartners-Latitude-D630:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_wmi               12601  0 
snd_rawmidi            25241  1 snd_seq_midi
sparse_keymap          13658  1 dell_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            13519  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  1 dell_laptop
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
pcmcia                 39822  0 
nouveau               663211  4 
yenta_socket           27428  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
psmouse                73673  0 
lib80211               14570  1 wl
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  6 nouveau,ttm,drm_kms_helper
serio_raw              12990  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  2 dell_wmi,mxm_wmi
video                  18908  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   132972  0

---

### Post by wildmanne39 on 2011-10-20
Hi, please try this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Then unplug wired connection and reboot.
Thank you

---

### Post by azpartners on 2011-10-20
Wildmanne39,

Many thanks, that worked perfectly!

Carl

---

### Post by wildmanne39 on 2011-10-20
Hi, your welcome! glad I could help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by ngilmour on 2011-10-21
Wildmanne,

I ran into the same problem after updating this morning, and your code fixed my laptop as well.  Kudos!

For the sake of the record, mine is a Dell Inspiron 1525.

---

### Post by esos on 2011-10-21
Thank you, Wildmanne. Mine is a Dell Latitude 120L with a Broadcom 4318.

---

### Post by laggy23 on 2011-10-22
Hello, This worked for me as well Acer aspire one (3g8)
Thank you!:p

---

### Post by wildmanne39 on 2011-10-22
Hi ngilmour, esos, laggy23, your welcome!
Enjoy

---

### Post by thijsE on 2011-10-31
It did not work for me :(
Here the results of the three commands:
titia@Dell-D630:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Dell-D630 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
titia@Dell-D630:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1021]
    Kernel driver in use: iwl3945
titia@Dell-D630:~$ lsmod
Module                  Size  Used by
rndis_wlan             28472  0 
rndis_host             13560  1 rndis_wlan
cdc_ether              13312  1 rndis_host
usbnet                 25214  3 rndis_wlan,rndis_host,cdc_ether
usb_storage            44173  0 
cdc_acm                22305  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
pcmcia                 39822  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
binfmt_misc            17292  1 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505108  3 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
cfg80211              172392  4 rndis_wlan,iwl3945,iwl_legacy,mac80211
wmi                    18744  1 dell_wmi
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
usbhid                 41905  0 
hid                    77367  1 usbhid
tg3                   132972  0 

Can you help me?? Thnx

---

### Post by wildmanne39 on 2011-10-31
Hi, it did not work because you do not have the right wireless card for that driver.

It also looks like you installed ndiswrapper if so we need to remove that.

Please run this command one line at a time:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

After you run the commands above then post the results of:
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep iwl
```
Then unplug wired connection and run the following command.
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e etwork | tail -n45
```
Thank you

---

### Post by thijsE on 2011-10-31
Thank you for helping me!

titia@Dell-D630:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:1F:3C:4E:5D:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1C:23:45:19:FD

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        CE:3C:D8:4D:EA:1F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.88
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


titia@Dell-D630:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
usb0      no wireless extensions.

titia@Dell-D630:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
titia@Dell-D630:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

usb0      Interface doesn't support scanning.

titia@Dell-D630:~$ lsmod | grep iwl
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  4 rndis_wlan,iwl3945,iwl_legacy,mac80211
titia@Dell-D630:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e etwork | tail -n45
Nov  1 00:02:21 Dell-D630 NetworkManager[862]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/net/usb0, iface: usb0)
Nov  1 00:02:21 Dell-D630 NetworkManager[862]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/net/usb0, iface: usb0): no ifupdown configuration found.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): carrier is OFF
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): new Ethernet device (driver: 'rndis_host' ifindex: 4)
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): exported as /org/freedesktop/NetworkManager/Devices/3
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): now managed
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): bringing up device.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): preparing device.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): deactivating device (reason 'managed') [2]
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/net/usb0
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): carrier now ON (device state 20)
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Auto-activating connection 'Wired connection 2'.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) starting connection 'Wired connection 2'
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) started...
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) scheduled...
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) complete.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) starting...
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) successful.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) complete.
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) started...
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> (usb0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> dhclient started with pid 1586
Nov  1 00:02:21 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) complete.
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info> (usb0): DHCPv4 state changed nbi -> preinit
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info> (usb0): DHCPv4 state changed preinit -> bound
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info>   address 192.168.42.88
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info>   prefix 24 (255.255.255.0)
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info>   gateway 192.168.42.129
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info>   hostname 'Dell-D630'
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info>   nameserver '192.168.42.129'
Nov  1 00:02:22 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 5 of 5 (IP Configure Commit) started...
Nov  1 00:02:23 Dell-D630 NetworkManager[862]: <info> (usb0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  1 00:02:23 Dell-D630 NetworkManager[862]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Nov  1 00:02:23 Dell-D630 NetworkManager[862]: <info> Activation (usb0) successful, device activated.
Nov  1 00:02:23 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  1 00:02:23 Dell-D630 NetworkManager[862]: <info> Activation (usb0) Stage 4 of 5 (IP4 Configure Get) complete.

---

### Post by wildmanne39 on 2011-10-31
Hi, I think you have several issues going on.

First your wireless is soft and hard blocked, please run this command:
```
sudo rmmod -f dell-laptop
```
Then you should have a switch that turns the wireless on and off find it then turn it on, and run these commands again so I can tell where to go from here.
```
rfkill list all
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e etwork | tail -n45
```
Thank you

---

### Post by thijsE on 2011-11-01
How stupid!!
It now works. The laptop has a wireless switch. I thought it was a switch to unlock the laptop's battery. Thank you very much for helping me out:D

---

### Post by wildmanne39 on 2011-11-01
Your welcome! glad to help.
Enjoy

---

### Post by noblecomputing on 2012-06-09
Your a God send man.  Found this post in Google.  After 2 hours of playing around, your solution worked!

---

### Post by tiger285 on 2012-06-27
hey could you guys please tell me where i have to put the code in. I will appreciate your help

THANK YOU!

---

### Post by wildmanne39 on 2012-06-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by tjen on 2012-08-11
Wildemanne39 - i've got a Dell Inspiron 1525 and wireless didn't work until I found your post.  You made my day. Thank you!

---

### Post by wildmanne39 on 2012-08-11
Your welcome!
Enjoy

---

### Post by Factorino on 2012-11-13
Hi, Wireless did not work on my Dell Latitude D630 with ubuntu.
 

 ```
:~$ cat /etc/lsb-release; uname -a 
 DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=11.10 
 DISTRIB_CODENAME=oneiric 
 DISTRIB_DESCRIPTION="Ubuntu 11.10" 
 Linux 2D50T3J 3.0.0-26-generic #43-Ubuntu SMP Tue Sep 25 17:20:50 UTC 2012 i686 i686 i386 GNU/Linux 
 
``` ```

:~$ lspci -nnk | grep -iA2 net 
 09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02) 
     Subsystem: Dell Device [1028:01f9] 
     Kernel driver in use: tg3 
 -- 
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
     Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b] 
     Kernel driver in use: b43-pci-bridge 
 
``` ```

:~$ lsmod 
 Module                  Size  Used by 
 bnep                   17923  2  
 rfcomm                 38408  8  
 parport_pc             32114  0  
 ppdev                  12849  0  
 snd_hda_codec_idt      60049  1  
 binfmt_misc            17292  1  
 joydev                 17393  0  
 snd_hda_intel          28358  2  
 dell_wmi               12601  0  
 sparse_keymap          13658  1 dell_wmi 
 snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel 
 snd_hwdep              13276  1 snd_hda_codec 
 snd_pcm                80435  2 snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13132  0  
 pcmcia                 39822  0  
 dell_laptop            13519  0  
 dcdbas                 14098  1 dell_laptop 
 snd_rawmidi            25241  1 snd_seq_midi 
 snd_seq_midi_event     14475  1 snd_seq_midi 
 arc4                   12473  2  
 yenta_socket           27428  0  
 pcmcia_rsrc            18367  1 yenta_socket 
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
 pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
 psmouse                73673  0  
 btusb                  18160  2  
 bluetooth             148869  23 bnep,rfcomm,btusb 
 b43                   318816  0  
 serio_raw              12990  0  
 snd_timer              28932  2 snd_pcm,snd_seq 
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
 mac80211              393421  1 b43 
 cfg80211              172427  2 b43,mac80211 
 wmi                    18744  1 dell_wmi 
 snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i915                  513798  3  
 drm_kms_helper         32889  1 i915 
 drm                   192194  4 i915,drm_kms_helper 
 soundcore              12600  1 snd 
 i2c_algo_bit           13199  1 i915 
 snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
 video                  19069  1 i915 
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp 
 firewire_ohci          35854  0  
 firewire_core          56937  1 firewire_ohci 
 crc_itu_t              12627  1 firewire_core 
 ssb                    50682  1 b43 
 tg3                   132972  0  
 
``` Can you help me, please ?
 

 Thank you

---

### Post by wildmanne39 on 2012-11-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Factorino on 2012-11-14
Hi,  the file is attached to the message.
Thank you for your help :)

---

### Post by wildmanne39 on 2012-11-14
Hi, please do:
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Reboot
Thanks

---

### Post by Factorino on 2012-11-15
Great !! :)
Thank you very much ;)

---

### Post by wildmanne39 on 2012-11-15
Your welcome!
Enjoy

---

### Post by JILD630U on 2013-01-18
Good Morning!

I'm having a similar issue in Ubuntu as well. I ran the script that you put in the forum above. 

wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
I have attached the file that it created below. 

Would you be so kind to assist me please?

Thanks!

---

### Post by sliberty on 2013-02-03
I tried the solution at the beginning of this thread for my Dell Latitude 630, but it didn't work. Here is my output from the commands you posted. I hope you can help me too.

steve@steve-Ubuntu-D630:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux steve-Ubuntu-D630 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
steve@steve-Ubuntu-D630:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
	Subsystem: Dell Device [1028:01f9]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb
steve@steve-Ubuntu-D630:~$ lsusb
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
steve@steve-Ubuntu-D630:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

steve@steve-Ubuntu-D630:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
steve@steve-Ubuntu-D630:~$ lsmod
Module                  Size  Used by
hid_generic            12445  0 
hidp                   21825  1 
hid                    82142  2 hid_generic,hidp
joydev                 17161  0 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  12 
bnep                   17707  2 
snd_hda_codec_idt      59761  1 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
gpio_ich               13159  0 
snd_seq_midi           13132  0 
psmouse                84843  0 
serio_raw              13031  0 
dell_laptop            17161  0 
dcdbas                 14054  1 dell_laptop
snd_rawmidi            25382  1 snd_seq_midi
microcode              18209  0 
nouveau               823577  5 
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
mac_hid                13037  0 
drm                   230463  7 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
wl                   2442848  0 
video                  18847  1 nouveau
lib80211               14040  1 wl
btusb                  17950  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            21505  2 yenta_socket,pcmcia_rsrc
wmi                    18590  3 dell_wmi,nouveau,mxm_wmi
bluetooth             183228  27 hidp,rfcomm,bnep,btusb
snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16925  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   130448  0 
steve@steve-Ubuntu-D630:~$ 


Thanks in advance.
Steve

---

### Post by bkratz on 2013-02-03
Steve,  see this thread

[http://ubuntuforums.org/showthread.php?t=2110823](http://ubuntuforums.org/showthread.php?t=2110823)


Just noticed that you have the incorrect STA driver installed. You probably should do it like this

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

---

### Post by sliberty on 2013-02-03
That worked, sort of. I got wireless until I rebooted. After rebooting, no wireless. I entered just the third command and wireless was back. But after rebooting, wireless was gone again.AGain if I entered the last command, wifi was back, but it will not stick.

Is there a way to make wireless more permanent?

---

### Post by wildmanne39 on 2013-02-04
Please do ```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by sliberty on 2013-02-04
That seems to have worked. Thanks guys - you are all GREAT help.
Steve

---

### Post by bkratz on 2013-02-04
> **sliberty said:**
> That seems to have worked. Thanks guys - you are all GREAT help.
Steve

Just got on
Glad you got it going! with a tip of the hat to Wild Man!

---

### Post by Vivek_Rangabhashyam on 2013-08-21
I am facing this same problem with my latitude d630.... I'm on ubuntu 13.04... tried the code but had no joy... Please help...

---

### Post by wildmanne39 on 2013-08-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz or netinfo.txt in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz or netinfo.txt file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

