---
title: "lucid 10.04 wireless card detected, not working"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by rhyz on 2010-05-07
I started on ubuntu 8.10 and my wireless card has always worked,
Since i did a fresh install of ubuntu 10.04 it still seems to work to a point.

I can see networks, click them and use a password to connect but it never seems to carry on, I typed the password correctly and after a minute it asks for it again.

I have read a post about problems other people are having and that i need to install a different program.

But i cant install another program if there is no wireless as apt-get doesn't work without internet connection.

So... I need to download something that will fix it (possible update if one has been released) to xp (partition) then access xp partition from ubuntu and install it.

Any help would be great thanks :) Rhys

---

### Post by Iowan on 2010-05-07
Did you happen to install the "restricted drivers"? 
[http://ubuntuforums.org/showthread.php?t=1471489]("http://ubuntuforums.org/showthread.php?t=1471489")

---

### Post by rhyz on 2010-05-08
I dont know, i used alternate install and installed ubuntu-desktop that was it i think.

How can i check if they have been installed and can i not just remove them instead of reinstall?

---

### Post by pdc on 2010-05-08
most computers now have google available

if you search on 

> 2010 how to install restricted drivers ubuntu

you get this

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

and if click on the restricted drivers button you get this guide

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html#proprietary%20restricted%20software](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html#proprietary%20restricted%20software)

and it even gives you a button to click on

---

### Post by rhyz on 2010-05-08
I dont know if i installed restricted drivers.

I used alternate cd and installed ubuntu-desktop,

It did the rest for me.

Is there no command i can put in terminal to list drivers?
Or i read on your link something about flash player if that was installed would it mean i installed the restricted drivers?

I am very confused about this!

---

### Post by rhyz on 2010-05-08
update: on wifi hotspots still does not connect. Off subject disk utility is a nice program told me a lot of info

update again

lshw for network

```

*-network
description: Wireless interface
physical id: eth1
serial: xxx
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b

```

---

### Post by rhyz on 2010-05-09
Bump!!!

---

### Post by pdc on 2010-05-10
this is a diagnostic script that analyses wireless setup; overseen by a linux enthusiast; 

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

download it and run it; it will provide answers; if they aren't enough, post all the results back here for folks to help you with it

---

### Post by rhyz on 2010-05-10
ok Ran the script nothings changed, output below (this was the text file the script made...)

```


--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: Â§Â§Â§Â§Â§Â§Â§Â§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
cat: /etc/resolv.conf: No such file or directory
==================================================================================================================
*** cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubuntu
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x8c00 
eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8680 (8.6 KB)  TX bytes:8680 (8.6 KB)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
==================================================================================================================
*** lspci
00:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
==================================================================================================================
*** lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==================================================================================================================
*** lsmod # (filtered)
Unrecognized character \xBF in column 40 at -e line 1.
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11b  ESSID:"Â§Â§Â§Â§Â§Â§Â§Â§2"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:7
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
16:10:55 2010-05-10
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May 10 11:11:38 ubuntu kernel: [  545.973155] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 11:11:43 ubuntu kernel: [  551.560132] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 15:53:33 ubuntu kernel: [ 1407.200280] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 15:53:39 ubuntu kernel: [ 1412.581132] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 15:53:44 ubuntu kernel: [ 1417.852908] eth1: Lucent/Agere firmware doesn't support manual roaming
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | ath3k-1.fw               |
| atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin      |
| atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin       |
| atmsar11.fw             | av7110                  | bnx2                    | bnx2x-e1-4.8.53.0.fw     |
| bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                      |
| cpia2                   | cxgb3                   | dabusb                  | dsp56k                   |
| dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                    | ea                       |
| edgeport                | emi26                   | emi62                   | ess                      |
| i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw           |
| ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw          |
| ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode     |
| iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| kaweth                  | keyspan                 | keyspan_pda             | korg                     |
| libertas                | matrox                  | mts_cdma.fw             | mts_edge.fw              |
| mts_gsm.fw              | mwl8k                   | myricom                 | NPE-B                    |
| NPE-C                   | ositech                 | ql2100_fw.bin           | ql2200_fw.bin            |
| ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin            |
| qlogic                  | r128                    | radeon                  | rt2561.bin               |
| rt2561s.bin             | rt2661.bin              | rt2860.bin              | rt2870.bin               |
| rt73.bin                | RTL8192SE               | sb16                    | scripts                  |
| slicoss                 | sun                     | sxg                     | tehuti                   |
| ti_3410.fw              | ti_5052.fw              | tigon                   | tr_smctr.bin             |
| ttusb-budget            | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    Channel:11
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Â§Â§Â§Â§Â§Â§Â§Â§3"
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Channel:11
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"Â§Â§Â§Â§Â§Â§Â§Â§4"
                    Channel:11
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"Â§Â§Â§Â§Â§Â§Â§Â§1"
                    Channel:11
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Â§Â§Â§Â§Â§Â§Â§Â§2"
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:eth1 IM:2 DI:2 AP:1 FALON:0 

```

---

### Post by msmoore on 2010-05-10
I'm having somewhat of the same problem (and so did my friend).  We each had working wifi cards with ubuntu 8, but now when we upgraded to ubuntu 10 they don't work.  He went back to 8.  I'm not upgrading my other computer for fear of the same thing!  They are 3 different computers having the same issues. 

I got the recent upgrade, just by hitting the upgrade button.  I didn't install with a cd and I don't recall an option regarding restricted items.  I looked at the links about restricted software and it said nothing about wifi cards.

Any ideas?

---

### Post by pdc on 2010-05-10
so the system shows; amongst other things

> lspci Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

if you google on 

> ubuntu RTL-8139

you such posts as this recent one

[http://ubuntuforums.org/showthread.php?t=1406907](http://ubuntuforums.org/showthread.php?t=1406907)

chili555 suggested

> sudo ethtool eth0
lsmod | grep 813
lspci -nn | grep Ethernet

what about you do the same, 

ie copy and paste those three separate commands into a terminal, and then copy and paste the results back here;

and also have a read at the post to see if you might have a similar problem; the rtl-8139 is a venerable warrior; there are posts back to at least 2005 with drivers from then;

---

### Post by Crio on 2010-05-11
10.04 supports switching off (blocking) wireless, but it seems to be somewhat buggy and tend to start in the off state. For example [http://ubuntuforums.org/showthread.php?t=1466992](http://ubuntuforums.org/showthread.php?t=1466992)
Try "rfkill list" and/or pressing wifi on/off buttons on your keyboard if you have them.

---

### Post by rhyz on 2010-05-11
Right i will have a look,

I didnt think the wired connection would effect the wireless but i will give it a go i will try anything!

---

### Post by rhyz on 2010-05-11
results of running

```


sudo ethtool eth0
lsmod | grep 813
lspci -nn | grep Ethernet


```

```


rhys@ubuntu:~$ sudo ethtool eth0
[sudo] password for rhys: 
sudo: ethtool: command not found
rhys@ubuntu:~$ lsmod | grep 813
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
rhys@ubuntu:~$ lspci -nn | grep Ethernet
00:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


```

---

### Post by framplinux on 2010-05-11
> !!! CND0110E: For the selected connection type there was no active network interface found on your system
That's a false positive. I'll fix the code.
> 
*** lsmod # (filtered)
Unrecognized character \xBF in column 40 at -e line 1.

That's a globalization issue which I fixed right now.

---

### Post by rhyz on 2010-05-13
Ive done a fresh install and still not working it trys to connect but asks for password after a min

---

### Post by chlorinekid on 2010-05-13
problem could be related to this thread

[http://ubuntuforums.org/showthread.php?p=9235630#post9235630](http://ubuntuforums.org/showthread.php?p=9235630#post9235630)

try blacklisting as suggested in the thread, let us know how you get on.

---

### Post by rhyz on 2010-05-16
Hello Sorry i have not replyed i work weekends.

I tried blacklisting nothing changed it is not a usb wireless card it is a cardbus card.

anyway some luck a little information from the terminal i think might help :)!!!

```

do lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:b6:df:72
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:10 ioport:8c00(size=256) memory:ec002800-ec0028ff
  *-network
       description: WLI-PCM-L11
       product: Version 01.01
       vendor: MELCO
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:4f:ae:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b


```

Ethernet is correct and i dont use this.
The second is my card that should work :) has the correct name and everything.
The last i dont know?

I can see networks but not connect even open networks!

Thanks

---

### Post by eltonw on 2010-05-16
> **rhyz said:**
> Hello Sorry i have not replyed i work weekends.

I tried blacklisting nothing changed it is not a usb wireless card it is a cardbus card.

anyway some luck a little information from the terminal i think might help :)!!!

```

do lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:b6:df:72
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:10 ioport:8c00(size=256) memory:ec002800-ec0028ff
  *-network
       description: WLI-PCM-L11
       product: Version 01.01
       vendor: MELCO
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:4f:ae:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b


```

Ethernet is correct and i dont use this.
The second is my card that should work :) has the correct name and everything.
The last i dont know?

