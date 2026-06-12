---
title: "Can't conect to a wireless line"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by manfredrasta on 2010-09-24
(GO TO POST #13 TO SEE QUICK SOLUTION)

Hi to everyone,

I am an absolute beginner and have installed LUbuntu from a desktop cd-rom in my Toshiba Satellite Pro 4600. There is a Pentium III inside.

I have searched in the forum and found that it is a common problem, but the solutions explained either did not work in my computer or I did not understand them. Maybe together we can fix the problem.

I do not know how to connect to mi wi-fi conection. In the menu of the Network conections, I choose the label "wireless", then click to "add", give a name to the conection, write the ESSID, and the password (WPA) and click "Ok" to save. So my conection appears on the list o Wireless connections. 

But now, what should I do? Nothing (as a wi-fi icon) appears on the bar (there is just the cabled connection icon, because I am conected with the ethernet cable). If I click on the cabled connection icon there is no wireless option available...

Can anybody help me please? Thanks a lot.

---

### Post by manfredrasta on 2010-09-27
I have done some researching. As with Xubuntu it "sees" my wifi line, I have typed some commands there so we can compare to the same commands in Lubuntu:



_**Using [SIZE="4"]Xubuntu 9.04[/SIZE]**_ (from the live cd):
```

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:1
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
and
```

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:b7:b6:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.1.3 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:23:9e:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.14 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:3c:77:94:74:5f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```



_**Using [SIZE="4"]Lubuntu 10.04[/SIZE]:**_
```

marino@marino-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
and
```

marino@marino-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:b7:b6:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.3 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:f7dff000-f7dfffff ioport:df40(size=64)

```
and
```

marino@marino-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)


```

Thank you!

---

### Post by cavalier911 on 2010-09-27
```
sudo apt-get install pcmciautils
```
Reboot with your wireless card in the slot.
```
lspci
```
```
ifconfig
```
Plus the commands you ran on xubuntu.
You should see the wireless card listed now.

Right click the network manager icon between the clock and volume control lower right corner of screen to bring up menu.
Left click Check **Enable Networking** and **Enable Wireless **
Left click **Edit Connections..**
Wireless Tab,Add username,password,etc...

---

### Post by manfredrasta on 2010-09-28
> **cavalier911 said:**
> 
Reboot with your wireless card in the slot.

I have a built-in wireless card. If it is important.

> **cavalier911 said:**
> ```
sudo apt-get install pcmciautils
```
Reboot with your wireless card in the slot.
```
lspci
```
```
ifconfig
```
Plus the commands you ran on xubuntu.
You should see the wireless card listed now.

Right click the network manager icon between the clock and volume control lower right corner of screen to bring up menu.
Left click Check **Enable Networking** and **Enable Wireless **
Left click **Edit Connections..**
Wireless Tab,Add username,password,etc...

Thank you very much cavalier911. I have done:
```
sudo apt-get install pcmciautils
```
then rebooted, and then, great! If I do left-click on the network manager icon it shows me a list of the wireless networks. So my card works! But I cannot still connect:
I do Right click on the network manager icon, edit conections, wireless tab, enter the name, the SSID and the password (in my case it is a WPA personal).

Now I do left-click on the NM icon and select my network. Then it ask me for the password (dont know why if I have just done it while editting my conection), so I type it, click Conect, wait, wait, wait, and it reopens the pasword form (without any message like 'the password is not correct'). I am writing the password correctly, I have entered the modem and look at the password and SSID, three times :)...

I paste you these commands runned after rebooting:

```

marino@marino-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)

```
[COLOR="Red"]here only changes that the last line is two times one with 02:0d.1[/COLOR]
and
```

marino@marino-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:b7:b6:81  
          indirizzo inet:192.168.1.3  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::200:39ff:feb7:b681/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1367 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:1428695 (1.4 MB)  Byte TX:179972 (179.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:23:9e:fe  
          indirizzo inet6: fe80::202:2dff:fe23:9efe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:88436 (88.4 KB)  Byte TX:1193 (1.1 KB)
          Interrupt:11 Indirizzo base:0xd100 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:49064 (49.0 KB)  Byte TX:49064 (49.0 KB)

```
and
```

marino@marino-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"\x02\xF4\xB2\xEDr\x16\xEC\xF3\x01M\xF0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-35 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and
```

marino@marino-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:b7:b6:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.3 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:f7dff000-f7dfffff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:23:9e:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b

