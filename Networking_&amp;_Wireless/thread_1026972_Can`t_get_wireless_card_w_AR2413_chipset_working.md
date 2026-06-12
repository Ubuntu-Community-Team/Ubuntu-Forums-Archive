---
title: "Can`t get wireless card w/ AR2413 chipset working"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by seubill on 2008-12-31
Using D-Link WDA-1320 wireless card on Dell desktop with dual-boot Windows XP / Ubuntu 8.10 setup.  Wireless connection works great in XP, but extremely poor in Ubuntu. Loopback ping (127.0.0.1) returns 0% loss, router/gateway ping (192.168.1.1) returns 100% loss, (in Ubuntu).

lshw output:


```
bill@J325P81:~$ sudo lshw -c network
[sudo] password for bill: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.3 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wmaster0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.5 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:ce:08:24:4f:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
bill@J325P81:~$ 
```

---

### Post by pytheas22 on 2008-12-31
It looks like the card is currently being driven by the ath9k driver.  I wonder if you would have better connectivity using ath_pci (madwifi).  To switch to that driver, run:
```

sudo modprobe -r ath_pci ath9k
sudo modprobe ath9k
sudo ifconfig ath0 up
```

Then connect again.  Is there a difference?  If so, we can make your machine use ath_pci permanently (for the time being, rebooting will cause you to default back to the current configuration).

---

### Post by seubill on 2008-12-31
After the last command, this returned:

Ath0: ERROR while getting interface flags: No Such Device

---

### Post by kevdog on 2008-12-31
After the last set of commands can you post lshw -C network again?

---

### Post by seubill on 2008-12-31
Here is the second run of lshw -c network:

bill@J325P81:~$ sudo lshw -c network
[sudo] password for bill: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.3 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wmaster0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.5 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:84:06:e7:5c:8a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
bill@J325P81:~$

---

### Post by pytheas22 on 2008-12-31
hmmm, it seems that ath_pci didn't want to claim your card, but the Internet is telling me it should.  Could you please post the output of these commands:
```

lspci -nn | grep -i atheros
sudo modprobe -r ath_pci ath9k
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
```

---

### Post by seubill on 2008-12-31
Is **ath9k[B] a typo? Should it not be [B]ath5k[B]?**[/B][/B][/B]

```
It looks like the card is currently being driven by the ath9k driver. I wonder if you would have better connectivity using ath_pci (madwifi). To switch to that driver, run:
Code:

sudo modprobe -r ath_pci ath9k
sudo modprobe ath9k
sudo ifconfig ath0 up


```

---

### Post by pytheas22 on 2008-12-31
> Is ath9k a typo? Should it not be ath5k?

Yes, you're right, sorry for that...but ath5k is not included by default in any version of Ubuntu that I know of.  Did you compile drivers yourself?  And which Ubuntu release are you using?

Please also still post the output of:
```

lspci -nn | grep -i atheros
sudo modprobe -r ath_pci ath5k
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
```

---

### Post by seubill on 2008-12-31
Using Ubuntu 8.10 desktop.  The driver comes in Linux backports modules intrepid generic.

1:~$ lspci -nn | grep -i atheros
05:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
bill@J325P81:~$ sudo modprobe -r ath_pci ath5k
bill@J325P81:~$ sudo modprobe ath_pci
bill@J325P81:~$ dmesg | grep -e ath -e wlan
[   16.568540] ath5k_pci 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.568584] ath5k_pci 0000:05:05.0: registered as 'phy0'
[   17.156703] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   31.904939] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.806879] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[   65.812526] wlan0: authenticated
[   65.812543] wlan0: associate with AP 00:1a:2b:69:06:3f
[   65.814533] wlan0: RX AssocResp from 00:1a:2b:69:06:3f (capab=0x411 status=0 aid=2)
[   65.814546] wlan0: associated
[   65.814982] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   76.040511] wlan0: no IPv6 routers present
[ 2075.129329] ath_hal: module license 'Proprietary' taints kernel.
[ 2075.132305] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 2075.152635] wlan: 0.9.4
[ 2075.162602] ath_pci: 0.9.4
[ 2534.852585] ath_pci: driver unloaded
[ 2534.860032] wlan: driver unloaded
[ 2534.862164] ath_hal: driver unloaded
[ 2534.929308] ath5k_pci 0000:05:05.0: PCI INT A disabled
[ 2555.367274] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 2555.386192] wlan: 0.9.4
[ 2555.395996] ath_pci: 0.9.4
[ 2555.396604] ath_pci 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2555.999875] ath_rate_sample: 1.2 (0.9.4)
[ 2570.496010] ath0: no IPv6 routers present

---

### Post by seubill on 2008-12-31
re-post coming shortly, I posted the ath9k by mistake

Note: have corrected post 9.

      and post 11 has the same info.

---

### Post by seubill on 2008-12-31
This should be correct:

```
bill@J325P81:~$ lspci -nn | grep -i atheros
05:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
bill@J325P81:~$ sudo modprobe -r ath_pci ath5k
bill@J325P81:~$ sudo modprobe ath_pci
bill@J325P81:~$ dmesg | grep -e ath -e wlan
[   16.568540] ath5k_pci 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.568584] ath5k_pci 0000:05:05.0: registered as 'phy0'
[   17.156703] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   31.904939] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.806879] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[   65.812526] wlan0: authenticated
[   65.812543] wlan0: associate with AP 00:1a:2b:69:06:3f
[   65.814533] wlan0: RX AssocResp from 00:1a:2b:69:06:3f (capab=0x411 status=0 aid=2)
[   65.814546] wlan0: associated
[   65.814982] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   76.040511] wlan0: no IPv6 routers present
[ 2075.129329] ath_hal: module license 'Proprietary' taints kernel.
[ 2075.132305] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 2075.152635] wlan: 0.9.4
[ 2075.162602] ath_pci: 0.9.4
[ 2534.852585] ath_pci: driver unloaded
[ 2534.860032] wlan: driver unloaded
[ 2534.862164] ath_hal: driver unloaded
[ 2534.929308] ath5k_pci 0000:05:05.0: PCI INT A disabled
[ 2555.367274] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 2555.386192] wlan: 0.9.4
[ 2555.395996] ath_pci: 0.9.4
[ 2555.396604] ath_pci 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2555.999875] ath_rate_sample: 1.2 (0.9.4)
[ 2570.496010] ath0: no IPv6 routers present
bill@J325P81:~$ 
```

---

### Post by seubill on 2008-12-31
Hello...What happened to the help?:confused:

---

### Post by seubill on 2008-12-31
Following are the results of:

ping -c 5 google.com
iwconfig
ifconfig


