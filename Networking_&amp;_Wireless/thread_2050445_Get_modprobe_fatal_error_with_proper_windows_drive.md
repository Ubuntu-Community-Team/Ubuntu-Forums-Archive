---
title: "Get modprobe fatal error with proper windows driver"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by AndyOpie150 on 2012-08-30
):P):PI have 2003 Sony VAIO all in one Desktop PVC V200G with a 2.80GHz Intel 4 processor and 1GB of PC-2700 DDR RAM. 
I have a Windows XP OS with service pack 3. It only has 120GB hard drive (I don't use that much, mostly just Utility programs for Android Development)
I just recently dual booted XP and Ubuntu 12.04, almost splitting in half the hard disk partition.
 
I have installed:
ndiswrapper-common
ndiswrapper-utils
libglade2
python2
ndisgtk
I have a Linksys WPC54G v2 wireless interface adapter. The proper windows driver (it's what I used to enable the card in my XP OS: works great)
I installed the LSTINDS.INF from the driver folder (ran the command to check, and it is installed)
When I try to give the command: sudo modprobe ndiswrapper I get "FATAL: Module ndiswrapper not found". This is also the same out put I got with another driver (v5) that had the .INF file. These are the only two drivers with .INF files for the Linksys WPC54G's, the rest do not have them.
Note: I had to wipe and reinstall Ubuntu to uninstall the drivers because:
sudo modprobe -r ndiswraper
sudo ndiswrapper-e <name of .INF>
sudo rm -rf /etc/ndiswrapper/<name of .INF> 
did not work at all both times.](*,)
 
lsusb does not show the Ethernet controller (Realtek RTL8139) or the Wireless Interface Adapter (Linksys WPC54G v2 with the Texas Instruments ACX 111 54Mpbs Wireless Interface chip set)
 
lspci lists the Ethernet controller.
lspci lists the chip set but it say's it's UNCLAIMED
 
I ran the command to check, and the ndiswrapper-common is installed.
 
I have been looking at the ACX 100/111 project driver but am too Linux green to attempt on my own.
 
Any Ideas on how to resolve my Wireless woe's would be greatly appreciated.
If you need more info just let me know.
 
Note: Do not have a wired connection at this time in either OS/Distro. I tried striaght to the modem and it was a no go. I have no extra Ethernet cable to try a connection from the router (poor and awfully bent to boot). Also: Installed Ubuntu with a USB drive (my CD's where only 702MB and Ubuntu was 711MB)

---

### Post by chili555 on 2012-08-31
Let's take a look at:```
lspci -nn | grep 0280
ndiswrapper -l
```Thanks.

---

### Post by AndyOpie150 on 2012-08-31
Ubuntu up, me on phone.
02:00.0 Network controller [**0280[COLOR="Red"][/COLOR]**] : Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]

lstinds : driver installed 
            device (104C:9066) present

---

### Post by chili555 on 2012-08-31
Please do:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by AndyOpie150 on 2012-08-31
Response will be delayed helping spiritual sister replace alternator. Will have to pick it up in a few.

---

### Post by AndyOpie150 on 2012-08-31
I'm back.
dkms was not installed. 
I then proceded to install:
dkms_2.2.0.3-1ubuntu3_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb
open-vm-dkms_2011.12.20-562307-0ubuntu1_all.deb
 
sudo modprobe ndiswrapper gave me no output at all.

---

### Post by chili555 on 2012-08-31
> sudo modprobe ndiswrapper gave me no output at all.Good! No errors or warnings. Did it create a wireless interface, ideally wlan0?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```Does it connect?

---

### Post by AndyOpie150 on 2012-08-31
Getting closer, The power LED is now on.
It now shows a selection of networks in the dropdown.
Would not connect to any, even an open network. 
Would try, connection beacon in task bar would scan but would never lock. Sometimes would go blank, and then pop up would ask for key again (secured network).
 
lo no wireless extensions.
wlan0 IEEE 802.11g ESSID:off/any 
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated 
Bit Rate:54 Mb/s Tx-Power:10 dBm Sensitivity=0/3 
RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
eth0 no wireless extensions.
 
wlan0 Scan completed :
Cell 01 - Address: **:**:**:**:**:**
ESSID:"******"
Protocol:IEEE 802.11b
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality:60/100 Signal level:-57 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Extra:bcn_int=200
Extra:atim=0
IE: Unknown: ********************
IE: Unknown: ********************
IE: Unknown: ***********
IE: Unknown: *******
Cell 02 - Address: **:**:**:**:**:**
ESSID:"******"
Protocol:IEEE 802.11b
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality:59/100 Signal level:-58 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
 
This continues for two more networks
 
EDIT: More
andrew@Sony-VAIO-PCV-V200G:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0e:a6:1e:e0:c7 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Base address:0x8800 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:205 errors:0 dropped:0 overruns:0 frame:0
TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:16142 (16.1 KB) TX bytes:16142 (16.1 KB)
wlan0 Link encap:Ethernet HWaddr 00:12:17:20:ec:2a 
inet6 addr: fe80::212:17ff:fe20:ec2a/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:49 errors:0 dropped:0 overruns:0 frame:0
TX packets:195 errors:0 dropped:25 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:12218 (12.2 KB) TX bytes:35508 (35.5 KB)
Interrupt:18 Memory:44020000-44022000 
andrew@Sony-VAIO-PCV-V200G:~$ nm-tool
NetworkManager Tool
State: connecting
- Device: wlan0 [linksys] -----------------------------------------------------
Type: 802.11 WiFi
Driver: ndiswrapper
State: connecting (getting IP configuration)
Default: no
HW Address: 00:12:17:20:EC:2A
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
Wireless Access Points 
DEREK: Infra, *, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WEP
NETGEAR_Secure: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WEP
NETGEAR_Guest1: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WEP
OTIS-HP_Network_1: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP
linksys: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
 
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: 8139too
State: unavailable
Default: no
HW Address: 00:0E:A6:1E:E0:C7
Capabilities:
Carrier Detect: yes
Wired Properties
Carrier: off
 
andrew@Sony-VAIO-PCV-V200G:~$ sudo /etc/init.d/networking restart
[sudo] password for andrew: 
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces... [ OK ] 
[EMAIL="andrew@Sony-VAIO-PCV-V200G:~$"]andrew@Sony-VAIO-PCV-V200G:~$[/EMAIL]
 
Bed Time Here. Check back in in 7 or 8 hours.

---

### Post by chili555 on 2012-08-31
> NETGEAR_Secure: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WEPIs this your network? Have you double-checked the WEP key? How many characters is it?

---

### Post by AndyOpie150 on 2012-09-01
I rent a room in a house. The router is shared by all and was set up for WPA2 security. My wireless card is only good for WPA security.
I had to set up a seperate network, NETGEAR_Guest1, with WPA security.
 
The Linksys is an open network with no security (one of the neighbors). I should have ben able to connect to it if anything. Doesn't even connect to it.
 
The NETGEAR_Guest1 key has 13 characters. 
 
Note: There is no option in the "edit networks" for WPA security by itself. There are three WEP's and then only WPA-WPA2.
I could try and set up MY network with only WEP which isn't secure at all,but I'm not crazy about the Idea. 
As a test I will try to connect to my phone's wireless hotspot (have used it on the windows OS from time to time when the WiFi was down). I can set it up with no security,just to see it I can connect.
 
EDIT: Had full signal with AndroidAP, no security. Connection timed out and the network manager attempted to connect to the Linksys network. I'm begining to get the impression my problem is with the network manager.
Can I use the wicd instead? It seemed like it had WPA security option all by itself. The package info said it had no Gnome dependencies. I downloaded the wicd, wicd-daemon, and wicd-gtk.
Will I need a text editor, or is there one provided in the installed Precise?
 
Note: Have edited build.props of ROM's for phone, so it shouldn't be a problem to edit whatever is necessary.
I catch on pretty quick, most times.

---

### Post by chili555 on 2012-09-01
> Note: There is no option in the "edit networks" for WPA security by itself. There are three WEP's and then only WPA-WPA2.Arrgh!

First, you do *NOT* want to 'Create New Wireless Network.' That is for ad-hoc, computer to computer networks. You want Network Manager to find and connect to an Infrastructure (router) to Managed (computer) arrangement.

Second, the WPA-WPA2 box really means, roughly, WPA and WPA2 mixed mode; which Network Manager and wpa_supplicant don't work very well with; OR WPA alone OR WPA2 alone. 

I only really asked about WEP because NM thinks that's what you have:> NETGEAR_Guest1: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 [COLOR="Red"]WEP[/COLOR]Is that not true?> Can I use the wicd instead? Certainly, but you'll need to remove NM altogether at the same time.> Will I need a text editor, or is there one provided in the installed Precise?There is. Depending on your version, Unity, lubuntu, xubuntu, et al, it is gedit, leafpad, kate or more. Usually, if you look for applications called 'text' it will appear.

What are you planning to edit?

I am worried that maybe NM and your driver see everything as WEP.

---

### Post by AndyOpie150 on 2012-09-01
I'm just throwing out Ideas and brainstorming with what little knowledge I have. This happens when it seems like I have run into a brick wall.
 
Why doesn't it connect to an open network? It seems like there is something up with network manager. Is there a dependency or update I'm missing (haven't been able to connect to a wired network)? I don't have normal problems.
 
The card is working and there is a list of networks (with the proper signal strenth indicated). Just can't seem to make the connection. This is the same thing it was doing with the wired connection.

---

### Post by chili555 on 2012-09-01
> **AndyOpie150 said:**
> I'm just throwing out Ideas and brainstorming with what little knowledge I have. This happens when it seems like I have run into a brick wall.
 
Why doesn't it connect to an open network? It seems like there is something up with network manager. Is there a dependency or update I'm missing (haven't been able to connect to a wired network)? I don't have normal problems.
 
The card is working and there is a list of networks (with the proper signal strenth indicated).If they all show as WEP here:```
nm-tool
```...then I'd suspect wpa_supplicant is not installed or not correctly installed. Let's check:```
sudo dpkg -s wpasupplicant | head -n3
```We can also see what the logs say when you try to connect:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by AndyOpie150 on 2012-09-01
andrew@Sony-VAIO-PCV-V200G:~$ nm-tool
NetworkManager Tool
State: connecting
- Device: wlan0 [linksys] -----------------------------------------------------
Type: 802.11 WiFi
Driver: ndiswrapper
State: connecting (configuring)
Default: no
HW Address: 00:12:17:20:EC:2A
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
Wireless Access Points 
NETGEAR_Secure: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP
NETGEAR_Guest1: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP
DEREK: Infra, *, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
linksys: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
 
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: 8139too
State: unavailable
Default: no
HW Address: 00:0E:A6:1E:E0:C7
Capabilities:
Carrier Detect: yes
Wired Properties
Carrier: off
 
andrew@Sony-VAIO-PCV-V200G:~$ sudo dpkg -s wpasupplicant | head -n3
[sudo] password for andrew: 
Package: wpasupplicant
Status: install ok installed
Priority: optional
andrew@Sony-VAIO-PCV-V200G:~$ sudo cat /var/log/syslog | grep etwork | tail -n20Sep 1 13:57:52 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> address 192.168.1.103
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> prefix 24 (255.255.255.0)
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> gateway 192.168.1.1
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> nameserver '65.32.5.111'
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> nameserver '65.32.5.112'
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> domain name 'tampabay.rr.com'
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 1 13:57:59 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 1 13:58:00 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> DNS: starting dnsmasq...
Sep 1 13:58:00 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep 1 13:58:01 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 1 13:58:01 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
Sep 1 13:58:01 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) successful, device activated.
Sep 1 13:58:01 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
andrew@Sony-VAIO-PCV-V200G:~$

---

### Post by chili555 on 2012-09-01
It looks like you connected just perfectly. Because of the signal strength, I wouldn't expect good performance from 'linksys.'> linksys: Infra, *, Freq 2437 MHz, Rate 54 Mb/s, [COLOR="Red"]Strength 30[/COLOR]Also, I note:> Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 1 13:58:13 Sony-VAIO-PCV-V200G NetworkManager[681]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.You might smooth things a bit by setting IPv6 to 'Ignore.'Please see attached.

I am still concerned that your card and driver see every encrypted network as WEP. Can that be true? What does this tell us?```
sudo iwlist wlan0 auth
```

---

### Post by AndyOpie150 on 2012-09-01
andrew@Sony-VAIO-PCV-V200G:~$ sudo iwlist wlan0 auth
[sudo] password for andrew: 
wlan0 Authentication capabilities :
WPA
CIPHER-TKIP
Current WPA version :
disabled
Current Key management :
Current Pairwise cipher :
none
Current Pairwise cipher :
none
Current Authentication algorithm :
open
 
 
andrew@Sony-VAIO-PCV-V200G:~$ 
 
 
 
 
 
 
 
sent from Ubuntu 12.04 and the linksys network (the signal was just strong enough)
Note: I know now why it didn't connect to my Hot Spot. I forgot to get a card and pay for service. Service starts on the First of the month. I will get card, 3G will then make it possible to: sudo apt-get update.
 
Tried while linksys network was strong enough but it died before I could complete the install of the 20 something updates.

---

### Post by chili555 on 2012-09-01
> wlan0 Authentication capabilities :
WPA
[COLOR="Red"]CIPHER-TKIP[/COLOR]I wonder if that's the clue we're looking for. Here is a redacted scan of my router:> Cell 01 - Address: xx:13:10:62:8D:xx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    IE: IEEE 802.11i/WPA2 Version 1
                        [COLOR="Red"]Group Cipher : CCMP[/COLOR]
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKMaybe your card is old enough, or lacks the firmware update, to do more modern authentication. 

You could look into a firmware update. You could look into a newer wireless card. You could ask the landlord to set the router to WPA-TKIP.

---

### Post by AndyOpie150 on 2012-09-01
> **chili555 said:**
> I wonder if that's the clue we're looking for. Here is a redacted scan of my router:Maybe your card is old enough, or lacks the firmware update, to do more modern authentication. 
 
You could look into a firmware update. You could look into a newer wireless card. You could ask the landlord to set the router to WPA-TKIP. It's actually my router, his gave out and I ran out and bought a NETGEAR N300 so I wouldn't be without. I have set up NETGEAR_Secure with WPA2-PSK for the other roomates and set up NETGEAR_Guest1 with WPA-TKIP for my wireless card. Works great on Windows so it can't be the card to Router connection.
I just need to get those updates installed on Ubuntu I would think. 23 in all. Just need to be connecrted to any network long enough to download and install them. That's probably what ails the network manager.
I'll try that first, if for some reason it don't fix the problem I post then.
Might take a day or two for that to all come together though.
 
Thanks greatly for all you help up to this point, hopefully will be able to free you up to help others. I'll know for sure in a couple of days.

---

### Post by AndyOpie150 on 2012-09-01
Did sudo apt-get update. It installed 43 updates. Anything else I should do?
(still having connection problems with secured networks)

---

### Post by chili555 on 2012-09-01
> **AndyOpie150 said:**
> Did sudo apt-get update. It installed 43 updates. Anything else I should do?
(still having connection problems with secured networks)Please try to connect to a secured network and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by AndyOpie150 on 2012-09-01
Sorry it took so long to get back to you:

andrew@Sony-VAIO-PCV-V200G:~$ Sudo cat /var/log/syslog | grep etwork | tail -n20No command 'Sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'udo' from package 'udo' (universe)
Sudo: command not found
andrew@Sony-VAIO-PCV-V200G:~$ sudo cat /var/log/syslog | grep etwork | tail -n20[sudo] password for andrew: 
Sep  1 21:30:46 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info>   address 192.168.1.103
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info>   prefix 24 (255.255.255.0)
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info>   gateway 192.168.1.1
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info>   nameserver '65.32.5.111'
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info>   nameserver '65.32.5.112'
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info>   domain name 'tampabay.rr.com'
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep  1 21:30:50 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep  1 21:30:51 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> DNS: starting dnsmasq...
Sep  1 21:30:51 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Sep  1 21:30:52 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep  1 21:30:52 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
Sep  1 21:30:52 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) successful, device activated.
Sep  1 21:30:52 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep  1 21:31:06 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep  1 21:31:06 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep  1 21:31:06 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep  1 21:31:06 Sony-VAIO-PCV-V200G NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
andrew@Sony-VAIO-PCV-V200G:~$

---

### Post by chili555 on 2012-09-01
> Please try to connect to a ***secured*** network and post:
```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

We already know you can barely connect to 'linksys,' an open network.

---

### Post by AndyOpie150 on 2012-09-01
Brain dead. Sorry. Will try to connect to NETGEAR_Guest1 then run command.
 
NOTE: The network manager had it set up as a ADHOC network. Security was set to: WEP 40/128-bit key (Hex or ASC11) ad hoc
 
EDIT: just before my last post I was using my phone as a hot spot and recieved 26 updates from the update manager. Just after last post data connection went south (I don't have the best carrier, but I can afford them) so I had to post here with in the Windows OS. Whent I back to Ubuntu OS to try the commands while trying to connect to NETGEAR_Guest1 the wireless card was dead. Back to the Windows OS and it's working again.
 
 
Ubuntu  is not for the easily frustrated.

---

### Post by AndyOpie150 on 2012-09-02
Wipe and re-install of Ubuntu and previously installed packages and card is functioning as before. Used hotspot to connect and to update. Card is now dead again after reboot. All previously installed packages are installed, but the ndiswrapper-utils is no longer recognized after the update's. Reinstalled, but still no go on being recognized. I think I'm going to wipe and re-install Ubuntu 12.04. Then blacklist the network manager and install the wicd.
This may keep the wpa supplicant from being disconnected.
 
I just know one thing: The card works perfectly in the Windows OS with my network that is set up for WPA security, It should work in Ubuntu. I'm going to have to figure some way to keep everything working, even after an update. The wicd seems like a viable solution, as the network manager is failing miserably. It's been a week now dealing with no decent Internet connect and feeling like I'm on a merry-go-round. I have little patience left.
 
I'm going to have to read up on how to blacklist the network manager and install the wicd.

---

### Post by kurt18947 on 2012-09-02
I assume money is tight for you but there are wifi adapters that work 'out of the box' and are not expensive.  

I know this work out of the box in 12.04, 11.10 and 11.04.  It needed a firmware patch in 10.xx

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&Tpk=trendnet%20tew-649ub](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&Tpk=trendnet%20tew-649ub)

I've used this one since 9.xx and it's been plug 'n' play.  Not real fast though, G speed

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&Tpk=trendnet%20tew-649ub](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&Tpk=trendnet%20tew-649ub)
and it looks like free shipping.

Here's a nano USB adapter that is now working in 12.04 without additional software or firmware.  The range seems surprisingly good for such a small device.  $9.99 with free shipping.

[http://www.amazon.com/s/ref=nb_sb_ss_i_1_6?url=search-alias%3Daps&field-keywords=edimax+ew-7811un&sprefix=edimax%2Caps%2C177](http://www.amazon.com/s/ref=nb_sb_ss_i_1_6?url=search-alias%3Daps&field-keywords=edimax+ew-7811un&sprefix=edimax%2Caps%2C177)

I'm not an advocate of spending money on frivolous things but how much is not pulling your hair out worth?

---

### Post by chili555 on 2012-09-02
> **AndyOpie150 said:**
> 
 
I'm going to have to read up on how to blacklist the network manager and install the wicd.You can't. Network Manager will re-spawn and try to take over again almost no matter what you do. The only sure-fire method is to remove NM altogether.

---

### Post by AndyOpie150 on 2012-09-02
kurt18947: I'm pretty stubborn, and when I put my mind to something I don't stop until all avenues are exhuasted. I know my card should work on Ubuntu, I shouldn't have to go out and by another that may or may not work with windows to well. There is some way, weather with wicd or a patch or ?, to get it to work with Ubuntu 12.04.
After all, this is the best open source OS out there, right? I don't give up very easy.
 
 
chili555: I tried sudo apt-get remove network-manager-kde. Was informed it could not be done for the network-manager-kde. This is why I thought my next move was to try and blacklist it.
Thanks for the info about it tryng to re-spawn. Will now concentrate on removal.
 
EDIT: I seemed to have used the remove command for the Kbuntu. Will now try with the proper command for Ubuntu .

---

### Post by chili555 on 2012-09-02
Please try:```
sudo apt-get remove --purge network-manage*
```

---

### Post by AndyOpie150 on 2012-09-02
Thanks.  I found that a while ago though. I just need to figure how to download the wicd. I tried: sudo apt-get install wicd,  but I get "unable to locate package wicd"

---

### Post by chili555 on 2012-09-02
> **AndyOpie150 said:**
> Thanks.  I found that a while ago though. I just need to figure how to download the wicd. I tried: sudo apt-get install wicd,  but I get "unable to locate package wicd"How about:```
sudo apt-get install wicd-kde
```Aren't you running KDE or did I get lost among the reinstalls?

---

### Post by AndyOpie150 on 2012-09-02
Same output. Could be my 3G signal is not strong enough. It seems to be good enough to post here though. Seems to be fairly fast for a 54Mbps wireless card.
??????? Lol
Could I be missing some dependency of the APT?

---

### Post by chili555 on 2012-09-02
If it couldn't find the connection, it would say 'server not found.' It appears, however, to say the package is not found, correct? Can you look around in System Administration, or some such, and look for Software Sources. Make sure that Main, Universe, Restricted and Multiverse are selected. Then, in a terminal, run:```
sudo apt-get update
sudo apt-get install wicd
```

---

### Post by AndyOpie150 on 2012-09-02
system/administration is where? It's not in the system settings. I don't see it in the task bar/tray, boy do I feel dumb!

---

### Post by AndyOpie150 on 2012-09-02
Installed the wicd the hard way. One package at a time. Now I just need to get the Icon in the tray.
 
EDIT: Well I have tried everything with wicd and can't get the power to the card, or the wicd icon in the system tray. Lost some dependency when I deleted network-manager. I'm back to square one. 
I have wireless with open networks until I update, then I loose power to the card. wicd won't work because Gnome is too dependent on the network-manager.
 
I think I have exahusted all avenues and need to think about installing the previous version of Ubuntu, at least that version of Gnome isn't dependent on the network-manager and I can swap with wicd if it doesn't work with my card. Who knows, it might very well work just fine with my card.
 
Unless there is a patch out there that I'm not yet aware of.
 
I'm going to give it one last ditch effort and try your last sugestion after a wipe and re-install:
 
Wipe and re-install, establish a wireless connection by installing the proper packages, total update with: sudo apt-get install update, install the 23 updates from the update manager, then sudo apt-get install wicd-kde (which should work after the toatal update), then remove network-manager and reboot.
 
If this doesn't work I'm going to throw in the towel right after rooting around in the system files to see if I can just delete a file or two without loosing the dependencies

---

### Post by AndyOpie150 on 2012-09-03
Decided I would try Lubuntu. It's lighter and uses LXDE, but it means I have to download more dependencies for each package that was needed in Gnome. If the network-manager doesn't work I know I can get the wicd to work on it.
 
Thanks for all the help on the Gnome merry-go-round.

---

### Post by AndyOpie150 on 2012-09-07
After trying every Ubuntu 12.04 version, Ubuntu 11.10 and 10.10 I have finally been able to establish a solid and lasting wireless connection.
I had no choice but to drop down to the only security level that the network-manager would recognize. Ubuntu 10.10 was the only version that would maintain my wireless card on a reboot without having to type in "sudo modprobe ndiswrapper" every time I booted into it.

---

### Post by chili555 on 2012-09-07
> Moderator: please prefix this as SolvedYou are the only one that can do this. Please use thread tools at the top to mark Solved.> Ubuntu 10.10 was the only version that would maintain my wireless card on a reboot without having to type in "sudo modprobe ndiswrapper" every time I booted into it.Very easily solved in any Ubuntu edition...

---

### Post by AndyOpie150 on 2012-09-08
> **chili555 said:**
> Very easily solved in any Ubuntu edition...I'm not crazy about using an unsupported version, so I'm all ears (eye's).

---

### Post by chili555 on 2012-09-08
> **AndyOpie150 said:**
> I'm not crazy about using an unsupported version, so I'm all ears (eye's).Open a terminal and do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```You should be all set.

---

### Post by AndyOpie150 on 2012-09-08
I see now where I went wrong. I just typed in this:

sudo echo ndiswrapper >> /etc/modules. 

Thanks again. Will download and install 12.04 again or just upgrade. Whichever is quicker, as just downloading and installing requires me to drag all my stuff into the living room where the router is set up; download the 12.04 and use the Pendrivelinux utility to load it on to the USB drive to make it bootable (12.04 is 711MB and my CD-R's are only 702MB); and last but not least, to wipe (7 pases), reformat, and merge all the partitions in preparation for the install (still haven't figured out how to use the advanced feature to get it to install in the same partition as a previous version)

Question: How do you get the "Code" box in the post?

---

### Post by chili555 on 2012-09-08
To put something in a Code box, highlight it and press the code button at the top. Please see attached.```
lsusb
```

---

### Post by necs on 2012-09-08
> **chili555 said:**
> Good! No errors or warnings. Did it create a wireless interface, ideally wlan0?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```Does it connect?

root@bt:~# iwconfig

lo      no wireless extension
eth0  no wireless extension

root@bt:~# sudo iwlist wlan0 scan

wlan0    Interface does not support scanning

Pls Help Meh Out...................

---

### Post by chili555 on 2012-09-08
> **necs said:**
> root@bt:~# iwconfig

lo      no wireless extension
eth0  no wireless extension

root@bt:~# sudo iwlist wlan0 scan

wlan0    Interface does not support scanning

Pls Help Meh Out...................Please start your own new thread and include:```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndiswrapper
```Thanks.

---

### Post by AndyOpie150 on 2012-09-08
OK, finally got it done. Thanks for the root script. It fixed me right up.
Of course I had to try everything the hard way first.
Updated to 11.04, then 11.10, then 12.04. That was a mess, to laggy and a blue screen where the wallpaper should have been. I rebooted after each install, but had an error when updating from 10.10 to 11.04 that started everything in a downward spiral.

Back to Windows and a fresh download and install onto the USB. When I got to the install of Ubuntu 12.04 it gave me the option to wipe and re-install Ubuntu 12.04 so I didn't have to go thru the whole partition nightmare in windows (still wouldn't mind learning how to do it from the install advanced options).

After installing the 7 packages that are required I installed the driver. Then ran the root script you mentioned.
Updated, but this time on the reboot the card had juice and the wireless networked connected with no problems.

Maybe I should write up a little tutorial on how to get everything installed (and in what order) with no wired connection, up to the driver install (to many different drivers and install methods, I'll leave that to the pros).
Then mention the root script you gave me to keep the driver module solid after an update and reboot.
This way new Ubuntu users won't have to spend so much time trying to figure it out the hard way.

Just my way of giving back. What do you think?

Thanks for all the help chili555!

PS: Sure wish I could figure out why it shows my card as being capable of WPA in the terminal, but the network-manager and wicd say no-go. Of course,  I'm not going to be happy until I figure this out.

---

