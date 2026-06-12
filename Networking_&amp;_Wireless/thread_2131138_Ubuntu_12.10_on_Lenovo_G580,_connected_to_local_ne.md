---
title: "Ubuntu 12.10 on Lenovo G580, connected to local network but no internet"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by ThisIsNuggets on 2013-03-31
According to the specs (which can be found at [http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g580/](http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g580/) ) of my Lenovo G580, I either have a Intel® WiMAX/WiFi 6250 2 x 2 AGN card or a Intel® WiMAX/WiFi 6150 2 x 2 AGN card. I am able to connect to my local network, but unable to reach the internet. I can connect to the internet if my comupter is plugged directly into my router, but I want to connect wirelessly. So, can anyone help me with this?

Thanks,
Nuggets

---

### Post by chili555 on 2013-03-31
Is your driver called iwlwifi? Please open a terminal Ctrl+Alt+t and run:```
lsmod
```Is iwlwifi listed? If so, please check here: [http://ubuntuforums.org/showthread.php?t=2009812&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2009812&highlight=11n_disable)

---

### Post by ThisIsNuggets on 2013-03-31
Nope, iwlwifi is not listed.

---

### Post by chili555 on 2013-04-01
> **ThisIsNuggets said:**
> Nope, iwlwifi is not listed.Let's try to find out what is. Please run and post:```
sudo lshw -C network
```Thanks.

---

### Post by ThisIsNuggets on 2013-04-01
Here are the results:
```
   *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 20:68:9d:a3:4c:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A ip=10.0.0.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)