bill@J325P81:~$ ping -c 5 google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=237 time=134 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=237 time=135 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=237 time=132 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=237 time=136 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=237 time=129 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 129.762/133.749/136.930/2.501 ms
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Broadband1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:69:06:3F   
          Bit Rate=12 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=29/100  Signal level:-74 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.1 KB)  TX bytes:1100 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fefb:4f83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6385 (6.3 KB)  TX bytes:7190 (7.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-FB-4F-83-66-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bill@J325P81:~$

---

### Post by pytheas22 on 2008-12-31
It looks like your card came up under the ath_pci module, and you were able to ping Google without a problem.  Could you access web pages?  If so, we can make the changes permanent.

Sorry for the delay; I'll respond again as soon as I can but at this point that may not be till tomorrow.

---

### Post by seubill on 2008-12-31
No sir, can not access web pages. If I hover the mouse pointer over the wireless strength icon/indicator at the top edge of the desktop, it often shows 21% or so. 
 
System>Administration>Hardware Drivers indicates "Support for 5xxx series of Atheros 802.11 wireless LAN cards" The green radio button next to it is on indicating "This driver is activated and currently in use"

BTW, I never have run the commands in the post (number 2) about using the madwifi driver, as I was unsure of the text being correct with regard to ath9 or ath5, and didn`t want to mess up the system any more than presently is.

Understand it is getting late now and I will check back in tommorrow:D

Happy New Year 2009 to all!:D

---

### Post by pytheas22 on 2009-01-01
> No sir, can not access web pages

Sorry, I thought you could because in post #13 you can clearly ping google.com without any packet loss.  What happens if you type:
```

wget google.com
```

It could be that your problem is Firefox-specific; the result of the command above will help rule that out (wget is basically a web browser, for our purposes).

---

### Post by seubill on 2009-01-01
Interesting notion there about Firefox specific problem, Internet Explorer works very well. Same machine, so I guess that rules out any hardware/location concern. Anyway, here is the output of wget google.com:


```
bill@J325P81:~$ wget google.com
--2008-12-31 23:56:35--  http://google.com/
Resolving google.com... 209.85.171.100, 72.14.205.100, 74.125.45.100
Connecting to google.com|209.85.171.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2008-12-31 23:57:00--  http://www.google.com/
Resolving www.google.com... 72.14.205.147, 72.14.205.99, 72.14.205.103, ...
Connecting to www.google.com|72.14.205.147|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 5,953       33.4K/s   in 0.2s    

2008-12-31 23:57:01 (33.4 KB/s) - `index.html' saved [5953]


``` 

It took forever to connect, still no webpages.

---

### Post by pytheas22 on 2009-01-01
hmmm, it looks like wget works without a problem, so that makes me lean more towards blaming Firefox.  If you type this command:
```

sudo apt-get install konqueror
```

it will download and install a different browser called Konqueror, which you'll be able to find under the Applications>Internet menu.  Does Konqueror work better?

Also, to get a better idea of exactly how long it's taking to wget Google, please post the output of:
```

time wget google.com
```

> 
Internet Explorer works very well

Do you mean that it works well under Windows on this computer, or did you install IE in Ubuntu through wine?

---

### Post by seubill on 2009-01-01
I meant that IE works well in Windows on the same computer; it`s a dual-boot XP/Ubuntu setup. Will run the command to download and install Konquer in a short...

Here is the output of time wget google.com:


```
bill@J325P81:~$ time wget google.com
--2009-01-01 00:35:49--  http://google.com/
Resolving google.com... 74.125.45.100, 209.85.171.100, 72.14.205.100
Connecting to google.com|74.125.45.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2009-01-01 00:35:49--  http://www.google.com/
Resolving www.google.com... 72.14.205.103, 72.14.205.104, 72.14.205.147, ...
Connecting to www.google.com|72.14.205.103|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.1'

    [ <=>                                   ] 5,953       35.2K/s   in 0.2s    

2009-01-01 00:35:49 (35.2 KB/s) - `index.html.1' saved [5953]


real	0m0.881s
user	0m0.004s
sys	0m0.008s
```

---

### Post by seubill on 2009-01-01
Trying now to download Konqueror, but is not looking good, 0% after several minutes.

---

### Post by seubill on 2009-01-01
Konqueror download connection failed:

```
bill@J325P81:~$ sudo apt-get install konqueror
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wamerican fakeroot gimp-help-en nvidia-settings
  openoffice.org-hyphenation-en-us openoffice.org-l10n-common gimp-help-common
  dkms openoffice.org-thesaurus-en-au openoffice.org-hyphenation
  openoffice.org-thesaurus-en-us openoffice.org-l10n-en-gb patch
  openoffice.org-l10n-en-za wbritish openoffice.org-help-en-gb
  openoffice.org-help-en-us
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dolphin kde-icons-oxygen kdebase-bin kdebase-data kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kfind khelpcenter4 konqueror-nsplugins
  libaudio2 libclucene0ldbl libkonq5 libkonq5-templates libmysqlclient15off
  libphonon4 libpq5 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-xml libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 mysql-common phonon
  phonon-backend-gstreamer qt4-qtconfig raptor-utils redland-utils
  soprano-daemon
Suggested packages:
  kdebase nas libqt4-dev phonon-backend-xine phonon-backend-vlc
  phonon-backend-mplayer
The following NEW packages will be installed:
  dolphin kde-icons-oxygen kdebase-bin kdebase-data kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kfind khelpcenter4 konqueror
  konqueror-nsplugins libaudio2 libclucene0ldbl libkonq5 libkonq5-templates
  libmysqlclient15off libphonon4 libpq5 libqt4-dbus libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4 libqtgui4 libraptor1
  librasqal0 librdf0 libsoprano4 libstreamanalyzer0 libstreams0
  libstrigiqtdbusclient0 mysql-common phonon phonon-backend-gstreamer
  qt4-qtconfig raptor-utils redland-utils soprano-daemon
0 upgraded, 48 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.6MB of archives.
After this operation, 147MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid-updates/main libqtcore4 4.4.3-0ubuntu1.1 [2085kB]
Err http://us.archive.ubuntu.com intrepid-updates/main libqtcore4 4.4.3-0ubuntu1.1
  Connection failed [IP: 91.189.88.31 80]
0% [Connecting to us.archive.ubuntu.com (91.189.88.40)]

```
:confused:

---

### Post by seubill on 2009-01-01
Maybe a little silly, but this is the rest of the Konqueror download attempt:


```
Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-dbus 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libaudio2 1.9.1-4
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqtgui4 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libphonon4 4:4.2.0-0ubuntu1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-script 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-designer 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-network 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-sql 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-qt3support 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-svg 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libclucene0ldbl 0.9.20-3
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libraptor1 1.4.17-1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main mysql-common 5.0.67-0ubuntu6
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libmysqlclient15off 5.0.67-0ubuntu6
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libpq5 8.3.5-0ubuntu8.10
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main librasqal0 0.9.15-2
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main librdf0 1.0.7-1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main soprano-daemon 2.1.1+dfsg.1-0ubuntu1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libsoprano4 2.1.1+dfsg.1-0ubuntu1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libstreams0 0.5.11-1ubuntu2
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libstreamanalyzer0 0.5.11-1ubuntu2
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-opengl 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main phonon-backend-gstreamer 4:4.2.0-0ubuntu1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main phonon 4:4.2.0-0ubuntu1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdelibs5-data 4:4.1.3-0ubuntu1~intrepid4
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdelibs-bin 4:4.1.3-0ubuntu1~intrepid4
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdelibs5 4:4.1.3-0ubuntu1~intrepid4
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main libstrigiqtdbusclient0 0.5.11-1ubuntu2
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime-bin-kde4 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime-data-common 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime-data 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kde-icons-oxygen 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libkonq5-templates 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libkonq5 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main dolphin 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-data 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-bin 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main kfind 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main khelpcenter4 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main konqueror 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main konqueror-nsplugins 4:4.1.3-0ubuntu1~intrepid1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-sql-mysql 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid-updates/main qt4-qtconfig 4.4.3-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main raptor-utils 1.4.17-1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main redland-utils 1.0.7-1
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.4.3-0ubuntu1.1_i386.deb  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.1-4_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.2.0-0ubuntu1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.20-3_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/raptor/libraptor1_1.4.17-1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.67-0ubuntu6_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.67-0ubuntu6_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.5-0ubuntu8.10_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rasqal/librasqal0_0.9.15-2_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/redland/librdf0_1.0.7-1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.1.1+dfsg.1-0ubuntu1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.1.1+dfsg.1-0ubuntu1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.5.11-1ubuntu2_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.5.11-1ubuntu2_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon-backend-gstreamer_4.2.0-0ubuntu1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon_4.2.0-0ubuntu1_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.1.3-0ubuntu1~intrepid4_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.1.3-0ubuntu1~intrepid4_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.1.3-0ubuntu1~intrepid4_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstrigiqtdbusclient0_0.5.11-1ubuntu2_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-bin-kde4_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data-common_4.1.3-0ubuntu1~intrepid1_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.1.3-0ubuntu1~intrepid1_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.1.3-0ubuntu1~intrepid1_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/libkonq5-templates_4.1.3-0ubuntu1~intrepid1_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/libkonq5_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/dolphin_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-data_4.1.3-0ubuntu1~intrepid1_all.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/khelpcenter4_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror-nsplugins_4.1.3-0ubuntu1~intrepid1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.4.3-0ubuntu1.1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.17-1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/redland/redland-utils_1.0.7-1_i386.deb  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
bill@J325P81:~$ 


```

---

### Post by seubill on 2009-01-01
Signing off for now gentlemen, will check back in around noon-ish (CST) tomorrow, 01 Jan.

---

### Post by pytheas22 on 2009-01-01
Given the failure of Konqueror to download, the only conclusion I can come to is that the ath5k driver that you're using is not going to work for you, at least not this version of it.  I still think that you should try switching to ath_pci, which seemed last night to be able to bring up your card.  Please run these commands and post all the output:
```

sudo rmmod ath5k
sudo rmmod ath9k
sudo rmmod ath_pci
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
sudo iwlist scan
```

Then see if you can connect.

Also, the commands above do have you removing both ath9k and ath5k.  Don't worry about this; if you try to remove a module that isn't there, nothing will happen besides an error message.  And if things get messed up worse than they are now because of those commands, rebooting your computer will cause you to default back to ath5k and your current situation.

---

### Post by seubill on 2009-01-01
Ran all the commands, rebooted, no connection. Hardware Drivers application still shows the green light as before for Atheros 5xxx driver being activated.


```
bill@J325P81:~$ sudo rmmod ath5k
[sudo] password for bill: 
bill@J325P81:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
bill@J325P81:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
bill@J325P81:~$ sudo modprobe ath_pci
bill@J325P81:~$ dmesg | grep -e ath -e wlan
[   15.728536] ath5k_pci 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.728581] ath5k_pci 0000:05:05.0: registered as 'phy0'
[   16.808233] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   30.604962] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  238.007133] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[  238.009418] wlan0: authenticated
[  238.009434] wlan0: associate with AP 00:1a:2b:69:06:3f
[  238.011859] wlan0: RX AssocResp from 00:1a:2b:69:06:3f (capab=0x411 status=0 aid=2)
[  238.011872] wlan0: associated
[  238.012637] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  248.800017] wlan0: no IPv6 routers present
[  438.109528] ath5k_pci 0000:05:05.0: PCI INT A disabled
[  514.431084] ath_hal: module license 'Proprietary' taints kernel.
[  514.434081] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  514.454394] wlan: 0.9.4
[  514.464327] ath_pci: 0.9.4
[  514.464403] ath_pci 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  515.063657] ath_rate_sample: 1.2 (0.9.4)
[  529.580009] ath0: no IPv6 routers present
bill@J325P81:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

bill@J325P81:~$ 
```

Additionally, now it keeps prompting for a WPA password, which I enter, still can not connect. Keeps prompting for password. Appears password gets changed into long string of alpha/numeric digits, perhaps encrypting, or messed up, I don`t know which.:confused:

---

### Post by pytheas22 on 2009-01-01
You can definitely at least see networks using ath_pci.

If you disable encryption on your router temporarily, can you connect using ath_pci and download at reasonable speeds?  If so, we at least know that ath_pci makes your card work without a problem; it's just a matter of figuring out the WPA association.  To make sure you're using ath_pci, type 'sudo iwlist scan'.  If you see scan results on an interface named 'ath0', you're using ath_pci.  If the interface is 'wlan0', your card is still being driven by ath5k and you should type:

```
sudo modprobe -r ath9k ath5k ath_pci
sudo modprobe ath_pci
```

to get it going under ath_pci again.

Also, another thought is that it might help to disable IPv6.  To do that, open up your /etc/modprobe.d/aliases file by typing:
```

sudo gedit /etc/modprobe.d/aliases
```

Look for the line that says 'alias net-pf-10 ipv6'.  Change it to say:
```

alias net-pf-10 off
```

Then save and close the file.  You will need to reboot for the change to take effect.

---

### Post by seubill on 2009-01-01
OK, just to check before I go any farther, does this mean the card is still being driven?



bill@J325P81:~$ sudo iwlist scan
[sudo] password for bill: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

bill@J325P81:~$

---

### Post by pytheas22 on 2009-01-01
> OK, just to check before I go any farther, does this mean the card is still being driven?


Yes, it's being driven by ath_pci, since the interface is named 'ath0' in the output of 'sudo iwlist scan':

```
bill@J325P81:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

**ath0**      Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by seubill on 2009-01-01
just edited post number 27

is now correct

---

### Post by pytheas22 on 2009-01-01
> just edited post number 27

is now correct

Oh, in that case, then the card wasn't being driven by ath_pci.  You want to run these commands:
```

sudo rmmod ath5k
sudo rmmod ath9k
sudo rmmod ath_pci
sudo modprobe ath_pci
sudo iwlist scan
```

And the last command should give output that shows ath_pci driving the card.  When you get to that point, try disabling encryption on your router and see if it connects at normal speeds.

---

### Post by seubill on 2009-01-01
I think that it`s back to ath_pci now:

```
bill@J325P81:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

bill@J325P81:~$ 

```

In the router should I select OPEN, SHARED, 802.1x to temporarily disable security?

---

### Post by seubill on 2009-01-01
OK, here is what I have now:

```
bill@J325P81:~$ sudo rmmod ath5k
[sudo] password for bill: 
bill@J325P81:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
bill@J325P81:~$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
bill@J325P81:~$ sudo modprobe ath_pci
bill@J325P81:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

bill@J325P81:~$ 

```

---

### Post by pytheas22 on 2009-01-01
Yes, it's on ath_pci again.  To disable security in your router, you should open up a web browser on a computer that's connected to the router and put 192.168.1.1 in the address bar (if that doesn't work, try 192.168.0.1 or 10.0.0.1).  That should bring you to a configuration page where you can turn off the wireless security.  Can you connect and download at normal speeds with it disabled?

---

### Post by seubill on 2009-01-01
I`m in the wireless security page of the router, but unsure of what selection to make. It is currently WPA-PSK. The other options are OPEN, SHARED, 802.1x and some WEP choices. I tried OPEN, but when I clicked save/apply, came back to WPA-PSK.

Also, have turned off IPv6 in gedit. Still no difference.:confused:

---

### Post by pytheas22 on 2009-01-01
> I`m in the wireless security page of the router, but unsure of what selection to make. It is currently WPA-PSK. The other options are OPEN, SHARED, 802.1x and some WEP choices. I tried OPEN, but when I clicked save/apply, came back to WPA-PSK.


You should have an option to disable security/encryption entirely.  Does that appear anywhere?

If not, see if you can connect if you switch to WEP encryption.

---

### Post by seubill on 2009-01-01
lost all wireless, got to another machine (ethernet). Can see any option for disabling security entirely, gives these:

Open
Shared
802.1x
WPA
WPA-PSK
WPA2
WPA2-PSK
mixed WPA2/WPA
mixed WPA/WPA-PSK

really a bugger!

---

### Post by pytheas22 on 2009-01-01
Sorry that made it worse.

Try changing to 'Open'.  I'm not sure if they're referring there to open authentication or an 'open network' in the sense of no security.  But if it's the latter, then switching to 'Open' will give what you want.

---

### Post by seubill on 2009-01-01
OK, if I go with "open" then WEP encryption can be disabled or enabled.

Also, do I need to reboot router?

---

### Post by seubill on 2009-01-01
"Open" is for network authentication. Should I disable WEP (default)?

---

### Post by pytheas22 on 2009-01-01
> Should I disable WEP (default)?

Yes, switch to open authentication and disable WEP, then see if you can connect.
> 
Also, do I need to reboot router?

On most routers, if you change the security type, it should automatically apply the change without having to reboot.  If you need to reboot for changes to take effect, it should tell you.

If you're not sure whether the router is operating with open security, post the output again of:
```

sudo iwlist scan
```

---

### Post by seubill on 2009-01-01
Just hit save/apply without re-booting router, network authentication is "open" and WEP encryption is disabled.

Still no connection at wireless machine.

Here is result:

```
bill@J325P81:~$ sudo iwlist scan
[sudo] password for bill: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

```

---

### Post by kevdog on 2009-01-01
Can you post ifconfig?

---

### Post by pytheas22 on 2009-01-01
Please also post the output of:
```

sudo iwconfig ath0 mode managed channel 11 essid "Broadband1"
sudo dhclient ath0
```

---

### Post by seubill on 2009-01-01
here is ifconfig:

```
bill@J325P81:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27163 (27.1 KB)  TX bytes:7890 (7.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-FB-4F-83-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36549 errors:0 dropped:0 overruns:0 frame:95
          TX packets:1053 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3496088 (3.4 MB)  TX bytes:78090 (78.0 KB)
          Interrupt:17 

bill@J325P81:~$ 


```

---

### Post by seubill on 2009-01-01
```
bill@J325P81:~$ sudo iwconfig ath0 mode managed channel 11 essid "Broadband 1"
[sudo] password for bill: 
bill@J325P81:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:fb:4f:83
Sending on   LPF/ath0/00:15:e9:fb:4f:83
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@J325P81:~$ 

```

---

### Post by pytheas22 on 2009-01-01
Unfortunately I have to head out now and may not be back till later tonight or tomorrow, but will check back then.  In the meantime, I hope kevdog, who knows a lot more about Ubuntu and wireless, might have some better suggestions than mine.

---

### Post by seubill on 2009-01-01
Understand, hey thanks for your help this far!:D

---

### Post by kevdog on 2009-01-01
Did you take your wired interface down first.

Something like
sudo ifconfig eth0 down
sudo ifconfig ath0 up
sudo iwconfig ath0 essid Broadband1
sudo dhclient ath0

If this doesnt work, try changing your broadcast channel on your router from 11 to something else like 6 or 7.  Ive seen something strange like that in the past also.

---

### Post by seubill on 2009-01-01
Have shutdown and rebooted problem machine since last post. Apparently has rebooted to ath5k_pci driver.

```
bill@J325P81:~$ sudo ifconfig eth0 down
[sudo] password for bill: 
bill@J325P81:~$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
bill@J325P81:~$ sudo iwconfig ath0 essid Broadband1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
bill@J325P81:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
bill@J325P81:~$ 



```

Will try changing the router channels and see what happens.

---

### Post by seubill on 2009-01-01
OK, here's the latest wierdness: switched router channel to 6, machine accessed web pages fairly good (50% connection in strength bars), rebooted into Windows to check it's connection, worked real good. Next, rebooted back to Ubuntu and very poor connection, could not access web pages. Tried out router channel 7 next and not good.:confused:

---

### Post by kevdog on 2009-01-01
Very strange b/c it seems to be a router / driver interaction problem which theoretically not possible, I've seen before.  Again you have two options for your wireless driver:the ath_5k driver or a patched madwifi version.  I'd have both on hand and available to use since its relatively easy to take down the interface, unload the kernel module, load the other kernel module and then bring up and then configure the interface.  What kernel version are you using?

---

### Post by seubill on 2009-01-01
I'm using the 2.6.27-9 generic kernel.

Tried every router channel and can't get a decent connection with any.

Here's something else that's weird; when the machine was a dedicated Windows only platform the wireless connection was very good. Same wireless card, same router.  Later same machine became a dedicated Ubuntu 8.10 only  platform with no wireless connection issue (connected well). Again, same card, same router. Currently the machine is a dual-boot Windows/Ubuntu platform, with wireless working well in Windows, but very poorly in Ubuntu. Same card, same router, and never any location change of machine or router.

Anyway, I've put router back on channel 11 as before and WPA/PSK enabled.

I also have a Dell Precision laptop with a dual-boot XP/Ubuntu [B]8.04[B] that connects well wirelessly in both OS's to the same router.

And finally---OK I REPENT!!

---

### Post by seubill on 2009-01-02
How about ndiswrapper, can this be a viable option for this chipset (AR2413)?

---

### Post by pytheas22 on 2009-01-02
Sorry to see that you still haven't made much progress.
> 
How about ndiswrapper, can this be a viable option for this chipset (AR2413)? 

Yes, I was thinking of ndiswrapper too as a final resort (it's really a shame to have to use ndiswrapper with wireless cards that are supposed to have such good native support...).  If you could post the output of just this one command (so that I know whether your system is 32 or 64-bit), I'll find instructions on installing ndiswrapper:

```

uname -m
```

---

### Post by seubill on 2009-01-02
I did uname -m yesterday, and the system is i686 and 32 bit.

Suddenly I got a 33% connection and have got ndisgtk package downloaded through synpatic package manager.

Systwm>Adm.>Windows Wireless Drivers wants to install, prompting me to select the .inf file for insatllation and I do not know what to select.

---

### Post by seubill on 2009-01-02
I did uname -m yesterday, and the system is i686 and 32 bit.

Suddenly I got a 33% connection and have got ndisgtk package downloaded through synpatic package manager.

System>Adm.>Windows Wireless Drivers wants to install, prompting me to select the .inf file for installation and I do not know what to select.

Some of the choices are "Recently used", "root",Desktop", "File System", and selecting one of these brings up another tree menu.
There is also a "none" option.:D

---

### Post by pytheas22 on 2009-01-02
Try running this command to download drivers for your card (I couldn't get the download to work through Firefox; I had to use wget):
```

cd ~/Desktop; wget ftp://ftp.work.acer-euro.com/notebook/travelmate_2310/driver/802bg.zip
```

This will save a zip file to your desktop containing the Windows drivers.  Unzip the file by right-clicking and selecting 'Extract Here'.  Then open up ndisgtk and point it to the file 'net5211.inf' inside the folder that you just unpacked.  This should get ndiswrapper set up.

Then please post the output of these commands so we can initiate ndiswrapper and see how well it works:
```

ndiswrapper -l
sudo modprobe -r ath9k ath5k ath_pci ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by seubill on 2009-01-02
Got connected with wget, but downoad is not co-operating too good. I have the original installation CD that came with the wireless card. Tried  running it to pull the drivers from, but every time I go to open the drivers folder, I get a null error. Sure wish this thing would give me a break!

I have another Ubuntu machine that is ethernet wired, what about using wget with it, saving to a jumpdrive, and then transferring to the desktop?

---

### Post by seubill on 2009-01-02
Closed the terminal window on the problem machine and the 802bg.zip was on the desktop. Right-clicked on it, selected "extract here" and returned "An error occurred while loading the archive (null)"

---

### Post by pytheas22 on 2009-01-02
Wow, you do have bad Linux luck :)
> 
I have another Ubuntu machine that is ethernet wired, what about using wget with it, saving to a jumpdrive, and then transferring to the desktop?

Yeah, just download it on a different machine and transfer it over.
> 
Closed the terminal window on the problem machine and the 802bg.zip was on the desktop. Right-clicked on it, selected "extract here" and returned "An error occurred while loading the archive (null)"

This is probably because the file wasn't completely downloaded and is corrupted.  Delete it, and try again using the file transferred from your other Ubuntu computer.

Don't try using the .inf file from your driver CD because according to what I read about your card, it's very particular about which Windows drivers it will take--many users said that ndiswrapper didn't work with the drivers that shipped with their CDs.  The ones from the link I gave you are reported to work, however, according to the [database]("http://burnthesorbonne.com/ndiswrapper/a.html").

---

### Post by seubill on 2009-01-02
OK, thanks for that good advice! I got the .zip file download from the ethernet machine and succussfully transferred over with the jumpdrive to the problem child. Opened ndisgtk and got to file 'net 5211.inf' without any problem and installed. Reported driver already installed.

Anyway will be running the commands from your post and posting the output here in just a few minutes..:D

---

### Post by seubill on 2009-01-02
OK, here are the command outputs;


```
bill@J325P81:~$ ndiswrapper -l
net5211 : driver installed
	device (168C:001A) present (alternate driver: ath5k)
bill@J325P81:~$ sudo modprobe -r ath9k ath5k ath_pci ndiswrapper 
[sudo] password for bill: 
bill@J325P81:~$ sudo modprobe
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
bill@J325P81:~$ sudo modprobe ndiswrapper
bill@J325P81:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

bill@J325P81:~$ dmesg | grep -e ndis -e wlan
[   18.234546] wlan: 0.9.4
[   33.866701] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[   33.868160] wlan0: authenticated
[   33.868174] wlan0: associate with AP 00:1a:2b:69:06:3f
[   33.870350] wlan0: RX AssocResp from 00:1a:2b:69:06:3f (capab=0x401 status=0 aid=1)
[   33.870364] wlan0: associated
[   33.871211] wlan0: disassociating by local choice (reason=3)
[  136.438821] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[  136.442953] wlan0: authenticated
[  136.442971] wlan0: associate with AP 00:1a:2b:69:06:3f
[  136.444817] wlan0: RX AssocResp from 00:1a:2b:69:06:3f (capab=0x401 status=0 aid=1)
[  136.444825] wlan0: associated
[  146.448107] wlan0: disassociating by local choice (reason=3)
[  196.494939] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[  196.496463] wlan0: authenticated
[  196.496473] wlan0: associate with AP 00:1a:2b:69:06:3f
[  196.498499] wlan0: RX AssocResp from 00:1a:2b:69:06:3f (capab=0x401 status=0 aid=1)
[  196.498508] wlan0: associated
[  196.499074] wlan0: disassociating by local choice (reason=3)
[ 2723.261284] wlan0: authenticate with AP 00:1a:2b:69:06:3f
[ 2723.262760] wlan0: authenticated
[ 2723.262770] wlan0: associate with AP 00:1a:2b:69:06:3f
[ 2723.265188] wlan0: RX ReassocResp from 00:1a:2b:69:06:3f (capab=0x411 status=0 aid=1)
[ 2723.265196] wlan0: associated
[10515.538395] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[10515.551474] usbcore: registered new interface driver ndiswrapper
[11363.216040] wlan: driver unloaded
[11363.269297] usbcore: deregistering interface driver ndiswrapper
[11408.587818] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[11408.606870] ndiswrapper: driver net5211 (,01/10/2004,4.0.0.14001) loaded
[11408.607261] ndiswrapper 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[11409.088038] ndiswrapper: using IRQ 17
[11409.289642] wlan0: ethernet device 00:15:e9:fb:4f:83 using serialized NDIS driver: net5211, version: 0x40000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001A.5.conf
[11409.293175] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[11409.293854] usbcore: registered new interface driver ndiswrapper
bill@J325P81:~$ 
```:P

---

### Post by seubill on 2009-01-02
Still have very poor internet connection, showing 34% on bars. Got to Gmail homepage, but could not log onto my account.

Should I try disabling WPA/PSK?

---

### Post by seubill on 2009-01-02
OK, I went into the router, set network authentication to "Open", disabled WEP encryption, went to the problem child and set wireless security to "none". Deactivated the "Support for Atheros 5xxx wireless drivers" in Hardware Drivers. Now the crazy thing prompts for a network key for WPA/PSK (which is turned off) and refuses to connect. Was thinking to re-boot, but not sure if it will boot the ath5k driver by default.:confused:

---

### Post by pytheas22 on 2009-01-02
Well, it's good that ndiswrapper gets you connected even with WPA enabled.

However, it's bad that ndiswrapper gives poor performance.  I was hoping originally that your performance issues stemmed from some problem with the ath5k drivers.  But ndiswrapper uses a completely different driver, obviously, and if you see the same poor connectivity there, it makes me worried that the source of your problem lies somewhere more obscure than your wireless driver.

If you reboot, the card will probably come up again under ath9k.  To get it to work under ndiswrapper, you would run these commands:
```

sudo modprobe -r ath9k ath5k ath_pci ndiswrapper
sudo modprobe ndiswrapper
```

Then wait a few seconds and type 'lshw -C Network'.  The output should indicate that ndiswrapper is driving the card; for example:
```

*-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=**ndiswrapper**+net5211.inf latency=32 module=**ndiswrapper**
```

But we obviously still need to figure out why the card won't work well even under ndiswrapper.  If you could please post the output of these commands with the card running under ndiswrapper and connected to your network, it will help to rule some things out:

```
lshw -C Network
iwconfig
ifconfig
ping -c 20 google.com
time wget google.com
time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
ping -c 20 192.168.1.1
```

And by the way (I can't remember), have you tried connecting via wired ethernet with this computer under Ubuntu, and if so did you have any problems there?

---

### Post by seubill on 2009-01-02
Unsure about what going on or not going on here, anyway, re-booted, checked the Hardware Divers graphic box and the Athreos 5xxx was showing deactivated. Open terminal window and entered the commands and the output follows here. So is it indeed running the ndiswrapper now? No connectivity at all.


```
bill@J325P81:~$ sudo modprobe -r ath9k ath5k ath_pci ndiswrapper
[sudo] password for bill: 
bill@J325P81:~$ sudo modprobe ndiswrapper
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.3 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ba:04:3c:73:51:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ 
```

---

### Post by seubill on 2009-01-02
Sorry, I didn`t notice the rest of those commands on your post.  Will do them and post in a minute....

---

### Post by seubill on 2009-01-02
Well, here they are...should I use a hammer or maybe a pistol next...


```
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  Mode:Managed  Frequency:2.462 GHz  
          Access Point: Not-Associated   Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fbdf0000-fbe00000 

bill@J325P81:~$ ping -c 20 google.com
ping: unknown host google.com
bill@J325P81:~$ time wget google.com
--2009-01-02 15:22:01--  http://google.com/
Resolving google.com... failed: Name or service not known.
wget: unable to resolve host address `google.com'

real	0m0.054s
user	0m0.004s
sys	0m0.008s
bill@J325P81:~$ time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
--2009-01-02 15:22:54--  http://burnthesorbonne.com/files/OSSEC.pdf
Resolving burnthesorbonne.com... failed: Name or service not known.
wget: unable to resolve host address `burnthesorbonne.com'

real	0m0.005s
user	0m0.004s
sys	0m0.000s
rm: cannot remove `OSSEC.pdf': No such file or directory
bill@J325P81:~$ ping -c 20 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable
From 192.168.1.3 icmp_seq=5 Destination Host Unreachable
From 192.168.1.3 icmp_seq=6 Destination Host Unreachable
From 192.168.1.3 icmp_seq=7 Destination Host Unreachable
From 192.168.1.3 icmp_seq=9 Destination Host Unreachable
From 192.168.1.3 icmp_seq=10 Destination Host Unreachable
From 192.168.1.3 icmp_seq=11 Destination Host Unreachable
From 192.168.1.3 icmp_seq=13 Destination Host Unreachable
From 192.168.1.3 icmp_seq=14 Destination Host Unreachable
From 192.168.1.3 icmp_seq=15 Destination Host Unreachable
From 192.168.1.3 icmp_seq=17 Destination Host Unreachable
From 192.168.1.3 icmp_seq=18 Destination Host Unreachable
From 192.168.1.3 icmp_seq=19 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
20 packets transmitted, 0 received, +15 errors, 100% packet loss, time 19033ms
, pipe 3
bill@J325P81:~$ 


```

---

### Post by seubill on 2009-01-02
About your wired ethernet connection concern, I guess I could disconnect the tower from the monitor & everything, and carry it into the room where I could plug it up to ethernet cabling. Would I have to enable the interface first?

---

### Post by seubill on 2009-01-02
Just re-booted the problem child into Windows, just to see, connected to web very well (still wireless).

---

### Post by yknivag on 2009-01-02
No help to you I'm afraid seubill, but I have a similar card "Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)" and have had no connectivity since upgrading from 7.10 to 8.04.  Was working perfectly in 7.10 using ath_pci and WICD but now I get this on the command line...

```

gavin@knuckle:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

```

...and "No wireless networks found" in WICD.

:(

---

### Post by seubill on 2009-01-02
Causes me to ponder if I need to invest in a different card. I don't have a clue what would be a good choice for this platform, but really the drivers I have should do the job without a problem with this present card. Thanks for the info!:D

---

### Post by yknivag on 2009-01-02
It's causing me to ponder returning to Ubuntu7.10 which was working perfectly well for me.  The problem only started with my Atheros card when I upgraded to Hardy Heron.

---

### Post by seubill on 2009-01-02
switched driver back to ath5k. google ping showed slight improvement;


```
bill@J325P81:~$ sudo modprobe -r ath9k ath5k ath_pci ndiswrapper
[sudo] password for bill: 
bill@J325P81:~$ sudo modprobe ath5k
bill@J325P81:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/100  Signal level:-73 dBm  Noise level=-92 dBm
                    Encryption key:on
                    IE: Unknown: 000A42726F616462616E6431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000008f84a675
                    Extra: Last beacon: 20ms ago

bill@J325P81:~$ ath5k -l
bash: ath5k: command not found
bill@J325P81:~$ sudo ath5k -l
sudo: ath5k: command not found
bill@J325P81:~$ ath5k_pci -l
bash: ath5k_pci: command not found
bill@J325P81:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.3 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wmaster0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.5 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:d3:08:c5:b8:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Broadband1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:69:06:3F   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=28/100  Signal level:-75 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32386 (32.3 KB)  TX bytes:4001 (4.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-FB-4F-83-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bill@J325P81:~$ ping -c 20 google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=237 time=143 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=237 time=132 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=237 time=134 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=6 ttl=237 time=131 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=7 ttl=237 time=130 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=8 ttl=237 time=130 ms

--- google.com ping statistics ---
20 packets transmitted, 6 received, 70% packet loss, time 19038ms
rtt min/avg/max/mdev = 130.147/133.699/143.033/4.471 ms
bill@J325P81:~$ 



```

---

### Post by pytheas22 on 2009-01-02
It looks like you weren't connected when you ran those commands, but you said you were able to connect before under ndiswrapper.  Would it just not connect for you?  Could you try again?  I would want to see the output of these commands when you're connected:
```

lshw -C Network
iwconfig
ifconfig
ping -c 20 google.com
time wget google.com
time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
ping -c 20 192.168.1.1
```

but if you have no connection, they don't tell very much.

> About your wired ethernet connection concern, I guess I could disconnect the tower from the monitor & everything, and carry it into the room where I could plug it up to ethernet cabling. Would I have to enable the interface first?

No, you should be able to just plug in the cable and it would auto-connect (although given your luck so far, anything could happen).  It's worth a try if it's not a huge amount of trouble to move your computer because it would be useful to know how well the ethernet connection works, but don't worry about it if it's too hard.
> 
No help to you I'm afraid seubill, but I have a similar card "Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)" and have had no connectivity since upgrading from 7.10 to 8.04. Was working perfectly in 7.10 using ath_pci and WICD but now I get this on the command line...

yknivag: this is interesting.  seubill of course has a different card--2413 rather than 5213--but at this point it might also be worth a shot for him to burn an Ubuntu 7.10 live CD and see what happens with that.

Also, you might have better luck if you compiled madwifi from source.  There's a script [here]("http://ubuntuforums.org/showthread.php?t=798485") that makes it easy to do that.

You could also figure out specifically which build of madwifi was used in Ubuntu 7.10, and download the source for that and compile it, since you know it works.

---

### Post by seubill on 2009-01-02
Pytheas22, intended to post the outputs of the commands in your last post, but I cannot get an internet connection now, so I guess there`s no point:(

BTW. I do have a 8.04 Live CD

---

### Post by seubill on 2009-01-02
Well now the strength bars indicated a 34% connection, so I ran the commands. Looks like it booted up with the ndiswrapper driver.

```
bill@J325P81:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.3 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 ip=192.168.1.5 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 7a:6f:e1:04:a2:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Broadband1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:69:06:3F   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23625 (23.6 KB)  TX bytes:3548 (3.5 KB)
          Interrupt:17 Memory:fbdf0000-fbe00000 

bill@J325P81:~$ ping -C 20 google.com
ping: invalid option -- 'C'
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
bill@J325P81:~$ ping -c 20 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=239 time=129 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=239 time=127 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=239 time=131 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=239 time=125 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=239 time=126 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=6 ttl=239 time=127 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=7 ttl=239 time=125 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=8 ttl=239 time=128 ms

--- google.com ping statistics ---
20 packets transmitted, 8 received, 60% packet loss, time 19030ms
rtt min/avg/max/mdev = 125.312/127.685/131.494/1.958 ms
bill@J325P81:~$ time wget google.com
--2009-01-02 21:09:20--  http://google.com/
Resolving google.com... failed: Name or service not known.
wget: unable to resolve host address `google.com'

real	0m40.083s
user	0m0.000s
sys	0m0.004s
bill@J325P81:~$ time wget burnthesorbonne.com/files/OSSED.pdf; rm OSSEC.pdf
--2009-01-02 21:11:05--  http://burnthesorbonne.com/files/OSSED.pdf
Resolving burnthesorbonne.com... failed: Name or service not known.
wget: unable to resolve host address `burnthesorbonne.com'

real	0m40.036s
user	0m0.000s
sys	0m0.004s
rm: cannot remove `OSSEC.pdf': No such file or directory
bill@J325P81:~$ ping -c 20 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable
From 192.168.1.3 icmp_seq=4 Destination Host Unreachable
From 192.168.1.3 icmp_seq=5 Destination Host Unreachable
From 192.168.1.3 icmp_seq=6 Destination Host Unreachable
From 192.168.1.3 icmp_seq=8 Destination Host Unreachable
From 192.168.1.3 icmp_seq=9 Destination Host Unreachable
From 192.168.1.3 icmp_seq=10 Destination Host Unreachable
From 192.168.1.3 icmp_seq=12 Destination Host Unreachable
From 192.168.1.3 icmp_seq=13 Destination Host Unreachable
From 192.168.1.3 icmp_seq=14 Destination Host Unreachable
From 192.168.1.3 icmp_seq=16 Destination Host Unreachable
From 192.168.1.3 icmp_seq=17 Destination Host Unreachable
From 192.168.1.3 icmp_seq=18 Destination Host Unreachable
From 192.168.1.3 icmp_seq=19 Destination Host Unreachable
From 192.168.1.3 icmp_seq=20 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
20 packets transmitted, 0 received, +17 errors, 100% packet loss, time 19032ms
, pipe 3
bill@J325P81:~$ 


```

Also, it would not be too much trouble for me to rig up to ethernet wired (for testing)

---

### Post by seubill on 2009-01-02
Gentlemen: logging off for the night. Will check back in tomorrow (Sat.)

Appreciate you all!:D

---

### Post by pytheas22 on 2009-01-02
hmmm, some interesting stuff there.  Do you know which device on your local network has IP 192.168.1.3?  Pings to 192.168.1.1 seem to be redirecting there and dying, which is really weird.  Do you have any out-of-the-ordinary port-forwarding or triggering configured on your router?

It would also be interesting to see the output of:
```

netstat -ra
cat /etc/hosts
cat /etc/resolv.conf
```

when you're connected wirelessly via ndiswrapper.

And I would definitely like to see the output of these commands when you're connected via the wire:
```

lshw -C Network
iwconfig
ifconfig
ping -c 10 google.com
time wget google.com
time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
ping -c 10 192.168.1.1
ping -c 10 192.168.1.3
host 192.168.1.3
netsta -ra
cat /etc/hosts
cat /etc/resolv.conf
```

I'm beginning to suspect that there's some kind of weird routing problem going on here.  If it occurs on wired as well as wireless, then we know that it has to do with your networking configuration as a whole and will have a better idea of where to look to fix it.

---

### Post by seubill on 2009-01-03
Pytheas22, The IP address 192.168.1.3 belongs to an ethernet wired connection machine running a dual boot XP-Ubuntu 8.04.1 setup. I`ve noticed an interesting situation lately concerning that machine- when I shut down from Ubuntu, the connection light on the router stays lit for that machine indefinety, as though the connection stays up continually even with the machine turned off. Only occurs when shutting down from Ubuntu, shutting down from XP, the router light turns off. Checking the router settings on the port triggering page and there does not look like anything is set up for that. I have never set up anything like that.

By the way, I slipped in a 8.04 LTS Live CD into the problem machine, and am running from it right now to send this reply, good internet connection.

Will send the output of the commands a little later if I can get a connection  without the CD.

---

### Post by kevdog on 2009-01-03
seubill, there was several ancient posts addressing a similar type issue with conflicts when dual booting xp a long time ago.  Not even sure if they are relevant.  I've tried searching but can not find them.  I think they involved something like disconnecting the network cable after logging out of xp or something.

---

### Post by seubill on 2009-01-03
Pytheas22, here are the command outputs. Sorry about the length of that first output, I finally hit Control +C to stop that one. Will be rigging up the problem child with ethernet cabling in the next few minutes and will post those commands shortly. I had intended to plug it up to the cabling for the 192.168.1.3 machine, but will do something else now. Kevdog, thanks for that info, I don`t know what`s causing the situation, but seems like it`s all connected (no pun intended!)

```
unix  3      [ ]         STREAM     CONNECTED     20197    /tmp/orbit-bill/linc-1722-0-2a44d2720dd4
unix  3      [ ]         STREAM     CONNECTED     20196    
unix  3      [ ]         STREAM     CONNECTED     20193    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     20192    
unix  3      [ ]         STREAM     CONNECTED     20187    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     20186    
unix  3      [ ]         STREAM     CONNECTED     20181    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20180    
unix  3      [ ]         STREAM     CONNECTED     20114    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     20113    
unix  3      [ ]         STREAM     CONNECTED     20070    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20069    
unix  3      [ ]         STREAM     CONNECTED     20067    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20066    
unix  2      [ ]         DGRAM                    20054    
unix  3      [ ]         STREAM     CONNECTED     20031    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20030    
unix  3      [ ]         STREAM     CONNECTED     20029    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     20028    
unix  3      [ ]         STREAM     CONNECTED     20027    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     20026    
unix  3      [ ]         STREAM     CONNECTED     20022    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20020    
unix  3      [ ]         STREAM     CONNECTED     20015    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     20014    
unix  3      [ ]         STREAM     CONNECTED     20011    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     20010    
unix  3      [ ]         STREAM     CONNECTED     20013    /tmp/orbit-bill/linc-16af-0-573c3a9bb67df
unix  3      [ ]         STREAM     CONNECTED     20009    
unix  3      [ ]         STREAM     CONNECTED     20007    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     20006    
unix  3      [ ]         STREAM     CONNECTED     20005    /tmp/orbit-bill/linc-16af-0-573c3a9bb67df
unix  3      [ ]         STREAM     CONNECTED     20004    
unix  3      [ ]         STREAM     CONNECTED     20002    /tmp/orbit-bill/linc-16ed-0-6012839ca88bf
unix  3      [ ]         STREAM     CONNECTED     20001    
unix  3      [ ]         STREAM     CONNECTED     20000    /tmp/orbit-bill/linc-16e9-0-6012839cd565f
unix  3      [ ]         STREAM     CONNECTED     19999    
unix  3      [ ]         STREAM     CONNECTED     19994    /tmp/orbit-bill/linc-16f8-0-76225d43954e
unix  3      [ ]         STREAM     CONNECTED     19993    
unix  3      [ ]         STREAM     CONNECTED     19992    /tmp/orbit-bill/linc-16b6-0-232038e88835
unix  3      [ ]         STREAM     CONNECTED     19991    
unix  3      [ ]         STREAM     CONNECTED     19988    /tmp/orbit-bill/linc-16f8-0-76225d43954e
unix  3      [ ]         STREAM     CONNECTED     19987    
unix  3      [ ]         STREAM     CONNECTED     19984    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19983    
unix  3      [ ]         STREAM     CONNECTED     19982    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19981    
unix  3      [ ]         STREAM     CONNECTED     19980    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     19979    
unix  3      [ ]         STREAM     CONNECTED     19975    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19974    
unix  3      [ ]         STREAM     CONNECTED     19959    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19958    
unix  3      [ ]         STREAM     CONNECTED     19939    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19938    
unix  3      [ ]         STREAM     CONNECTED     19937    /tmp/orbit-bill/linc-16f9-0-1b97961df00e4
unix  3      [ ]         STREAM     CONNECTED     19936    
unix  3      [ ]         STREAM     CONNECTED     19933    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19932    
unix  3      [ ]         STREAM     CONNECTED     19928    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19927    
unix  3      [ ]         STREAM     CONNECTED     19926    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19925    
unix  3      [ ]         STREAM     CONNECTED     19893    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19892    
unix  3      [ ]         STREAM     CONNECTED     19884    /tmp/orbit-bill/linc-16f1-0-1fccff0365789
unix  3      [ ]         STREAM     CONNECTED     19883    
unix  3      [ ]         STREAM     CONNECTED     19880    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19879    
unix  3      [ ]         STREAM     CONNECTED     19878    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19877    
unix  3      [ ]         STREAM     CONNECTED     19876    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19875    
unix  3      [ ]         STREAM     CONNECTED     19853    /tmp/orbit-bill/linc-16f3-0-1fccff035d449
unix  3      [ ]         STREAM     CONNECTED     19852    
unix  3      [ ]         STREAM     CONNECTED     19849    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19848    
unix  3      [ ]         STREAM     CONNECTED     19847    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19845    
unix  3      [ ]         STREAM     CONNECTED     19777    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19776    
unix  3      [ ]         STREAM     CONNECTED     19775    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19774    
unix  3      [ ]         STREAM     CONNECTED     19770    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19769    
unix  3      [ ]         STREAM     CONNECTED     19843    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     19672    
unix  3      [ ]         STREAM     CONNECTED     19668    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19667    
unix  3      [ ]         STREAM     CONNECTED     19663    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19662    
unix  3      [ ]         STREAM     CONNECTED     19842    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     19653    
unix  3      [ ]         STREAM     CONNECTED     19649    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19648    
unix  3      [ ]         STREAM     CONNECTED     19613    /tmp/orbit-bill/linc-16f2-0-2b220c50991db
unix  3      [ ]         STREAM     CONNECTED     19612    
unix  3      [ ]         STREAM     CONNECTED     19578    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19577    
unix  3      [ ]         STREAM     CONNECTED     19572    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19571    
unix  3      [ ]         STREAM     CONNECTED     19570    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19569    
unix  3      [ ]         STREAM     CONNECTED     19568    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19567    
unix  3      [ ]         STREAM     CONNECTED     19459    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19458    
unix  3      [ ]         STREAM     CONNECTED     19393    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19392    
unix  3      [ ]         STREAM     CONNECTED     19391    /tmp/orbit-bill/linc-16e9-0-6012839cd565f
unix  3      [ ]         STREAM     CONNECTED     19390    
unix  3      [ ]         STREAM     CONNECTED     19389    /tmp/orbit-bill/linc-16b6-0-232038e88835
unix  3      [ ]         STREAM     CONNECTED     19388    
unix  3      [ ]         STREAM     CONNECTED     19387    /tmp/orbit-bill/linc-16e9-0-6012839cd565f
unix  3      [ ]         STREAM     CONNECTED     19386    
unix  3      [ ]         STREAM     CONNECTED     19383    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19382    
unix  3      [ ]         STREAM     CONNECTED     19381    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19380    
unix  3      [ ]         STREAM     CONNECTED     19376    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19375    
unix  3      [ ]         STREAM     CONNECTED     19369    /tmp/orbit-bill/linc-16ed-0-6012839ca88bf
unix  3      [ ]         STREAM     CONNECTED     19368    
unix  3      [ ]         STREAM     CONNECTED     19367    /tmp/orbit-bill/linc-16b6-0-232038e88835
unix  3      [ ]         STREAM     CONNECTED     19366    
unix  3      [ ]         STREAM     CONNECTED     19365    /tmp/orbit-bill/linc-16ed-0-6012839ca88bf
unix  3      [ ]         STREAM     CONNECTED     19364    
unix  3      [ ]         STREAM     CONNECTED     19361    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19360    
unix  3      [ ]         STREAM     CONNECTED     19359    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19358    
unix  3      [ ]         STREAM     CONNECTED     19354    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19353    
unix  3      [ ]         STREAM     CONNECTED     19275    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19274    
unix  3      [ ]         STREAM     CONNECTED     19272    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19271    
unix  3      [ ]         STREAM     CONNECTED     19266    @/dbus-vfs-daemon/socket-pJQGDns9
unix  3      [ ]         STREAM     CONNECTED     19265    
unix  3      [ ]         STREAM     CONNECTED     19264    @/dbus-vfs-daemon/socket-DXDhspD5
unix  3      [ ]         STREAM     CONNECTED     19263    
unix  3      [ ]         STREAM     CONNECTED     19258    @/dbus-vfs-daemon/socket-3eMeW494
unix  3      [ ]         STREAM     CONNECTED     19257    
unix  3      [ ]         STREAM     CONNECTED     19256    @/dbus-vfs-daemon/socket-4M4W6jIQ
unix  3      [ ]         STREAM     CONNECTED     19255    
unix  3      [ ]         STREAM     CONNECTED     19249    @/dbus-vfs-daemon/socket-8OkcIR4G
unix  3      [ ]         STREAM     CONNECTED     19248    
unix  3      [ ]         STREAM     CONNECTED     19250    @/dbus-vfs-daemon/socket-dgNI42XK
unix  3      [ ]         STREAM     CONNECTED     19247    
unix  3      [ ]         STREAM     CONNECTED     19240    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19239    
unix  3      [ ]         STREAM     CONNECTED     19218    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19217    
unix  3      [ ]         STREAM     CONNECTED     19215    /tmp/orbit-bill/linc-16af-0-573c3a9bb67df
unix  3      [ ]         STREAM     CONNECTED     19214    
unix  3      [ ]         STREAM     CONNECTED     19212    /tmp/orbit-bill/linc-16dc-0-727b80148b9ac
unix  3      [ ]         STREAM     CONNECTED     19211    
unix  3      [ ]         STREAM     CONNECTED     19213    @/dbus-vfs-daemon/socket-GUA7LeVm
unix  3      [ ]         STREAM     CONNECTED     19209    
unix  3      [ ]         STREAM     CONNECTED     19210    @/dbus-vfs-daemon/socket-I8gkVhbD
unix  3      [ ]         STREAM     CONNECTED     19208    
unix  3      [ ]         STREAM     CONNECTED     19202    @/dbus-vfs-daemon/socket-JFiBOTYB
unix  3      [ ]         STREAM     CONNECTED     19201    
unix  3      [ ]         STREAM     CONNECTED     19203    @/dbus-vfs-daemon/socket-wIjrvjLq
unix  3      [ ]         STREAM     CONNECTED     19200    
unix  3      [ ]         STREAM     CONNECTED     19195    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19194    
unix  3      [ ]         STREAM     CONNECTED     19189    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19188    
unix  3      [ ]         STREAM     CONNECTED     19167    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19166    
unix  3      [ ]         STREAM     CONNECTED     19165    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19164    
unix  3      [ ]         STREAM     CONNECTED     19163    /tmp/orbit-bill/linc-16dc-0-727b80148b9ac
unix  3      [ ]         STREAM     CONNECTED     19162    
unix  3      [ ]         STREAM     CONNECTED     19161    /tmp/orbit-bill/linc-16b6-0-232038e88835
unix  3      [ ]         STREAM     CONNECTED     19160    
unix  3      [ ]         STREAM     CONNECTED     19159    /tmp/orbit-bill/linc-16dc-0-727b80148b9ac
unix  3      [ ]         STREAM     CONNECTED     19158    
unix  3      [ ]         STREAM     CONNECTED     19155    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19154    
unix  3      [ ]         STREAM     CONNECTED     19153    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19152    
unix  3      [ ]         STREAM     CONNECTED     19148    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19147    
unix  3      [ ]         STREAM     CONNECTED     19111    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19110    
unix  3      [ ]         STREAM     CONNECTED     19108    /tmp/orbit-bill/linc-1690-0-349b8e0a7ae91
unix  3      [ ]         STREAM     CONNECTED     19107    
unix  3      [ ]         STREAM     CONNECTED     19104    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19103    
unix  3      [ ]         STREAM     CONNECTED     19099    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19098    
unix  3      [ ]         STREAM     CONNECTED     19096    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19095    
unix  3      [ ]         STREAM     CONNECTED     19094    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19093    
unix  3      [ ]         STREAM     CONNECTED     19092    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19091    
unix  3      [ ]         STREAM     CONNECTED     19090    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19089    
unix  3      [ ]         STREAM     CONNECTED     19081    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19080    
unix  3      [ ]         STREAM     CONNECTED     19077    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19076    
unix  3      [ ]         STREAM     CONNECTED     19075    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19074    
unix  3      [ ]         STREAM     CONNECTED     19066    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19065    
unix  3      [ ]         STREAM     CONNECTED     19061    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19060    
unix  3      [ ]         STREAM     CONNECTED     19058    /tmp/orbit-bill/linc-16b0-0-5fbaecb28bc0
unix  3      [ ]         STREAM     CONNECTED     19057    
unix  3      [ ]         STREAM     CONNECTED     19056    /tmp/orbit-bill/linc-16af-0-573c3a9bb67df
unix  3      [ ]         STREAM     CONNECTED     19055    
unix  3      [ ]         STREAM     CONNECTED     19054    /tmp/orbit-bill/linc-16b6-0-232038e88835
unix  3      [ ]         STREAM     CONNECTED     19052    
unix  3      [ ]         STREAM     CONNECTED     19053    /tmp/orbit-bill/linc-16b6-0-232038e88835
unix  3      [ ]         STREAM     CONNECTED     19051    
unix  3      [ ]         STREAM     CONNECTED     19049    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19048    
unix  3      [ ]         STREAM     CONNECTED     19012    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19011    
unix  3      [ ]         STREAM     CONNECTED     19010    /tmp/orbit-bill/linc-16c8-0-68ab7bfe4065e
unix  3      [ ]         STREAM     CONNECTED     19009    
unix  3      [ ]         STREAM     CONNECTED     19006    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     19005    
unix  3      [ ]         STREAM     CONNECTED     19001    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     19000    
unix  3      [ ]         STREAM     CONNECTED     18999    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18998    
unix  3      [ ]         STREAM     CONNECTED     18921    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18920    
unix  3      [ ]         STREAM     CONNECTED     18854    /tmp/orbit-bill/linc-16b0-0-5fbaecb28bc0
unix  3      [ ]         STREAM     CONNECTED     18853    
unix  3      [ ]         STREAM     CONNECTED     18848    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     18847    
unix  3      [ ]         STREAM     CONNECTED     18846    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18845    
unix  3      [ ]         STREAM     CONNECTED     18844    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     18843    
unix  3      [ ]         STREAM     CONNECTED     18839    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18838    
unix  3      [ ]         STREAM     CONNECTED     18835    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18834    
unix  3      [ ]         STREAM     CONNECTED     18832    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18831    
unix  3      [ ]         STREAM     CONNECTED     18776    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18775    
unix  3      [ ]         STREAM     CONNECTED     18771    /tmp/orbit-bill/linc-16af-0-573c3a9bb67df
unix  3      [ ]         STREAM     CONNECTED     18770    
unix  3      [ ]         STREAM     CONNECTED     18767    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     18766    
unix  3      [ ]         STREAM     CONNECTED     18765    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18764    
unix  3      [ ]         STREAM     CONNECTED     18681    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     18680    
unix  3      [ ]         STREAM     CONNECTED     18676    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18675    
unix  3      [ ]         STREAM     CONNECTED     18642    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     18641    
unix  3      [ ]         STREAM     CONNECTED     18639    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18638    
unix  3      [ ]         STREAM     CONNECTED     18631    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18630    
unix  3      [ ]         STREAM     CONNECTED     18605    /tmp/orbit-bill/linc-1698-0-75033a4cc9712
unix  3      [ ]         STREAM     CONNECTED     18604    
unix  3      [ ]         STREAM     CONNECTED     18601    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     18600    
unix  3      [ ]         STREAM     CONNECTED     18596    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18595    
unix  3      [ ]         STREAM     CONNECTED     18594    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18593    
unix  3      [ ]         STREAM     CONNECTED     18520    /tmp/orbit-bill/linc-1696-0-4b9150fdf315e
unix  3      [ ]         STREAM     CONNECTED     18519    
unix  3      [ ]         STREAM     CONNECTED     18516    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     18515    
unix  3      [ ]         STREAM     CONNECTED     18485    /tmp/.ICE-unix/5703
unix  3      [ ]         STREAM     CONNECTED     18484    
unix  3      [ ]         STREAM     CONNECTED     18480    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18479    
unix  3      [ ]         STREAM     CONNECTED     18472    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18471    
unix  3      [ ]         STREAM     CONNECTED     18470    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18469    
unix  2      [ ]         DGRAM                    18378    
unix  3      [ ]         STREAM     CONNECTED     18377    /tmp/orbit-bill/linc-1647-0-135a5e01ecd94
unix  3      [ ]         STREAM     CONNECTED     18376    
unix  3      [ ]         STREAM     CONNECTED     18373    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     18372    
unix  3      [ ]         STREAM     CONNECTED     18336    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18335    
unix  3      [ ]         STREAM     CONNECTED     18333    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18332    
unix  3      [ ]         STREAM     CONNECTED     18308    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18307    
unix  3      [ ]         STREAM     CONNECTED     18300    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18299    
unix  3      [ ]         STREAM     CONNECTED     18298    /tmp/orbit-bill/linc-1688-0-7dd80217ee8c8
unix  3      [ ]         STREAM     CONNECTED     18297    
unix  3      [ ]         STREAM     CONNECTED     18294    /tmp/orbit-bill/linc-168a-0-423b27f9c696a
unix  3      [ ]         STREAM     CONNECTED     18293    
unix  3      [ ]         STREAM     CONNECTED     18287    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18286    
unix  3      [ ]         STREAM     CONNECTED     18054    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18053    
unix  3      [ ]         STREAM     CONNECTED     18040    @/tmp/dbus-KQQpam2giR
unix  3      [ ]         STREAM     CONNECTED     18039    
unix  3      [ ]         STREAM     CONNECTED     17996    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17995    
unix  3      [ ]         STREAM     CONNECTED     17971    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17970    
unix  3      [ ]         STREAM     CONNECTED     17966    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17965    
unix  3      [ ]         STREAM     CONNECTED     17964    
unix  3      [ ]         STREAM     CONNECTED     17963    
unix  4      [ ]         STREAM     CONNECTED     17950    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17949    
unix  3      [ ]         STREAM     CONNECTED     17766    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17765    
unix  3      [ ]         STREAM     CONNECTED     17730    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17729    
unix  4      [ ]         STREAM     CONNECTED     17541    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17538    
unix  3      [ ]         STREAM     CONNECTED     17537    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17536    
unix  2      [ ]         DGRAM                    17340    
unix  3      [ ]         STREAM     CONNECTED     17316    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17315    
unix  3      [ ]         STREAM     CONNECTED     17276    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     17275    
unix  3      [ ]         STREAM     CONNECTED     17196    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17195    
unix  2      [ ]         DGRAM                    17194    
unix  3      [ ]         STREAM     CONNECTED     17190    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17189    
unix  3      [ ]         STREAM     CONNECTED     17091    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17090    
unix  2      [ ]         DGRAM                    17085    
unix  3      [ ]         STREAM     CONNECTED     16990    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16989    
unix  2      [ ]         DGRAM                    16983    
unix  3      [ ]         STREAM     CONNECTED     16689    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16686    
unix  3      [ ]         STREAM     CONNECTED     16685    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16684    
unix  3      [ ]         STREAM     CONNECTED     16662    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16661    
unix  3      [ ]         STREAM     CONNECTED     16658    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16657    
unix  3      [ ]         STREAM     CONNECTED     16624    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16623    
unix  3      [ ]         STREAM     CONNECTED     16620    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16619    
unix  3      [ ]         STREAM     CONNECTED     16585    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16584    
unix  3      [ ]         STREAM     CONNECTED     16581    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16580    
unix  3      [ ]         STREAM     CONNECTED     16547    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16546    
unix  3      [ ]         STREAM     CONNECTED     16543    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16542    
unix  3      [ ]         STREAM     CONNECTED     16509    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16508    
unix  3      [ ]         STREAM     CONNECTED     16506    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16505    
unix  3      [ ]         STREAM     CONNECTED     16448    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16447    
unix  2      [ ]         DGRAM                    16446    
unix  3      [ ]         STREAM     CONNECTED     16445    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     16444    
unix  3      [ ]         STREAM     CONNECTED     16428    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16427    
unix  3      [ ]         STREAM     CONNECTED     16425    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16424    
unix  3      [ ]         STREAM     CONNECTED     16323    @/var/run/hald/dbus-HdSeGsLQwx
unix  3      [ ]         STREAM     CONNECTED     16308    
unix  3      [ ]         STREAM     CONNECTED     16209    @/var/run/hald/dbus-OkCgGam5bs
unix  3      [ ]         STREAM     CONNECTED     16208    
unix  3      [ ]         STREAM     CONNECTED     16190    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16189    
unix  3      [ ]         STREAM     CONNECTED     16178    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16177    
unix  3      [ ]         STREAM     CONNECTED     15979    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15978    
unix  3      [ ]         STREAM     CONNECTED     15973    
unix  3      [ ]         STREAM     CONNECTED     15972    
unix  2      [ ]         DGRAM                    15970    
unix  3      [ ]         STREAM     CONNECTED     15931    
unix  3      [ ]         STREAM     CONNECTED     15930    
unix  2      [ ]         DGRAM                    15886    
^C
bill@J325P81:~$ cat /etc/hosts
127.0.0.1	localhost
192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@J325P81:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 205.167.142.101
nameserver 205.167.142.82
bill@J325P81:~$ 

```

---

### Post by seubill on 2009-01-03
This is getting too weird. How can two different machines both have the same IP address at the same time?

```
bill@FLRC2C1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:ea:09:87  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:feea:987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1519193 (1.4 MB)  TX bytes:196101 (191.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70600 (68.9 KB)  TX bytes:70600 (68.9 KB)

bill@FLRC2C1:~$ 

```



```
bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37896 (37.8 KB)  TX bytes:3009 (3.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2844 (2.8 KB)  TX bytes:2844 (2.8 KB)


```

---

### Post by seubill on 2009-01-03
Having difficulty trying to connect with ethernet. Machine defaults to ndiswrapper wireless connection, then I uncheck "enable wireless", and then looked into the wired connection network manager box, and it`s set for auto connect. Maybe an interface not up?  Also, I unplugged the ethernet cable from the router to the other machine, but made no difference.

---

### Post by pytheas22 on 2009-01-03
> Having difficulty trying to connect with ethernet. Machine defaults to ndiswrapper wireless connection, then I uncheck "enable wireless", and then looked into the wired connection network manager box, and it`s set for auto connect. Maybe an interface not up? Also, I unplugged the ethernet cable from the router to the other machine, but made no difference.

In order to connect with ethernet, it should be sufficient to run these commands:
```

sudo dhclient -r wlan0
sudo ifconfig wlan0 down
sudo dhclient eth0
```

Network Manager should also default to a wired connection whenever available, but with all the hacking that we've done to your machine, maybe NM isn't doing what it's supposed to.

It's also definitely very interesting--and problematic--that two different computers on your network are receiving the same IP address from your router.  Do you have specific IPs assigned anywhere in your router configuration?  Usually these would be specified according to MAC address or hostname (on the problem machine, the MAC is 00:13:72:ea:09:87 and the hostname is FLRC2C1).

Your /etc/hosts file also looks a little strange.  Could you please open it up by typing:
```

sudo gedit /etc/hosts
```

and comment out the second line (by prefixing a # to it) so that the file looks like this:
```

127.0.0.1	localhost
**###192.168.1.3	J325P81.MSHOME	J325P81**

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Then save the file, reboot and see if the connectivity issues still occur.

It would also be helpful if you could boot to Windows on the problem machine, open a terminal (by typing 'cmd' in the 'Run' dialog box, which you can open by pressing [Windows key+R] I think), run this command and post the output:
```

ipconfig /all
```

Finally, you say that things worked fine on an Ubuntu 8.04 live CD.  Were you connected wirelessly then?

---

### Post by seubill on 2009-01-03
Haven`t run any of the commands yet from your last post, but looking in the router, the ARP info is messed up. It is showing the same MAC address (00:12:3F:77:A3:89) for two different IP addresses; 192.168.1.5 and 192.168.1.3.  That MAC address is for the ethernet hardware on the J325P81 machine (the wireless problem child).

In the DHCP leases page of the router, the MAC addresses and IP addresses look to be correct.


And, when is was running the 8.04 Live CD earlier, that was on wireless.

---

### Post by seubill on 2009-01-03
Ran the commands to get eternet up, commented out that second line, saved, re-booted to Ubuntu, defaulted straight to wireless again, unchecked "enable wireless", still no ethernet.

Rebooted to Windows to run ipconfig /all, but now have no mouse function and can not click onto my user account to get to the command box.

I`ll try cold rebooting a time or two...



By the way, a couple of weeks back I had connected the problem child wireless machine (J325P81) up to the eternet cable for the other machine in order to download Ubuntu updates, hoping there was something in there that would help with the wireless issue, as this was just shortly after installing 8.10. Perhaps that may be the reason for the messed up ARP table in the router?

---

### Post by seubill on 2009-01-03
Ok, finally made it to XP.

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

I:\Documents and Settings\Bill>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : j325p81
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : D-Link WDA-1320 Desktop Adapter
        Physical Address. . . . . . . . . : 00-15-E9-FB-4F-83
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 205.167.142.101
                                            205.167.142.82
        Lease Obtained. . . . . . . . . . : sábado, 3 de janeiro de 2009 13:29:0
1
        Lease Expires . . . . . . . . . . : domingo, 4 de janeiro de 2009 13:29:
01

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Cont
roller
        Physical Address. . . . . . . . . : 00-12-3F-77-A3-89
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 205.167.142.101
                                            205.167.142.82
        Lease Obtained. . . . . . . . . . : sábado, 3 de janeiro de 2009 13:28:5
0
        Lease Expires . . . . . . . . . . : domingo, 4 de janeiro de 2009 13:28:
50

I:\Documents and Settings\Bill>




```

---

### Post by pytheas22 on 2009-01-03
Try running these commands to get Ubuntu connected via ethernet:
```

sudo killall NetworkManager
sudo ifconfig wlan0 down
sudo ifconfig ath0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

This should work; if it doesn't, please post the output.  It would be really good to know what happens when you're connected via ethernet.

I'm also wondering if changing the hostname of your machine might make a difference.  Try typing:
```

sudo hostname generic-hostname
```

Then reboot and try connecting again via wireless.  Still the same problems?

Also, if you boot to an Ubuntu 8.10 live CD, do things work?  Or is it only under 8.04 that they work?

---

### Post by seubill on 2009-01-03
```
bill@J325P81:~$ sudo killall NetworkManager
sudo: unable to resolve host J325P81
[sudo] password for bill: 
bill@J325P81:~$ sudo ifconfig wlan0 down
sudo: unable to resolve host J325P81
bill@J325P81:~$ sudo ifconfig ath0 down
sudo: unable to resolve host J325P81
ath0: ERROR while getting interface flags: No such device
bill@J325P81:~$ sudo ifconfig eth0 up
sudo: unable to resolve host J325P81
bill@J325P81:~$ sudo dhclient eth0
sudo: unable to resolve host J325P81
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:77:a3:89
Sending on   LPF/eth0/00:12:3f:77:a3:89
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.6 from 192.168.1.1
bound to 192.168.1.6 -- renewal in 35060 seconds.
bill@J325P81:~$ 

```

Will try changing the host name...

---

### Post by seubill on 2009-01-03
Tried to change the hostname, got "unable to resolve host J325P81"

no change on reboot, goes straight into wireless with ndiswrapper.

Next, slipped in 8.10 Live CD...

8.10 Live CD gives good connection wired and wireless.

---

### Post by seubill on 2009-01-03
Would this possibly have anything to do with not being able to resolve the host?

```
and comment out the second line (by prefixing a # to it) so that the file looks like this:
Code:

127.0.0.1	localhost
###192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by pytheas22 on 2009-01-03
Did you always get all those messages about being unable to resolve hostname, or did they only start today after you edited your /etc/hosts file?

I don't know why it thinks it needs to resolve your hostname in the first place.  What is the output now of:
```

cat /etc/hosts
```

---

### Post by seubill on 2009-01-03
```
and comment out the second line (by prefixing a # to it) so that the file looks like this:
Code:

127.0.0.1	localhost
###192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by seubill on 2009-01-03
Sorry for that last post, hit the wrong button.

```
bill@J325P81:~$ cat /etc/hosts
127.0.0.1	localhost
###192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@J325P81:~$ 

```

---

### Post by pytheas22 on 2009-01-03
If you reboot now can you change your hostname by typing:
```

sudo hostname generic-hostname
```

Since you say that the Ubuntu 8.10 live CD works fine, I think the problem must come down to some networking issues with your particular configuration, and I suspect that the hostname stuff has something to do with it.

One possible solution might be just to reinstall Ubuntu 8.10 from scratch, and choose a different hostname this time.  But we can also keep on trying to figure stuff out to fix your existing system if you like.

Also, from your output in post #90, it looks like you were able to get online on the wired interface using dhclient.  Since we know that works, could you please post the output of:

```
sudo dhclient eth0
lshw -C Network
iwconfig
ifconfig
ping -c 10 google.com
time wget google.com
time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
ping -c 10 192.168.1.1
ping -c 10 192.168.1.3
host 192.168.1.3
netsta -ra
cat /etc/hosts
cat /etc/resolv.conf
```

---

### Post by seubill on 2009-01-03
Pytheas22, Ok, will try rebooting and changing that host name. I tend to agree with your thinking, and would just almost bet that the problem lies either in the router and/or the wired XP/8.04.1 machine (FLRC2C1). The (xxx....) are actually Dell service tag numbers that help me identify my machines. That issue with the wired machine staying connected to the router after shutdown in Linux has me thinking that may be (at least)part of the problem. I really do not want to re-install Ubuntu as this wireless machine (J325P81) is also configured with RAID Level 1 mirroring and it was no trival task getting XP/Ubuntu and a NTFS file share partition all rigged up properly with RAID (with a big THANKS to caljohnsmith for his help on that). Even now, the RAID status has changed from NORMAL to VERIFY, I believe from so much rebooting. Would like to take some time and let the disks rebuild themselves, and then continue on with where we left off. Will post those command outputs you need, but I prefer to wait until the hard drives normalize themselves. Question- since the ndiswrapper driver obviously was not the solution, should we later get the proper native driver (ath5k) up and going?  Appreciate you!:D

---

### Post by seubill on 2009-01-04
Ran the command "sudo hostname generic-hostname" and here are the command outputs from your list;

Note: these commands were performed with the wired XP/8.04.1 (FLRC2C1) machine powered off, which had last been booted on XP, connectivity light at router OFF for said machine.


```
bill@J325P81:~$ sudo dhclient eth0
sudo: unable to resolve host J325P81
[sudo] password for bill: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:77:a3:89
Sending on   LPF/eth0/00:12:3f:77:a3:89
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.6 from 192.168.1.1
bound to 192.168.1.6 -- renewal in 39694 seconds.
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 ip=192.168.1.5 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:70:17:b8:ff:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Broadband1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:69:06:3F   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10857 (10.8 KB)  TX bytes:5066 (5.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2032 (2.0 KB)  TX bytes:2032 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10434 (10.4 KB)  TX bytes:3959 (3.9 KB)
          Interrupt:17 Memory:fbdf0000-fbe00000 

bill@J325P81:~$ ping -c 10 google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=4 ttl=242 time=122 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=5 ttl=242 time=121 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=6 ttl=242 time=126 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=7 ttl=242 time=119 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=8 ttl=242 time=121 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=9 ttl=242 time=120 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=10 ttl=242 time=118 ms

--- google.com ping statistics ---
10 packets transmitted, 7 received, 30% packet loss, time 9037ms
rtt min/avg/max/mdev = 118.914/121.601/126.848/2.499 ms
bill@J325P81:~$ time wget google.com
--2009-01-04 11:50:00--  http://google.com/
Resolving google.com... 209.85.171.100, 72.14.205.100, 74.125.45.100
Connecting to google.com|209.85.171.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2009-01-04 11:50:01--  http://www.google.com/
Resolving www.google.com... 72.14.205.103, 72.14.205.104, 72.14.205.147, ...
Connecting to www.google.com|72.14.205.103|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.2'

    [ <=>                                   ] 5,838       --.-K/s   in 0.1s    

2009-01-04 11:50:01 (42.1 KB/s) - `index.html.2' saved [5838]


real	0m0.886s
user	0m0.000s
sys	0m0.004s
bill@J325P81:~$ time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
--2009-01-04 11:51:10--  http://burnthesorbonne.com/files/OSSEC.pdf
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 184180 (180K) [application/pdf]
Saving to: `OSSEC.pdf'

100%[======================================>] 184,180     51.4K/s   in 3.5s    

2009-01-04 11:51:14 (51.4 KB/s) - `OSSEC.pdf' saved [184180/184180]


real	0m4.534s
user	0m0.008s
sys	0m0.000s
bill@J325P81:~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.60 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.661 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.613 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.607 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.606 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.593 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.743 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.634 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.928 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.681 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9003ms
rtt min/avg/max/mdev = 0.593/0.766/1.603/0.296 ms
bill@J325P81:~$ ping -c 10 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable
From 192.168.1.6 icmp_seq=5 Destination Host Unreachable
From 192.168.1.6 icmp_seq=6 Destination Host Unreachable
From 192.168.1.6 icmp_seq=7 Destination Host Unreachable
From 192.168.1.6 icmp_seq=8 Destination Host Unreachable
From 192.168.1.6 icmp_seq=9 Destination Host Unreachable
From 192.168.1.6 icmp_seq=10 Destination Host Unreachable

--- 192.168.1.3 ping statistics ---
10 packets transmitted, 0 received, +10 errors, 100% packet loss, time 9062ms
, pipe 3
bill@J325P81:~$ host 192.168.1.3
Host 3.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)
bill@J325P81:~$ netsta -ra
bash: netsta: command not found
bill@J325P81:~$ netstat -ra
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
localnet        *               255.255.255.0   U         0 0          0 eth0
localnet        *               255.255.255.0   U         0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
bill@J325P81:~$ cat /etc/hosts
127.0.0.1	localhost
###192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@J325P81:~$ cat /etc/resolv.conf
nameserver 205.167.142.101
nameserver 205.167.142.82
bill@J325P81:~$ 


```

---

### Post by seubill on 2009-01-04
For the purpose of comparison, these are the same command outputs as post #98, but performed with wired machine (FLRC2C1) powered ON, booted to Ubuntu, and connectivity light at router ON.


```
bill@J325P81:~$ sudo dhclient eth0
sudo: unable to resolve host J325P81
[sudo] password for bill: 
There is already a pid file /var/run/dhclient.pid with pid 6080
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:77:a3:89
Sending on   LPF/eth0/00:12:3f:77:a3:89
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.6 from 192.168.1.1
bound to 192.168.1.6 -- renewal in 41018 seconds.
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 ip=192.168.1.5 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:70:17:b8:ff:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Broadband1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:69:06:3F   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2466714 (2.4 MB)  TX bytes:258621 (258.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3152 (3.1 KB)  TX bytes:3152 (3.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40850 (40.8 KB)  TX bytes:5386 (5.3 KB)
          Interrupt:17 Memory:fbdf0000-fbe00000 

bill@J325P81:~$ ping -c 10 google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=1 ttl=242 time=118 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=2 ttl=242 time=121 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=3 ttl=242 time=121 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=4 ttl=242 time=119 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=5 ttl=242 time=117 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=6 ttl=242 time=121 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=7 ttl=242 time=120 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=8 ttl=242 time=120 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=9 ttl=242 time=125 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=10 ttl=242 time=122 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9036ms
rtt min/avg/max/mdev = 117.640/120.943/125.143/1.932 ms
bill@J325P81:~$ time wget google.com
--2009-01-04 12:14:28--  http://google.com/
Resolving google.com... 209.85.171.100, 72.14.205.100, 74.125.45.100
Connecting to google.com|209.85.171.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2009-01-04 12:14:28--  http://www.google.com/
Resolving www.google.com... 72.14.205.103, 72.14.205.104, 72.14.205.147, ...
Connecting to www.google.com|72.14.205.103|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.3'

    [ <=>                                   ] 5,838       --.-K/s   in 0.1s    

2009-01-04 12:14:28 (41.3 KB/s) - `index.html.3' saved [5838]


real	0m0.826s
user	0m0.000s
sys	0m0.000s
bill@J325P81:~$ time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
--2009-01-04 12:15:30--  http://burnthesorbonne.com/files/OSSEC.pdf
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 184180 (180K) [application/pdf]
Saving to: `OSSEC.pdf'

100%[======================================>] 184,180     51.3K/s   in 3.5s    

2009-01-04 12:15:34 (51.3 KB/s) - `OSSEC.pdf' saved [184180/184180]


real	0m3.854s
user	0m0.000s
sys	0m0.004s
bill@J325P81:~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.675 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.588 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.653 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.688 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.601 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.588 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.600 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.599 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.643 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.679 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8996ms
rtt min/avg/max/mdev = 0.588/0.631/0.688/0.044 ms
bill@J325P81:~$ ping -c 10 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.605 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.151 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.162 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=0.162 ms
64 bytes from 192.168.1.3: icmp_seq=5 ttl=64 time=0.162 ms
64 bytes from 192.168.1.3: icmp_seq=6 ttl=64 time=0.142 ms
64 bytes from 192.168.1.3: icmp_seq=7 ttl=64 time=0.159 ms
64 bytes from 192.168.1.3: icmp_seq=8 ttl=64 time=0.161 ms
64 bytes from 192.168.1.3: icmp_seq=9 ttl=64 time=0.161 ms
64 bytes from 192.168.1.3: icmp_seq=10 ttl=64 time=0.160 ms

--- 192.168.1.3 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9000ms
rtt min/avg/max/mdev = 0.142/0.202/0.605/0.135 ms
bill@J325P81:~$ host 192.168.1.3
Host 3.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)
bill@J325P81:~$ netstat -ra
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
localnet        *               255.255.255.0   U         0 0          0 eth0
localnet        *               255.255.255.0   U         0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
bill@J325P81:~$ cat /etc/hosts
127.0.0.1	localhost
###192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@J325P81:~$ cat /etc/resolv.conf
nameserver 205.167.142.101
nameserver 205.167.142.82
bill@J325P81:~$ 


```

---

### Post by seubill on 2009-01-04
Again, for the purpose of further comparison, now with wired machine (FLRC2C1) powered OFF, last booted to Ubuntu, connectivity light at router remains ON.


```
bill@J325P81:~$ sudo dhclient eth0
sudo: unable to resolve host J325P81
There is already a pid file /var/run/dhclient.pid with pid 6218
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:77:a3:89
Sending on   LPF/eth0/00:12:3f:77:a3:89
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.6 from 192.168.1.1
bound to 192.168.1.6 -- renewal in 35564 seconds.
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 ip=192.168.1.5 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:70:17:b8:ff:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Broadband1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:2B:69:06:3F   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bill@J325P81:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2923045 (2.9 MB)  TX bytes:308570 (308.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3152 (3.1 KB)  TX bytes:3152 (3.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49836 (49.8 KB)  TX bytes:5638 (5.6 KB)
          Interrupt:17 Memory:fbdf0000-fbe00000 

bill@J325P81:~$ ping -c 10 google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=237 time=131 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=237 time=135 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=237 time=132 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=237 time=131 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=237 time=131 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=6 ttl=237 time=131 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=7 ttl=237 time=138 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=8 ttl=237 time=133 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=9 ttl=237 time=135 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=10 ttl=237 time=133 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9034ms
rtt min/avg/max/mdev = 131.135/133.473/138.771/2.350 ms
bill@J325P81:~$ time wget google.com
--2009-01-04 12:25:28--  http://google.com/
Resolving google.com... 74.125.45.100, 209.85.171.100, 72.14.205.100
Connecting to google.com|74.125.45.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2009-01-04 12:25:28--  http://www.google.com/
Resolving www.google.com... 72.14.205.99, 72.14.205.103, 72.14.205.104, ...
Connecting to www.google.com|72.14.205.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.4'

    [ <=>                                   ] 5,838       --.-K/s   in 0.1s    

2009-01-04 12:25:29 (41.8 KB/s) - `index.html.4' saved [5838]


real	0m0.855s
user	0m0.000s
sys	0m0.004s
bill@J325P81:~$ time wget burnthesorbonne.com/files/OSSEC.pdf; rm OSSEC.pdf
--2009-01-04 12:26:29--  http://burnthesorbonne.com/files/OSSEC.pdf
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 184180 (180K) [application/pdf]
Saving to: `OSSEC.pdf'

100%[======================================>] 184,180     51.6K/s   in 3.5s    

2009-01-04 12:26:32 (51.6 KB/s) - `OSSEC.pdf' saved [184180/184180]


real	0m3.809s
user	0m0.000s
sys	0m0.012s
bill@J325P81:~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.815 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.781 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.645 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.603 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.598 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.587 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.602 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.670 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.676 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.678 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8999ms
rtt min/avg/max/mdev = 0.587/0.665/0.815/0.078 ms
bill@J325P81:~$ ping -c 10 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable
From 192.168.1.6 icmp_seq=5 Destination Host Unreachable
From 192.168.1.6 icmp_seq=6 Destination Host Unreachable
From 192.168.1.6 icmp_seq=8 Destination Host Unreachable
From 192.168.1.6 icmp_seq=9 Destination Host Unreachable
From 192.168.1.6 icmp_seq=10 Destination Host Unreachable

--- 192.168.1.3 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9038ms
, pipe 3
bill@J325P81:~$ host 192.168.1.3
Host 3.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)
bill@J325P81:~$ netstat -ra
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
localnet        *               255.255.255.0   U         0 0          0 eth0
localnet        *               255.255.255.0   U         0 0          0 wlan0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
bill@J325P81:~$ cat /etc/hosts
127.0.0.1	localhost
###192.168.1.3	J325P81.MSHOME	J325P81

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@J325P81:~$ cat /etc/resolv.conf
nameserver 205.167.142.101
nameserver 205.167.142.82
bill@J325P81:~$ 


```

Hope this helps :D

---

### Post by pytheas22 on 2009-01-04
Sorry for not responding all day.

It looks like your connectivity with the ethernet plugged in was good, regardless of whether or not the other Ubuntu machine was on.  Are you able to browse web pages via ethernet with no problem?

If so, that's good, but also sort of bad because it means that your networking problem is wireless-specific, and I'm still a bit puzzled as to where exactly the problem might lie, since it occurs under both ndiswrapper and the ath5k driver.

And your wireless connectivity is still bad even if the machine is right next to the router (and the ethernet is UNplugged)?

---

### Post by seubill on 2009-01-05
Not a problem about not being able to respond all day, I wanted to give the hard drives time to get back to NORMAL status anyway.  

Internet web pages browsing is very good with the ethernet connection ( I have to do the "sudo dhclient eth0" thing every time).

With the ethernet cable UNPLUGGED, web browsing is nearly impossible even though the machine is physically next to the router. Strength bars at the top edge of the desktop for the wireless connection show full strength, mouse pointer hover of that shows 89%, and the active network connections box indicates the ndiswrapper driver active.

Hey THANKS for hanging in here with me this long!:D

Will be gone tomorrow (Mon.) from around 2pm till about midnight or so (CST).

---

### Post by kevdog on 2009-01-05
Have you reset your router just for the heck of it? (Hard reset)?

---

### Post by seubill on 2009-01-05
Kevdog, yes twice. Nothing changed, and on the same machine XP runs like a champ wireless.

---

### Post by kevdog on 2009-01-05
You have a dual boot correct -- not a wubi or vm install correct?

And just for reference
You have tried both ndiswrapper and the ath5k driver?
AR2413 chipset I believe is equivalent to the AR5005G chipset(?)  Although I find it puzzling that the ath5k website states it only supports these chipsets:
AR5210 - 802.11a
AR5211 - 802.11ab
AR5212 - 802.11abg
AR5213 - 802.11abg
AR5414 - 80211abg

Have you used a third solution which would be a patched madwifi driver such as the instructions listed here:
[http://madwifi-project.org/wiki/Compatibility/Atheros/AR5005G](http://madwifi-project.org/wiki/Compatibility/Atheros/AR5005G)

Is this an Acer machine?  and if so do you have a ath_wmi module?
modinfo ath_wmi

What is your kernel version?
uname -r

---

### Post by seubill on 2009-01-05
Kevdog, yes sir, this is a true dual-boot installation, NOT a Wubi and NOT a virtual machine. Ubuntu 8.10 was installed with the Alternate CD because that included the dmraid module. Partitioning was done manually.

I was also a little puzzled about the ath5k driver listing not showing this chipset. Have tried out the ath5k, ath_pci, and ndiswrapper drivers, and none really seem to get it done right.

No, this is not an Acer machine. It is a Dell Precision 380 desktop. Just for whatever it's worth, I have a Dell Precision M65 laptop that runs from the same router (wireless of course) with no problem, (Ububtu 8.04/XP dual-boot).

The kernel for the 8.10 wireless desktop problem machine is  version 2.6.27-9 generic kernel.

My understanding is that the AR2413 chipset and the AR5005G are supposed to run the ath5k driver, but arguably, the D-link website leaves a good bit to be desired.

Thanks!

---

### Post by kevdog on 2009-01-05
Lets investigate the ath_pci

Given its a 5005G, I think a specific patched madwifi source needs to be compiled and installed.  Did you install the specific source as referenced above, or just use a generic madwifi install, or just use the built in drivers?

And yes from everything Ive read the ath5k should support the 5005G chipset, however it is very strange this particular chipset revision isn't listed on the main linux wireless website.  Either this is a rumor or the docs haven't been updated in quite a while.  I hate potential misinformation.

---

### Post by seubill on 2009-01-05
I really can't say with absolute certainty, but I'm thinking the ath_pci driver used come from the built in set.

---

### Post by kevdog on 2009-01-05
If you know how to compile from source I would say lets try the patched madwifi driver as given here:
[http://madwifi-project.org/wiki/Compatibility/Atheros/AR5005G](http://madwifi-project.org/wiki/Compatibility/Atheros/AR5005G)
Forget the parts that are Acer specific -- you don't need these.

Its really the last option I can think of.

---

### Post by seubill on 2009-01-05
Some of the commands there have me a little confused. If you would not mind, could you post a list of specific commands for me to follow?

Guess I will probably have to hook up to the net with the 'sudo dhclient eth0' deal.

I really appreciate your willingness to help me out here, but unfortunately I have to leave out of here for the rest of the day, shortly.  Will check back in either late tonight or tomorrow morning. Sure hope this does it!:D

Thanks!

---

### Post by kevdog on 2009-01-06
To compile from subversion you need first to install some utilities

sudo apt-get install build-essential linux-headers-$(uname -r) perl subversion 

build-essential -- contains the compiler and other libraries
linux-headers-$(uname -r) -- Contains the header files for your specific kernel version
perl -- Not sure if you need to install perl but it won't hurt
subversion -- Utility to download source files from a subversion repository (live cvs, bazaar, git -- if you know what those are)

cd ~
mkdir -p madwifi
cd madwifi

Grab the source files from subversion repository
```
svn checkout [http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6](http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6) madwifi-hal-0.10.5.6
```

cd madwifi-hal-0.10.5.6

Now I'm assuming you are not currently running the madwifi ath_pci or ath_hal modules.  You can check if you are with:
lsmod | grep ath

If you are not proceed to the next step.  If you are:
sudo ifconfig ath0 down
sudo rmmod ath_pci ath_hal

Compile and then install the modules
make
sudo make install

Then load the module into the kernel
sudo modprobe ath_hal ath_pci   (I think ath_hal will get loaded automatically with ath_pci)

Should should then check lsmod to make sure the module has loaded:
lsmod | grep ath

If the ath modules are not showing, make sure you check dmesg for errors to give you some clues potentially why the module didn't load

If if did load, then I think when you do a 
ifconfig

You should see a wifi0 and potentially a ath0 interface listed.  I would double check particularly for a ath0 interface.

If ath0 is shown then configure with whatever you use to make a network connection (ie command line, network manager, wicd, etc).

---

### Post by seubill on 2009-01-06
Kevdog, slipped in the 8.10 Live CD to get wireless internet connection to do this, as I had to move the machine.

Anyway- before I go any farther- is this syntax messed up here, or do I continue on. Also, lsmod | grep ath showed ath5k.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$2.6.27-9-generic perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-.6.27-9-generic
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$2.6.27-9 perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-.6.27-9
ubuntu@ubuntu:~$ sudo apt-get install build-esstial linux-headers-$(uname-r) perl subversion
bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-esstial
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$(uname-r) perl subversion
bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
perl is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc subversion-tools db4.6-util
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
  subversion
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 3555kB/9757kB of archives.
After this operation, 33.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 



```

---

### Post by seubill on 2009-01-06
Figured out that I skipped the spacebar one place in the syntax. Got this far and am a bit puzzled. Why no file

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$2.6.27-9-generic perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-.6.27-9-generic
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$2.6.27-9 perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-.6.27-9
ubuntu@ubuntu:~$ sudo apt-get install build-esstial linux-headers-$(uname-r) perl subversion
bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-esstial
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$(uname-r) perl subversion
bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
perl is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc subversion-tools db4.6-util
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
  subversion
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 3555kB/9757kB of archives.
After this operation, 33.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$(uname -r) perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
linux-headers-2.6.27-7-generic set to manually installed.
perl is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc subversion-tools db4.6-util
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libapr1 libaprutil1 libmysqlclient15off
  libneon27-gnutls libpq5 libstdc++6-4.3-dev libsvn1 mysql-common patch
  subversion
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 3555kB/9757kB of archives.
After this operation, 33.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/main libapr1 1.2.12-4 [109kB]
Get:2 http://archive.ubuntu.com intrepid/main mysql-common 5.0.67-0ubuntu6 [60.7kB]
Get:3 http://archive.ubuntu.com intrepid/main libmysqlclient15off 5.0.67-0ubuntu6 [1841kB]
Get:4 http://archive.ubuntu.com intrepid/main libpq5 8.3.4-2.2 [281kB]         
Get:5 http://archive.ubuntu.com intrepid/main libaprutil1 1.2.12+dfsg-7 [75.7kB]
Get:6 http://archive.ubuntu.com intrepid/main libneon27-gnutls 0.28.2-2build1 [114kB]
Get:7 http://archive.ubuntu.com intrepid/main libsvn1 1.5.1dfsg1-1ubuntu2 [734kB]
Get:8 http://archive.ubuntu.com intrepid/main subversion 1.5.1dfsg1-1ubuntu2 [340kB]
Fetched 3555kB in 1min6s (53.3kB/s)                                            
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 102335 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.2.12-4_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.4-2.2_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-7_i386.deb) ...
Selecting previously deselected package libneon27-gnutls.
Unpacking libneon27-gnutls (from .../libneon27-gnutls_0.28.2-2build1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.5.1dfsg1-1ubuntu2_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.5.1dfsg1-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up libapr1 (1.2.12-4) ...

Setting up mysql-common (5.0.67-0ubuntu6) ...
Setting up libmysqlclient15off (5.0.67-0ubuntu6) ...

Setting up libpq5 (8.3.4-2.2) ...

Setting up libaprutil1 (1.2.12+dfsg-7) ...

Setting up libneon27-gnutls (0.28.2-2build1) ...

Setting up libsvn1 (1.5.1dfsg1-1ubuntu2) ...

Setting up subversion (1.5.1dfsg1-1ubuntu2) ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ cd~
bash: cd~: command not found
ubuntu@ubuntu:~$ cd ~
ubuntu@ubuntu:~$ mkdir -p madwifi
ubuntu@ubuntu:~$ cd madwifi
ubuntu@ubuntu:~/madwifi$ svn checkout http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6 madwifi-hal-0.10.5.6
svn: URL 'http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6' doesn't exist
ubuntu@ubuntu:~/madwifi$ svn checkout http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6 madwifi-hal-0.10.5.6
svn: URL 'http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6' doesn't exist
ubuntu@ubuntu:~/madwifi$ cd madwifi-hal-0.10.5.6
bash: cd: madwifi-hal-0.10.5.6: No such file or directory
ubuntu@ubuntu:~/madwifi$ 


```

---

### Post by pytheas22 on 2009-01-06
Try typing this; it should get those packages installed and complete the first part of the steps as outlined by kevdog:
```

sudo apt-get install build-essential linux-headers-2.6.27-9-generic perl subversion
```

(Make sure there's no $ in the command because apparently apt-get doesn't know how to interpret that.)

You should not get errors this time.  When this completes, you can move on to the next step in kevdog's instructions, i.e.:
```

cd ~
mkdir -p madwifi
cd madwifi
```

---

### Post by kevdog on 2009-01-06
Pytheas has hit the nail on the head about for some strange reason apt-get interpreting the $ sign as a literal $ rather than for a variable substitution.

Another way to represent this would be:
linux-headers-`uname -r`

uname -r obviously lists your kernel version.  So its basically a statement to install the linux-headers for your kernel version. 

As pytheas as pointed out:
linux-headers-`uname -r` = linux-headers-2.6.27-9-generic

Here is another link in case you get stuck:
[http://ubuntuforums.org/showpost.php?p=6505471&postcount=5](http://ubuntuforums.org/showpost.php?p=6505471&postcount=5)

---

### Post by seubill on 2009-01-07
Ok, somebody please tell me what I am not doing right:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-2.6.27-9-generic perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.27-9-generic
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-2.6.27-9-generic perl subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.27-9-generic
ubuntu@ubuntu:~$ cd ~
ubuntu@ubuntu:~$ mkdir -p madwifi
ubuntu@ubuntu:~$ cd madwifi
ubuntu@ubuntu:~/madwifi$ svn checkout http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6 madwifi-hal-0.10.5.6
The program 'svn' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found
ubuntu@ubuntu:~/madwifi$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapr1 libaprutil1 libmysqlclient15off libneon27-gnutls libpq5 libsvn1
  mysql-common
Suggested packages:
  subversion-tools db4.6-util patch
The following NEW packages will be installed:
  libapr1 libaprutil1 libmysqlclient15off libneon27-gnutls libpq5 libsvn1
  mysql-common subversion
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3555kB of archives.
After this operation, 11.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/main libapr1 1.2.12-4 [109kB]
Get:2 http://archive.ubuntu.com intrepid/main mysql-common 5.0.67-0ubuntu6 [60.7kB]
Get:3 http://archive.ubuntu.com intrepid/main libmysqlclient15off 5.0.67-0ubuntu6 [1841kB]
Get:4 http://archive.ubuntu.com intrepid/main libpq5 8.3.4-2.2 [281kB]         
Get:5 http://archive.ubuntu.com intrepid/main libaprutil1 1.2.12+dfsg-7 [75.7kB]
Get:6 http://archive.ubuntu.com intrepid/main libneon27-gnutls 0.28.2-2build1 [114kB]
Get:7 http://archive.ubuntu.com intrepid/main libsvn1 1.5.1dfsg1-1ubuntu2 [734kB]
Get:8 http://archive.ubuntu.com intrepid/main subversion 1.5.1dfsg1-1ubuntu2 [340kB]
Fetched 3555kB in 1min12s (49.3kB/s)                                           
Selecting previously deselected package libapr1.
(Reading database ... 102335 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.12-4_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.4-2.2_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-7_i386.deb) ...
Selecting previously deselected package libneon27-gnutls.
Unpacking libneon27-gnutls (from .../libneon27-gnutls_0.28.2-2build1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.5.1dfsg1-1ubuntu2_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.5.1dfsg1-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libapr1 (1.2.12-4) ...

Setting up mysql-common (5.0.67-0ubuntu6) ...
Setting up libmysqlclient15off (5.0.67-0ubuntu6) ...

Setting up libpq5 (8.3.4-2.2) ...

Setting up libaprutil1 (1.2.12+dfsg-7) ...

Setting up libneon27-gnutls (0.28.2-2build1) ...

Setting up libsvn1 (1.5.1dfsg1-1ubuntu2) ...

Setting up subversion (1.5.1dfsg1-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~/madwifi$ svn checkout http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6 madwifi-hal-0.10.5.6
svn: URL 'http://svn.madwifi-project.org/madwi...i-hal-0.10.5.6' doesn't exist
ubuntu@ubuntu:~/madwifi$ cd madwifi-hal-0.10.5.6
bash: cd: madwifi-hal-0.10.5.6: No such file or directory
ubuntu@ubuntu:~/madwifi$ 


```

Question, since I am doing all this with the Live CD, once I FINALLY get it done right, what do I need to do in order not to lose anything after rebooting (with the CD removed)?

Thanks!:D

---

### Post by seubill on 2009-01-07
Tried out the method in the link from Kevdog`s post 115. Here`s what happened:

```
ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82955X Memory Controller Hub
	Subsystem: Dell Device 01a8
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82955X PCI Express Root Port
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fc000000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fbe00000-fbefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 01a8
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Memory behind bridge: fbd00000-fbdfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01a8
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]
	Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Device 01a8
	Flags: medium devsel, IRQ 10
	I/O ports at ece0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation NV41 [Quadro FX 3450/4000 SDI] (rev a2)
	Subsystem: nVidia Corporation Device 029b
	Flags: fast devsel, IRQ 11
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

05:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10)
	Subsystem: Dell Device 8010
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fbdef000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

05:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: D-Link System Inc Device 3a1d
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci

ubuntu@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6203kB of archives.
After this operation, 21.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 102452 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...
ubuntu@ubuntu:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ cd ~
ubuntu@ubuntu:~$ mkdir madwifi
mkdir: cannot create directory `madwifi': File exists
ubuntu@ubuntu:~$ cd madwifi
ubuntu@ubuntu:~/madwifi$ svn co http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6
svn: URL 'http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6' doesn't exist
ubuntu@ubuntu:~/madwifi$ cd madwifi-hal-0.10.5.6
bash: cd: madwifi-hal-0.10.5.6: No such file or directory
ubuntu@ubuntu:~/madwifi$ 


```
:confused:

---

### Post by kevdog on 2009-01-07
Ok take a break for a minute 

You've got some errors here that are easily correctable

#1
```

sudo aptitude install linux-headers-`uname -r`

```

Just cut and paste that into the command line


#2
Your svn sources -- the formatting of the forums cut off the entire address and replaced them with .....
Here is what you want: (cut and paste the svn line)
```

cd ~/madwifi
svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6
cd madwifi-hal-0.10.5.6

Then proceed as above

```

Hopefully that helps.

PS If doing this with the live CD -- all changes will be lost upon reboot!  Sorry!!!

---

### Post by seubill on 2009-01-07
Thanks Kevdog, will do it!  Would it be better if I move the machine back again to where I can plug it up to ethernet cabling and then connect with dhclient eth0? (totally avoiding the live CD)

Will have to continue with this tomorrow as the demands of earning a living are calling now.

---

### Post by kevdog on 2009-01-07
Id recommend an ethernet connection if you have access.  You can see by the delay between my long posts, I am also busy earning a living also.

---

### Post by seubill on 2009-01-08
Got back onto 'dhclient eth0' and ran all the commands without too much trouble. A little confused regarding the order of operations, but anyway I believe everything is here. All the way at the bottom, under 'dmesg' it says 'unknown parameter ath_pci. So what else to I need to do, or correct? Have not rebooted or shutdown, and still have the terminal running. 

```
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.768337] uhci_hcd 0000:00:1d.3: UHC
[    6.904388] ata5.00: ATAPI: HL-DT-ST C
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.768373] uhci_hcd 0000:00:1d.3: new USB
[    6.904414] ata5.01: ATAPI: PHILIPS DVD+/-
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.768409] uhci_hcd 0000:00:1d.3: ir
[    6.940311] ata5.00: configured for U
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.768545] usb usb5: configuration #
[    6.956570] ata5.01: configured for U
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.768585] hub 5-0:1.0: USB hub fo
[    6.956626] ata6: port disabled. ig
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.768596] hub 5-0:1.0: 2 ports detected
[    6.957255] scsi 5:0:0:0: CD-ROM         bash: [: missing `]'

bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.872351] ahci 0000:00:1f.2: version 3.0
[    6.957463] scsi 5:0:0:0: Attached scsi ge
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.872367] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (leve
[    6.959504] scsi 5:0:1:0: CD-ROM            PHILIPS bash: syntax error near unexpected token `(' 
DVD
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.872471] ahci 0000:00:1f.2: AHCI 0001.0100 32 slo
[    6.959634] scsi 5:0:1:0: Attached scsi generic sg3 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.872476] ahci 0000:00:1f.2: flags: 64bi
bash: [: missing `]'
[    7.027914] Driver 'sr' needs updating - p
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.872482] ahci 0000:00:1f.2: setting l
bash: [: missing `]'
[    7.031592] sr0: scsi3-mmc drive: 48x/48
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.873104] scsi1 : ahci
bash: [: missing `]'
[    7.031597] Uniform CD-R
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.873566] scsi2 : ahci
bash: [: missing `]'
[    7.031716] sr 5:0:0:0: 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.874010] scsi3 : ahci
bash: [: missing `]'
[    7.040102] sr1: scsi3-m
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.874481] scsi4 : ahci
bash: [: missing `]'
[    7.040204] sr 5:0:1:0: 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.874549] ata1: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd00
bash: [: missing `]'
[    7.949720] PM: Starting manual resume from disk
[    7.949725] PM: Resumbill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.8745533 abar m1024@0xfebfbA/13 
bash: [: missing `]'
e from partition 254:3
[    7.949728] PM: Checking hibernabill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [ 3 abar m102] ata3: SATA max UDMA/13 
bash: [: missing `]'
tion image.
[    7.949904] PM: Resume from disk fbill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ 3 abar m1024@0xfebfbc00 A max UDMA/13 
ailed.
[    7.953470] ieee1394: Host added: ID:BUS[0-00:1023] bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    4.884037] usb 4-1: new low speed USB device using uhci
 GUID[0000d100818c531f]
[    8.002785] kjournald starting.  bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.058686] usb 4-1: configuration #1 chosen from 1 c
Commit interval 5 seconds
[    8.002806] EXT3-fs: mountedbash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.172074] usb 4-2: new low speed USB de
 filesystem with ordered data mode.
[    9.69bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.192033] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
3593] usb-storage: device scan complete
[    9bash: syntax error near unexpected token `('.
698194] scsi 0:0:0:0: Dbill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.193376]13AS, 8.12, max UDMA/133
bash: [: missing `]'
irect-Access     TEAC     USB   HS-CF Card 4.00 PQ: 0 ANSI: 0
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.193381] ata1.00: 156250000 sectors, multi 0: LBA48 NCQ (depth 31/32
[    9.701563] scsi 0:0:0:1: Direct-Access     TEAC     USBbash: syntax error near unexpected token `(' 
  HS-xD/SM   4.
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.194966] ata1.00: configured for UDMA/133
[    9.705565] scsi 0:0:0:2: Direct-Access     
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.345678] usb 4-2: configuration #1 chosen from
bash: [: missing `]'
[    9.708815] scsi 0:0:0:3: Direct-Access     TEAC 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    5.528030] ata2: SATA link down (SStatus 0 SControl 300)
bash: syntax error near unexpected token `('
[    9.713781] sd 0:0:0:0: [sdc] Attached SCSI removable dis
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.268042] ata3: SATA link up 3.0 Gbps (SStatus 123 SCont
bash: syntax error near unexpected token `('
[    9.713926] sd 0:0:0:0: Attached scsi generic sg4 type 0
[bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.269087] ata3.00: ATA-7: ST38019AS, 8.04, 
bash: [: missing `]'
    9.718879] sd 0:0:0:1: [sdd] Attached SCSI remo
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.269091] ata3.00: 156250000 sectors, multi 0: LBA48 NCQ (depth 31
bash: syntax error near unexpected token `('
[    9.718952] sd 0:0:0:1: Attached scsi generic sg5 type 0
[    9.7237bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.270231] ata3.00: cor UDMAed fo 
bash: [: missing `]'
54] sd 0:0:0:2: [sde] Attached SCSI removabl
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.604038] ata4: SATA link down (SStatus 0 SControl 300)
bash: syntax error near unexpected token `('
[    9.723827] sd 0:0:0:2: Attached scsi generic sg6 type 0
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.620178] scsi 1:0:0:0: Direct-Access     ATA     
bash: [: missing `]'
[    9.773259] sd 0:0:0:3: [sdf] Attached SCSI removable
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.620335] scsi 1:0:0:0: Attached scsi 
bash: [: missing `]'
[    9.773332] sd 0:0:0:3: Attached scsi ge
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.620453] scsi 3:0:0:0: Direct-A[   14.206262] udevd version 124 star
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.620590] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[   15.120887] pci_hotplug: PCI Hot Plug PCI Core version: 0.
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.620646] ohci1394 0000:05:02.0: PCI INT A -> G
[   15.144262] shpchp: Standard Hot Plug PCI Control
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.672382] ohci1394: fw-host0: OHCI-1
[   15.247272] intel_rng: Firmware space 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.688772] pata_acpi 0000:00:1f.1: PCI I
[   15.247276] intel_rng: don't want to disa
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.688819] pata_acpi 0000:00:1f.1: se
[   15.247280] intel_rng: you are certain
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.688843] pata_acpi 0000:00:1f.1: PCI
[   15.247283] intel_rng: RNG, try using t
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.715750] ata_piix 0000:00:1f.1: version 2.12
bash: [: missing `]'
[   15.327283] iTCO_vendor_support: vendor-support
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.715765] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
bash: syntax error near unexpected token `('
[   15.337712] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[  bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.715824] ata_piix 0000:00:1f setting latency timer to 
bash: [: missing `]'
 15.337891] iTCO_wdt: failed to reset NO_REBOOT flag, reboot dis
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.719529] scsi5 : ata_piix
bash: [: missing `]'
[   15.337917] iTCO_wdt: No car
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.719693] scsi6 : ata_piix
bash: [: missing `]'
[   15.910811] input: Power But
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.719771] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
bash: [: missing `]'
[   15.936536] ACPI: Power Button (FF) [PWRF]
[   15.936668] input: Power Buttbill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    0 cmd 0x170 ctl 0x376max UDMA/10 
bash: [: missing `]'
on (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.781297] usbcore: registered new inter
bash: [: missing `]'
[   15.968539] ACPI: Power Button (CM) [VBTN
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.795943] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2
bash: [: missing `]'
[   16.192435] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.7421bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.808769] input,hidra v1.10 Keyboard [Dell De
bash: [: missing `]'
06] ndiswrapper: driver net5211 (,01/10/2004,4.0.0.14001) load
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.809275] Driver 'sd' needs updating - please use
bash: [: missing `]'
[   16.742458] ndiswrapper 0000:05:05.0: PCI INT A -> 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810673] sd 1:0:0:0: [sda] 156250000 512-byte hardware sectors
[   17.223617] ndiswrapper: using IRQ 17
[   17.274076] parport_pc 0bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810712] sd 1:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
0:07: reported by Plug and Play ACPI
[   17.274138] pabill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810719] sd 1: Sense: 00 3a 00 00
rport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCS
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810786] sd 1:0:0:0: [sda] Write cache: enabled,
bash: [: missing `]'
[   17.728781] wlan0: ethernet device 00:15:e9:fb:4f:8
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810923] sd 1:0:0:0: [sda] 156250000 5
bash: [: missing `]'
[   17.732264] wlan0: encryption modes suppo
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810958] sd 1:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
[   17.732449] usbcore: registered new interface driv
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.810964] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
bash: [: missing `]'
[   18.455177] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [    6.811012] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't suppor
> [    6.811017]  sda:<6>input: Dell Dell USB Mouse as /devi
> [    6.821991] input,hidraw1: USB HID v1.10 Mouse [Dell Dell USB Mouse] on us
> [    6.822018] usbcore: registered new interface driver usbhid
> [    6.822023] usbhid: v2.6:USB H
> [    6.831335]  sda1 sda2 sda3 sda4
[   18.455215] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.679994] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.002395] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.175774] loop: module loaded
[   21.200466] lp0: using parport0 (interrupt-driven).
[   21.315314] cfg80211: Using static regul> [    6.850434] sd 1:0:0:0: [sda] Attached SCSI dis
atory domain info
[   21.315319] cfg80211: Regulato> [    6.850549] sd 3:0:0:0: [sdb] 156250000 512-byte hardware 
ry domain: US
[   21.315321] 	(start_freq - end_freq @ bandwid> [    6.850582] sd 3:0:0:0: [sdb] Write Protect is off
th), (max_antenna_gain, max_eirp)
[   21.315325] 	(240> [    6.850586] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
2000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
> [    6.850640] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled,
[   21.315329] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
> [    6.850734] sd 3:0:0:0: [sdb] 156250000 512-byte hardware sector
[   21.315332] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 
> [    6.850764] sd 3:0:0:0: [sdb] Write Protect is o
[   21.315335] 	(5210000 KHz - 5230000 KHz @ 40000 
> [    6.850768] sd 3:0:0:0: [sdb] Mode Sense: 
[   21.315338] 	(5230000 KHz - 5330000 KHz @ 
> [    6.850821] sd 3:0:0:0: [sdb] Write cache: e
[   21.315342] 	(5735000 KHz - 5835000 KHz @ 40
> [    6.850827]  sdb: sdb1 sdb2 sdb3 sdb4
[   21.315344] cfg80211: Calling CRDA fo
> [    6.885937] sd 3:0:0:0: [sdb] Attac
[   21.509094] Adding 4192956k swap on
> [    6.904388] ata5.00: ATAPI: HL-DT-ST C
[   22.076690] EXT3 FS on dm-2, internal 
> [    6.904414] ata5.01: ATAPI: PHILIPS DVD+/-
[   23.213288] type=1505 audit(1231400524.183
> [    6.940311] ata5.00: configured for U
[   23.398000] type=1505 audit(123140052
> [    6.956570] ata5.01: configured for U
[   23.398191] type=1505 audit(123140052
> [    6.956626] ata6: port disabled. ig
[   23.586211] ip_tables: (C) 2000-200
> [    6.957255] scsi 5:0:0:0: CD-ROM         
[   24.672718] ACPI: WMI: Mapper loaded
[   > [    6.957463] scsi 5:0:0:0: Attached scsi ge
25.277368] tg3: eth0: Link is up at 100 Mbps, 
> [    6.959504] scsi 5:0:1:0: CD-ROM            PHILIPS  DVD
[   25.277372] tg3: eth0: Flow control is on for TX and on 
> [    6.959634] scsi 5:0:1:0: Attached scsi generic sg3 
[   25.650736] warning: `avahi-daemon' uses 32-bit capa
> [    7.027914] Driver 'sr' needs updating - p
[   25.763358] apm: BIOS version 1.2 Flags 0x
> [    7.031592] sr0: scsi3-mmc drive: 48x/48
[   25.763366] apm: disabled - APM is not S
> [    7.031597] Uniform CD-R
[   25.943748] ppdev: user-
> [    7.031716] sr 5:0:0:0: 
[   28.575573] Bluetooth: C
> [    7.040102] sr1: scsi3-m
[   28.576274] NET: Registe
> [    7.040204] sr 5:0:1:0: 
[   28.576280] Bluetooth: H
> [    7.949720] PM: Starting manual resume from disk
[   28.576313] Bluetooth: HCI socket layer initiali
> [    7.949725] PM: Resume from partition 254:3
[   28.592759] Bluetooth: L2CAP ver 2.11
[   2> [    7.949728] PM: Checking hibernation image.
8.592773] Bluetooth: L2CAP socket layer initial
> [    7.949904] PM: Resume from disk failed.
> [    7.953470] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000d100818c531f]
[   28.606770] Bluetooth: SCO (Voice Link) ver 0.6
[   28.606779] Bluetooth: SCO socket layer initialized
[   28.617809] B> [    8.002785] kjournald starting.  Commit interval 5 seconds
> [    8.002806] EXT3-fs: mounted filesystem with ordered data mode.
> [    9.693593] usb-storage: device scan complete
> [    9.698194] scsi 0:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.00 PQ: 0 ANSI: 0
> [    9.701563] scsi 0:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.
> [    9.705565] scsi 0:0:0:2: Direct-Access     
> [    9.708815] scsi 0:0:0:3: Direct-Access     TEAC 
> [    9.713781] sd 0:0:0:0: [sdc] Attached SCSI removable dis
> [    9.713926] sd 0:0:0:0: Attached scsi generic sg4 type 0
> [    9.718879] sd 0:0:0:1: [sdd] Attached SCSI remo
> [    9.718952] sd 0:0:0:1: Attached scsi generic sg5 type 0
> [    9.723754] sd 0:0:0:2: [sde] Attached SCSI removabl
> [    9.723827] sd 0:0:0:2: Attached scsi generic sg6 type 0
> [    9.773259] sd 0:0:0:3: [sdf] Attached SCSI removable
> [    9.773332] sd 0:0:0:3: Attached scsi ge
> [   14.206262] udevd version 124 star
> [   15.120887] pci_hotplug: PCI Hot Plug PCI Core version: 0.
> [   15.144262] shpchp: Standard Hot Plug PCI Control
> [   15.247272] intel_rng: Firmware space 
> [   15.247276] intel_rng: don't want to disa
bash: [: missing `]'
luetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.617818] Bluetooth: BNEP filters: protocol multicast
[   28.639949] Bridge firewalling registered
[   28.640517] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.673664] Bluetooth: RFCOMM socket layer initialized
[   28.674175] Bluetooth: RFCOMM TTY layer initialized
[   28.674189] Bluetooth: RFCOMM ver 1.10
[   33.126443] NET: Registered protocol family 17
[  133.740463] ppdev0: registered pardevice
[  133.788185] ppdev0: unregistered pardevice
[  133.864353] ppdev0: registered pardevice
[  133.912277] ppdev0: unregistered pardevice
[  136.204102] ppdev0: registered pardevice
[  136.252033] ppdev0: unregistered pardevice
[ 2113.277988] ath_hal: Unknown parameter `ath_pci'
[ 2318.632390] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ bill@J325P81:~/madwifi/madwifi-hal-0.tain.6$ [   15.247280] intel_rng: you are cer 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.247283] intel_rng: RNG, try using t
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.327283] iTCO_vendor_support: vendor-support
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.337712] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.337891] iTCO_wdt: failed to reset NO_REBOOT flag, reboot dis
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.337917] iTCO_wdt: No car
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.910811] input: Power But
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.936536] ACPI: Power Button (FF) [PWRF]
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.936668] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   15.968539] ACPI: Power Button (CM) [VBTN
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   16.192435] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   16.742106] ndiswrapper: driver net5211 (,01/10/2004,4.0.0.14001) load
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   16.742458] ndiswrapper 0000:05:05.0: PCI INT A -> 
bash: syntax error near unexpected token `newline'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   17.223617] ndiswrapper: using IRQ 17
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   17.274076] parport_pc 00:07: reported by Plug and Play ACPI
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   17.274138] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCS
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   17.728781] wlan0: ethernet device 00:15:e9:fb:4f:8
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   17.732264] wlan0: encryption modes suppo
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   17.732449] usbcore: registered new interface driv
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   18.455177] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   18.455215] HDA Intel 0000:00:1b.0: setting latency timer to 64
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   18.679994] input: PC Speaker as /devices/platform/pcspkr/input/input5
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   19.002395] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.175774] loop: module loaded
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.200466] lp0: using parport0 (interrupt-driven).
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315314] cfg80211: Using static regulatory domain info
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315319] cfg80211: Regulatory domain: US
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315321] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315325] (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315329] (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315332] (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315335] (5210000 KHz - 5230000 KHz @ 40000 
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315338] (5230000 KHz - 5330000 KHz @ 
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315342] (5735000 KHz - 5835000 KHz @ 40
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.315344] cfg80211: Calling CRDA fo
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   21.509094] Adding 4192956k swap on
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   22.076690] EXT3 FS on dm-2, internal 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   23.213288] type=1505 audit(1231400524.183
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   23.398000] type=1505 audit(123140052
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   23.398191] type=1505 audit(123140052
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   23.586211] ip_tables: (C) 2000-200
bash: syntax error near unexpected token `('
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   24.672718] ACPI: WMI: Mapper loaded
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   25.277368] tg3: eth0: Link is up at 100 Mbps, 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   25.277372] tg3: eth0: Flow control is on for TX and on 
bash: [: missing `]'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ [   25.650736] warning: `avahi-daemon' uses 32-bit capa
> [   25.763358] apm: BIOS version 1.2 Flags 0x
> [   25.763366] apm: disabled - APM is not S
> [   25.943748] ppdev: user-
> [   28.575573] Bluetooth: C
> [   28.576274] NET: Registe
> [   28.576280] Bluetooth: H
> [   28.576313] Bluetooth: HCI socket layer initiali
> [   28.592759] Bluetooth: L2CAP ver 2.11
> [   28.592773] Bluetooth: L2CAP socket layer initial
> [   28.606770] Bluetooth: SCO (Voice Link) ver 0.6
> [   28.606779] Bluetooth: SCO socket layer initialized
> [   28.617809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
> [   28.617818] Bluetooth: BNEP filters: protocol multicast
> [   28.639949] Bridge firewalling registered
> [   28.640517] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
> [   28.673664] Bluetooth: RFCOMM socket layer initialized
> [   28.674175] Bluetooth: RFCOMM TTY layer initialized
> [   28.674189] Bluetooth: RFCOMM ver 1.10
> [   33.126443] NET: Registered protocol family 17
> [  133.740463] ppdev0: registered pardevice
> [  133.788185] ppdev0: unregistered pardevice
> [  133.864353] ppdev0: registered pardevice
> [  133.912277] ppdev0: unregistered pardevice
> [  136.204102] ppdev0: registered pardevice
> [  136.252033] ppdev0: unregistered pardevice
> [ 2113.277988] ath_hal: Unknown parameter `ath_pci'
> [ 2318.632390] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
> bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ 


```

---

### Post by kevdog on 2009-01-08
Ok, lets just double check a few things:

modinfo ath_pci

Make sure the module is loaded with the sudo modprobe ath_pci statement (forget loading ath_hal -- not needed)

Then post lshw -C network along with iwlist scan

Why do you have many statements like this:
bash: [: missing `]'


I downloaded from svn and compiled on my own machine without a problem.  I didn't however install the module b/c I dont have a chipset to test on.  The compilation went without any errors.

---

### Post by seubill on 2009-01-08
```
bill@J325P81:~$ modinfo ath_pci
filename:       /lib/modules/2.6.27-9-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3879
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     53828DCE2B2CEC52C9E9103
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 ip=192.168.1.5 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:68:88:6e:27:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.

bill@J325P81:~$ 


```

---

### Post by seubill on 2009-01-08
Checked in my home directory and I actually created two different madwifi folders: Madwifi>madwifi-hal-0.10.5.6 (containing 29 items), and also: Madwifi-hal-0.10.5.6 (containing 22 items). I was following the commands in both posts 111 and 118, and apparently messed-up by creating two different folders. Maybe could be why the missing stuff entries? Should I delete one out?

```
05:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: D-Link System Inc Device 3a1d
	Flags: bus master, fast Back2Back, medium devsel, latency 128, IRQ 17
	Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: ath5k, ath_pci


```

What commands do I need to change out of ndiswrapper and try out the new one?

---

### Post by seubill on 2009-01-08
```
bill@J325P81:~$ sudo modprobe ath_pci
sudo: unable to resolve host J325P81
[sudo] password for bill: 
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:fb:4f:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,01/10/2004,4.0.0.14001 ip=192.168.1.5 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:80:16:8b:61:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:2B:69:06:3F
                    ESSID:"Broadband1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.

bill@J325P81:~$ 


```

---

### Post by kevdog on 2009-01-08
seubill

You seem like a very competent and smart guy, but try to analyze the things I ask you for.  That's my biggest stumbling block for persons new to linux.  One of your problems is staring you right in the face:

 driver=ndiswrapper+net5211

Basically ndiswrapper is still claiming the device.  To correct this

#1. Unload ndiswrapper - sudo rmmod ndiswrapper
#2. Remove ndiswrapper from the /etc/modules file to prevent it loading from boot (Again as discussed previously external modules are never loaded by default at boot, only if mentioned in the /etc/modules file are they loaded
#3. Load the ath_pci module - sudo modprobe ath_pci

Double check the device is claimed by the ath_pci driver with lshw -C network

As a corollary to #2 - if you want ath_pci to load at boot and claim the device - list ath_pci in the /etc/modules file.

Once the device is claimed by ath_pci we can begin configuring the device to see if its actually going to work -- which is a big IF!

Please note that the modinfo ath_pci statement gives information about the ath_pci kernel module.  This statement tells me that you have installed the svn version version:        svn r3879
I'm not exactly sure if this is the correct version or not. Let me double check on my own machine.  Did you compile ath_pci or madwifi on previous attempts from svn?

Please do a:
sudo updatedb

Then a:
locate ath_pci

To see other ath_pci modules you may have somewhere in the system.

---

### Post by seubill on 2009-01-08
OK, started over and re-done everything from the beginning, copying and pasting the commands to make sure I got it right.

```
bill@J325P81:~$ sudo aptitude install linux-headers-`uname -r`
sudo: unable to resolve host J325P81
[sudo] password for bill: 
Sorry, try again.
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

bill@J325P81:~$ cd ~/madwifi
bill@J325P81:~/madwifi$ svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6

Fetching external item into 'madwifi-hal-0.10.5.6/tools/ath_info'
Checked out external at revision 3901.

Checked out revision 3901.
bill@J325P81:~/madwifi$ cd madwifi-hal-0.10.5.6
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/bill/madwifi/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ sudo make install
sudo: unable to resolve host J325P81
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/bill/madwifi/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.27-9-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.27-9-generic/net
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath'
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_hal'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.27-9-generic/net
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_hal'
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/amrr'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/amrr'
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/onoe'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/onoe'
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/sample'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/sample'
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/minstrel'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate/minstrel'
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/ath_rate'
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/net80211'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.27-9-generic/net; \
	done
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/net80211'
(export KMODPATH=/lib/modules/2.6.27-9-generic/net; /sbin/depmod -ae 2.6.27-9-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/bill/madwifi/madwifi-hal-0.10.5.6/tools'
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ sudo modprobe ath_hal ath_pci
sudo: unable to resolve host J325P81
FATAL: Error inserting ath_hal (/lib/modules/2.6.27-9-generic/net/ath_hal.ko): Unknown symbol in module, or unknown parameter (see dmesg)
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ sudo modprobe ath_pci
sudo: unable to resolve host J325P81
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ lsmod | grep ath
ath_pci               216504  0 
wlan                  240624  1 ath_pci
ath_hal               312288  1 ath_pci
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:77:a3:89  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:654589 (654.5 KB)  TX bytes:72881 (72.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2032 (2.0 KB)  TX bytes:2032 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:fb:4f:83  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15336 (15.3 KB)  TX bytes:31445 (31.4 KB)
          Interrupt:17 Memory:fbdf0000-fbe00000 

bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6$ 


```

Don't see any ath0 listed under ifconfig. :confused:

---

### Post by kevdog on 2009-01-08
Please also unload the ath5k driver as this may be competing:

sudo rmmod ath5k  (also remove from /etc/modules).

See previous post above. (In case you have not)

Things to double check at this time:
Making sure the ath_pci module is the actual module you compiled and installed.
Make sure all competing modules are unloaded - ndiswrapper, ath5k
Make sure the device is claimed by the correct ath_pci module.

---

### Post by seubill on 2009-01-08
I guess we both were working at the same time. On your last post, how do I do #2, remove ndiswrapper from /etc/modules?

---

### Post by kevdog on 2009-01-08
I'm not sure if it is in there, however

gksu gedit /etc/modules

This is a text file.  Remove or comment (#) any line that has ndiswrapper on it!  This is just a configuration file.  The system reads this file upon startup to know which external kernel modules to load at startup.

---

### Post by seubill on 2009-01-08
was not in there, but the ath5k is, so I will comment that out while I'm there

---

### Post by seubill on 2009-01-08
```
bill@J325P81:~$ sudo modprobe ath_pci
sudo: unable to resolve host J325P81
[sudo] password for bill: 
bill@J325P81:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=128 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:fb:f3:39:a8:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~$ gksu gedit /etc/modules
sudo: unable to resolve host J325P81bill@J325P81:~$ sudo updatedb
sudo: unable to resolve host J325P81
bill@J325P81:~$ locate ath_pci
/home/bill/madwifi/madwifi-hal-0.10.5.6/.tmp_versions/ath_pci.mod
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.ko.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.mod.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.if_ath_pci.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.ko
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.mod.c
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.mod.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.c
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.h
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.c
/home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.h
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci/if_ath_pci.o
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci/if_ath_pci.o
/lib/modules/2.6.27-9-generic/net/ath_pci.ko
/usr/share/linux-restricted-modules/2.6.27-7-generic/modules.alias.override/ath_pci
/usr/share/linux-restricted-modules/2.6.27-9-generic/modules.alias.override/ath_pci
bill@J325P81:~$ sudo rmmod ath5k
sudo: unable to resolve host J325P81
bill@J325P81:~$ 


```

---

### Post by kevdog on 2009-01-08
?

---

### Post by kevdog on 2009-01-08
Sorry

I think you have the linux-restricted modules installed.  Can you remove these using synaptic or aptitude?

---

### Post by seubill on 2009-01-08
Please, would you tell me what commands to use for doing this;


```
Things to double check at this time:
Making sure the ath_pci module is the actual module you compiled and installed.
Make sure all competing modules are unloaded - ndiswrapper, ath5k
Make sure the device is claimed by the correct ath_pci module.
```

Thanks!

---

### Post by seubill on 2009-01-08
checked in synaptic package manager and there are 4 different linux restricted modules showing green. Looks like I can remove them in there. Should I do so?

---

### Post by kevdog on 2009-01-08
You have two ath_pci modules contained in your system (not loaded, but contained)

If you look at your output from the locate ath_pci statement, there are a lot of lines, however it basically comes down to your 10.5.6 folder tree and the linux-restricted folder tree.  Both of these packages supply a ath_pci driver.  Obviously you want to use one and not the other.  

The best way I know how to do this (although I am sure there are other ways) is to remove the linux-restricted-drivers package (which is a meta package that contains video drivers, wireless drivers, etc).

Are you running an Nvdia card or ATI card?
The restricted package contains the following:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)

---

### Post by seubill on 2009-01-08
Ok, have removed the restricted drivers packages.

---

### Post by seubill on 2009-01-08
Yes, it has a Nvida graphics card, but I had de-activated the driver for it (in the Hardware Drivers box) a while back because the thing would make the desktop go sideways with the mouse instead of vertical.

I wrote down on a pad the drivers that I just removed, in case need to re-install later

---

### Post by kevdog on 2009-01-08
Glad to know things are still working. 

Update the search database
sudo updatedb

Then 
locate ath_pci

Just to make sure no ath_pci module is competing.  Then install your compiled kernel module within the source directory with a 
sudo make install

Update the dependency database
sudo depmod -a

Then load the module
sudo modprobe ath_pci

Double check a few things
modinfo ath_pci
lsmod ath_pci
lshw -C network

And if all fails check dmesg to see what happened if things are not working are the driver is UNCLAIMED or something like this.

---

### Post by seubill on 2009-01-08
Hit a stumbling block at install:

```
bill@J325P81:~$ sudo updatedb
sudo: unable to resolve host J325P81
[sudo] password for bill: 
bill@J325P81:~$ locate ath_pci
/home/bill/madwifi/madwifi-hal-0.10.5.6/.tmp_versions/ath_pci.mod
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.ko.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.mod.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.if_ath_pci.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.ko
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.mod.c
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.mod.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.c
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.h
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.c
/home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.h
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
/lib/modules/2.6.27-9-generic/net/ath_pci.ko
bill@J325P81:~$ sudo make install
sudo: unable to resolve host J325P81
make: *** No rule to make target `install'.  Stop.
bill@J325P81:~$ 


```

---

### Post by kevdog on 2009-01-08
You have to be within the source directory:

cd /home/bill/madwifi-hal-0.10.5.6
sudo make install

---

### Post by seubill on 2009-01-08
OK, got all the way. Shows the network UNCLAIMED, all the way at the bottom.

```
bill@J325P81:~$ sudo updatedb
sudo: unable to resolve host J325P81
[sudo] password for bill: 
bill@J325P81:~$ locate ath_pci
/home/bill/madwifi/madwifi-hal-0.10.5.6/.tmp_versions/ath_pci.mod
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.ko.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.mod.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.ath_pci.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.if_ath_pci.o.cmd
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.ko
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.mod.c
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.mod.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/ath_pci.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.c
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.h
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/if_ath_pci.o
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
/home/bill/madwifi/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.c
/home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.h
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
/home/bill/madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
/lib/modules/2.6.27-9-generic/net/ath_pci.ko
bill@J325P81:~$ sudo make install
sudo: unable to resolve host J325P81
make: *** No rule to make target `install'.  Stop.
bill@J325P81:~$ cd /home/bill/madwifi-hal-0.10.5.6
bill@J325P81:~/madwifi-hal-0.10.5.6$ sudo make install
sudo: unable to resolve host J325P81
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/bill/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath/if_ath.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath/if_ath_radar.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath/if_ath_hal_extensions.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath/if_ath_pci.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath/ath_pci.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath_hal/ah_os.o
  HOSTCC  /home/bill/madwifi-hal-0.10.5.6/ath_hal/uudecode
  UUDECODE /home/bill/madwifi-hal-0.10.5.6/ath_hal/i386-elf._hal.o
  UNMANGLE /home/bill/madwifi-hal-0.10.5.6/ath_hal/i386-elf.hal.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_hal/ath_hal.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/amrr/amrr.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/onoe/onoe.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/sample/sample.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/if_media.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_skb.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_beacon.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_none.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_input.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_node.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_output.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_power.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_proto.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_scan.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_wireless.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_linux.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_monitor.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_rate.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_acl.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_scan_ap.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_scan_sta.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/ieee80211_xauth.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_wep.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_tkip.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_ccmp.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_acl.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_xauth.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_scan_sta.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/bill/madwifi-hal-0.10.5.6/ath/ath_pci.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath/ath_pci.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/ath_hal/ath_hal.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_hal/ath_hal.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/ath_rate/sample/ath_rate_sample.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_acl.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_acl.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_ccmp.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_ccmp.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_scan_ap.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_scan_sta.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_tkip.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_tkip.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_wep.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_wep.ko
  CC      /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_xauth.mod.o
  LD [M]  /home/bill/madwifi-hal-0.10.5.6/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.27-9-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.27-9-generic/net
make[1]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath'
make[1]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath_hal'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.27-9-generic/net
make[1]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath_hal'
make[1]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/amrr'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/amrr'
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/onoe'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/onoe'
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/sample'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/sample'
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/minstrel'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.27-9-generic/net
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate/minstrel'
make[1]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/ath_rate'
make[1]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/net80211'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.27-9-generic/net; \
	done
make[1]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/net80211'
(export KMODPATH=/lib/modules/2.6.27-9-generic/net; /sbin/depmod -ae 2.6.27-9-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
ath_info.c: In function 'main':
ath_info.c:2841: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
athstats.c: In function 'main':
athstats.c:289: warning: format not a string literal and no format arguments
athstats.c:291: warning: format not a string literal and no format arguments
athstats.c:311: warning: format not a string literal and no format arguments
athstats.c:313: warning: format not a string literal and no format arguments
athstats.c:348: warning: format not a string literal and no format arguments
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/bill/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/bill/madwifi-hal-0.10.5.6/tools'
bill@J325P81:~/madwifi-hal-0.10.5.6$ sudo depmod -a
sudo: unable to resolve host J325P81
bill@J325P81:~/madwifi-hal-0.10.5.6$ sudo modprobe ath_pci
sudo: unable to resolve host J325P81
bill@J325P81:~/madwifi-hal-0.10.5.6$ modinfo ath_pci
filename:       /lib/modules/2.6.27-9-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3879
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     53828DCE2B2CEC52C9E9103
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
bill@J325P81:~/madwifi-hal-0.10.5.6$ lsmod ath_pci
Usage: lsmod
bill@J325P81:~/madwifi-hal-0.10.5.6$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=128 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:fb:f3:39:a8:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bill@J325P81:~/madwifi-hal-0.10.5.6$ 

```

---

### Post by kevdog on 2009-01-08
Did you load the module?

sudo depmod -a (if you have done this skip it!)
sudo modprobe ath_pci
lsmod | grep ath
lshw -C network

Check dmesg for any errors?

---

### Post by seubill on 2009-01-08
Kevdog, these two comands here were done:

```
sudo depmod -a (if you have done this skip it!)
sudo modprobe ath_pci
```

The next two,I just did:

```
bill@J325P81:~$ lsmod | grep ath
ath_pci               216504  0 
wlan                  240624  1 ath_pci
ath_hal               312288  1 ath_pci
bill@J325P81:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:77:a3:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a ip=192.168.1.6 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=128 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:fb:f3:39:a8:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Ran the dmesg, I did not post it here because it's as long as Denver to Omaha. It is like reading Greek to me, but I did not see anything about an error or unclaimed driver.

---

### Post by seubill on 2009-01-08
Found this in dmesg:

```
[ 2747.134629] ath_hal: Unknown parameter `ath_pci'

```

:confused:

---

### Post by kevdog on 2009-01-09
Wow, I'm really confused about this one, maybe its not meant to be :(

Here is what I would try (I'm running out of ideas)

cd /home/bill/madwifi/madwifi-hal-0.10.5.6/scripts

./find-madwif-modules.sh -l

sudo ./madwifi-unload

sudo modprobe ath_pci

Then recheck dmesg

---

### Post by seubill on 2009-01-09
I'm puzzled by the output of 'no such file'

```
bill@J325P81:~$ cd /home/bill/madwifi/madwifi-hal-0.10.5.6/scripts
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6/scripts$ ./find-madwif-modules.sh -lbash: ./find-madwif-modules.sh: No such file or directory
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6/scripts$ 
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6/scripts$ sudo ./madwifi-unload
sudo: unable to resolve host J325P81
Unloading "ath_pci"
Unloading "wlan"
Unloading "ath_hal"
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6/scripts$ sudo modprobe ath_pci
sudo: unable to resolve host J325P81
bill@J325P81:~/madwifi/madwifi-hal-0.10.5.6/scripts$ 

```

An issue of some confusion for me; the ndiswrapper driver continues to load at boot, yet I have used the command rmmod ndiawrapper more than once and checked the /etc/modules file in gedit. There is no ndiswrapper there, but could the ath_pci entry possibly get the ndiswrapper booting?

Will be examining dmesg over the next little while.

Hey listen, I very much appreciate your time and continued effort to help me out with this thing. Thank you very much for your kind attention! If it turns out that the wireless just absolutely will not function with this chipset--well, life will still go on as we know it!:D

---

### Post by seubill on 2009-01-09
This is from dmesg. Did not see anything else that would appear to be out of the ordinary.

```
STATE,COMPAT,ECP]
[   16.943657] ndiswrapper: driver net5211 (,01/10/2004,4.0.0.14001) loaded
[   16.944029] ndiswrapper 0000:05:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.424954] ndiswrapper: using IRQ 17
[   18.642631] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   18.736733] wlan0: ethernet device 00:15:e9:fb:4f:83 using serialized NDIS driver: net5211, version: 0x40000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001A.5.conf
[   18.740216] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.740390] usbcore: registered new interface driver ndiswrapper
[   18.741317] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.741358] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.054704] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.232494] loop: module loaded
[   21.257323] lp0: using parport0 (interrupt-driven).
[   21.349258] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)

