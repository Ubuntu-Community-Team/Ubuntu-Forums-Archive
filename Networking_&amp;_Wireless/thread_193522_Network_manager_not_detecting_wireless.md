---
title: "Network manager not detecting wireless"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by kurushi on 2006-06-10
Hi

I've a little problem with my internet connection, I'll be very thankfull if someone helps me to find the solution.

I'm using Dapper for amd64, my wireless card is a Broadcom but I'm using Ndiswrapper because for me is impossible to make it work with fwcutter firmware. Well, my wireless network is working fine, but network manager doesn't show any wireless network, in the list.

My wireless network connection is named 'eth1' and I've this '[COLOR="Blue"]/etc/network/interfaces[/COLOR]' file :

[COLOR="Blue"]auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid UAB

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp[/COLOR]

This is the result when I type '[COLOR="Blue"]iwconfig[/COLOR]' in a terminal :

[COLOR="Blue"]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"UAB"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:A9:54:C1:84
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-61 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3470  Invalid misc:10866   Missed beacon:0

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.[/COLOR]

Please, can anyone know how to solve this problem ? Thanks in advance.

---

### Post by precinto on 2006-06-10
In my /etc/network/interfaces I had to do some changes for it to work, since it didn't load the wireless connection.

Try editing these /etc/network/interfaces lines, so that it looks like:

```

auto eth1
iface eth1 inet dhcp
#wireless-essid UAB

```

You'll probably need to reboot.
I hope it helps.

---