```

Thank you again. Its been 3 days of fighting with my laptop and now it look like there is a ligth at he other end of the tunnel :)


_EDIT:_ to see if it was a problem of the password, I entered the modem, cancelled the password so my network is unlocked, and reboot.
Now left-click in the MN icon, and see my network unlocked. Nice. I click on it and it tries to conect (the NM icon changes to a 'loading' icon). Wait, wait, wait, and it returns to the NM icon (in the 'disconected style') and shows a dialog saying wire-less network is disconnected.
So, it is not a problem of the password, isn't it?
Shall I install orinoco drivers?

---

### Post by grahammechanical on 2010-09-28
In my experience (little experience) I have found that if you have not ticked Connect Automatically then you will be asked for a password (Authenticate) whenever you select your wireless network (or any secured wireless network).

I have also found that repeat requests for authentication are due to wrong password. Your are right. You do not get a "wrong password" message. 

Further more, once you put a wrong password in then that is remembered and is compared to the next attempt which may be the correct password but it is rejected because it is not accepted as official. Go back to Edit Connections, tick Show Password and see if the password is still the correct one. I speak from experience.

Regards.

---

### Post by grahammechanical on 2010-09-28
I have just had another idea. :P in a terminal code

```
nm-tool
``` 

It will list all the devices being managed by network manager. Do you see a list of wireless Access Points? Is your one among them? Do you see Device wlan0? My listing shows that the Wireless connection is disconnected. This is because I am connected by cable. eth0 [Auto eth0].  Does the first line say, State:Connected. I am not sure what that means but I think that it is important.

I hope this helps. Regards.

---

### Post by manfredrasta on 2010-09-29
Hi, and thanks for answering.

```

marino@marino-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:00:39:B7:B6:81

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:23:9E:FE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    FionaWeb:        Infra, 00:24:01:4B:72:D5, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA
    Pc-Portatile-Wireless: Infra, 00:26:F2:60:79:EA, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    Alice-75202547:  Infra, 00:1D:6A:71:60:F3, Freq 2462 MHz, Rate 11 Mb/s, Strength 67 WPA WPA2

```

So I am not connected. It is not a problem of the password because I have entered the modem settings, cancell the password, and try to connect, but nothing. It just try. After 1 minute trying to connect, it disconnects.

---

### Post by cavalier911 on 2010-09-29
The early internal wireless cards use an internal pcmcia to pci bridge.
This would explain the wireless card not identifying itself on lspci and not installing without pcmciautils.
You may be able to get more info on the card:
```
pccardctl ident
```Run pccardctl --help and man pccardctl for a description and explanation of each command.Try them all, if something comes up post it.
lshw -C Network indicates you have the HERMES chip manufactured by lucent/agere
One difference of possible significance could be that on Xubuntu 9.04 which works the firmware is version 6.14 , Lubuntu 10.04 which does not work is firmware version 9.48
There are problems Ubuntu 10.04 with the orinoco_cs drivers firmware
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336)
The firmware files:
/lib/firmware/agere_ap_fw.bin 
/lib/firmware/agere_sta_fw.bin

Check dmesg for errors related to the loading of driver or firmware.
```
dmesg | grep -e orinoco -e eth
```To see where the connection attempt fails:
Stop NetworkManager:
```
sudo service network-manager stop
```Restart in verbose mode:
```
sudo NetworkManager --no-daemon
```

---

### Post by grahammechanical on 2010-09-30
Hi manfredrastra

From the listing of nm-tool I see that your WiFi is listed as eth1. On my computer the WiFi is listed as wlan0. May I suggest that you use the Network Manger Icon to disconnect from eth0 (Auto eth0) and then connect to eth1. Set to Connect automatically using edit connections. Then it should become Auto eth1.

regards.

nm-tool is listing wireless access points and showing their signal strength. That tells me that wirless on ypour computer is working.

---

### Post by manfredrasta on 2010-10-01
> **cavalier911 said:**
> The early internal wireless cards use an internal pcmcia to pci bridge.
This would explain the wireless card not identifying itself on lspci and not installing without pcmciautils.
You may be able to get more info on the card:
```
pccardctl ident
```Run pccardctl --help and man pccardctl for a description and explanation of each command.Try them all, if something comes up post it.

So,
```

marino@marino-laptop:~$ pccardctl --help
pcmciautils 014
Copyright (C) 2004-2005 Dominik Brodowski, (C) 1999 David A. Hinds
Report errors and bugs to <linux-pcmcia@lists.infradead.org>, please.
Usage: pccardctl COMMAND
Supported commands are:
	ls
	insert
	eject
	suspend
	resume
	reset
	info
	status
	config
	ident

```

```

marino@marino-laptop:~$ pccardctl ident
Socket 0:
  product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
Socket 1:
  no product info available
Socket 2:
  no product info available

```

```