```

---

### Post by ThisIsNuggets on 2013-04-01
Nevermind, It just randomly started working. Many thanks for the attempted help, though.

---

### Post by harishankar on 2013-04-01
Hi 

I wonder can i hijack this thread. I have a similar problem, with small variation.

Mine is lenovo y560 and i have dual partition: Ubuntu 12.04 and Windows 7. All these while i had no problem with my network connectivity in ubuntu, but a day back my laptop suddenly switched off due to over heating, and when i turned on I couldnt connect to the internet in ubuntu. Internet in windows working fine.

I can connect to the wireless network(atleast thats what it says), but when i open a browser, i coudnt actually get the internet. Even with the wired connection, it is the case. It says it is connected to the wired network, but no internet. I followed this thread and couple of other threads and tried some of the recipes, but the problem still persists! I am not sure whether the power management in ubuntu disabled any network related drivers as the laptop switched off suddenly!?!

I will really appreciate any help on this issue. Thanks.

Here are some of the outputs for the commands you mentioned.

hash@ubuntu:~$ lsmod
> 
Module                  Size  Used by
joydev                 17693  0 
vesafb                 13844  1 
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
fglrx                4713410  156 
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
video                  19651  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               401140  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506862  1 iwlwifi
jmb38x_ms              17646  0 
uvcvideo               72627  0 
wmi                    19256  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
memstick               16569  1 jmb38x_ms
intel_ips              18174  0 
snd                    79041  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
cfg80211              205774  2 iwlwifi,mac80211
psmouse                97485  0 
i7core_edac            28102  0 
serio_raw              13211  0 
soundcore              15091  1 snd
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  1 i7core_edac
tg3                   152085  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci




hash@ubuntu:~$ lspci -nnk | grep -iA2 net
> 
05:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlwifi
--
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Lenovo Device [17aa:38cf]
	Kernel driver in use: 


hash@ubuntu:~$ iwconfig
> 
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"jthomas's Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: F8:1E:DF:FF:C1:4D   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0

eth0      no wireless extensions.



hash@ubuntu:~$ rfkill list all
> 
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




> 
hash@ubuntu:~$ ping 127.0.0.1

PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_req=5 ttl=64 time=0.032 ms
64 bytes from 127.0.0.1: icmp_req=6 ttl=64 time=0.033 ms
^C
--- 127.0.0.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 0.028/0.032/0.038/0.006 ms
hash@ubuntu:~$ 


    ping 192.168.X.X
hash@ubuntu:~$ ping 192.168.1.24
PING 192.168.1.24 (192.168.1.24) 56(84) bytes of data.
64 bytes from 192.168.1.24: icmp_req=1 ttl=64 time=0.036 ms
64 bytes from 192.168.1.24: icmp_req=2 ttl=64 time=0.029 ms
64 bytes from 192.168.1.24: icmp_req=3 ttl=64 time=0.031 ms
64 bytes from 192.168.1.24: icmp_req=4 ttl=64 time=0.028 ms
64 bytes from 192.168.1.24: icmp_req=5 ttl=64 time=0.029 ms
64 bytes from 192.168.1.24: icmp_req=6 ttl=64 time=0.030 ms
^C
--- 192.168.1.24 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4996ms
rtt min/avg/max/mdev = 0.028/0.030/0.036/0.006 ms
hash@ubuntu:~$ 




    ping 8.8.8.8

hash@ubuntu:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=47 time=37.2 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=47 time=36.6 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=47 time=38.1 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=47 time=37.2 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=47 time=37.8 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=47 time=38.0 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=47 time=37.4 ms
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6009ms
rtt min/avg/max/mdev = 36.670/37.523/38.134/0.545 ms




    ping google.com
hash@ubuntu:~$ ping google.com
ping: unknown host google.com



---

### Post by c24ck32 on 2013-04-02
Hi harishankar,

Have you check /etc/resolv.conf ? it seems that you could ping the IP 8.8.8.8 but it can't resolv the domain google.com

---

### Post by harishankar on 2013-04-02
Hi

No, i havent checked that file. Can you please throw in some more information on what i should look for in it? If there is any other thing i should also look for, please state that too. Sorry for pulling things, it is because i have to hop between ubuntu,for trying out the suggestions and windows,for posting it on the net. :) :(.

Thanks.

---

### Post by harishankar on 2013-04-02
Hi 

This is the content of my /etc/resolv.conf
> hash@ubuntu:~$ cat /etc/resolv.conf
#nameserver 10.182.70.107
#nameserver 10.180.15.160
nameserver 128.141.1.1


here is the route -n
hash@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0            128.141.1.1     0.0.0.0         UG    0      0        0 wlan0
128.141.0.0     0.0.0.0         255.255.0.0     U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

---

### Post by chili555 on 2013-04-02
> I can connect to the wireless network(atleast thats what it says), but when i open a browser, i coudnt actually get the internet. Please check here: [http://ubuntuforums.org/showthread.php?t=2009812&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2009812&highlight=11n_disable)  Especially see post #4.

---

### Post by harishankar on 2013-04-16
Hi chili555

I tried the suggestion in that thread, but still i couldnt connect to internet!

---

### Post by chili555 on 2013-04-16
> **harishankar said:**
> Hi chili555

I tried the suggestion in that thread, but still i couldnt connect to internet!Which Ubuntu version are you running?```
lsb_release -a
```May we see:```
nm-tool
```Are you getting your IP address automatically, by DHCP or did you set up a static IP address? Where? In Network Manager?> hash@ubuntu:~$ cat /etc/resolv.conf
#nameserver 10.182.70.107
#nameserver 10.180.15.160
nameserver [COLOR="#FF0000"]128.141.1.1[/COLOR] Very interesting! Where did that address come from? Did you enter it?

---

### Post by harishankar on 2013-04-16
Hi

```
lsb_release -a
```
hash@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

```
nm-tool

