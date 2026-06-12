---
title: "WPA Wireless Issue with Dell Latitude X200 and Ubuntu 8.10"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Nasreen on 2009-01-25
Hi All,
I am new here and new to Ubuntu/*nix all together.  I have to say sorry in advance for the long post.  
I have a Dell Latitude X200 (a little machine) that I am trying to use for Ubuntu.  After overcoming an issue with my video card (I had to uninstall compiz-*) I am now trying to get my wireless to work.  I have spent the last week searching the net for my answer but none of the suggestions are working for me. Tried [http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html) and [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and a few others.  My problem as it stands is this.  THe wireless networks around me are detected with no problem.  I can see them in Network manager and in System -> Preferences -> Network Options. In Network tools, I have the wpa security option for my wireless device but in Network Manager I do not.  I need WPA security for my network and I probably would prefer a solution other than "change your security to WEP". I have had a similar problem in the past on XP (can't remember if it was on this machine) and it was resolved by updating the driver for the wireless.  If this is an option for me, I really need a "Dummies guide to updating drivers".  By the way my wired connection is working.
Details Below.  Any help would be appreciated
LSPCI
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:03.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:05.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
kids@kids-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:89:63:ca  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe89:63ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1310606 (1.3 MB)  TX bytes:221268 (221.2 KB)
          Interrupt:11 Base address:0x8800 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:6e:a7:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xa080 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1038 (1.0 KB)  TX bytes:1038 (1.0 KB)
kids@kids-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
kids@kids-laptop:~$ sudo lshw -C network
[sudo] password for kids: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:89:63:ca
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.2 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 1
       resources: irq:10
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6e:a7:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 56:2a:cf:01:33:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kids@kids-laptop:~$ sudo lshw -C network
[sudo] password for kids: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:89:63:ca
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.2 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 1
       resources: irq:10
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6e:a7:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 56:2a:cf:01:33:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kids@kids-laptop:~$ 
kids@kids-laptop:~$ lsb_release -d
Description:	Ubuntu 8.10
kids@kids-laptop:~$ uname -mr
2.6.27-9-generic i686
kids@kids-laptop:~$

---

### Post by Nasreen on 2009-01-28
I still have no reply.
I am still having issues but found a bit more information related to my problem.
I have realised not to use Network Manager and I am (trying to) connect from the terminal.  I have installed wpasupplicant.  I modified the wpa_supplicant.conf to this:

ap_scan=2
ctrl_interface=/var/run/wpa_supplicant 

network={
    ssid="my network name"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       psk="my asci password"
       pairwise=TKIP
       group=TKIP
}
Apparently I need ap_scan=2 for orinoco driver.  It didn't work even with ap_scan=1 (the default)

I can connect to the internet with a wired connection to my router.  No issue with detection of laptop and this happens automatically when i connect the ethernet cable.
It seems the problem is related to the orinoco driver installed for wireless.  It may be that it is not compatible with wpa encryption.  When i removed encryption from the connection, I was able to connect wirelessly to the router and the internet.  When I turn the encryption back on and type sudo dhclient eth1 I get the following

kids@kids-laptop:~$ sudo dhclient eth1
[sudo] password for kids: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:02:2d:6e:a7:2d
Sending on   LPF/eth1/00:02:2d:6e:a7:2d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


If it be a new wireless driver that I need, can some-one please help me out with some decent instructions as to how to update the driver.  I am new to Linux and find it a bit difficult compared to the Update driver options in Windows.  I don't want to go back to windows but would like some good informative instructions that let me know what i am doing as well as what i need to do.

I think I'm pretty close to the solution.
Please help out this newbie.

---

### Post by Nasreen on 2009-01-28
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd
returns
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=2
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     4b 41 41 44 41 4e                                 KAADAN          
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='KAADAN'
Initializing interface (2) 'eth1'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3 flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:02:2d:6e:a7:2d
wpa_driver_wext_set_wpa
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: Invalid argument
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Operation not supported

---

### Post by trundlenut on 2009-01-29
The orinoco driver that your wireless card uses doesn't support WPA, that's why there is no option for WPA in the network manager.

Look at this [thread]("http://ubuntuforums.org/showthread.php?t=304217&page=11") for help and there is a deb package with a ready made driver for kernel version 2.6.27-9 [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/66696").  I got this working with a similar HermesI card but it doesn't work now the kernel has been upgraded to 2.6.27-11.  That will teach me not to look through all the updates before installing them.

Also I found that WICD worked a lot better than the network manager at connecting to networks using WPA.

---

### Post by Nasreen on 2009-01-30
SUCCESS!

Downloaded Wlags49-h1-cs.ko from [http://launchpadlibrarian.net/21332662/wlags49-h1-cs-2.6.27-9-generic_2.6.27-9-generic-0ubuntu1_i386.deb](http://launchpadlibrarian.net/21332662/wlags49-h1-cs-2.6.27-9-generic_2.6.27-9-generic-0ubuntu1_i386.deb).  File downloaded to desktop so I did a right mouse click on file and selected open with GDebi Package Manager and the file was run automatically.

At this point I installed downloaded wicd from [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) that have detailed instructions about how to install the app including a command that needs to be run in terminal otherwise you will get an error.  Installing WICD will uninstall Network Manager and if you don't reboot you will constantly get errors but I didn't reboot at this stage.  Mind you the wireless still wouldn't connect.

I then went to the infamous [http://ubuntuforums.org/showthread.php?t=304217&page=11](http://ubuntuforums.org/showthread.php?t=304217&page=11) page and only did 2 things from this page.
Firstly I blacklisted the orinoco driver by typing in Terminal 
sudo gedit /etc/modprobe.d/blacklist 
and then adding 
#blacklist orinoco drivers (wireless) for new wlags WPA support
blacklist orinoco_cs
to the end of the file --> Save and close.
I rebooted PC.
Secondly, I ran the commands (with sudo in front of each line)
depmod
rmmod orinoco_cs (I got errors but moved on)
modprobe wlags49-h1-cs
I now have WICD working and WPA next to my wireless network.

Thanks for your help.  I was looking at this wlags file but thought it was not for the kernel I had (older ones only).  I will try to remember not to update my kernel version until a new wlags file is available.

---

### Post by trundlenut on 2009-02-02
Got it working again, reinstalled upgraded kernel to 2.6.27-9 and the rest was easy.  Just need to be carefull updating things.  Roll on Jaunty and WPA support for the Orinoco driver.

---

### Post by trundlenut on 2009-02-06
Now its stopped working.  Either doesn't show any wireless networks in WICD or it shows them but refuses to connect and then the networks disappear.  Aarrghhhhh.

---

### Post by Nasreen on 2009-05-22
> **trundlenut said:**
> Now its stopped working.  Either doesn't show any wireless networks in WICD or it shows them but refuses to connect and then the networks disappear.  Aarrghhhhh.

Do you know if there is a new wlags driver for this wireless network card for the new ubuntu???

---

### Post by sandrogalli on 2009-05-23
well i spent the better part of yesterday trying to compile a wpa driver for jaunty but ran into all sorts of problems.

But for those of you who want a workaround, here's how I got WPA to work for me in jaunty:

i simply installed the 2.6.27-9-generic kernel and used the wlags49-h1-cs.deb in post #5. I now have full WPA support on my Buffalo WLI-PCM-L11 PCMCIA card, and it seems to be working rock solid for me.

if you've had the 2.6.27-9-generic kernel installed on your intrepid system before, you can simple select it from your grub menu but for jaunty users, a .deb can be found here:

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-9-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-9-generic)

i know this isn't an ideal solution, but its simple enough for me, and most importantly it works. ;)

---

