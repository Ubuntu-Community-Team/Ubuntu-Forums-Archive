---
title: "No wired or wireless connection but connected to the router"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by duuchung on 2011-08-26
My ubuntu box has been connected to wire or wireless since time forgotten. After some upgrade, I lost my wireless connection. I had been connected to the wire as my last resort. Unluckily I have lost my wired internet connection for 2 weeks.

I tried everything. My ubuntu wire at one stage could not even connect to the router. No green light was shown. The NIC was switched off. There was wake on lan, clear cmos, apci…… .  The connection with the router was back at last. It could be pinged to 192.168.2.1 but no more.

Now NetworkManager, the culprit, has taken over the stewardship of the internet setting silently and ruthlessly. I set and set again /etc/network/interfaces but to no avail. I followed jackol’s e cure by adding the open nameserver to resolv.conf.
Thanks jackol. 
[http://www.thejackol.com/2008/05/20/fixing-networkmanager-dns-issue-in-ubuntu-hardy-herongutsy/](http://www.thejackol.com/2008/05/20/fixing-networkmanager-dns-issue-in-ubuntu-hardy-herongutsy/)

---

### Post by praseodym on 2011-08-26
Hi,

can you show:

```
cat /etc/network/interfaces
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
rfkill list
route -n
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
```
If you want to use a manual config with "interfaces" you should deactivate the NM in autostart, and login again.

---

### Post by duuchung on 2011-08-27
I am not as learned as you are.
I just follow instructions in setting up my machine.
I checked my router. DHCP has assigned an ip to my connection instead of using my setting in /etc/network/interfaces.
I copied my codes beneath hoping others can know what to do when there is a nameserver problem.

cat /etc/network/interfaces
auto lo
iface lo inet loopback
# default wireless
auto wlan0
iface wlan0 inet static
address 192.168.2.114
netmask 255.255.255.0
gateway 192.168.2.1
wpa-psk 123456
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid hakka


#default wired
auto eth3
iface eth3 inet static
address 192.168.2.116
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1



lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)

	Subsystem: ASRock Incorporation Device [1849:8201]

	Kernel driver in use: sis900


lsmod
Module                  Size  Used by

ipt_MASQUERADE          1419  1 

xt_state                1014  1 

ipt_REJECT              2004  2 

xt_tcpudp               1927  4 

iptable_filter          1302  1 

nf_nat_h323             5121  0 

nf_conntrack_h323      46894  1 nf_nat_h323

nf_nat_pptp             1996  0 

nf_conntrack_pptp       4681  1 nf_nat_pptp

nf_conntrack_proto_gre     3901  1 nf_conntrack_pptp

nf_nat_proto_gre        1271  1 nf_nat_pptp

nf_nat_tftp              728  0 

nf_conntrack_tftp       2905  1 nf_nat_tftp

nf_nat_sip              5574  0 

nf_conntrack_sip       18703  1 nf_nat_sip

nf_nat_irc              1168  0 

nf_conntrack_irc        3348  1 nf_nat_irc

nf_nat_ftp              1398  0 

nf_conntrack_ftp        5361  1 nf_nat_ftp

iptable_nat             3752  1 

nf_nat                 16289  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat

nf_conntrack_ipv4      10783  4 iptable_nat,nf_nat

nf_conntrack           63258  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4

nf_defrag_ipv4          1117  1 nf_conntrack_ipv4

ip_tables              10492  2 iptable_filter,iptable_nat

x_tables               15921  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables

binfmt_misc             6599  1 

nfsd                  240992  11 

lockd                  65605  1 nfsd

nfs_acl                 2257  1 nfsd

auth_rpcgss            34001  1 nfsd

sunrpc                193146  12 nfsd,lockd,nfs_acl,auth_rpcgss

exportfs                3449  1 nfsd

usbhid                 36882  0 

snd_intel8x0           25664  3 

snd_ac97_codec         99227  1 snd_intel8x0

ac97_bus                1014  1 snd_ac97_codec

snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec

nvidia               4700667  22 

snd_seq_midi            4588  0 

snd_rawmidi            17783  1 snd_seq_midi

snd_seq_midi_event      6047  1 snd_seq_midi

snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event

snd_timer              19067  2 snd_pcm,snd_seq

snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq

ppdev                   5556  0 

ns558                   3068  0 

ndiswrapper           184207  0 

gameport                9327  2 ns558

parport_pc             26058  1 

sis_agp                 4123  1 

snd                    49102  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

i2c_sis96x              3196  0 

soundcore                880  1 snd

snd_page_alloc          7120  2 snd_intel8x0,snd_pcm