### Post by kurushi on 2006-06-10
Thanks for your help, now network-manager shows the list of available wireless networks, but when I  ask to connect it tries for a while and then shows the 'not connected' icon.:(

---

### Post by Patsoe on 2006-06-10
[QUOTE=precinto]In my /etc/network/interfaces I had to do some changes for it to work, since it didn't load the wireless connection.

Try editing these /etc/network/interfaces lines, so that it looks like:

```

auto eth1
iface eth1 inet dhcp
#wireless-essid UAB

```

You'll probably need to reboot.
I hope it helps.[/QUOTE]

Actually, NetworkManager instructions explicitly state that you shouldn't do this: having these lines in the file doesn't allow NM to configure the connection anymore.

I had the same problem you mention - the system didn't load the ndiswrapper module at all, because that usually gets loaded after the /etc/network/interfaces file is read. Then, NM can't find the interface. I added a note to the end of wiki.ubuntu.com/NetworkManager about this.

I suggest that you comment out the interface again, like in the first post. Then force loading the ndiswrapper module by adding it to the end of /etc/modules.

---

### Post by precinto on 2006-06-10
I know the wiki says that, but it didn't work for me. (Maybe I did something wrong.)

Or maybe it's beacuse I'm not using ndsiwrapper...
I'm sorry if my info was misleading.

---

### Post by kurushi on 2006-06-11
Thank you very much for your help, I think network-manager is not working because I'm using it with 'acer-acpi' module. At last, I decided to use 'Wifi-radar' and is working perfectly.

Thanks again.

---

### Post by Bruhthakuga on 2006-08-12
Please help, I am losing hope, I exaulsted all resourses trying to use the native driver and now I am near my end with the ndsiwrapper.

I need help there when I am doing it like a phone call or IM.

I am sure that part of the problem is that no one source has all that I need and so I am gettin info from too many sources some are like me, nuckle heads, but they are trying to transmit info that they them selves are not yet done digesting.  Some of the instructions are too vaugue for Newbies, no exact code syntax.  If we can copy and paste we may make less mistakes.  

I just spent a lot of time on this forum got a lot of pages bookmarked.

I even keep a copy of everything that I do and everything in the Terminal, every code I enter and the output I copy to a document.

I am going to wash my car and when I get back I am going to try again and it would be a fine thing if I can get a helper on IM or the phone.

I may have to do a clean install again but till then here is everything I've done so far, The bold black is the code I entered without the results the blue is as it was copied from the Terminal but not nessasarily in one screen I may have a reboot or two not listed and some hand entered text I wrote to discribe some things I've done
:
[COLOR="Black"][B]
[B]sudo lspci
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
man fsch
fsch
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules
sudo gedit /etc/modprobe.d/ndiswrapper
sudo ndiswrapper -l
ifconfig
sudo ethtool eth0
sudo ethtool eth1
cat /etc/network/intefaces
sudo ifconfig eth1 up
sudo ifup eth1
ifconfig device eth1
help
ipconfig device wlan1
ipconfig device wlan0
sudo ifup eth1
ifconfig
lsmod
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
iwlist eth1 scan
sudo iwlist eth1 scan[/B][/B][/COLOR]
_________________________[COLOR="Blue"]

n@n-laptop:~$ **sudo lspci**
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:02.0 Network controller:** Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

n@n-laptop:~$ **sudo apt-get install ndiswrapper-utils**
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.2kB of archives.
After unpacking 139kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ndiswrapper-utils 1.8-0ubuntu2 [28.2kB]
Fetched 28.2kB in 0s (48.6kB/s)
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 71984 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.8-0ubuntu2_amd64.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

n@n-laptop:~$ **sudo ndiswrapper -i ~/Desktop/bcmwl5.inf**
Password:
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

n@n-laptop:~$ **sudo ndiswrapper -m**
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper


n@n-laptop:~$ **man fsch**
No manual entry for fsch

n@n-laptop:~$ **fsch**
bash: fsch: command not found

n@n-laptop:~$ [B]modprobe ndiswrapper
[/B]
n@n-laptop:~$ **echo ndiswrapper >> /etc/modules**
bash: /etc/modules: Permission denied

n@n-laptop:~$ **sudo gedit /etc/modprobe.d/ndiswrapper**
Password:

n@n-laptop:~$ **sudo ndiswrapper -l**
Installed ndis drivers:
bcmwl5          driver present, hardware present

n@n-laptop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:16:36:2C:7D:F2
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2c:7df2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2595464 (2.4 MiB)  TX bytes:288548 (281.7 KiB)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

n@n-laptop:~$ **sudo ethtool eth0**
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

n@n-laptop:~$ **sudo ethtool eth1**
Password:
Settings for eth1:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

n@n-laptop:~$ **cat /etc/network/intefaces**
cat: /etc/network/intefaces: No such file or directory

n@n-laptop:~$ **sudo ifconfig eth1 up**
Password:
eth1: ERROR while getting interface flags: No such device

n@n-laptop:~$ **sudo ifup eth1**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

n@n-laptop:~$ **ifconfig device eth1**
eth1: Unknown host
ifconfig: `--help' gives usage information.

n@n-laptop:~$ **ipconfig device wlan1**
bash: ipconfig: command not found

n@n-laptop:~$ **ipconfig device wlan0**
bash: ipconfig: command not found

n@n-laptop:~$ **sudo ifup eth1**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

n@n-laptop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:16:36:2C:7D:F2
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2c:7df2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2187523 (2.0 MiB)  TX bytes:223546 (218.3 KiB)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

n@n-laptop:~$ **lsmod**
Module                  Size  Used by
nls_utf8                3584  1
nls_cp437               8320  1
vfat                   16768  1
fat                    57136  1 vfat
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
radeon                124320  0
drm                    96296  1 radeon
powernow_k8            12992  0
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
ac                      7176  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
i2c_core               26624  1 i2c_acpi_ec
ndiswrapper           224064  0
ipv6                  300416  10
dm_mod                 63176  1
af_packet              28172  2
md_mod                 76792  0
sr_mod                 19748  0
sbp2                   27908  0
scsi_mod              160504  2 sr_mod,sbp2
parport_pc             40816  0
lp                     15040  0
parport                44172  3 ppdev,parport_pc,lp
joydev                 13184  0
snd_atiixp             23704  1
snd_atiixp_modem       19468  0
snd_ac97_codec        110396  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104584  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_p cm_oss
snd_timer              29064  1 snd_pcm
snd                    68576  9 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_p cm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  3 snd_atiixp,snd_atiixp_modem,snd_pcm
tsdev                  10240  0
usbhid                 43040  0
pcmcia                 46368  0
sdhci                  17024  0
mmc_core               35460  3 sdhci
psmouse                40324  0
serio_raw               9732  0
pcspkr                  3592  0
8139cp                 26752  0
8139too                31744  0
mii                     7680  2 8139cp,8139too
yenta_socket           30604  1
rsrc_nonstatic         14592  1 yenta_socket
pcmcia_core            48036  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
evdev                  14464  4
ext3                  145936  1
jbd                    70952  1 ext3
ide_generic             2816  0
ohci1394               37324  0
ieee1394              369048  2 sbp2,ohci1394
ehci_hcd               36232  0
ohci_hcd               23684  0
usbcore               147004  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
ide_cd                 35744  0
cdrom                  41144  2 sr_mod,ide_cd
ide_disk               19456  3
generic                 7300  0
atiixp                  8464  1
thermal                16524  0
processor              29736  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
n@n-laptop:~$

n@n-laptop:~$ **sudo ndiswrapper -i bcmwl5.inf**
Password:
bcmwl5 is already installed. Use -e to remove it

n@n-laptop:~$ **sudo ndiswrapper -m**
modprobe config already contains alias directive[/COLOR]

I used the Synaptic Package Maneger to install ndisgtk

I rebooted[COLOR="Blue"]

n@n-laptop:~$ **iwlist eth1 scan**
eth1      Interface doesn't support scanning.

n@n-laptop:~$ **sudo iwlist eth1 scan**
Password:
eth1      Interface doesn't support scanning.[/COLOR]

When I check the “interfaces” file in the /etc/network folder with a text editor it says:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by arthur_kalm on 2006-11-27
Hmm why are you using ndiswrapper that is in the repository. That one sucks balls. Check out [this howto]("http://www.ubuntuforums.org/showthread.php?t=297092").

---

### Post by coln_sanders on 2006-11-27
Bruhthakuga,

I've also went through quite a bit to get my wireless working, and I was just looking for the reason why mine doesn't display what wireless networks are in range.  Anyway, onto what you are trying to do, I noticed you had commands like:

[COLOR="Blue"]n@n-laptop:~$ ifconfig device eth1
eth1: Unknown host
ifconfig: `--help' gives usage information.

n@n-laptop:~$ ipconfig device wlan1
bash: ipconfig: command not found

n@n-laptop:~$ ipconfig device wlan0
bash: ipconfig: command not found[/COLOR]

and:

[COLOR="Blue"]n@n-laptop:~$ iwlist eth1 scan
eth1 Interface doesn't support scanning.

n@n-laptop:~$ sudo iwlist eth1 scan
Password:
eth1 Interface doesn't support scanning.[/COLOR]

The reason you're getting the "eth# Interface doesn't support scanning" is that the devices you're trying to use are not wireless devices.
When you're trying to use your wireless connections, you have to use:

[COLOR="Blue"]sudo iwconfig wlan0[/COLOR]

and:

[COLOR="Blue"]sudo iwlist wlan0 scan[/COLOR]

When you ran

[COLOR="Blue"]n@n-laptop:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper[/COLOR]

you set your wireless connection to be "wlan0".  I also have a Broadcom wireless device, and I went through all of this twice... once in Dapper and once in Edgy =D.  I hope a this makes a few things a little clearer.  I am also quite new to Linux in general, so if you need any more than that, I probably won't be able to help you.

My regards,
Coln_Sanders

---

### Post by domer on 2007-03-30
I upgraded to Edgy from Dapper and wireless is not working anymore on my laptop with the infamous Broadcom 4813 wireless card. 

When I run [COLOR="Red"] iwconfig[/COLOR] I get the following: 

[COLOR="RoyalBlue"]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/COLOR]

Can anyone please help me how to fix this. My network mananager does not show the wireless network adapter, but typing "lspci" reveals that I have a Broadcom 4813 card installed. Please help.

---