```

---

### Post by seubill on 2009-01-09
Here is the file 'find-madwifi-modules.sh' that does not exist!

```
fi#!/bin/sh

if [ -z "${1}" ] ; then
	echo "Purpose:"
	echo "Locate all madwifi-related kernel modules for a given kernel"
	echo "(including all its subdirectories)."
	echo
	echo "Usage:"
	echo "$0 [-l] [-r] <kernelrelease> [destdir]"
	echo
	echo "<kernelrelease>: the kernel release that madwifi has been compiled for"
	echo "[destdir]: destination directory for the compiled madwifi modules (optional)"
	echo "-l list the modules we find."
	echo "-r remove the modules we find."
	echo "If neither -l or -r is specified, the user will be prompted."
	echo
	exit 1
fi

LIST_CMD=0
REMOVE_CMD=0
while [ 1 ]; do
	case $1 in
		-l)
			LIST_CMD=1
			shift;
			;;
		-r)
			REMOVE_CMD=1
			shift;
			;;
		*) 	
			break;
			;;
	esac;
done;

KVERS="${1}"

if [ -n "${2}" ]; then
	KDEST="${2}"
else
	KDEST=""
fi

SEARCH="${KDEST}/lib/modules/${KVERS}"

PATTERN="^.*\/(ath_(hal|pci|rate_[^.]*)\.k?o)|(wlan(_(acl|ccmp|scan_(ap|sta)|tkip|wep|xauth))?\.k?o)$"
OLD_MODULES=$(find ${SEARCH} -type f -regex '.*\.k?o' 2>/dev/null | grep -w -E "${PATTERN}")



