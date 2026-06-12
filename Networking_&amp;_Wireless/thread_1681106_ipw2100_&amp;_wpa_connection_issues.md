---
title: "ipw2100 &amp; wpa connection issues"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by theShire on 2011-02-03
Hi all,
I recently installed Ubuntu10.10 using wubi on my Dell Inspiron 510m. It's a pretty old laptop but does the job for the moment.
Ubuntu boots and runs seemlessly - no major issues except connecting to my wireless network.
The SSID is hidden and security is WPA-1. The OS attempts to connect to my network but appears to just time-out. This happens indefinately and it never connects.
Any help would be much appreciated.

I compiled the following info based on the sticky:
```

###########################################################
1) Machine Brand and Model (PC/Laptop):
Dell Inspiron 510M (from around 2002)
Intel PRO/Wireless 2100
###########################################################
2) Wireless Brand, Model and Wireless Chipset:
lspci -nn | grep 'Wireless':
01:03.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
###########################################################
3) check interface:
ifconfig eth1:
eth1      Link encap:Ethernet  HWaddr 00:0c:f1:14:bf:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x8000 Memory:fcffe000-fcffefff

iwconfig eth1:
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
###########################################################
4) Check for modules:
lsmod ipw:
<nothing>

modprobe ipw:
FATAL: Error inserting ipw (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/ipw.ko): Operation not permitted
###########################################################
5) Kernel boot messages
dmesg | grep 'ipw':
[   15.711263] libipw: 802.11 data/management/control stack, git-1.1.13
[   15.711268] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.791833] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   15.791839] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   15.798918] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   15.799562] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  406.074715] usbcore: registered new interface driver ipwtty
[  406.074721] ipw: v0.4:IPWireless tty driver
###########################################################
6) Network configuration
sudo lshw -c network:
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 04
       serial: 00:0c:f1:14:bf:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:5 memory:fcffe000-fcffefff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 81
       serial: 00:0d:56:e3:30:e3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:fcffd000-fcffdfff ioport:ecc0(size=64)
###########################################################
7) Scan for networks
iwlist scanning:
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:24:92:41:8F:40
                    ESSID:"eircom2032 5722"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1144ms ago
          Cell 02 - Address: 00:25:68:FE:A9:93
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:75  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 6948ms ago
###########################################################
8) Ubuntu Version
lsb_release -d:
Description:	Ubuntu 10.10
###########################################################
9) Kernel/architecture
uname -mr:
2.6.35-22-generic i686
###########################################################
10) Restarting the network
sudo /etc/init.d/networking restart:
 * Reconfiguring network interfaces...                                   [ OK ]


```

---

### Post by theShire on 2011-02-04
bump...

---

### Post by theShire on 2011-02-06
Anyone??
Any ideas?

---

### Post by theShire on 2011-02-07
no one??

---

### Post by nm_geo on 2011-02-07
Shire,

While I am not to familiar with Wubi installs, it would be a good idea to get all the upgrades with the wired connection.  Checking my Maverick I see there is even an upgrade kernel (you need those upgrades anyway).  You can see two wireless connections so I would say your driver is working okay and it is even out-of-the -box Intel driver.. as they say.

If the upgrades don't resolve the problem a clean live CD/USB install would be the next recommended solution.  Good Luck

9) Kernel/architecture
uname -mr:
2.6.35-22-generic i686

---

### Post by chili555 on 2011-02-07
Are you quite sure it does WPA?```
sudo iwlist eth0 auth
```I wonder why here your wireless is eth1:> iwconfig eth1:
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
However here it's eth0:> *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 04
       serial: 00:0c:f1:14:bf:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:5 memory:fcffe000-fcffefff
Is there a typo?

---

### Post by theShire on 2011-02-08
> **chili555 said:**
> Is there a typo?

Possibly a typo alright as I'm rebooting my machine to boot into linux and grab the info I need and then booting back into Windows to be able to post the info.

