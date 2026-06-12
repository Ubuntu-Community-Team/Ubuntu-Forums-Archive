---
title: "iwlist ra0 scan | no results | rt3290 kernel 3.9-raring"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by daaatz on 2013-06-27
Hi,

heres some details:
```

lspci:
07:00.0 Network controller: Ralink corp. Device 3290
07:00.1 Bluetooth: Ralink corp. Device 3298

root@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej# uname -r
3.9.0-030900-generic

root@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej# iwconfig 
ra0       Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej# iwlist ra0 scan
ra0       No scan results


```
On kernel 3.2 was working ok, but after upgrading compiling drivers like in : [http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)
ubuntu see my wireless card but its not working properly, in wifi network manager I dont see any wifi ( saw them on kernel 3.2) and as You see ra0 scan no results..

Can someone help me ? Thanks

---

### Post by varunendra on 2013-06-27
Maybe I can try. Pleas follow the "Wireless Script" link in my signature, do what the linked post asks to do, and post back the contents of the "wireless-info.txt" file the script creates.

Along with that report, please also post the output of -
```
modinfo rt3290sta
```

---

### Post by daaatz on 2013-06-27
```

root@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej# modinfo rt3290sta
filename:       /lib/modules/3.9.0-030900-generic/kernel/drivers/net/wireless/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     7185F5CFFEC4762B7465928
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
depends:        
vermagic:       3.9.0-030900-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

root@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej/Toolz# cat wireless-info.txt 

*************** info trace ***************

***** uname -a *****

Linux maciej-HP-Pavilion-g6-Notebook-PC 3.9.0-030900-generic #201304291257 SMP Mon Apr 29 16:58:15 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2860
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 

***** iwconfig *****

ra0       Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

rt3290sta            1182459  1 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63


- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

ra0       No scan results


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800pci
blacklist rt2x00pci
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt2800pci

***** dmesg *****

[   29.574004] rt3290sta: module license 'unspecified' taints kernel.
[   29.574620] rt3290sta: module verification failed: signature and/or required key missing - tainting kernel
[   33.247593] <==== rt28xx_init, Status=0
[   33.287085] <==== rt28xx_init, Status=0
[  537.061284] <==== rt28xx_init, Status=0
[ 1150.400838] <==== rt28xx_init, Status=0

****************** done ******************



```

Thanks !

---

### Post by daaatz on 2013-06-27
Some one any ideas what to do with this wifi ? Thanks

---

### Post by varunendra on 2013-06-27
A few things in your outputs that I'm not comfortable with :
> **daaatz said:**
> ```

**[COLOR="#FF0000"]root[/COLOR]@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej[COLOR="#FF0000"]#[/COLOR]** modinfo rt3290sta
filename:       /lib/modules/3.9.0-030900-generic/kernel/drivers/net/wireless/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     **[COLOR="#FF0000"]7185F5CFFEC4762B7465928[/COLOR]**
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
....
....
[/etc/modprobe.d/blacklist.conf]
[B][COLOR="#FF0000"]blacklist rt2800pci
blacklist rt2x00pci[/COLOR][/B]
blacklist evbug
...
blacklist amd76x_edac
**[COLOR="#FF0000"]blacklist rt2800pci[/COLOR]**

```

First of all, where exactly did you download the driver from?
Both the official one downloaded from Ralink's site and the one on the "download link" on the blog post you linked to have the same version number which is different from the one reflected in your modinfo above (7185F5CFFEC4762B7465928). Which means you used a different version of source for the driver.

The blog post itself seems to be confusing to me, as it was clearly originally written for rt3562 driver and poorly edited for the rt3290 later (only changing the driver name, without caring about details).

Second, why did you need to install the latest kernel 3.9? Was it really needed for something?

Third, why are you running the system as root? (may not be related with the problem though)

Last, you have blacklisted the rt2800pci driver twice. It, combined with the fact that your driver source version is different, indicates that maybe you have tried more things than only the blog post above.

Depending on what all you have tried so far, we can try re-installing the driver version I trust (as it have been tested ok on 12.04).

---

### Post by daaatz on 2013-06-28
Heh now I downloaded drivers from [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working) ( 
wget [http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz](http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz) ) and they are not compliling well.

I need kernel 3.9 really.
I'm software dev, and on kernel 3.2 I often have situations that my system hangs, its really annoying on kernel 3.9 system is stable no hangs at all.

---