```
hash@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Buffalo_Joe] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        00:26:C7:89:6A:AC

  Capabilities:
    Speed:           2 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CERN:            Infra, 00:24:A8:98:58:70, Freq 2462 MHz, Rate 54 Mb/s, Strength 62
    3Com:            Infra, 00:14:7C:53:20:F3, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    CERN:            Infra, 00:24:A8:98:38:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    CERN:            Infra, 00:0F:61:58:44:40, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    NETGEAR:         Infra, 00:18:4D:2E:86:F3, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    CERN:            Infra, 00:24:A8:98:48:F0, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    OUHEP-WIFI:      Infra, 00:22:3F:8C:04:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    *Buffalo_Joe:    Infra, 00:0D:0B:05:D5:3D, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WEP
    CERN:            Infra, 00:0F:61:57:C3:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 24

  IPv4 Settings:
    Address:         192.168.11.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        60:EB:69:99:D7:0D

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         128.141.138.207
    Prefix:          16 (255.255.0.0)
    Gateway:         128.141.1.1

    DNS:             137.138.16.5
    DNS:             137.138.17.5

>     hash@ubuntu:~$ cat /etc/resolv.conf
    #nameserver 10.182.70.107
    #nameserver 10.180.15.160
    nameserver 128.141.1.1
    Very interesting! Where did that address come from? Did you enter it? 
Yes i manually entered that..in my previous try..but currently this is the content of /etc/resolv.conf

```

hash@ubuntu:~$ cat /etc/resolv.conf
nameserver 10.182.70.107
nameserver 10.180.15.160
```

- Hari

---

### Post by harishankar on 2013-04-16
I am not sure, whether this information will be of any help, but just FYI.

I installed ubuntu 12.04 through Wubi.

---

### Post by chili555 on 2013-04-16
We wonder why you are connected to both wired and wireless but to different access points and therefor different routes and DNS nameservers. I suggest you detach the ethernet, reboot and let us have your report.> NetworkManager Tool

State: connected (global)

- Device: wlan0 [Buffalo_Joe] -------------------------------------------------
Type: 802.11 WiFi
Driver: iwlwifi
State: connected
Default: no
HW Address: 00:26:C7:89:6A:AC

Capabilities:
Speed: 2 Mb/s

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points (* = current AP)

*Buffalo_Joe: Infra, 00:0D:0B:055:3D, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WEP
<snip>
IPv4 Settings:
Address: 192.168.11.3
Prefix: 24 (255.255.255.0)
Gateway: [COLOR="#FF0000"]192.168.11.1[/COLOR]

DNS: 192.168.11.1


- Device: eth0 [Wired connection 1] -------------------------------------------

Type: Wired
Driver: tg3
State: connected
Default: yes
HW Address: 60:EB:69:997:0D

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: on

IPv4 Settings:
Address: 128.141.138.207
Prefix: 16 (255.255.0.0)
Gateway: [COLOR="#FF0000"]128.141.1.1[/COLOR]

DNS: 137.138.16.5
DNS: 137.138.17.5
I suspect your system is pretty confused.

---

### Post by harishankar on 2013-04-16
Hi,

Here it is, i have removed the cable and the output

```
nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        60:EB:69:99:D7:0D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Buffalo_Joe] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:26:C7:89:6A:AC

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    atlgoewireless:  Infra, 00:22:3F:2C:A0:A2, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    3Com:            Infra, 00:14:7C:53:20:F3, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    NETGEAR:         Infra, 00:18:4D:2E:86:F3, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    *Buffalo_Joe:    Infra, 00:0D:0B:05:D5:3D, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WEP
    OUHEP-WIFI:      Infra, 00:22:3F:8C:04:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    SLAC:            Infra, 00:1F:F3:C3:2C:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2

  IPv4 Settings:
    Address:         192.168.11.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1

---

### Post by chili555 on 2013-04-16
So now does it connect to the internet?```
ping -c3 8.8.8.8
ping -c3 www.google.com
```

---

### Post by harishankar on 2013-04-16
Hi,

Still no. I couldnt connect to internet..

hash@ubuntu:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=47 time=38.3 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=47 time=37.9 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=47 time=37.4 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 37.403/37.911/38.351/0.421 ms
hash@ubuntu:~$ 
hash@ubuntu:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
hash@ubuntu:~$

---

### Post by chili555 on 2013-04-17
Now may we see:```
cat /etc/resolv.conf
nm-tool
```Are you using dnsmasq?```
cat /etc/NetworkManager/NetworkManager.conf
```We hope it says, in part:```
dns=dnsmasq
```

---