marino@marino-laptop:~$ pccardctl ls
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:0c.0)
Socket 0 Device 0:	[orinoco_cs]		(bus ID: 0.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:0d.0)
Socket 2 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:0d.1)

```

```

marino@marino-laptop:~$ pccardctl info
PRODID_1="TOSHIBA"
PRODID_2="Wireless LAN Card"
PRODID_3="Version 01.01"
PRODID_4=""
MANFID=0156,0002
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```

```

marino@marino-laptop:~$ pccardctl status
Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "orinoco_cs"
Socket 1:
  no card
Socket 2:
  no card

```

```

marino@marino-laptop:~$ pccardctl config
Socket 0:
command 'config' not yet handled by pccardctl

```

The other commands didn't do anything.

> **cavalier911 said:**
> lshw -C Network indicates you have the HERMES chip manufactured by lucent/agere
One difference of possible significance could be that on Xubuntu 9.04 which works the firmware is version 6.14 , Lubuntu 10.04 which does not work is firmware version 9.48

I have to tell you that with Xubuntu I could see my wifi line (without 'sudo apt-get install pcmciautils'), but couldn't connect aswell. I had the same problem.

> **cavalier911 said:**
> There are problems Ubuntu 10.04 with the orinoco_cs drivers firmware
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336)
The firmware files:
/lib/firmware/agere_ap_fw.bin 
/lib/firmware/agere_sta_fw.bin

Check dmesg for errors related to the loading of driver or firmware.
```
dmesg | grep -e orinoco -e eth
```

OK,
```
marino@marino-laptop:~$ dmesg | grep -e orinoco -e eth
[    2.951790] e100: eth0: e100_probe: addr 0xf7dff000, irq 11, MAC addr 00:00:39:b7:b6:81
[   16.772963] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   19.671830] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.930120] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   20.009906] orinoco_cs 0.0: Hardware identity 0005:0002:0001:0002
[   20.010017] orinoco_cs 0.0: Station identity  001f:0001:0006:000e
[   20.010028] orinoco_cs 0.0: Firmware determined as Lucent/Agere 6.14
[   20.373455] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.376241] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   20.376629] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.396380] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   20.733009] orinoco_cs 0.0: Hardware identity 0005:0002:0001:0002
[   20.733146] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[   20.733157] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[   20.733165] orinoco_cs 0.0: Ad-hoc demo mode supported
[   20.733172] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[   20.733180] orinoco_cs 0.0: WEP supported, 104-bit key
[   20.733187] orinoco_cs 0.0: WPA-PSK supported
[   21.281011] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.968138] eth1: Lucent/Agere firmware doesn't support manual roaming
[   30.712047] eth0: no IPv6 routers present
[   32.123345] eth1: Lucent/Agere firmware doesn't support manual roaming
[   37.271901] eth1: Lucent/Agere firmware doesn't support manual roaming
[   42.436817] eth1: Lucent/Agere firmware doesn't support manual roaming
[   47.592543] eth1: Lucent/Agere firmware doesn't support manual roaming
[   52.788325] eth1: Lucent/Agere firmware doesn't support manual roaming
[   57.950177] eth1: Lucent/Agere firmware doesn't support manual roaming
[   63.106899] eth1: Lucent/Agere firmware doesn't support manual roaming
[   68.260837] eth1: Lucent/Agere firmware doesn't support manual roaming
[   73.428860] eth1: Lucent/Agere firmware doesn't support manual roaming
[   78.575235] eth1: Lucent/Agere firmware doesn't support manual roaming
[  387.536427] eth1: Lucent/Agere firmware doesn't support manual roaming
[  392.695906] eth1: Lucent/Agere firmware doesn't support manual roaming
[  397.860642] eth1: Lucent/Agere firmware doesn't support manual roaming
[  403.029618] eth1: Lucent/Agere firmware doesn't support manual roaming
[  408.241003] eth1: Lucent/Agere firmware doesn't support manual roaming
[  413.463053] eth1: Lucent/Agere firmware doesn't support manual roaming
[  418.649989] eth1: Lucent/Agere firmware doesn't support manual roaming
[  423.932584] eth1: Lucent/Agere firmware doesn't support manual roaming
[  429.124975] eth1: Lucent/Agere firmware doesn't support manual roaming
[  434.287595] eth1: Lucent/Agere firmware doesn't support manual roaming
[  439.455880] eth1: Lucent/Agere firmware doesn't support manual roaming
[  444.621741] eth1: Lucent/Agere firmware doesn't support manual roaming
```

So I have the same error as in that page ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336)). Isn't it? I must say that I have cacelled the password in the modem so now I am trying to access a non protected wifi line.

In that bug-report Bernie du Breuil wrote on 2009-12-29: "I have the same problem on my Dell C400. But first I had to install the Lucent/Agere 9.48 firmware in /lib/firmware. Also Karmic 9.10. Identical problem occurred when booting from the LiveDVD."

Does it mean that I have to install the Lucent/Agere 9.48 firmware in /lib/firmware? How do i do it? :)

> **cavalier911 said:**
> To see where the connection attempt fails:
Stop NetworkManager:
```
sudo service network-manager stop
```Restart in verbose mode:
```
sudo NetworkManager --no-daemon
```
This is what it writes on the terminal while trying to connect:
```
marino@marino-laptop:~$ sudo service network-manager stop
[sudo] password for marino: 
network-manager stop/waiting
marino@marino-laptop:~$ sudo NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  Trying to start the modem-manager...
NetworkManager:    SCPlugin-Ifupdown: init!
NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
NetworkManager:    SCPluginIfupdown: management mode: unmanaged
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0, iface: eth0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/0.0/net/eth1, iface: eth1)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/0.0/net/eth1, iface: eth1): no ifupdown configuration found.
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
NetworkManager:    SCPlugin-Ifupdown: end _init.
NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/0.0/ieee80211/phy0/rfkill0) (driver <unknown>)
NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
NetworkManager:    SCPlugin-Ifupdown: (135283440) ... get_connections.
NetworkManager:    SCPlugin-Ifupdown: (135283440) ... get_connections (managed=false): return empty list.
NetworkManager:    Ifupdown: get unmanaged devices count: 0
NetworkManager: <info>  (eth0): carrier is OFF
NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
NetworkManager: <info>  (eth0): now managed
NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device (reason: 2).
NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0
NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'orinoco_cs')
NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
NetworkManager: <info>  (eth1): now managed
NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (eth1): bringing up device.
NetworkManager: <info>  (eth1): preparing device.
NetworkManager: <info>  (eth1): deactivating device (reason: 2).
NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
NetworkManager: <info>  Activation (eth1) starting connection 'Auto FionaWeb'
NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto FionaWeb' requires no security.  No secrets needed.
NetworkManager: <info>  Config: added 'ssid' value 'FionaWeb'
NetworkManager: <info>  Config: added 'scan_ssid' value '1'
NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Config: set interface ap_scan to 1
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  eth1: link timed out.
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  eth1: link timed out.
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
NetworkManager: <info>  Activation (eth1/wireless): association took too long, failing activation.
NetworkManager: <info>  (eth1): device state change: 5 -> 9 (reason 11)
NetworkManager: <info>  Activation (eth1) failed for access point (FionaWeb)
NetworkManager: <info>  Marking connection 'Auto FionaWeb' invalid.
NetworkManager: <info>  Activation (eth1) failed.
NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (eth1): deactivating device (reason: 0).