### Post by daaatz on 2013-06-28
I made changes like in [http://ubuntuforums.org/showthread.php?t=2104129](http://ubuntuforums.org/showthread.php?t=2104129)
> 
 				[INDENT] 					Any kernel >= 3.7.x should work (get the -image and -headers  .debs that correspond to your architecture as well as the -all .deb): [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
The firmware file is attached to this post.

Just for reference, here is the Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1049466]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466") 				[/INDENT] 			
  			 			  			  			  			  			 				 					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG] Attached Files 					
[LIST]
[*] 	[IMG]http://ubuntuforums.org/images/attach/gz.gif[/IMG] 	[rt3290firmware.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=240210&d=1363363920")  (2.6 KB, 321 views)
[/LIST]
 				 			  			  			




Also copied firmware. Now results from wireless-info :
```


*************** info trace ***************

***** uname -a *****

Linux maciej-HP-Pavilion-g6-Notebook-PC 3.7.2-030702-generic #201301111424 SMP Fri Jan 11 19:25:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel modules: rt2800pci
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 001 Device 004: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse

***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800pci
blacklist rt2x00pci
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****


****************** done ******************

maciej@maciej-HP-Pavilion-g6-Notebook-PC:~/Toolz$ sudo modinfo rt3290sta
ERROR: modinfo: could not find module rt3290sta




```

I dont understand..

---

### Post by daaatz on 2013-06-28
Hmm on this kernel [http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz](http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz) complies ok.
But still 
```

root@maciej-HP-Pavilion-g6-Notebook-PC:/home/maciej/Toolz# modinfo rt3290sta
filename:       /lib/modules/3.7.2-030702-generic/kernel/drivers/net/wireless/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     13F483178C6DF2E02D874C3
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
depends:        
vermagic:       3.7.2-030702-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


*************** info trace ***************

***** uname -a *****

Linux maciej-HP-Pavilion-g6-Notebook-PC 3.7.2-030702-generic #201301111424 SMP Fri Jan 11 19:25:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2860
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 001 Device 004: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse

***** iwconfig *****

ra0       Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

rt3290sta            1182502  1 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63


- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

ra0       No scan results


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800pci
blacklist rt2x00pci
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[    8.091135] rt3290sta: module license 'unspecified' taints kernel.
[   18.348184] <==== rt28xx_init, Status=0
[   18.387838] <==== rt28xx_init, Status=0

****************** done ******************




```

and wifi doesnt work..

---

### Post by daaatz on 2013-06-28
Do You have some other drivers ? Thanks.

---

### Post by daaatz on 2013-06-29
I got back to kernel 3.2.0.45 wifi works fine :
```


*************** info trace ***************

***** uname -a *****

Linux maciej-HP-Pavilion-g6-Notebook-PC 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2860
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 

***** iwconfig *****

ra0       Ralink STA  ESSID:"UBU"  Nickname:"RT3290STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=39 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=89/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

rt3290sta            1182379  1 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: ra0  [UBU] -----------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    gizela:          Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA2
    *UBU:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89 WPA2
    Robak:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA
    DraGon:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2
    cichy:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 16 Mb/s, Strength 4 WPA WPA2
    UPC0045223:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 16 Mb/s, Strength 7 WPA WPA2
    jar4693:         Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 4 WPA2
    UPC008945:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"UBU"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/100  Signal level=-76 dBm  Noise level=-71 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"gizela"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/100  Signal level=-78 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"Robak"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/100  Signal level=-94 dBm  Noise level=-89 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"net_fri8"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/100  Signal level=-94 dBm  Noise level=-89 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 05 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"cichy"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/100  Signal level=-100 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000236926B42B103C000101
          Cell 06 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"jar4693"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=0/100  Signal level=-100 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"DraGon"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/100  Signal level=-96 dBm  Noise level=-91 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 08 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"UPC0045223"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/100  Signal level=-96 dBm  Noise level=-91 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"UPC008945"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/100  Signal level=-98 dBm  Noise level=-93 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800pci
blacklist rt2x00pci
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   32.660630] rt2860 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.660660] rt2860 0000:07:00.0: setting latency timer to 64
[   35.592414] <==== rt28xx_init, Status=0
[   35.682703] <==== rt28xx_init, Status=0

****************** done ******************
maciej@maciej-HP-Pavilion-g6-Notebook-PC:~$ modinfo rt3290sta
filename:       /lib/modules/3.2.0-45-generic/kernel/drivers/net/wireless/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     13F483178C6DF2E02D874C3
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-45-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)




```

Dont see much difference with 3.7.2 which I wrote upper..

---