### Post by harishankar on 2013-04-17
```
cat /etc/resolv.conf
```
hash@ubuntu:~$ cat /etc/resolv.conf
nameserver 10.182.70.107
nameserver 10.180.15.160

```
nm-tool
```
hash@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        60:EB:69:99:D7:0D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [jthomas's Network] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:26:C7:89:6A:AC

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Livebox-D95E:    Infra, 7C:03:D8:78:D9:5E, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Livebox-dc78:    Infra, 5C:33:8E:0D:C6:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    Livebox-BFC2:    Infra, C0:AC:54:44:BF:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NEUF_D4B8:       Infra, 00:17:33:2F:D4:BC, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    SFR WiFi Mobile: Infra, A2:17:33:2F:D4:BF, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    Buffalo_Joe:     Infra, 00:0D:0B:05:BC:4D, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WEP
    SFR WiFi Public: Infra, A2:17:33:2F:D4:BD, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    *jthomas's Network: Infra, F8:1E:DF:FF:C1:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA2

  IPv4 Settings:
    Address:         192.168.1.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```
cat /etc/NetworkManager/NerworkManager.conf
```
hash@ubuntu:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

---

### Post by chili555 on 2013-04-17
In 12.10, if you are using dnsmasq, which it says you are, /etc/resolv.conf should read:```
 nameserver 127.0.0.1
```I suggest you change it:```
gksudo gedit /etc/resolv.conf
```Change it to:```
 nameserver 127.0.0.1
```Proofread, save and close gedit. Reboot. Then show us:```
ping -c3 8.8.8.8
ping -c3 www.google.com
cat /etc/resolv.conf
```We may also have some other file to address. Let's see what happens.

---

### Post by harishankar on 2013-04-17
Hi 

Actually sometime earlier i hijacked this thread, as I had a similar problem, but I am not the one who initiated this thread. I never thought my issue will go this long. Sorry about that.

Mine is lenovo Y560 with ubuntu 12.04 in it. I have problem with both wired and wireless.

---

### Post by harishankar on 2013-04-17
Hi

It did the job. :)

Now i can connect to the net... 

```
cat /etc/resolv.conf

```
hash@ubuntu:~$ cat /etc/resolv.conf
nameserver 127.0.0.1

Btw, I wonder what actually happnened? At the beginning i was able to connect to internet from ubuntu, then my laptop suddenly switched off due to over heating and from then on, I couldnt connect to internt, both through wired and wireless. So this sudden turn off changed certain parameters?

---

### Post by chili555 on 2013-04-18
> So this sudden turn off changed certain parameters? That's certainly possible. I suspect that the system was stopped in the middle of writing to hard disk and the changes or corrections were lost. I suspect the damage could have been a lot worse. I hope you have found and corrected the reason for overheating.

I'm very glad it's working!

---

### Post by harishankar on 2013-04-18
Hi

Whenever i make video chatting/meeting i encounter overheating with Ubuntu. I am not sure whether there is any additional driver i would need. when i check System Settings-> Additional drivers, it asked to activate 'AMD proprietary FGLRX graphic driver', which i did. But my laptop is still overheating for certain video application. Even for movies(played in VLC) over time, it is getting over heated. Any suggestion?

---

### Post by chili555 on 2013-04-18
> **harishankar said:**
> Hi

Whenever i make video chatting/meeting i encounter overheating with Ubuntu. I am not sure whether there is any additional driver i would need. when i check System Settings-> Additional drivers, it asked to activate 'AMD proprietary FGLRX graphic driver', which i did. But my laptop is still overheating for certain video application. Even for movies(played in VLC) over time, it is getting over heated. Any suggestion?I am not very experienced at video issues. I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

I also suggest you avoid overheating until you are sure it is fixed. It is possible to fry your video card and/or your CPU without much warning. I own two Lenovo laptops and I sure hate for either of them to burn up. 

I'd suspect it may be that the fan is not speeding up properly and I'd also Google 'overheating Ubuntu fglrx.'

There you are: everything I know about video!

---