if [ -n "${OLD_MODULES}" ]; then
	if [ "$LIST_CMD" -eq 1 ] || [ "$REMOVE_CMD" -eq 1 ]; then
		if [ "$LIST_CMD" -eq 1 ]; then
			for m in ${OLD_MODULES}; do echo ${m}; done
		fi;
		if [ "$REMOVE_CMD" -eq 1 ]; then
			rm -f ${OLD_MODULES}
		fi;
	else
		echo ""
		echo "WARNING:"
		echo "It seems that there are modules left from previous MadWifi installations."
		echo "If you are unistalling the MadWifi modules please press \"r\" to remove them."
		echo "If you are installing new MadWifi modules, you should consider removing those"
		echo "already installed, or else you may experience problems during operation."
		echo "Remove old modules?"
		
		while true; do
			echo
			echo -n "[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? "
			echo
			read REPLY
			case ${REPLY} in
				l|L)
					for m in ${OLD_MODULES}; do echo ${m}; done
					continue
					;;
				
				r|R)
					rm -f ${OLD_MODULES}
					exit
					;;
			
				i|I)
					exit 0
					;;
		
				x|X)
					exit 1
					;;
	
				*)
					continue
					;;
			esac
		done
	fi;

exit 0
```

---

### Post by kevdog on 2009-01-09
Ok, did you install ndiswrapper via repository?

If you did, I would first unload the module and the driver contained inside ndiswrapper.

sudo rmmmod ndiswrapper
sudo ndiswrapper -r net5211

Then try uninstalling ndiswrapper via the method you used to install it (synaaptic, aptitude, or whatever).

I think I noticed a typo:
/find-madwif-modules.sh

should be ./find-madwifi-modules.sh -l  (Thats the letter l)

If this patched version of madwifi doesn't work, then I suggest doing a very similar process and getting the latest svn revision.  Its exactly the same method with compiling, however you just need to checkout a different revision with svn.  More on that if need so -- however since you are now a pro at this, you should be able to unload, uninstall, download svn, compile, and install the madwifi set in about 2-3 minutes.  It only takes about 2-3 tries with this stuff until a light bulb turns on and you say -- compiling from source is no big deal.

---

### Post by seubill on 2009-01-10
Have now ndiswrapper uninstalled and the compiled madwifi driver up and going. Gets internet connection, however web pages browsing is extremely slow, 6Mb/s, with frequent timeouts.

Began looking through the madwifi.org stuff, and there is so much in there that it will take a few days for a greenhorn as myself to take it all in. 

Interested in checking out the revision/update material, if I can find it!:)

---

### Post by kevdog on 2009-01-10
So, seems like that was a no go for you.

Madwifi seems intimidating at first, but once you go actually through the exercise of downloading from svn, compiling, and installing (and learning the commands to do all this stuff), its actually very straightforward.

Do you want to try to check out the latest svn trunk?  The version you compiled previously was a patched version that I had read somewhere may have worked for your card version, but obviously that info was incorrect.

Tell me if you want to try.  The process is nearly identical to what you just did -- except you need to check out a different svn branch.

---

### Post by seubill on 2009-01-10
O YES--you bet that I would like to try the latest svn trunk that you mention. I'm willing to try out anything. This time around I am going to keep a journal, writing out each specific command, what the command does, and the proper sequence of commands. That way I can learn to do this on my own.

 In the whatever it's worth dept., I read something last evening about having to configure with something known as wpa_supplicant. That one's a new wrinkle on me, but then I went into the router and turned off WPA/PSK , but still did not change anything, so I guess that was not relevant.

---

### Post by kevdog on 2009-01-10
Here is what to do:

cd ~ (You can make this directory whatever you want -- I typically put all of my svn stuff within the root directory ~/src, but do whatever you please)

mkdir -p madwifi  (This command makes a directory madwifi if it doesn't exist)
svn co [http://svn.madwifi-project.org/madwifi/trunk](http://svn.madwifi-project.org/madwifi/trunk) madwifi

Ok so you now have the latest and greatest svn sources.  Since svn sources are frequently updated by the developers, you can always update your source tree by doing the following:

cd ~/madwifi
svn up

Whether you downloaded for the first time or simply updated the sources, you will always need to recompile and reinstall since all you have are non-compiled source files. (Not binaries!!!)

If you have updated your source trees, or what to compile everything again (not just the new sources) do the following:

cd ~/madwifi
make clean  (Get used to using the command a lot when things don't go right -- its common among any compiled program)

Again to compile

cd ~/madwifi
make
sudo make install (This will install the driver -- which basically means it places the executables within the /lib/modules/<kernel version/net/ath_pci.ko

Again just words of advice
1. Downloading (updating) from svn, and compiling these wireless drivers are usually a piece of cake, and can readily be done within minutes.  Its not hard.
2. Installation (sudo make install) is also a very easy process
3. The difficult part about the entire process, is making sure the version you installed is the actual kernel module that is going to be loaded into the kernel (via the sudo modprobe ath_pci command).  Again competing versions whether installed through a .deb package, synaptic, or other compilation process can cause numerous problems. 

Use the modinfo statement:
modinfo ath_pci
At look at the first line that states the filename: directive.  This will tell you the path its finding the ath_pci driver.

To locate other possible competing ath_pci modules, update the search database:
sudo updatedb

Then:
locate ath_pci | grep ath_pci$

Other directories will be listed, however you want to exclude your own source directory, and possibly other kernel versions that are listed -- since you can only use one kernel version at a time.  This should leave you with one line that matches the modinfo statement.

Once the module is loaded with the modprobe statement, you want to verify that this process actually claimed your wireless device.  Ways of doing this are:
lshw -C network
And verifying that the driver listed under your wireless device is listed as ath_pci.  You DO NOT want to see an UNCLAIMED statement within your wireless networking block.  If things are not as they seem, always check dmesg for any possible errors.  I always use the command dmesg | less, however there are other ways of doing this also.

Once the device is successfully claimed and such, you then want to configure wireless parameters and such.  This can either be done on the command line, or using higher level programs such as Network Manager or WICD.  I personally prefer WICD, however Network Manager works for me most of the time, however if getting any errors with device configuration, I always default to the manual command line entry so I can see where the process is failing.  Its good to become at least familiar with the manual process, although I wouldn't recommend this for everyday use just for sake of simplicity, although its definitely a viable alternative and usually the most reliable.

The wpa_supplicant.conf file is only really needed if you are going to be configuring a wpa network manually or via the command line.  Just a word of advice, if troubleshooting buggy connections, always turn off all forms of encryption at the router (WEP/WPA/Mac Filtering), since this usually just adds layers of complexity into a process that is generally not working.  Add layers once you get the basics up and running.  Do not add confusion to an already complicated process.

---

### Post by seubill on 2009-01-10
Hey-hey-hey, was just going thru the madwifi.org FAQ's and came across this:

```
http://madwifi-project.org/wiki/UserDocs/Troubleshooting#EverythingappearstobeoperationalbutIstillcantaccessthenetwork
```

ran the 'ifconfig eth0 down' and now the thing is browsing the web pretty darn good! 

Question, what command would I need to do in order to keep in like this?  Would like to try it out for a few days before changing anything:)

---

### Post by pytheas22 on 2009-01-10
Glad to see you've gotten so far.

> ran the 'ifconfig eth0 down' and now the thing is browsing the web pretty darn good!

Question, what command would I need to do in order to keep in like this? Would like to try it out for a few days before changing anything

That's an interesting thought, that eth0 could be causing routing issues.  I'm not sure it's your problem because if your machine were trying to use eth0 as the only route to a gateway, you shouldn't have wireless connectivity at all.  But if it really solves the problem, let's not think too hard about it.

If you type 'sudo ifconfig eth0 down' once, eth0 should stay down till you either reboot or bring it up again (with 'sudo ifconfig eth0 up').  If you wanted to take it down permanently, you could either blacklist the module that drives it, or write a boot script to put it down at boot time.  If you want to get rid of eth0 permanently, we can provide instructions, but you should probably make sure that this really solves the problem first.

---

### Post by seubill on 2009-01-10
Sounds like good advice:

```
If you want to get rid of eth0 permanently, we can provide instructions, but you should probably make sure that this really solves the problem first.
```

I will just leave things as they are for a few days to test drive it out. No big deal if I have to do 'ifconfig eth0 down' each time I start the computer, for temporary anyway.


Just so I understand, in the post 155, beginning with cd~

would I actually be making 'cd ~/src' and both 'mkdir -p madwifi'?

Thanks very much for the detail and advice in there, I copied the entire post to a jump drive!

---

### Post by kevdog on 2009-01-11
Oh no?!!

Just to clarify -- you mean you never took down the wired interface when bringing up the wireless interface?  ::Smacks himself in head!  I thought we had covered this step way, way back!  What pytheas is telling you is that if you have 2 network interfaces active that both access the same gateway (or router), how is the OS supposed to differentiate which adapter to route packets through?  Its possible to run 2 adapters at once in other situations such as internet connection sharing, or when the two are on different subnets.

As yes it would be 
cd ~/src
Then run the commands as indicated above. 
Just wondering what driver you finally ended up using?

---

### Post by seubill on 2009-01-11
OK, understand. I remember something way back about taking down the wired interface, but I guess since I had to use the ethernet cabling to get the compiled driver it auto-connected? Anyway, I just cold started the machine and would not web browse until I did 'ifconfig eth0 down' again. Works good after that. Here's the driver info:

```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Device 01a8
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

05:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10)
	Subsystem: Dell Device 8010
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fbdef000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

05:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: D-Link System Inc Device 3a1d
	Flags: bus master, medium devsel, latency 96, IRQ 17
	Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath_pci
	Kernel modules: ath5k, ath_pci

bill@J325P81:~$ 

```

Question, do I need to comment out (#) eth0 somewhere, in order to boot up without it?

---

### Post by kevdog on 2009-01-11
Want are you using to connect?  Network Manager?  There are at least a couple of different ways to do this, depending on what you are using to configure your devices.

---

### Post by seubill on 2009-01-11
The only thing I have used to connect (wireless) is the 'Network Connections' graphical box, where a person enters in the SSID, BSSID. and so on.


I have never configured or used a wired connection for the machine, other than for testing in these posts and also downloading the madwifi from source.

Had to do the 'sudo ifconfig eth0 down' thing again at the command line to send this .

Checked the 'Network Connections' box, and for 'wired', there is nothing. The only entry in it is the wireless.

---

### Post by kevdog on 2009-01-11
Can you post your /etc/network/interfaces file?

---

### Post by seubill on 2009-01-11
/etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	dns-search MSHOME
```

---

### Post by kevdog on 2009-01-11
If you are not using eth0 at all I would just delete the entire section below:

auto eth0
iface eth0 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	dns-search MSHOME

If you want eth0 (since its basically setting up a static IP) but don't want it to start automatically, just remove the auto eth0 line.

---

### Post by seubill on 2009-01-11
Tried to remove 'auto eth0' but would not let me save the file.

---

### Post by kevdog on 2009-01-12
Edit it with the following:

gksu gedit /etc/network/interfaces

This file is owned by root, hence you need root privileges to edit (gksu).

---

### Post by seubill on 2009-01-12
That's great! Removed 'auto eth0', saved, quit, and rebooted. Connected straight up to the wireless. Browsed to hotmail and gmail and opened up both email accounts real good.

The 'Active Network Connections' box shows the speed at 24Mb/s, but I don't think is accurate because is connecting rather quickly.

Anyway, I will run with this for a day or two and report back in.

Now that probably 50,000+ people have seen how ignorant I am, sure hope some of them have gleaned beneficial, useful information from these threads. I sure have!:p

---

### Post by kevdog on 2009-01-12
Anytime you make changes to the /etc/network/interfaces file and you want to apply the changes without doing something so drastic as a reboot (although this will work) try:

sudo /etc/init.d/networking restart

---

### Post by seubill on 2009-01-12
Kevdog, hey thank you for this:

sudo /etc/init.d/networking restart

Just hate having to reboot, especially  with a raid setup.

So far, so good. Working excellently today.

---

### Post by seubill on 2009-01-15
Wireless internet connection has been working flawlessly over the past several days. Clearly, the patched version madwifi driver has provided solution for this chipset.

A sincere thank you to the two gentlemen, Pytheas22 and Kevdog, both of whom tirelessly guided me through 160+ posts to resolve the issue! Appreciate you both for your kind attention and interest with solving my problem!

---

### Post by seubill on 2009-01-15
Wireless internet connection has been working flawlessly over the past several days. Clearly, the patched version madwifi driver has provided solution for this chipset.

A sincere thank you to the two gentlemen, Pytheas22 and Kevdog, both of whom tirelessly guided me through 160+ posts to resolve the issue! Appreciate you both for your kind attention and interest with solving my problem!


Intended to mark the thread as [SOLVED], clicked on 'thread tools', but no option.

---

### Post by kevdog on 2009-01-16
Now that you know how to switch drivers back and forth real quick, would be interested if you had a different experience with the ath5k driver now!

---

### Post by seubill on 2009-01-16
kevdog, I was thinking the same thing  but a little shaky on the proper commands. Working real good now and of course don't want to mess it up.

would I use these commands to switch the drivers?

sudo modprobe -r ath_pci

sudo modprobe ath5k

---

### Post by kevdog on 2009-01-16
Take the interface down first (dont know what it is -- lets just say ath0 for now, but your's might be eth1 or something)

sudo ifconfig ath0 down
sudo rmmod (or modprobe -r) ath_pci
sudo modprobe ath5k
sudo ifconfig ath0 up

:)

Do not be scared about messing with things on your system.  Fear will get you nowhere since something after some update is going to break and you will need to fix it.  You have the appropriate knowledge now to troubleshoot your wireless adapter.  Use your knowledge!

---

### Post by seubill on 2009-01-16
Ok, as far as the interface name is concerned, I've ran into a bit of confusion.

'lshw -c network' shows the wireless interface with logical name 'wifi0'.

'iwlist scan' shows that wifi0 doesn't support scanning, but gives the information under 'ath0'.

Unsure of using 'wifi0' or 'ath0' for the command (to take down the interface).

---

### Post by kevdog on 2009-01-17
wifi0 is the actual device name, ath0 is the virtual device.  All commands must be put through the virtual device.  This is explained in the madwifi documentation.

---

### Post by seubill on 2009-01-17
Kevdog, thanks for that info in your last post.  Switched over to the ath5k driver. When the last command was entered 'sudo ifconfig ath0 up', returned an error, no such device 'ath0'. Entered dmesg and after browsing through a seemingly endless list of data, could not find anything that looked out of the ordinary. Perhaps received error because of virtual device?

Anyway, running the ath5k driver now and there is very little difference with web pages browsing, maybe just a tad slower, but nothing even close to warrant complaining about.

---

### Post by kevdog on 2009-01-18
I'm not sure but ath5k may be wlan0 and ath_pci may be ath0.  Good to know you don't notice much difference.  ath5k is completely open source whereas the HAL layer with ath_pci (or madwifi) is not.  Hopefully drivers like ath5k will be the future.

---

### Post by theDaveTheRave on 2009-02-14
Hello All

I've read this thread, and followed the majoity of the instructions but still seem unable to get my AR2413 802.11bg NIC wireless card to function!

First some history.

I am using an acer Aspire 3680. I have run this laptop exclusively on ubuntu since gusty, and the atheros wifi worked fine (most of the time), with occasional requirement to "re-install" the module when I did have a failure. I am now running hardy (and did try out intrepid for a bit), and the Wifi worked fine. But just before christmas I lost the wifi access, and I don't understand why. I tried my usual re-install trick, but no joy.

I had some many problems with Intrepid, that I even went an dug out my old Hardy install disk and did a clean install. I was plugged into the net via the ethernet card, and took all the updates that were available.... and still no wireless?

Is it possible that a Kernel update broke the module?

Can I install and use the module that worked on Fiesty (assuming I can find out the Kernel version!).

here is the output from the following some of the commands I think you may find usefull...

uname -a
```

Linux Dartagnon 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

```

lshw -C network

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.120 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

```

This one leads me not to be surprised that I get no reports from either of the next 2 commands for the <unclaimed> controller (it is this that is causing me grief)

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1454019 (1.3 MB)  TX bytes:187795 (183.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73900 (72.1 KB)  TX bytes:73900 (72.1 KB)

```

I did a quick hunt on modprobe stuff, and thought that this info may be of interest to you all...

lsmod | grep ath
```

ath_pci               101024  0 
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci

```

NOW...

As it happens I have written a post on the forum and have a copy of the output of <lshw -C network> from when my card was functioning...

here it is

OLD <lshw -C network> when wifi worked!
```

WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 14
serial: 00:16:36:c8:51:d3
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
*-network
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications, Inc.
physical id: 3
bus info: pci@0000:0a:03.0
logical name: wifi0
version: 01
serial: 00:19:7d:40:b8:c0
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci ip=192.168.2.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

and also the output of an old iwlist scan
```

iwlist scan

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wifi0 Interface doesn't support scanning.

ath0 Scan completed :
Cell 01 - Address: 00:17:3F:15:5D:43
ESSID:"Mousquetaires"
Mode:Master
Frequency:2.462 GHz (Channel 11)
Quality=53/70 Signal level=-42 dBm Noise level=-95 dBm
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100

```

From the above it seems as though everything in my setup should be making the card work OK, but it doesn't.

Does anyone have any ideas??

thanks in advance...

David

---

### Post by pytheas22 on 2009-02-14
David: what is the output of:
```

sudo modprobe ath_pci
dmesg | grep ath
```

Hopefully that will provide a better idea of why ath_pci doesn't want to claim your card.

> 
Can I install and use the module that worked on Fiesty (assuming I can find out the Kernel version!).

Not really.  You'd have to install the whole Feisty kernel, which might make your wireless work but would probably break a lot of other things.

I'm thinking however that compiling ath_pci from source would probably be a solution, but please post the dmesg output first.

---

### Post by theDaveTheRave on 2009-02-14
Cool, thanks for the help,

here goes...

```

davem@Dartagnon:~$ dmesg | grep ath
[   33.039685] ath_hal: module license 'Proprietary' taints kernel.
[   33.101965] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   33.634026] ath_pci: 0.9.4
davem@Dartagnon:~$ sudo modprobe ath_pci
[sudo] password for davem: 
davem@Dartagnon:~$ dmesg | grep ath
[   33.039685] ath_hal: module license 'Proprietary' taints kernel.
[   33.101965] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   33.634026] ath_pci: 0.9.4
davem@Dartagnon:~$ 

```

I decided to do the dmesg thing before and after modprobe
Which in my mind didn't help much!!

You gave me a though actually...

here is the output of the syslog for the various modules... and another iwlist, just for good measure...

```

