---
title: "messy situation with bcm4311 (Dell Inspiron 1501)"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by an.erni on 2009-02-01
Hi guys

I originally installed Ubuntu quiet a while ago and went through several version updates (probably starting with Ubuntu 6.06). Unfortunately, my WLAN never really worked. Okay, sometimes it worked when I used ndiswrapper - but not really reliable. Oveer the time, I was looking for similar issues on this page and tried several solutions, which in my case never worked out. In facts, I'm not anymore able to tell which commands I run under which version (which means, my system might be a little messy).
The original problem was, that typing "iwconfig" said ESSID="", even though other notebooks recognized various networks (encrypted and open). Just in case if this is helpful: In one of my most recent attempts, I edited something like init.d and removed kernel modules (something like rmmod -r ndiswrapper, wl, bcm43, b43, ...?)

So I'll just start from scratch:
I am using a Dell Inspiron 1501.
The WiFi network is not encrypted (it used to use WEP128, but I disabled it for debugging purposes).
```
uname -r
2.6.27-9-generic
```

```
lspci -nnm|grep 14e4
05:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Dell [1028]" "Device [0007]"
08:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401-B0 100Base-TX [170c]" -r02 "Dell [1028]" "Device [01f5]"
```


First of all, I follow this guide:
[Wireless troubleshooting guide]("https://help.ubuntu.com/8.10/internet/C/troubleshooting.html")

1. Check that the device is on
=> there is no switch, which could turn off the module

2. Check for device recognition
```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
```
=> I can't find an output like "CLAIMED, UNCLAIMED, ENABLED or DISABLED"

3. Check for a connection to the router
```
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
```
=> eth0 is the wired network. back in the days using ndiswrapper, the WiFi network was called eth1.

4. Check IP assignment
As seen above, there is no eth1.

5. Check DNS
Won't work.

6. IPv6 Not Supported
Not tested.


Second, I look around search for "BCM4311" on [ubuntuforums.org]("http://ubuntuforums.org"):

There, I followed the procedure to get help:
[Supported wireless hardware and Procedure to get help]("http://ubuntuforums.org/showthread.php?t=370108")

```
lspci -v | less
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: Dell Device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb, wl
```

The [list of supported WiFi cards]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom") says that the BCM4311 requires the bcm43xx driver. However, it forwards me to the ndiswrapper tutorial...

So I follow the [HOWTO post a wireless issue]("http://ubuntuforums.org/showthread.php?p=6183681"):

1 ) Machine Brand and Model (PC/Laptop):
Dell Inspiron 1501

2 ) Wireless Brand, Model and Wireless Chipset:
```
lspci -nn | grep Broadcom
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
```
```
lsusb
=> does not apply (using a MiniPCI WiFi card)
```

3 ) check interface:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:5b:5e:40  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe5b:5e40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160370156 (160.3 MB)  TX bytes:6295426 (6.2 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```

```
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
```

4 ) Check for modules:
```
lsmod | grep b43
=> no results

```
```
lsmod | grep wl
wl                   1085520  0 
ieee80211_crypt        14596  1 wl
```
```
lsmod | grep ndiswrapper
ndiswrapper           253696  0 
usbcore               175376  4 ndiswrapper,ehci_hcd,ohci_hcd
```


5 ) Kernel boot messages
```
dmesg | grep b43
[    2.467069] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.467082] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[   16.203256] b43-phy0: Broadcom 4311 WLAN found
[   29.538654] input: b43-phy0 as /devices/virtual/input/input9
[   29.656064] firmware: requesting b43/ucode5.fw
[   29.835818] firmware: requesting b43/pcm5.fw
[   29.873289] firmware: requesting b43/b0g0initvals5.fw
[   29.895362] firmware: requesting b43/b0g0bsinitvals5.fw
[   30.040064] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   30.211557] Registered led device: b43-phy0::tx
[   30.211602] Registered led device: b43-phy0::rx
[   30.211626] Registered led device: b43-phy0::radio
[   30.568100] b43-phy0: Radio hardware status changed to DISABLED
[   30.668048] b43-phy0: Radio turned on by software
[   30.668053] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
```

6 ) Network configuration
```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5b:5e:40
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.4 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
```

7 ) Scan for networks:
```
iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
```

8 ) Ubuntu Version:
```
lsb_release -d
Description:	Ubuntu 8.10
```

9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
uname -mr
2.6.27-9-generic x86_64
```

10 ) Restarting the network:
```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth0.pid with pid 11052
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:b9:5b:5e:40
Sending on   LPF/eth0/00:19:b9:5b:5e:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:b9:5b:5e:40
Sending on   LPF/eth0/00:19:b9:5b:5e:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 37988 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```



Thank you very much!
Andy

---