```

Thank very much.

---

### Post by grahammechanical on 2010-10-01
According to the listing from the command: NetworkManager --no-daemon, your wireless card is being activated and the wireless network is being detected.

> <info> Activation (eth1/wireless): connection 'Auto Fionaweb' requires no security. No secrets needed.

As you say, it is no longer secured. The system then tries repeatedly to connect. It scans, tries to associate, and then disconnects. finally after several attempts it gives up trying.

I do not know how any of this helps but can you link to the modem/router by cable and access the modem set up program with a web browser. There might be something that you will notice. Something is stopping the OS from "associating" with the modem.

regards.

---

### Post by manfredrasta on 2010-10-03
> **grahammechanical said:**
> According to the listing from the command: NetworkManager --no-daemon, your wireless card is being activated and the wireless network is being detected.



As you say, it is no longer secured. The system then tries repeatedly to connect. It scans, tries to associate, and then disconnects. finally after several attempts it gives up trying.

I do not know how any of this helps but can you link to the modem/router by cable and access the modem set up program with a web browser. There might be something that you will notice. Something is stopping the OS from "associating" with the modem.

regards.

Thanks again. But I don't think I should modify any settings of the modem because I have another laptop (with windows) that connects perfectly (wouldn't like to get that not working :)).

---

### Post by manfredrasta on 2010-10-04
Finnaly I solved this.

I just installed wicd (another program like network manager), then uninstalled network manager. Reboot the laptop... Click on the wicd icon near the clock, clicked on conect to my wireless nw, and it done it! I'm so happy... XD

Thank you everyone who helped me! Thank you very much!

---

### Post by manfredrasta on 2010-10-04
QUICK SOLUTION (what I have done since the begining):

[LIST=1]
[*]Run the command ```
sudo apt-get install pcmciautils
``` to be able to see my wifi network
[*]Install wicd from synaptics
[*]Uninstall network manager package
[/LIST]

Thanks again

---