davem@Dartagnon:~$ more /var/log/syslog | grep ath_hal
Feb 14 12:10:23 Dartagnon kernel: [  406.969126] ath_hal: driver unloaded
Feb 14 12:10:33 Dartagnon kernel: [  407.425869] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Feb 14 12:39:27 Dartagnon kernel: [  147.872402] ath_hal: module license 'Proprietary' taints kernel.
Feb 14 12:39:28 Dartagnon kernel: [  147.874903] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Feb 14 18:02:23 Dartagnon kernel: [   33.039685] ath_hal: module license 'Proprietary' taints kernel.
Feb 14 18:02:23 Dartagnon kernel: [   33.101965] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
davem@Dartagnon:~$ more /var/log/syslog | grep ath_pci
Feb 14 12:10:23 Dartagnon kernel: [  406.966754] ath_pci: driver unloaded
Feb 14 12:10:33 Dartagnon kernel: [  407.535768] ath_pci: 0.9.4
Feb 14 12:20:22 Dartagnon kernel: [  448.744511] ath_pci: driver unloaded
Feb 14 12:20:54 Dartagnon kernel: [  449.403181] ath_pci: 0.9.4
Feb 14 12:39:30 Dartagnon kernel: [  148.426184] ath_pci: 0.9.4
Feb 14 18:02:23 Dartagnon kernel: [   33.634026] ath_pci: 0.9.4
davem@Dartagnon:~$ more /var/log/syslog | grep wlan
Feb 14 12:10:23 Dartagnon kernel: [  406.968362] wlan: driver unloaded
Feb 14 12:10:33 Dartagnon kernel: [  407.511187] wlan: 0.9.4
Feb 14 12:39:30 Dartagnon kernel: [  148.401100] wlan: 0.9.4
Feb 14 18:02:23 Dartagnon kernel: [   33.294316] wlan: 0.9.4
davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

and that gave me another idea...
```

davem@Dartagnon:~$ more /var/log/syslog | grep network
Feb 14 12:37:31 Dartagnon NetworkManager: <info>  Updating allowed wireless network lists. 
Feb 14 12:37:31 Dartagnon NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): message arguments were invalid (could not deserialize wireless network security information. 
Feb 14 18:03:11 Dartagnon NetworkManager: <info>  Updating allowed wireless network lists. 
Feb 14 18:03:11 Dartagnon NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): message arguments were invalid (could not deserialize wireless network security information. 

```

so is it somehow related to this invalid argument?

Thanks for the help guys..

David

---

### Post by pytheas22 on 2009-02-14
David: it looks like ath_pci is not trying to claim your device at all.  There must have been some regression since Feisty.

It might work to compile ath_pci from source.  The easiest way to do that is to run these commands, which will run a script from [this thread]("http://ubuntuforums.org/showthread.php?t=798485"):
```

wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
sudo ./madwifi.sh
```

When the script finishes, run these commands to insert the new ath_pci module:
```

sudo rmmod ath_pci
sudo modprobe ath_pci
```

Does it claim your card now?  Does 'dmesg | grep ath' mention anything different from before?

If this doesn't help, there are other things to try...

> davem@Dartagnon:~$ more /var/log/syslog | grep network
Feb 14 12:37:31 Dartagnon NetworkManager: <info>  Updating allowed wireless network lists. 
Feb 14 12:37:31 Dartagnon NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): message arguments were invalid (could not deserialize wireless network security information. 


Unfortunately I think this is just generic NetworkManager spam.  I don't think it has anything to do with your wireless card not working--you need to have a wireless interface to bring up before NetworkManager can do anything wirelessly.

---

### Post by theDaveTheRave on 2009-02-14
Pythaes

I'm running the commands as I type...

> 
There must have been some regression since Feisty.


ERR!! bad news I'm affraid... the regression happened in Hardy, I was working like a dream since last June / July, and then it all went wrong just before christmass.... anyway back to the CLI.....

so I've run the script...

```

Found at least one Atheros device.
Checking build dependencies...
Installing subversion...Selecting previously deselected package libsvn1.
(Reading database ... 114407 files and directories currently installed.)
Unpacking libsvn1 (from .../libsvn1_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Setting up libsvn1 (1.4.6dfsg1-2ubuntu1) ...

Setting up subversion (1.4.6dfsg1-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
OK
...build dependencies OK
Fetching sources from SVN...svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname (http://svn.madwifi.org)

```

and that last line "could not resolve hostname..." doesn't sound helpfull... but I'll carry on anyhow...

so now my dmesg
```

Found at least one Atheros device.
Checking build dependencies...
Installing subversion...Selecting previously deselected package libsvn1.
(Reading database ... 114407 files and directories currently installed.)
Unpacking libsvn1 (from .../libsvn1_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Setting up libsvn1 (1.4.6dfsg1-2ubuntu1) ...

Setting up subversion (1.4.6dfsg1-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
OK
...build dependencies OK
Fetching sources from SVN...svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname (http://svn.madwifi.org)

```

and it doesn't seem to be being claimed still...

```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.120 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

```

and I can confirm there is still no change to the iwlist scan or ifconfig...

should I try a reboot?

David.

---

### Post by pytheas22 on 2009-02-14
David: I'm not sure what's going on, but I think that madwifi moved the location of its subversion repository and the script doesn't reflect that.  So the script didn't do anything.

Since the script doesn't work, let's try downloading and compiling the latest code directly from the site:
```

sudo apt-get install build-essential
wget http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz
tar -xzvf madwifi-0.9.4.tar.gz 
cd madwifi*
make
sudo make install
```

Then reboot and see if there's any change.

Sorry this is not going so smoothly, but we'll get there.
> 
ERR!! bad news I'm affraid... the regression happened in Hardy, I was working like a dream since last June / July, and then it all went wrong just before christmass.... anyway back to the CLI.....

Sorry, I was confused before.  That's bad that Hardy updates broke your wireless.  It's very embarrassing when stuff like this happens in Ubuntu, especially on LTS releases...

---

### Post by theDaveTheRave on 2009-02-14
PYhtaes

sorry I was having dinner... and it is Valentine's day also, so I can't really get away with being here too much longer, ubuntu forums don't seem to be very "romantic" :lolflag: which I find surprising #-o

I've allready been onto the original link in your other post, and taken the download from sourceforge.

I'm yet to re-boot... I'll do so after I have posted... but I get a worrying message at the end, here is the final line of code, as advised by kajasta

```

sudo ./madwifi.sh --tarball /home/davem/downloads/madwifi-0.9.4,tar.gz
./madwifi.sh: line 49: Tarball not found in /home/davem/downloads/madwifi-0.9.4,tar.gz, exiting...: No such file or directory
davem@Dartagnon:~$ sudo ./madwifi.sh --tarball /home/davem/downloads/madwifi-0.9.4.tar.gz
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version 0.9.4...OK
Removing previous MadWifi installations.FATAL: Module wlan is in use.
..OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.

```

So no compatible hardware??? reboot time I think,

back in a mo

---

### Post by theDaveTheRave on 2009-02-14
Hello again...

OK re-boot and no change,

I'm now going to perform the download as suggested by pythaes in his previous posting (message 185)..

> 
Sorry, I was confused before. That's bad that Hardy updates broke your wireless. It's very embarrassing when stuff like this happens in Ubuntu, especially on LTS releases...


you shouldn't worry about that really, my wife has an issue with her works XP laptop and printing, very weird, and I can't get a solution for it, other than change to a really old black ink only printer!


OK.. back to the install....

<make install> threw out a strange message...

```

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 

```

I guess that all the "buggering about" has caused this, so I'm going to hit 'r'.

And reboot time again... back soon

David

Edit 1;

OK i've rebooted, and still no change, lshw still shows the card is unclaimed.

do you think I should try the ath5k driver (even though I don't think I'm using a device that it was made for? how can I check?), or maybee an upgrade to Intrepid? My only issue with intrepid is... it isn't the LTS (and I wanted to stay on the version that the server at work is using as a "test bed" in case it broke).

In fact that is a thought... the version on the server should be a kernel prior to my wireless problems, would knowing that information help (although the server is on 64bit and my laptop is on 32).

David

---

### Post by pytheas22 on 2009-02-14
> OK i've rebooted, and still no change, lshw still shows the card is unclaimed.

Does 'dmesg | grep ath' say anything different?  Also, what is the output of:
```

lspci -nn | grep -i atheros
modinfo ath_pci
```
> 
do you think I should try the ath5k driver (even though I don't think I'm using a device that it was made for? how can I check?), or maybee an upgrade to Intrepid?

ath5k would probably support your card, but to know for sure you'd have to figure out your device ID, which will be given in the output of 'lspci -nn | grep -i atheros' that I ask for above.  The device ID will be in the form XXXX:XXXX.  You would then have to look at the source code for ath5k to see if it supports your device; if so, it will mention your device ID somewhere.  I'll look it up for you once we figure out the device ID, unless you want to do it yourself, in which case I'll explain how--but if you don't care, it's probably faster for me to look it up for you.  If ath5k thinks it will support your device, I can provide instructions for compiling it.

This device might also work in Intrepid, if you're willing to upgrade.  You might at least want to burn an Intrepid live CD to see if it would work.

Another thought I've had is that booting into an older kernel on your Hardy system might get your wireless working.  You should have a few different kernels to choose from at the grub boot menu, which is the menu that appears before Ubuntu starts to load (if this computer isn't a dual-boot, you may need to press 'escape' right after BIOS finishes in order to get into grub).  The newest kernel is at the top of the list.  You might want to try booting into an older once, where you wireless may work better, since it was probably under an older kernel that things were working smoothly until an update broke them.

Anyway I suppose you won't be up much longer if you're in France, but I'll keep checking back for your replies whenever you can make them.

---

### Post by theDaveTheRave on 2009-02-14
Pythaes...

hers the infor

```

davem@Dartagnon:~$ lspci -nn | grep -i atheros
0a:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

```

so now I understand a little more why you needed that....

> 
ath5k would probably support your card, but to know for sure you'd have to figure out your device ID, which will be given in the output of 'lspci -nn | grep -i atheros' that I ask for above.


so you are very kind

> I'll look it up for you once we figure out the device ID

Most cool in fact, to be honest it would be good to know where to find the info, just in case I need it again in the future... but then I guess there is this thread..:)

Do you get multiple kernels on a standard install?? as I re-installed in the week thinking that it may solve my proble, but then realised they must have updated the live CD (I grabbed a new version in the end as I had given the old disk to a friend in Lyon...).

I've just checked my <boot/grub/menu.list> and I only have the 2.6.24-23 kernel (normal and recovery), I think I'm buggered!

It seems we are going to have to keep trying at this one for now.. maybee I'll upgrade to intrepid tomorrow if we are really unable to get things working!

David

Edit:

I've gone for a hunt on the linux wireless homepage, and my card (AR2413) is listed on the compatibility page for ath5k... so I figured, why not, and I'm downloading and installing as I type... Whats the worst that can happen?? Maybe I could loose my wireless connectivity... OH, I allready have, that why I'm here... OK must have been too much wine for dinner!

---

### Post by pytheas22 on 2009-02-14
> Do you get multiple kernels on a standard install?? as I re-installed in the week thinking that it may solve my proble, but then realised they must have updated the live CD (I grabbed a new version in the end as I had given the old disk to a friend in Lyon...).

Didn't realize/remember that this was a fresh install of Hardy using the updated ISO--that explains why you have no older kernels.  Unfortunately, I don't know of a way to get an older kernel.

> I've gone for a hunt on the linux wireless homepage, and my card (AR2413) is listed on the compatibility page for ath5k... so I figured, why not, and I'm downloading and installing as I type... Whats the worst that can happen?? Maybe I could loose my wireless connectivity... OH, I allready have, that why I'm here... OK must have been too much wine for dinner!

You can't always trust that information as much as you can the source code, but if they say it works, it probably will.  And in any case, as you note, there's nothing to lose!  So hopefully this will do the trick.  If you need help compiling the compat-wireless stack, let me know.

EDIT: the source code does say that ath5k supports your device.  You can tell by looking at the file drivers/net/wireless/ath5k/base.c inside the compat-wireless directory.  Line 97 (at least in the copy of the source that I have) reads:

```
{ PCI_VDEVICE(ATHEROS, 0x**001a**), .driver_data = AR5K_AR5212 }, /* 2413 Griffin-lite */
```

Your device ID is 168c:001a.  The first part (168c) is the Atheros vendor identifier--all Atheros wireless cards begin with this number (it's already been defined somewhere else in the source code).  The second part (001a) defines your particular model of Atheros card, and is the part that really matters.  You can see in the line above that it says it's supported.  So that's good.

Most people should never need to know this stuff, but it can be useful once in a while.  In some cases, editing the source code to say that it supports a particular device is all it takes to make it actually work (I'm wondering if editing the madwifi source that you unsuccessfully tried earlier today would have made it recognize your device).  But you should be careful doing that because you could damage your card if you try to force it to use a driver that's not meant for it.

---

### Post by theDaveTheRave on 2009-02-14
Pythaes (and whoever else is following this)

I've downloaded and seem to have had some small success with the ath5k driver, folowing the instruction on the ath5k home page [here]("http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers"). As I say this seems to have given a small improvement, here are the code return values.... the iwlist and lshw are seemingly hopefull

```


davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

davem@Dartagnon:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.120 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
davem@Dartagnon:~$ 

```

however I guess because the interface is still "DISABLED" I'm still getting nothing in ifconfig

```

davem@Dartagnon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2144558 (2.0 MB)  TX bytes:291861 (285.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70900 (69.2 KB)  TX bytes:70900 (69.2 KB)

davem@Dartagnon:~$

```

so now all i need is a method to "enable" my card and i should be away.... I'm off to celebrate with some sleep, in the morning (if you are able to help with the enabling bit) I will add full details of what I have done.

big thanks are due so far.

untill tomorrow all...

David

---

### Post by pytheas22 on 2009-02-14
Yes, that's definitely good that the card is no longer unclaimed.

Usually the 'disabled' bit means that you have the card turned off via a physical switch.  Is there a button on your computer that you use to enable and disable the wireless?  If so, try flipping it.

If that doesn't help, try typing:
```

sudo ifconfig wlan0 up
```

That may take care of it.

If not, hopefully dmesg will explain what's wrong.  What is the output of:
```

dmesg | grep -i -e radio -e wlan -e ath
```

---

### Post by kevdog on 2009-02-14
I'm confused.  I thought ath5k was in the linux-backports repository.  Maybe its not for Hardy.  This whole mess proves what I suspected for a long time.  The Feisty kernel had a bunch of things right with it.  Beginning with Gutsy and then Hardy a bunch of wireless drivers went afoul along with old video drivers.  The Feisty kernel was good!!  Anyway just as an aside, MasterKernel is currently writing code that will make it possible not only to upgrade to any kernel, but also downgrade to any kernel in the past (I requested this feature).  I'm looking forward to going back to the past in the future!

---

### Post by theDaveTheRave on 2009-02-14
OK

This really is my last post before getting some sleep  :sad:

So I suddenly decided to hunt for enable NIC and this lead me to do the following...

```

davem@Dartagnon:~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

which seems hopefull as it is finding the harware (even if it is unknown), but what is this about a pid file allready existing??

so anyway, now with lshw i get this

```

davem@Dartagnon:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.120 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

so I think to myself...

```

davem@Dartagnon:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
davem@Dartagnon:~$ sudo ifup wmaster0
Ignoring unknown interface wmaster0=wmaster0.

```

so then I had another quick look here, and I've done pythaes' suggestions.

```

davem@Dartagnon:~$ sudo ifconfig wlan0 up
davem@Dartagnon:~$ dmesg | grep -i -e radio -e wlan -e ath
[   32.868772] ath5k_pci 0000:0a:03.0: registered as 'phy0'
[   33.343998] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   46.838314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  260.571069] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  296.097684] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  296.160032] ADDRCONF(NETDEV_UP): wlan0: link is not ready
davem@Dartagnon:~$ 

```

so then I think to myself, I could try the wmaster0 also, but that is the same, as they are symbolic links to one another I guess...

but then how about my more normal bringing up / down of interfaces..

```

davem@Dartagnon:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
davem@Dartagnon:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
davem@Dartagnon:~$ sudo ifup wmaster0
Ignoring unknown interface wmaster0=wmaster0.
davem@Dartagnon:~$ sudo ifdown wmaster0
ifdown: interface wmaster0 not configured
davem@Dartagnon:~$ 
```

so how can the interface be both not configured and unknown at the same time, and still no change to the result of a scan

```

davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

I feel we are really close... but I'm desperate fro some sleep.... the wife and the dog are already snoring happily :lolflag: and I think I will join them...

Maybe the reboot will make things work.. I'll report bak in the morning.

David

---

### Post by pytheas22 on 2009-02-15
Please reboot, then post the output of these commands, in this order:
```

ifconfig
sudo ifconfig wmaster0 up
sudo ifconfig wlan0 up
ifconfig
sudo iwlist scan
dmesg | tail -50
dmesg | grep -e ath -e wlan
```

According to [this thread]("http://forum.ubuntu-fr.org/viewtopic.php?id=274385") (which deals with ath5k on the same exact wireless card), 'ifup wlan0' doesn't do the same thing as 'ifconfig wlan0 up'.  I think you'll have better luck using ifconfig to bring the interface up.

> 
which seems hopefull as it is finding the harware (even if it is unknown), but what is this about a pid file allready existing??

Don't worry about this; it doesn't mean anything important.  dhclient won't work until you have an interface up and active.

> 
so then I think to myself, I could try the wmaster0 also, but that is the same, as they are symbolic links to one another I guess...

wlan0 is a 'virtual' interface based on 'wmaster0'.  This means that you don't actually manipulate wmaster0; you work with wlan0.  This is the new way that Linux does wireless, since it permits much more flexibility.  (Incidentally, the implementation of this feature and other major changes in Linux wireless is the reason that it's been such a mess over the last year, as kevdog wrote above.  Most drivers are being completely rewritten--this is why ath_pci is being replaced by ath5k/ath9k, for example.  When the new drivers are finished, Linux will have much more innovative wireless capabilities, but for the time being there are bugs like the one affecting you.)

Anyway it's bedtime on the east coast, but I'll be back tomorrow and hope your problem is sorted out by then!

---

### Post by theDaveTheRave on 2009-02-15
pytheas

So i'm back online, before I read this thread I had allready done most of the commands you had suggested, but not in your order...

so I'll do it again in the order you suggest, but first off, here is the result of my first iwlist and ifconfig..

```

davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

davem@Dartagnon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:374 (374.0 B)  TX bytes:2356 (2.3 KB)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:169.254.8.62  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71016 (69.3 KB)  TX bytes:71016 (69.3 KB)

```

so now onto your stuff..

```

davem@Dartagnon:~$ sudo ifconfig wmaster0 up
[sudo] password for davem: 
SIOCSIFFLAGS: Operation not supported
davem@Dartagnon:~$ sudo ifconfig wlan0 up
davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

I've seen this <SIOCSIFFLAGS: Operation not supported> when I've had problems previously, I found then the solution was to re-install the drivers etc... normally it was post update, and I would 3 or 4 drivers selected (when looking in synaptic), so I would make a note of the most up to dat (which would match with uname -r) and remove all of them, reboot and then re-install the most recent one... I don't know if this will work in this instance, but I could try it?

the ifconfig is now different to at boot time...

```

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2974 (2.9 KB)  TX bytes:6942 (6.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71016 (69.3 KB)  TX bytes:71016 (69.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:40:b8:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7D-40-B8-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I seem to have lost the ath0:avahi entry? I don't feel that this is anything to worry too much about, as I'm still hooked into the net via the ethernet card...

but still no scan results..

```

davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

I hope this will help, right now I'm a bit lost,

here is the dmesg stuff...

```

davem@Dartagnon:~$ dmesg | tail 50
tail: cannot open `50' for reading: No such file or directory
davem@Dartagnon:~$ dmesg | tail -50
[   34.786720] acer_acpi: Detected Acer WMID interface
[   34.848550] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   34.890775] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   34.905895] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   35.886680] sky2 eth0: enabling interface
[   36.383393] cs: IO port probe 0x100-0x3af: clean.
[   36.385439] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   36.386291] cs: IO port probe 0x820-0x8ff: clean.
[   36.386994] cs: IO port probe 0xc00-0xcf7: clean.
[   36.387876] cs: IO port probe 0xa00-0xaff: clean.
[   36.550307] lp: driver loaded but no devices found
[   36.794027] Adding 979924k swap on /dev/sda7.  Priority:-1 extents:1 across:979924k
[   36.827196] EXT3 FS on sda8, internal journal
[   37.026056] NET: Registered protocol family 17
[   37.107966] ReiserFS: sda9: found reiserfs format "3.6" with standard journal
[   37.107981] ReiserFS: sda9: using ordered data mode
[   37.117192] ReiserFS: sda9: journal params: device sda9, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   37.117619] ReiserFS: sda9: checking transaction log (sda9)
[   37.131437] ReiserFS: sda9: Using r5 hash to sort names
[   37.165031] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   37.165053] ReiserFS: sda5: using ordered data mode
[   37.171551] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   37.172043] ReiserFS: sda5: checking transaction log (sda5)
[   37.218118] ReiserFS: sda5: Using r5 hash to sort names
[   37.919082] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.371631] ACPI: ACPI Dock Station Driver 
[   41.544853] apm: BIOS not found.
[   41.744146] ppdev: user-space parallel port driver
[   41.832329] audit(1234684306.457:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5079 profile="/usr/sbin/cupsd" namespace="default"
[   45.314619] Bluetooth: Core ver 2.11
[   45.315297] NET: Registered protocol family 31
[   45.315302] Bluetooth: HCI device and connection manager initialized
[   45.315307] Bluetooth: HCI socket layer initialized
[   45.337462] Bluetooth: L2CAP ver 2.9
[   45.337467] Bluetooth: L2CAP socket layer initialized
[   45.406801] Bluetooth: RFCOMM socket layer initialized
[   45.406819] Bluetooth: RFCOMM TTY layer initialized
[   45.406822] Bluetooth: RFCOMM ver 1.8
[   48.358737] NET: Registered protocol family 10
[   48.359208] lo: Disabled Privacy Extensions
[   48.359759] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.360342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.542246] [drm] Initialized drm 1.1.0 20060810
[   48.697305] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.697316] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.697401] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   58.958226] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   58.958711] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   59.733834] eth0: no IPv6 routers present
[  136.321191] ADDRCONF(NETDEV_UP): wlan0: link is not ready
davem@Dartagnon:~$ dmesg | grep -e ath -e wlan
[   34.526025] ath5k_pci 0000:0a:03.0: registered as 'phy0'
[   34.890775] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   48.360342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  136.321191] ADDRCONF(NETDEV_UP): wlan0: link is not ready
davem@Dartagnon:~$ 

```

looking at this the the chip is definately being found, but also in the dmseg tail -50 the ath0 link is not ready, the part that I think is interesting (or relevant) is here
```

[   48.359759] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.360342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.542246] [drm] Initialized drm 1.1.0 20060810
[   48.697305] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.697316] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.697401] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   58.958226] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   58.958711] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   59.733834] eth0: no IPv6 routers present
[  136.321191] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

do I need to get the wlan0 to be initialised via the sky2 thing?

well I guess you guys will understand it better than me!

David

Edit:

OK I just found an on file with help stuff in it relating to networking (static IP), and I happen to do a <name -a>, I know at this time my wifi worked beautifully...

in this instance (from 3 or 4 months ago) it says my kernel is....
> 
Linux Dartagnan 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux


so definately different to my current kernel

```

davem@Dartagnon:~$ uname -a
Linux Dartagnon 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux
davem@Dartagnon:~$ 

```

What did they do to break it!

Oh and I've got a question for you.... where do you learn all this stuff ?

---

### Post by kevdog on 2009-02-15
How did you install the ath5k driver?  I know of many success stories of people using Intrepid along with ath5k to get the wireless working.  The kernel version you are using is quite old -- however I suspect that is because you are using Hardy.  For example with Intrepid, I have a kernel version of 2.6.27-11-generic.  The only other solution I can offer for you, since it looks like ath5k is not going to work for you, is to use a patched version of the madwifi sources as described here:
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

The actual repository for the drivers is here:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

Ive seen reports working for the 3938 build.

Again I'm not saying this is going to work. 

Im going to guess overall its your old kernel which is the conflict here.  The ath5k page mentions something about 2.6.25 or higher:
[http://wireless.kernel.org/en/users/Drivers/ath5k#supportedchips](http://wireless.kernel.org/en/users/Drivers/ath5k#supportedchips)

---

### Post by theDaveTheRave on 2009-02-15
Kevdog and pytheas

So it looks like I should update to intrepid then.

I'm still a bit miffed to have to do that, especially after my previous experience!

Oh well, with a bit of luck it will work out OK this time, I've definately heard that it has improved in the last few months...

Oh well... here goes...

David.

---

### Post by kevdog on 2009-02-15
You will like Intrepid :)

---

### Post by pytheas22 on 2009-02-15
> seem to have lost the ath0:avahi entry? I don't feel that this is anything to worry too much about, as I'm still hooked into the net via the ethernet card...

Don't worry about this.  It happens because the ath_pci driver names devices ath*, while ath5k names them wlan*.  This just represents different naming conventions.
> 
looking at this the the chip is definately being found, but also in the dmseg tail -50 the ath0 link is not ready, the part that I think is interesting (or relevant) is here

I'm still wondering if the radio in the card is turned off.  Do you have a button or a key-combination (like function+F2) on your laptop to enable the radio?  If so, try toggling it, then see if 'sudo iwlist scan' gives you any results.  This is the only thing I can think of, because everything else looks like it should be working now.
> 
So it looks like I should update to intrepid then.

You should at least burn the live CD and give it a try.  If things work there, I'd definitely upgrade.  If the wireless doesn't work in the live environment at first, try running these commands to switch from the ath_pci driver (which is still the default in Intrepid) to ath5k:
```

sudo apt-get install linux-backports-modules-intrepid
sudo rmmod ath_pci
sudo rmmod ath5k
sudo modprobe ath5k
sudo ifconfig wlan0 up
sudo iwlist scan
```