### Post by Crafty Kisses on 2009-02-01
Let's try this, install the following package:
```
sudo apt-get install ndisgtk
```
Once you have this package installed, you can run it by running the following command:
```
sudo ndisgtk
```
Once it's open, you need to download the driver, I'm pretty sure you can get the Windows driver for that right here: [http://www.bioticaindia.com/broadcom-bcm4311-802-11g.html](http://www.bioticaindia.com/broadcom-bcm4311-802-11g.html). Look for the one you need, once you have it downloaded, extract it to wherever you want, look for the ".inf" file, once you have done that, bring up ndisgtk, then where it says "Browse" you want to click that and look for the ".inf" file, then click "Install Driver" see if that works for you. If that doesn't work for you, you can always try the manual way again, and see if you don't get different results:
```
sudo ndiswrapper -i bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
iwconfig
sudo ndiswrapper -m
cat /etc/modprobe.d/ndiswrapper
sudo ifdown wlan0
sudo ifup wlan0
sudo iwlist scanning
sudo dhclient wlan0
```
Also I'm not sure if there's any competing drivers, but you should probably blacklist those as well, just in case, but If there isn't you don't have to worry about it, you can blacklist any competing drivers by running the following:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by Ayuthia on 2009-02-01
Before you try Codename's post, I see three things that seem to be a problem.  The first is that you have the wl module and ndiswrapper loaded.  The other problem is that the RF swtich is currently turned off.  Finally, you have a b44 wired ethernet card which means that ssb is currently enabled (which will block out ndiswrapper and wl unless it is loaded after the wireless modules).  We should try to solve those problems before we go the ndiswrapper route.

One thing that we can try before we check about the RF switch (If you do have a button or switch for your wireless card, make sure that it is on) is to try the wl module:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```
I am suggesting this route first because the wl module is made by Broadcom.  So if the wireless switch is on, hopefully the wl module will know how to flip the switch.  In theory, the wl module brings up eth1 instead of wlan0 but it might not always be the case.

Please let us know if it is able to see wireless sites.  If it does, then we just need to add a couple of things to make it work on reboots.

---

### Post by an.erni on 2009-02-01
Hi there

Thanks for the fast replies!
As suggestet, I followed Ayuthia's commands:

```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
=> no output
```

```
 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 30259
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:b9:5b:5e:40
Sending on   LPF/eth0/00:19:b9:5b:5e:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 30445
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:7e:11:82:54
Sending on   LPF/eth1/00:19:7e:11:82:54
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:b9:5b:5e:40
Sending on   LPF/eth0/00:19:b9:5b:5e:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 37370 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:7e:11:82:54
Sending on   LPF/eth1/00:19:7e:11:82:54
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[eth1]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth1]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth1]: waiting for interface wlan0 before doing NFS mounts
                                                                         [ OK ]

```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:A7:B5:E0
                    ESSID:"WG_Fadegrad"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-36 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0F:CC:90:14:A4
                    ESSID:"ec3f3udpyh"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:5/5  Signal level:-52 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

```

Where "WG_Fadegrad" is the network I want to connect to.

It turns out, that *somehow* it works (thank you so far!). But it's very, very unstable!!! First of all, I can connect to the Internet ([www.wikipedia.org](www.wikipedia.org)). I was able to visit tons of pages in the same language, but as soon as I switched the language or I tried to connect to another webpage, it didn't work. Trying in the original language still worked. To me, this seems very strange!!!

Cheers, Andy

---

### Post by Ayuthia on 2009-02-01
Based on the information that you posted, it looks like it connected with the wired connection instead of the wireless.  It also seems that there might be some additional information in /etc/network/interfaces because it looks like it found some unknown interfaces.  You might try the commands again, but instead of calling /etc/init.d/networking we will try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo ifconfig eth1 up
sudo iwconfig eth1 essid WG_Fadegrad
sudo dhclient eth1
```
You might want to also make sure that you unplug the wired connection so that we are sure that the system does not try to connect to it.  Hopefully that will bring better results.

---

### Post by an.erni on 2009-02-02
Hey there

Thanks a lot, it seems like this works!

Here is the output I got:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl

sudo modprobe wl

sudo modprobe b44

sudo ifconfig eth1 up

sudo iwconfig eth1 essid WG_Fadegrad

sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 7054
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:7e:11:82:54
Sending on   LPF/eth1/00:19:7e:11:82:54
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.7 from 192.168.1.1
DHCPREQUEST of 192.168.1.7 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.7 from 192.168.1.1
bound to 192.168.1.7 -- renewal in 42286 seconds.

```

Most importantly, the WiFi connection to the internet works, after typing these commands. It would be nice, though, to execute them during startup procedure. What would be an elegant way to do so?

Furthermore, the ubuntu GUI doesn't realize that I'm connected to the Internet:
- The NetworkManager Applet doesn't display any of the networks found using "sudo iwlist scanning" - even in opposite, it says "device unmanaged".
- Plus the gnome-netstatus-applet counts the transfered packets, but constantly displays a signal strength of 36%, which can't be true as I'm sitting next to the access point...

Thanks a lot!
Cheers, Andy

---

### Post by Ayuthia on 2009-02-02
> **an.erni said:**
> Hey there

Thanks a lot, it seems like this works!

Here is the output I got:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl

sudo modprobe wl

sudo modprobe b44

sudo ifconfig eth1 up

sudo iwconfig eth1 essid WG_Fadegrad

sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 7054
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:7e:11:82:54
Sending on   LPF/eth1/00:19:7e:11:82:54
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.7 from 192.168.1.1
DHCPREQUEST of 192.168.1.7 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.7 from 192.168.1.1
bound to 192.168.1.7 -- renewal in 42286 seconds.

```

Most importantly, the WiFi connection to the internet works, after typing these commands. It would be nice, though, to execute them during startup procedure. What would be an elegant way to do so?

Furthermore, the ubuntu GUI doesn't realize that I'm connected to the Internet:
- The NetworkManager Applet doesn't display any of the networks found using "sudo iwlist scanning" - even in opposite, it says "device unmanaged".
- Plus the gnome-netstatus-applet counts the transfered packets, but constantly displays a signal strength of 36%, which can't be true as I'm sitting next to the access point...

Thanks a lot!
Cheers, Andy

You can try this first to get it to work each time you restart your computer:
```
echo -e '#ssb workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

Hopefully when you restart it this way, NetworkManager might respond better.  I am not too sure about the signal strength though.  I know that the wl module reports the signal strength differently.  They go on a scale of 0-5 where others use a scale of 0-100.

---