shpchp                 29886  0 

agpgart                32011  2 nvidia,sis_agp

lp                      7342  0 

parport                31492  3 ppdev,parport_pc,lp

hid                    67742  1 usbhid

sis900                 17316  0 

floppy                 54311  0 

mii                     4425  1 sis900


ifconfig -a
eth3      Link encap:Ethernet  HWaddr 00:0b:6a:31:9d:7b  

          inet addr:192.168.2.116  Bcast:192.168.2.255  Mask:255.255.255.0

          inet6 addr: fe80::20b:6aff:fe31:9d7b/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:3158 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3318 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2161716 (2.1 MB)  TX bytes:513140 (513.1 KB)

          Interrupt:19 Base address:0xd400 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:193 errors:0 dropped:0 overruns:0 frame:0

          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:13580 (13.5 KB)  TX bytes:13580 (13.5 KB)



wlan0     Link encap:Ethernet  HWaddr 00:1d:0f:ba:a0:e4  

          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0

          inet6 addr: fe80::21d:fff:feba:a0e4/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:34 errors:0 dropped:0 overruns:0 frame:0

          TX packets:525 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:5692 (5.6 KB)  TX bytes:75651 (75.6 KB)



iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.


wlan0     IEEE 802.11g  ESSID:off/any  

          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 06:7C:FC:A6:32:56   

          Bit Rate=54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  

          RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


rfkill list
nil

route -n
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0

192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth3

169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth3

0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth3


cat /etc/resolv.conf
# Generated by NetworkManager



nameserver 208.67.222.222

nameserver 208.67.220.220