If the last command shows you a list of networks, then things will work in Intrepid.
> 
Im going to guess overall its your old kernel which is the conflict here. The ath5k page mentions something about 2.6.25 or higher:
[http://wireless.kernel.org/en/users/...supportedchips](http://wireless.kernel.org/en/users/...supportedchips)

As I understand it, ath5k will work on older kernels; you just need to install it yourself using the compat-wireless-old source code from linuxwireless.org.  I think that web page you linked to mentions 2.6.25 because ath5k is included by default in the wireless stack of generic 2.6.25 and higher kernels...but Ubuntu's version of the kernel for both Hardy and Intrepid has ath5k removed.
> 
Oh and I've got a question for you.... where do you learn all this stuff ? 

For me, by spending a lot of time on the forums trying to figure out other people's problems :)

---

### Post by kevdog on 2009-02-15
pytheas


I'm definitely no ath5k expert -- I have a much older atheros card which is supported by madwifi, not ath5k.  But my understanding is that with older kernels you need to compile the kernel after patching in the source.  Its not that this process is difficult, its just that it opens up a whole can of worms with kernel compilation.

---

### Post by theDaveTheRave on 2009-02-16
Hi guys.

so I've upgraded to Intrepid, which went rather nicely in fact.

However I got to work this morning and I have no networking activity at all! which seems strange, as post upgrade I got lots of updates etc via my home ethernet link.

I'm entering this via my works desktop....

so here is something interesting....

I can ping my laptop, and I can do a port scan (showing that port 80 is open). but I can't surf the web or ping any other terminals (the exception being the DHCP server, default route router.

I need to get the ethernet interface going again at a bare minimum, I think upgrading was a bit premature! but i've never had networking through the eth0 interface stop working before!

And of course I can't get any update or do your suggested <apt-get> stuff as I can't get a network connection!

so this is what I have on Intrepid.

I now have a <network connections> GUI that give me all sorts of options, that I have tried to play around with, using the information for my old settings, which are in a file I saved!

so my /var/lib/dhcp3/dhclient.eth0.leases file has nothing relating to my current ip address (which seems strange to me, I expected it to have at least something in there!)

I adjusted my /etc/network/interfaces file, to have the info for my staticIP and stuff (the same as the old), so why is the dhclient.eth0.leases file not getting the new info from the server?

so I've now deleted the entries in the files and I'm rebooting, to see if there is a change at all....and i'm connected... and it is with the correct static IP?? and i've got results from an iwlist scan!!

WOW... but what did i do...?? Oh I did log onto the OLD kernel from before so not the current Intrepid kernel my old 2.6.24-23 generic kernel?

However, quick network settings query....

in the network connections dialog, on the first tab <Wired> I have a connection called <ZeroConfig> which is an old config from Hardy I had set up (basically all on DHCP).

How can I check if it is on Dynamic or Static??

And on the same line is say "never", what does this mean??

Ok I've just found something... very strange....

I have a button on the front of my pc for turning the wifi on / off... This has never worked before on any version of ubuntu (or at least not that it made any difference to the return value of an <iwlist scan>

Now I've got some very "enhanced" activity....

At start up I got 21 wireles access points, if I side the switch (once), I just get one, slide it one more time and I get none!

then slide it multiple times in succesion... and I get 23 wireless access points!

I'm yet to work out what the "sliding order" is - ie slide and hold, slide 3 or 4 time, or lots of times?? but I do eventually get them all back!

Even more interesting.... I can pull up just the master access points or all of them!

How very interesting, but how do I find out what I'm supposed to do to the button!?

Well for now though, I don't really care, as it seems I should be able to connect back up to the network! thank god....

I'll try going into the "new" kernel later on today, I'll report how it works.

My only question now is, am I on static....

So I've done a <sudo ifconfig eth0 down> which brought down my interface, and then a <sudo ifconfig eth0 up> which brought it back up... and guess what... I'm on a different IP - so I must be on dynamic, right!?

And I'm completely lost with this button thing! I bet that was what my problem was all along!!!  ](*,)

I'm going to try bringing dowm my interface, setting a static, and then brining it back up again....

David

Edit 1, StaticIP seems to work OK, I added a new connection, selcted <connect automatically> and <system setting> in the edit dialog, and turned of both for the <ZeroConfig> option.

I then brought down the interface (via the little applet in the menu / system tray, brought is back up afterwards... and hey presto... great stuff....

However... I have just checked the 2 options, and they both have the <connect automatically> and the <system setting> selected?? does this mean that NetworkManager will now select the most appropriate option from my list!? if so that it a vast improvement compared to when I was persistently having to change them over!

Edit 2.

Ok so i've just done a reboot, as i wanted to be sure it worked, but now into the new kernel....

so I've can ping everwhere on my local network, up to the server, but can't surf / ping the web!?

any ideas gents?? or is it releated to the stuff that I installed yesterday regarding the ath5k???

I'm not going to mess around for now, I'm going to use the old kernel, as I can network (which I need... sort of?).

I've gone back to the old kernel, and guess what. its still buggered, I don't get it it worked jut now! the issue here is that I need staticIP for my DBase connections!

Dave

Edit 3:

Ok I can get connected if I use staticIP on my ethernet connetion and hand edit the </etc/network/interfaces> file.

for now that is not a problem.... but I would like to be able to have my locations in the applet to choose between them, if that is possible.

also I can't really play around much more until I get home tonight, when i can add in a wireless network, and see if I can use both. Then we can start the fun and games again at the weekend.... although the StaticIP stuff is required for work, as I say I'm happy to edit my interfaces file... and write a script is neccesary to make it work properly....

David

---

### Post by kevdog on 2009-02-16
Can you be a little bit more clear in what you want to do?  I'm glad things are working for you.

---

### Post by theDaveTheRave on 2009-02-16
Kevdog

Appologies for the lack of clarity.

OK I think you understand my situation, but by way of a quick re-cap.

I'm still not sure if wireless is working, will check tonight.

Ethernet is functioning, but not how I want!

Currently to be able to surf the web I have to set a static IP directly in my </etc/network/interfaces> file.

Otherwise I can ping (and be pinged) by other terminals in my local network. But I can't ping outside of my DHCP name server. Or I use network manager to set the IP to a static value, and I get the same result of not being able to ping other machines, but they can ping me!

kernel.

I know that the new version of the kernel on the Intrepid is 2.6.27.11 (I've taken it from the GRUB list), however I have no connectivity at all using this kernel.
If I use the old Hardy kernel (2.6.24-23) I have everything, including wifi. so for now I am logging into that kernel to work. I'm going to re-load the ath5k driver tonight to see if that gets the new kernel working.

Button on front of machine.

this suddenly works (never did anythin prior to Hardy) and may have been why I was having problems over the weekend - as i hadn't noticed that it was working untill Pytheas suggesting pressing it! My question here is how does it work - That may seem like a silly question but bear with me here...

At boot - I see all network access points
Press once -  I now only see the "master" access points
Press again - I only see the one most local to me - ie strongest signal

Trying to get them all back again I haven't been able to work out what I need to do! press / Hold, press multiple times ?? any clues!? The good news is however that is does work!


Otherwise...

Interpid seems more slick that it did when I tried it last September / October. Fewer "slow downs" and stuff. I'm not sure I appreciate the new network manager, but I guess it is just a matter of what you learn to use - to be honest I didn't like the old one much either, at least the new one seems to have more functionality, it is just a matter of learning how to use it!

for now I can only offer both you an pytheas large quantities of gratitude for helping out as much as you did... Although the hop up to Intrepid may have been all I needed, I have learnt an awfull lot about compiling from source and general modules and stuff over the weekend. I feel a little more "guru'd" up than this time last week.

So thanks to you both.

David

---

### Post by kevdog on 2009-02-16
I know Im not answering your question, however I'll take a stab at some off the cuff comments.  The ath5k driver is a custom kernel module -- meaning its not included in the default kernel (yet!!).  That means for every new kernel you try -- you need to reinstall the driver.  Hence probably the reason why the 2.6.27-11 kernel has no embedded ath5k driver.  You'll need to boot into this kernel and install the kernel module.

Wireless switch on front of your box??? I have no clue.  Seems like it isnt a big deal to me, however I can see its giving you fits.

If you can not ping outside the local LAN -- its either a route problem (ie gateway not specified) or dhcp problem.  route -n lists your UG or universal gateway.  I used to know exactly, but I believe off memory the dhcp server addresses are either manually specified for manual configuration or located in /etc/dhcp/dhcp3.conf (something like that) for dhcp configuration.

---

### Post by pytheas22 on 2009-02-16
> Currently to be able to surf the web I have to set a static IP directly in my </etc/network/interfaces> file.

Otherwise I can ping (and be pinged) by other terminals in my local network. But I can't ping outside of my DHCP name server. Or I use network manager to set the IP to a static value, and I get the same result of not being able to ping other machines, but they can ping me!


I agree with kevdog that this is probably a routing and/or DNS problem.  I suspect that for some reason, when you acquire a dynamic IP address from your dhcp server, Ubuntu doesn't get told what the gateway and/or DNS servers are--but if you configure it all manually with a static IP, of course, you don't run into this problem.  This could just be a peculiarity with your dhcp at work, and wouldn't occur with other networks.  If it does occur with other networks, let us know. 

> I know that the new version of the kernel on the Intrepid is 2.6.27.11 (I've taken it from the GRUB list), however I have no connectivity at all using this kernel.
If I use the old Hardy kernel (2.6.24-23) I have everything, including wifi. so for now I am logging into that kernel to work. I'm going to re-load the ath5k driver tonight to see if that gets the new kernel working.


On the 2.6.27-11 kernel, your ethernet works if you set a static IP, correct?  If so, then I suspect, as explained in the paragraph above, that this is just a weird peculiarity with your network at work, and that you wouldn't run into this problem at home.  But I could be wrong; if so, let us know.

You will need, as kevdog explains, to install the ath5k driver for your 2.6.27-11 kernel in order to get wifi working there.  You could do that by compiling from source as you did before, or you could simply run the command:
```

sudo apt-get install linux-backports-modules-intrepid
```

The linux-backports-modules-intrepid package includes the ath5k driver.

> 
this suddenly works (never did anythin prior to Hardy) and may have been why I was having problems over the weekend - as i hadn't noticed that it was working untill Pytheas suggesting pressing it! My question here is how does it work - That may seem like a silly question but bear with me here...

At boot - I see all network access points
Press once - I now only see the "master" access points
Press again - I only see the one most local to me - ie strongest signal

That's a bit puzzling.  I would expect the button to either turn your wireless on or turn it off completely, but it sounds like it modifies the strength of the radio signal instead.  You could check the output of 'dmesg'; it should mention something when you press the button, and will hopefully provide more information about what exactly the button is doing.

> 
Interpid seems more slick that it did when I tried it last September / October. Fewer "slow downs" and stuff. I'm not sure I appreciate the new network manager, but I guess it is just a matter of what you learn to use - to be honest I didn't like the old one much either, at least the new one seems to have more functionality, it is just a matter of learning how to use it!

I think the new NM actually is a lot better, but in general I've never been a big fan of NM either.  If you want to try an alternate connection manager, look into [wicd]("http://wicd.sourceforge.net").  It doesn't have all of the features that NM has acquired recently (no wizards for configuring WPA-enterprise connections for example), but if you don't need those things and want a more straight-forward utility, wicd might be it.

Anyway, we can continue with this when you get more time to play with it.

---

### Post by theDaveTheRave on 2009-02-17
Hi guys,

quick update.

So at home last night, boot into new kernel and <iwlist scan> is there (I'm begining to think this may also have been a "switch" thing also?)

OK some odd stuff...

Network manager certainly seems to ignore the /etc/network/interfaces file, and certainly demands more info than the old one did.

for instance, I now have to get the domain name server IP address correct (to allow my static IP to work in ubuntu), and I have to tell it what my "domain" is - i just used local!

I'm happy because everything now seems to be working.

just a quick network question though.

how do I determine my domain name server - this isn't an issue for me at the moment as I can grab it from another terminal (it sits in the dhclient.eth0.leases file on the other terminal), but I don't know how I would determine this if I hadn't had another Ubuntu machine?

As I say I could ping and view all the terminals in the team, and even the various subnetworks domains. But couldn't get to the internet untill I had the correct domain name server details. I've checked all the things i can think of eg ifconfig, the dhclient.eth0.leases, but had no joy to find the other server until I checked the first log on dhclient.eth0.leases file from the other ubuntu terminal... and my latop (even though it grabbed a dynamic address) didn't have the same details in it?

Could a potential solution have been this.

Delete the dhclient.eth0.leases file,

bring down the ethernet interface, then bring it back up again (in dynamic mode) and see what the interfaces file says?

I may try it now in fact.

David

Edit.

Ok i tried that.

I deleted the contents of /var/lib/dhcp3/dhclient.eth0.leases (don't worry i saved them elsewhere!).

I logged off.

I changed the name of my current connection, and then created a new "blank" connection (I called this ZeroConfigETH0). The Details are the bare minimum I can think it needs.

I brought the interface back up (into the new ZeroConfigETH0 network location).

NO JOY - no internet?

also there was stilll no /var/lib/dhcp3/dhclient.eth0.leases file? I thought that this file was automatically created by the system when it received the required information from the network.

I went back and re-selected the "Office" location and everything worked fine?

I'm going to test again on the ZeroConfigETH0 when I get home tonight.

David

---

### Post by pytheas22 on 2009-02-17
> how do I determine my domain name server - this isn't an issue for me at the moment as I can grab it from another terminal (it sits in the dhclient.eth0.leases file on the other terminal), but I don't know how I would determine this if I hadn't had another Ubuntu machine?


In most cases, on a local network your DNS server will be the same as your gateway (i.e., your router).  Your ISP must have a DNS server as well (which is actually what your router uses to resolve DNS requests), and you should be able to find its IP address in your router's configuration page, or you could call your ISP and ask.

There are also free public DNS servers that should work in any situation; [here's a list]("http://www.tech-faq.com/public-dns-servers.shtml").
> 
I changed the name of my current connection, and then created a new "blank" connection (I called this ZeroConfigETH0). The Details are the bare minimum I can think it needs.

I brought the interface back up (into the new ZeroConfigETH0 network location).

NO JOY - no internet?

Which details did you specify in the file?  And are you sure the syntax was correct?  Could you post the file here?

Also, I'm not sure, but wouldn't your /var/lib/dhcp3/dhclient.eth0.leases file apply only to dynamic IPs, not static ones?  You've been using only static IPs since upgrading to Intrepid, correct?

---

### Post by theDaveTheRave on 2009-02-18
Hi guys,

by way of an update and to answer some of the questions....

Firstly - wirelessly logged into my home network and posting this from that location - so wireless is working on my Intrepid.

Thanks for the list of DNS servers and stuff... I'm going to keep a hold of that one, I haven't looked yet but will soon.

My situation where I work is that I need to have a static IP.

HOWEVER, and this is were things are rather strange.

When I first get to work the wireless will default to an auto IP retreival (DHCP), and I have to switch it too my static setup.

This isn't really an issue, but leads to a rather odd instance, which I have described above but will again here for good measure.

when I'm on the DHCP all the settings in network manager are blank - I've included a screenshot of the IP settings page with a view of all three setups, so you can see the different setings.

Now when I am connected through either the <Auto eth0> (which appeared automatically from network manager when I got to work this morning), or if I connect via the <ZeroConfEth0> setup (which I created the other day) I am unable to reach the internet (ie I can ping everyone, everyone can ping me ~ eg the DNS servers in the setup for MyologyOffice, but I can't ping external locations such as [www.google.com)-](www.google.com)-) I can however reach all the other terminals and servers at work. BUT I can't determine where my IP address came from.

If when using these configs I run a <ifconfig> I will get details of the network mask and default gateway that match those in the <MyologyOffice> setting. But I still have no entries in my dhclient.eth0.leases file.

However if I switch over to the <MyologyOffice> setting everything works just fine.

So, if I understand correctly what pytheas 
> 
In most cases, on a local network your DNS server will be the same as your gateway (i.e., your router).
I would guess that I am being given an IP address from a server that doesn't have a route to the outside world. I do know that I am plugged into a router box at the other end of the office (this has notoriously bad connections that keep failing, and I have followed my network cable to the box). If I do a traceroute to any other IP address it allways seems to pass through the gateway addres (134.157.195.126) which I assume is the router?

I've tried playing with nmap using the various IP addresses as targets, but my knowledge isn't great on this tool, I guess however that I can use it to find out where my IP address came from (by looking for the pertinent port - quick reading this [link]("http://linuxgazette.net/issue50/tag/1.html") says its via UDP port 53 I've tagged this page too!).

So I hope that explains things!?

I'm about to do another test though...

I'm going to connect on my home network through the ethernet port via both of the "dynamic" setups, to see what (if anything) happens...

back soon...


David

Edit: now connected and posting via Auto eth0

report from various commands...

```

davem@Dartagnon:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0

auto pan0
davem@Dartagnon:~$ more /etc/hosts
127.0.0.1 localhost
127.0.1.1 Dartagnon


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
davem@Dartagnon:~$ more /etc/resolv.conf
# Generated by NetworkManager
domain darty
search darty
nameserver 192.168.1.254
davem@Dartagnon:~$ more /etc/dhcp3/dhclient.eth0.leases
/etc/dhcp3/dhclient.eth0.leases: No such file or directory
davem@Dartagnon:~$ 

```

I'm guessing the important stuff is the </etc/resolv.conf> file, but how does this renew when I change to a different location?? I actually thought that this was the job of the dhcpclient ? (and looking at the dhclient.conf file it certainly seems to demand a server name.

Anyway I'm going to hit save then move over to the <ZeroConfigEth0> connection that I created to test that one also.... back soon....

EDIT 2; same stuff from the <ZeroConfigEth0> setings, which I am posting from as we speak...

> davem@Dartagnon:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0

auto pan0
davem@Dartagnon:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
davem@Dartagnon:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0

auto pan0
davem@Dartagnon:~$  more /etc/hosts
127.0.0.1 localhost
127.0.1.1 Dartagnon


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
davem@Dartagnon:~$ more /etc/resolv.conf
# Generated by NetworkManager
domain darty
search darty
nameserver 192.168.1.254
davem@Dartagnon:~$ more /etc/dhcp3/dhclient.eth0.leases
/etc/dhcp3/dhclient.eth0.leases: No such file or directory
davem@Dartagnon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1064454 (1.0 MB)  TX bytes:175559 (175.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

davem@Dartagnon:~$ 


Tomorrow morning I will post the same output from my work location... just for good measure!

---

### Post by pytheas22 on 2009-02-18
If I understand everything correctly, it sounds like what's happening is that when you get to work, NetworkManager auto-connects you to the first connection available, which for some reason doesn't work.  I'm guessing that this has to do some DNS problem--if you can ping 74.125.45.100 (Google's IP address) but not 'google.com', then this is the issue.  If you can't ping either, then you must have no route to the outside world, but I think the first scenario is more likely.

If it's a DNS problem, you could resolve it simply by editing your /etc/resolv.conf file to specify one of the free DNS servers that I linked to, rather than the one that gets auto-assigned to you (which seems to have the address 192.168.1.254--do you know which machine that is at your work?).

I'm not sure why you would be assigned an incorrect DNS server at work, but it could be a misconfiguration of your work's network, or a bug in Network Manager.  I had a similar situation once where a certain dhcp server kept giving incorrect DNS and routing information to a Fedora machine, because of some weird disagreement between the two computers.

Anyway, if you post your settings at home, that might help to clarify things more.

---

### Post by theDaveTheRave on 2009-02-19
> **pytheas22 said:**
> If I understand everything correctly, it sounds like what's happening is that when you get to work, NetworkManager auto-connects you to the first connection available, which for some reason doesn't work. 

exactly

> if you can ping 74.125.45.100 (Google's IP address) but not 'google.com', then this is the issue.
there is an idea, I'll try it on my arrival

> 
If it's a DNS problem, you could resolve it simply by editing your /etc/resolv.conf file to specify one of the free DNS servers that I linked to, rather than the one that gets auto-assigned to you 

OK i'll try that so see if it works...

> 
the DNS server seems to have the address 192.168.1.254--do you know which machine that is at your work?).

This isn't my work machine it is the wireless hook / router at home!


>   I had a similar situation once where a certain dhcp server kept giving incorrect DNS and routing information to a Fedora machine, because of some weird disagreement between the two computers.

There is an oddity with the network mask, that I really don't understand, The ubutu terminal (there are 3 of them) all have a network mask of 255.255.255.128 compared to the more "normal" that you get on all the windows and MACs of 255.255.255.0

> 
Anyway, if you post your settings at home, that might help to clarify things more.
In fact all the setting for the auto and ZeroConfig match with what works when I'm at home. And it doesn't change (appart from the IP) when I get to work...


David

---

### Post by pytheas22 on 2009-02-19
> There is an oddity with the network mask, that I really don't understand, The ubutu terminal (there are 3 of them) all have a network mask of 255.255.255.128 compared to the more "normal" that you get on all the windows and MACs of 255.255.255.0


That's strange.  What happens if you change the netmask by typing:
```

sudo ifconfig eth0 netmask 255.255.255.0
```

(you may need to replace 'eth0' with 'wlan0' if this is on the wireless interface.)

Also let us know what happens when you try to ping 'google.com' vs. 74.125.67.100.

---

### Post by theDaveTheRave on 2009-02-20
Pytheas

Sorry I wasn't able to investigate this yesterday... so I did it this morning...

> 
I'm guessing that this has to do some DNS problem--if you can ping 74.125.45.100 (Google's IP address) but not 'google.com', then this is the issue


So I just tried this, and guess what...

```

davem@Dartagnon:~$ ping 74.125.45.100 
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=237 time=108 ms
64 bytes from 74.125.45.100: icmp_seq=2 ttl=237 time=106 ms
64 bytes from 74.125.45.100: icmp_seq=3 ttl=237 time=106 ms
64 bytes from 74.125.45.100: icmp_seq=4 ttl=237 time=108 ms
^C
--- 74.125.45.100 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 106.778/107.637/108.772/0.892 ms
davem@Dartagnon:~$ ping www.google.com
^C
davem@Dartagnon:~$ ping www.google.com
^Z
[1]+  Stopped                 ping www.google.com
davem@Dartagnon:ifconfig


~$eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:134.157.195.85  Bcast:134.157.195.127  Mask:255.255.255.128
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14440 (14.4 KB)  TX bytes:14007 (14.0 KB)
          Interrupt:16

```

So definately a domain name resolution issue, and not a networking problem!

Also I should confirm that I am hard wired in when I'm at work.

so now I switch over to the <MyologyOffice> setting and...

```
davem@Dartagnon:~$ ping www.google.com
PING www.l.google.com (72.14.221.103) 56(84) bytes of data.
64 bytes from fg-in-f103.google.com (72.14.221.103): icmp_seq=1 ttl=243 time=11.1 ms
64 bytes from fg-in-f103.google.com (72.14.221.103): icmp_seq=2 ttl=243 time=11.1 ms
64 bytes from fg-in-f103.google.com (72.14.221.103): icmp_seq=3 ttl=243 time=11.8 ms
64 bytes from fg-in-f103.google.com (72.14.221.103): icmp_seq=4 ttl=243 time=11.2 ms
64 bytes from fg-in-f103.google.com (72.14.221.103): icmp_seq=5 ttl=243 time=11.2 ms
^C
--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4016ms
rtt min/avg/max/mdev = 11.147/11.332/11.871/0.279 ms
davem@Dartagnon:~$

```

I'm going to keep hold of that google IP address, for future reference, make for a nice networking tool, as it shows the problem was name resolution.

> 
sudo ifconfig eth0 netmask 255.255.255.0


I have a feeling that I loose networking entirely... lets check though..

```

davem@Dartagnon:~$ sudo ifconfig eth0 netmask 255.255.255.0
[sudo] password for davem: 
davem@Dartagnon:~$ ping www.google.com
ping: unknown host www.google.com
davem@Dartagnon:~$ ping 74.125.45.100 
connect: Network is unreachable
davem@Dartagnon:~$
```

Yep thought so..!?

The strange thing about this netmask thing is the following. The desktop is connected with exactly the same setting within it's windows dual boot logon, and has a netmask of 255.255.255.0 an no networking issues.

I recently did an XP refresh on a colleagues terminal (:( ) and when it was on DHCP it could "see" all the names of the other terminals in the network places (ubuntu terminals host names and XP host names), but as soon as I added the static IP and the netmask, all the ubuntu terminals dissapeared.

Anyhow..

David

---

### Post by pytheas22 on 2009-02-22
So the problem does seem to be that for whatever reason, Ubuntu is confused about the DNS server when it receives an IP via dhcp.  I'm thinking that as a possible workaround, you could edit your dhclient.conf file to specify a DNS server explicitly.  To do that, type:
```

sudo gedit /etc/dhcp3/dhclient.conf
```

and add these lines to the bottom of the file that pops open:
```

lease {
interface "eth0";
option domain-name-servers 151.197.0.38;
}

lease {
interface "wlan0";
option domain-name-servers 151.197.0.38;
}


lease {
interface "ath0";
option domain-name-servers 151.197.0.38;
}
```

I think that this will tell your computer to use 151.197.0.38 as the DNS server when using a dynamic IP.  151.197.0.38 is a public server that should work for you (it works here in the United States).

After you've made these changes, you'll want to reboot.  Then grab an IP manually by typing:
```

sudo ifconfig eth0 up
sudo dhclient eth0
```

After you've done that, does DNS work?  Which DNS server is specified in /etc/resolv.conf?
> 
I'm going to keep hold of that google IP address, for future reference, make for a nice networking tool, as it shows the problem was name resolution.

You can find the IP address of any website by typing 'host website.com' in a terminal.  'dig website.com' also works if you want a bit more information.

---

### Post by theDaveTheRave on 2009-02-27
Hi gents.

thought I would post to say hi, and say that everything has been working just fine.

but today.... no wireless!

nothing in iwlist scan! The driver is enabled, and in use. I'm getting a little peeved now!

here is the output of lshw...

[code]davem@Dartagnon:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=134.157.195.83 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:c6:f5:5b:d4:bb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
davem@Dartagnon:~$ 
[code]

once again my atheros chip is uncliamed!!!

i seem to recall I had this earlier, so I'll see if I can resolve my own problem from reading through the thread again (I suspect I will need to remove and re-install the modules, *sigh*)

Oh well, is there anything I can do to attempt to find out why the wireless suddently stopped? I don't remember "changing" anything?

I did however have my laptop running on the train this morning, and it may not have "shut down" properly, so maybee the switch at the front got knocked somehow... I've already tried to use the switch as before, but so far no joy!

speak soon.

David.

---

### Post by pytheas22 on 2009-02-27
That's strange.  The card shouldn't become unclaimed for no reason--and even if the radio had been turned off accidentally by the switch, the card would still be listed as claimed.

The only things that make sense to me are that 1) you kernel without realizing it, which would make the ath5k driver not work if you built it from source (as opposed to using the linux-backports-modules-intrepid package), because each time you upgrade your kernel, ath5k needs to be rebuilt to match; or 2) you booted into an older kernel, against which no ath5k module is built, accidentally.

If you want to see which kernels have an ath5k module associated with them, run these commands:
```

sudo updatedb ###to update the 'locate' database
locate ath5k | grep lib
```

The output should look something like this:
```

/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.27-7-generic/ath_pci/if_ath_pci.o
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci/ath_pci.mod.o
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci/if_ath.o
/lib/linux-restricted-modules/2.6.27-9-generic/ath_pci/if_ath_pci.o
/lib/modules/2.6.27-7-generic/net/ath_pci.ko
```

only pretend that ath_pci in the example above were replaced by ath5k (I don't have ath5k on my system).  You can see that I have ath_pci modules for both the 2.6.27-7 and 2.6.27-9 kernels.  My current running kernel is 2.6.27-9, which I can tell by running the command 'uname -r'.  So I have an ath_pci module built against my current running kernel.  Do you have an ath5k for yours?  If not, you should compile compat-wireless again while running your newest kernel.

---

### Post by theDaveTheRave on 2009-02-28
Pythaes.

Ahh,

OK that explains it......

```

davem@Dartagnon:~$ uname -r
2.6.27-11-generic
davem@Dartagnon:~$ locate ath5k | grep lib
/lib/modules/2.6.24-23-generic/updates/drivers/net/wireless/ath5k
/lib/modules/2.6.24-23-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
davem@Dartagnon:~$ 

```


so now I need to write a script to perform a comparison, then automatically re-install the modules!

or is there another way of doing stuff automatically.

thanks for your help, I'll add this info into my help file.

David.

Edit..

Yep that did it, do that then reboot. Everything is back to normal.

---