The card should be fine to use WPA cos in WinXP i connect to the wireless network using WPA-TKIP.

Theres another Laptop, Printer and Android phone all connected to the same wireless network without issue.

I'll check the authorizations available for the card now in linux and post back

---

### Post by theShire on 2011-02-08
```

sudo iwlist eth0 auth:
eth0      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		Unknown
          Current Key management :
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : no
          Current Privacy invoked : no

```
It says that it supports WPA

While trying to connect
```

dmesg | grep 'ipw'
[   15.717852] libipw: 802.11 data/management/control stack, git-1.1.13
[   15.717857] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.790813] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   15.790819] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   15.799821] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   15.800553] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  193.627459] usbcore: registered new interface driver ipwtty
[  193.627464] ipw: v0.4:IPWireless tty driver
[  341.549550] ipw2100: Can't get TKIP countermeasures: crypt not set!

```

---

### Post by chili555 on 2011-02-08
I hope it looks something like this:> eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
etc., etc.The fact that it does WPA in Windows 7 simply means the Windows driver and firmware work; not necessarily that the Linux driver and firmware work. Let's see what the command yields.

---

### Post by theShire on 2011-02-08
> **chili555 said:**
> I hope it looks something like this:The fact that it does WPA in Windows 7 simply means the Windows driver and firmware work; not necessarily that the Linux driver and firmware work. Let's see what the command yields.

Sorry, is there another command that you want me to run?
eth0 is my wireless card

---

### Post by chili555 on 2011-02-08
> **theShire said:**
> Sorry, is there another command that you want me to run?
eth0 is my wireless cardNope; we have the answer, the card, driver and firmware do WPA just fine. We crossed posts by a few moments.

I am a bit confused by this:> [  193.627459] usbcore: registered new interface driver ipwtty
[  193.627464] ipw: v0.4:IPWireless tty driverI think this is for a USB modem; do you have one? I wonder how this gets loaded.

I think this is benign:> ipw2100: Can't get TKIP countermeasures: crypt not set!Is this your network?> Cell 02 - Address: 00:25:68:FE:A9:93
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:75  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 6948ms ago
Did you click the Network Manager icon and set up a connection to a hidden wireless network?

---

### Post by theShire on 2011-02-09
> **chili555 said:**
> Nope; we have the answer, the card, driver and firmware do WPA just fine. We crossed posts by a few moments.
Sorry about the late reply, we're in different timezones I think (I'm in Ireland)

> I am a bit confused by this:I think this is for a USB modem; do you have one? I wonder how this gets loaded.
No USB modem on my Laptop but I have had to tether my android phone to it to get on the net a few times.
It definitely wasn't connected when I ran those commands though.

> Is this your network?
Yes, that is my network.
I have since un-hidden the SSID in case this was causing an issue but no luck.

> Did you click the Network Manager icon and set up a connection to a hidden wireless network?
Yes, connection was set-up for a Hidden Wireless Network via the Network Manager applet/icon

---

### Post by chili555 on 2011-02-09
Wow! My favorite kind of problem; everything looks perfect, except it just doesn't work. Please try to connect and let it fail. Then run and post:```
sudo tail -n25 /var/log/syslog
```Let's see if there are any clues as to why it doesn't connect.

May I assume the same ssid and key work seamlessly in other systems on the network? Have you double-checked that there are no case errors? For instance, the ssid Myrouter is not the same as myrouter nor MyRouter. As well, in your PSK, 123abc is not the same as 123ABC.

---

### Post by theShire on 2011-02-09
Apologies chilli,
This evening after coming home from work I decided to try un-hiding the SSID again and what do you know - it works!
I have tried everything to get it to connect with the SSID hidden but it just doesn't work for me.

Thanks for your help and apologies for taking up your time

---

### Post by chili555 on 2011-02-09
No problem at all; I'm just glad it's working.

---