cat /var/lib/NetworkManager/NetworkManager.state
[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true


cat /etc/NetworkManager/nm-system-settings.conf

[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true

xyz@xyz-desktop:~$ cat /etc/NetworkManager/nm-system-settings.conf

# This file is installed into /etc/NetworkManager, and is loaded by 

# NetworkManager by default.  To override, specify: '--config file' 

# during NM startup.  This can be done by appending to DAEMON_OPTS in 

# the file:

#

# /etc/default/NetworkManager

#



[main]

plugins=ifupdown,keyfile



[ifupdown]

managed=false

---

### Post by northd_tech on 2011-08-27
> **duuchung said:**
> 
lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)

    Subsystem: ASRock Incorporation Device [1849:8201]

    Kernel driver in use: sis900


lsmod
Module                  Size  Used by
[COLOR=Red]**ndiswrapper**[/COLOR]           184207  0 
i2c_sis96x              3196  0 
**sis900**                 17316  0 
mii                     4425  1 **sis900**


ifconfig -a
eth3      Link encap:Ethernet  HWaddr 00:0b:6a:31:9d:7b  
inet addr:**192.168.2.11**6  Bcast:192.168.2.255  Mask:255.255.255.0
**inet6 addr: fe80::20b:6aff:fe31:9d7b/64 **Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
**RX packets:3158** errors:0 dropped:0 overruns:0 frame:0
**TX packets:3318** errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
          **RX bytes:2161716 (2.1 MB)  TX bytes:513140 (513.1 KB)**
          Interrupt:19 Base address:0xd400 


**wlan0 **    Link encap:Ethernet  HWaddr 00:1d:0f:ba:a0:e4  
**inet addr:10.42.43.1**  Bcast:10.42.43.255  Mask:255.255.255.0
**inet6 addr: fe80::21d:fff:feba:a0e4/64** Scope:Link
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:34 errors:0 dropped:0 overruns:0 frame:0
TX packets:525 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
**RX bytes:5692 (5.6 KB)  TX bytes:75651 (75.6 KB)**

iwconfig
**wlan0 **    IEEE 802.11g  ESSID: off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 06:7C:FC:A6:32:56   
          Bit Rate=54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rfkill list
nil

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth3
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth3

From what I have **bolded** above, it looks like you have a SiS 900 PCI Fast Ethernet controller (which appears to be working on "eth3" or it's getting traffic at least).  You also appear to have a working wireless interface at "wlan0" (but the "wlan0" IP address looks a little strange to me).

Can you also post the results of the following terminal commands:
```
sudo lshw -C network
lsusb
```We should also probably get rid of that [COLOR=Red]**ndiswrapper**[/COLOR] (for Windows Wireless drivers) module, but let's see what those other 2 commands say first.

EDIT:  Although this old thread wasn't all that helpful, it sounds like someone had the SiS 900 ethernet working under Ubuntu 9.10:

[http://ubuntuforums.org/showthread.php?t=1370526&highlight=SiS+900+ethernet](http://ubuntuforums.org/showthread.php?t=1370526&highlight=SiS+900+ethernet)

---

### Post by duuchung on 2011-08-27
Tks, pal.
I have a SiS900 built-in ethernet and a TP-LINK WN322G usb, i.e. ZyDAS. The wired line worked very well before the setting has bee hijacked. I removed wicd, purged dhcp and autoremoved networkmanager. Wicd or networkmanager, alternatively,  would come back through the back door automatically if I remove either of them. I tried many times already. I could no nothing before I found the nameserver cure.

I post my codes below.
sudo lshw -C network
 *-network               

       description: Ethernet interface

       product: SiS900 PCI Fast Ethernet

       vendor: Silicon Integrated Systems [SiS]

       physical id: 4

       bus info: pci@0000:00:04.0

       logical name: eth3

       version: 90

       serial: 00:0b:6a:31:9d:7b

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.116 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s

       resources: irq:19 ioport:d400(size=256) memory:cfffc000-cfffcfff memory:60000000-6001ffff

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:1d:0f:ba:a0:e4

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=ndiswrapper+zd1211bu driverversion=1.56+TP-LINK,06/25/2007,6.22.0.0 ip=10.42.43.1 link=no multicast=yes wireless=IEEE 802.11g


lsusb

Bus 003 Device 002: ID 15d9:0a33 Trust International B.V. Optical Mouse

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 003: ID 0ace:1215 ZyDAS ZD1211B 802.11g

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by northd_tech on 2011-08-27
> **duuchung said:**
> 
**sudo lshw -C network**
 *-network               
description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth3
       version: 90
       serial: 00:xx:xx:xx:xx:xx:xx
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=sis900 driverversion=v1.08.10** Apr. 2 2006 duplex=full **ip=192.168.2.116** latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=**MII speed=100MB/s**
resources: irq:19 ioport:d400(size=256) memory:cfffc000-cfffcfff memory:60000000-6001ffff

  *-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:yy:yy:yy:yy:yy:yy:yy
capabilities: ethernet physical wireless
configuration: broadcast=yes **driver=[COLOR=Red]ndiswrapper[/COLOR]+zd1211bu** **driverversion=1.56+TP-LINK,06/25/2007,6.22.0.0 ip=10.42.43.1** link=no multicast=yes wireless=IEEE 802.11g


**lsusb**
Bus 001 Device 003: ID 0ace:1215 **ZyDAS ZD1211B 802.11g**


I've reformatted and boldfaced the important parts above. It looks to me like you have a conflict with that [COLOR=Red]**ndiswrapper**[/COLOR] module and your USB ZyDAS wireless interface.

Please post the output of these commands:
```
lsmod | grep nd
ndiswrapper -l
lsusb -v
```Then run these commands later to get rid of the [COLOR=Red]**ndiswrapper**[/COLOR] module:
```
sudo rmmod ndiswrapper
sudo su
echo "ndiswrapper" >> /etc/modprobe.d/blacklist.conf

```You might need to reboot the computer into Ubuntu and see if that improves either or both of your wired & wireless connections.  If not, we might still need to play with Network Manager a little.  You also might want to try unplugging the USB wireless and restarting again with the ethernet cable plugged in before the restart (and you might want to try a different ethernet cable if you have one easily available).

---

### Post by duuchung on 2011-08-27
One of the listings is 10 pages long. I'll upload the file. In my case, I have already used ndiswrapper to import a window internet driver. Does it mean that the ndiswrapper must be removed once the window driver has been installed for people with the same set-up as mine?

---

### Post by northd_tech on 2011-08-27
If ndiswrapper is giving  you wireless, then it is fine to keep using that.  It's just that calling all the Windows API function calls can slow down your connection a lot and the added complexity can cause your wireless connections to drop out.  (This is why most people prefer to get a Linux driver for wireless, but ndiswrapper sometimes is the only option for some of the more obscure wireless interfaces).

I know that I never wanted anything more to do with ndiswrapper once Broadcom released their STA driver for Linux on my laptop.

This is one strange thing that I noticed from your file:
> **ndiswrapper -l**
 rt2870 : driver installed  
 smcwgu : driver installed  
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.  
 zd1211bu : driver installed  
     device (0ACE:1215) present (alternate driver: zd1211rw)  
 It looks to me like you've got **3** drivers intstalled under ndiswrapper- rt2870, smcwgu, and zd1211bu.  I only remember seeing 1 driver way back when I used ndiswrapper, but USB interfaces might do things differently (and yours could possibly have a bluetooth dongle built in too).

Here is the relevant part for that ZyDAS ZD1211B USB wireless interface:
> Bus 001 Device 003: ID 0ace:1215 **ZyDAS ZD1211B** 802.11g 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass          255 Vendor Specific Class 
  bDeviceSubClass       255 Vendor Specific Subclass 
  bDeviceProtocol       255 Vendor Specific Protocol 
  bMaxPacketSize0        64 
  idVendor           0x0ace **ZyDAS **
  idProduct          0x1215 **ZD1211B** 802.11g 
  bcdDevice           48.10 
  iManufacturer          16 ZyDAS 
  iProduct               32 USB2.0 WLAN 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           46 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              500mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           4 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x01  EP 1 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x82  EP 2 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x83  EP 3 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               1 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x04  EP 4 OUT 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               1 
Device Qualifier (for other device speed): 
  bLength                10 
  bDescriptorType         6 
  bcdUSB               2.00 
  bDeviceClass          255 Vendor Specific Class 
  bDeviceSubClass       255 Vendor Specific Subclass 
  bDeviceProtocol       255 Vendor Specific Protocol 
  bMaxPacketSize0        64 
  bNumConfigurations      1 
Device Status:     0x0000 
  (Bus Powered)  
 If ndiswrapper won't load after restarting Ubuntu, this command should get your wireless back:

```
sudo modprobe ndiswrapper
```If ndiswrapper fails to load repeatedly, you will need to add the text "ndiswrapper" at the bottom of your /etc/modules file- post here if you need help with that part.

EDIT:
> device (0ACE:1215) present (alternate driver: zd1211rw)   			 		
 Looking at this "alternate driver" zd1211rw, I found some information on the following threads (but there isn't a lot of helpful information that I saw):

[http://ubuntuforums.org/showthread.php?t=1786570&highlight=Zydas+USB](http://ubuntuforums.org/showthread.php?t=1786570&highlight=Zydas+USB)

[http://ubuntuforums.org/showthread.php?t=1218052&highlight=Zydas+USB](http://ubuntuforums.org/showthread.php?t=1218052&highlight=Zydas+USB)

---

### Post by duuchung on 2011-08-31
Tks, Northd_tech.

I upgraded to v11.04. As soon as I could start my ubuntu after fixing the nvidia black screen, the machine could be connected to the internet. However I lost my internet connection later on. It was still connected to my router loyally and honestly.

I purged wicd, ndiswrapper and networkmanager. My machine still could not be connected to the outside world. I checked the router setting and turned off the firewall. Bingo, the connection came back. The firewall of the router prevented the ubuntu to reach out.

What I don't understand is that there are a Mac, an ipad and several Windows connected to the obedient router all along. How come their connection was not shut off by the firewall setting? Had all the machines been shut-off, I would have noticed this was a router problem with the setting.

---

### Post by duuchung on 2011-09-01
I lost my wired  and wireless connection again. As I have removed networkmanager, I have this in the /var/log/syslog 

"WPA: CCMP is used, but EAPOL-Key descriptor version (1) is not 2.
---authentication--- timed out---  ".

More hard work is needed.

---

### Post by praseodym on 2011-09-01
```
iwconfig
lo no wireless extensions.

eth3 no wireless extensions.


wlan0 IEEE 802.11g ESSIDff/any

Mode:[COLOR="Red"]Ad-Hoc[/COLOR] Frequency:2.412 GHz Cell: 06:7C:FC:A6:32:56 
```
You created an Ad-Hoc-network, which is wrong, because it means "Internet Connection Sharing (ICS)". Remove your current profile and setup a new on in "Infrastructure"-modus.

For this stick
```
Bus 001 Device 003: ID 0ace:1215 ZyDAS ZD1211B 802.11g
```
you dont need ndiswrapper, remove it completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/ndiswrapper/*
sudo depmod -a
sudo modprobe -v zd1211rw
``` 
Then replugin your stick and check:

```
iwconfig
lsmod
sudo iwlist scan
dmesg | egrep 'ndis|zd1'
rfkill list
```

---

### Post by duuchung on 2011-09-29
After almost one month, I found the cure. At last, my wired connection is back.

Question #108900  [https://answers.launchpad.net/](https://answers.launchpad.net/)
"ethtool -s eth0 speed 100 duplex full"

I might have changed the setting of SiS900 causing
the media link to drop off as per /var/log/syslog.

---

### Post by duuchung on 2011-11-19
I just set up a 10.04 LTS server. It was well connected with the internet. After I installed xubutu desktop, it was disconnected.

This time the machine has a RTL 8139 NIC card. I added "blacklist 8139cp" in  /etc/modprobe.d/blacklist.conf. I also removed network-manager. It is finally hooked up with the outside world.

---