I can see networks but not connect even open networks!

Thanks

What machine are you running? I have an Asus netbook with a _**[COLOR="Sienna"]RaLink[/COLOR]**_ card.
This is how I installed Lucid (and had network connectivity WORKING):
[http://ubuntuforums.org/showthread.php?p=9203922#post9203922]("http://ubuntuforums.org/showthread.php?p=9203922#post9203922") [#136]

In your case, yours is a **[COLOR="Red"]Realtek[/COLOR]** product, and linux [COLOR="Red"]drivers[/COLOR] are here: [http://www.opendrivers.com/company/2358/realtek-free-driver-download.html]("http://www.opendrivers.com/company/2358/realtek-free-driver-download.html")

If you are stil unsuccessful, you might try a newer kernel than the current one / available update in Lucid.

You might want to try the 2.6.33 one:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

[COLOR="Purple"][FONT="Comic Sans MS"]There are fixes in the newer kernels which have resolved connection problems for others[/FONT][/COLOR].

(FWIW: I'm using the 2.6.34 rc kernel.) 

HTH

---

### Post by rhyz on 2010-05-16
The realtek is my ethernet built in to the laptop,

I want the wireless working, I didnt think they would mess each other up,

You can see my wireless card is a

> 
  *-network
       description: WLI-PCM-L11
       product: Version 01.01
       vendor: MELCO
       physical id: 0
       slot: Socket 0
       resources: irq:3


I will try a newer kernel. The only thing i cant see is why it would work in 8.10 9.04 and not 10.04

---

### Post by rhyz on 2010-05-16
now have new kernel and nothing has changed apart from loosing boot screen but not bothered by that

---

### Post by rhyz on 2010-05-18
Bump

---

### Post by MACE1 on 2010-11-18
Did you ever get to the bottom of your problem ?

I have a Buffalo WLI-PCM-L11 802.11B CARD which was natively supported in V8 but now 10.04 does not even detect it ! I believe some used orinoco_cs.c which covered quite a number of devices to use my device and probably yours.
As yet I have no idea how if at all I am supposed to make use of the C driver in 10.04 but I will persevere.

---

### Post by rhyz on 2010-11-18
Hello :)

I have not found a answer to sorting the card!
My card was detected and would see networks but on connection would ask for the password.

I was hoping it would be fixed by 10.10 and have only just got the cd. i tried it live and still the same problem!

As far as i can tell they updated the oronico driver from ubuntu8.10-9.04 (never tried 9.10) and so by 10.04 it didnt work.

I havent got a clue how to change drivers ect and didnt receive much help on getting it fixed.

Still ubuntu is a good os and 10.10 seemed very fast running from cd!

If you find any info id be greatfull and will be happy to help get it fixed (if i can :D)

---

### Post by wallydallas on 2011-10-07
Plus one here.  Ubutu 8.04 was working on laptop with Lucent PCMCIA wifi card.  Wiped the drive with Dban.  Installed Ubuntu 10.04 from the default CD.  

steps: 
1- boot freshly installed 10.04 system from CD
[http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts)

2- notice: wifi can see networks using the menu bar at the top right hand side of screen.

3- use mouse to select a network that works, and uses wep password
4- see dialog box asking for password
5- enter on keyboard the 5 digit WEP password

result: the system tries for 60 seconds, then asks for the password again.  

expected result: enter password, see the 5 bars of signal at the top left corner of the screen near the clock.

footnotes:
connected cat5 to the laptop
apt-get update
apt-get upgrade
removed cat5
rebooted
same result, wifi fails to connect.

If you google 
ubuntu wifi lucent fail
the result:
lots of people have the same problem. None of the wild guesses at fixes work.    It would be great if someone from Canonical or paid would test this Lucent PCMCI card. It's an extremely common card out there.  

I can send you the PCMCIA card.  I was able to get my laptop working by using a Dlink wifi pcmcia card.

---

### Post by rhyz on 2011-10-08
Hey bit of a old post now but i never did manage to get it working! Then we updated our wifi router and card became totaly useless as it wouldnt even connect with xp, so updated card and this was another one with hard to install drivers on ubuntu so got a bit fed up lol...

Anyway bought myself a lovley new laptop 
hp dv6-3122sa
2.4ghz amd dual, 4gb, power saving 4250 and performance 5470 gpu, 500gb 7200 gb hdd!
and its all good using live cd but im staying with windows 7 for a little! though i miss learning things with terminal :/ and just general linux!

Sorry im not much help!

---

### Post by wallydallas on 2011-10-08
Thanks for saying hello Mr/Ms Rhyz.   No worries.  Enjoy your new hardware. Dump windows 7 in a few months and leave the dark side of the force to join the rebels again.  

You did a good job reporting this bug.  You also got some advice that put a lot of burden on you, and you took on that burden.

Here is the summary:  Laptops often use PCMCIA cards for WiFi.  A very common PCMCIA card is the Lucent or Orinoco card.   It works great with Ubuntu 8.04 out of the box. No technician needed.

With Ubuntu 10.04 the card seems to see hotspots and lists the SSID names.  However, if you use WEP passwords, it does not work and fails when you try to enter a password.  If you have no passwords on your hotspot it will connect, and then stop after a short while. 

None of the advice I've found with Google will let an expert user user repair the system with a fix.

the fix:  Buy a different PCMCIA wifi card.   

I'll be reporting this to the staff working on Ubuntu 11 beta.  The bug still exists there.    Someone might argue this bug fix is not significant due to the small number of humans with this hardware.    However, fixing this bug may reveal a flaw in the system that would cause future bugs, or resolve failures that are too hard to debug.    Many times after software is patched for bug #2 then magically bug 3,4 and 5 vanish. 

There are still a lot of old laptops in various countries that depend on PCMCIA.   Fixing this in Ubuntu will help Xubuntu and other lean linux distros that run on older hardware.

Lucent Orinoco Gold PCMCIA card
FCC ID:   IMRWLPCE24H
PN: 014916/A
TN:  03039366
[http://www.techedgeezine.com/images/lucent_orinoco_gold.jpg]("http://www.techedgeezine.com/images/lucent_orinoco_gold.jpg")


Lucent Silver WaveLan PCMCIA card
FCC ID: IMRWLPCE24H
PN:  012372/D
TN: 03859204

[http://www.alldigitalhome.com/network/images/WaveLan.gif]("http://www.alldigitalhome.com/network/images/WaveLan.gif")

---

### Post by Stolgrove on 2011-10-09
This is looking like a common problem, I'm running the netbook version of 10.04 with Artheros wifi, and I just managed to get the card to a point where it sees the networks and tries to connect, but then times out. 
The Ethernet is on a different level and doesnt even register when I plug a cable into it. 
I'm still working trying to figure this out for myself. Maybe someone will have an ideal soon.

---

### Post by rhyz on 2011-10-09
Wow wally! Thanks for the support you've summed it up nicley but i could actually never get connected to a open network either! I dont know if this is because the hotspot was a newer radio signal or just because of the driver problems! I belive i was connecting to a btfon and as i couldn't via XP im guessing this is why i couldnt in ubuntu?!

And about joining the "dark side" i was thinking of starting off with a live USB drive ubuntu 11.10 with gnome3?! Iv'e played on gnome3 and love it! And as our hardware is more capable :D and supports USB booting think its the best of both worlds Kind of!

Thanks
_MR_ Rhys :)

---

