---
title: "Terminal Wireless problem"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Chesamo on 2009-04-16
I installed Xubuntu on an older machine, then disabled GDM so it wouldn't graphically boot. This made me log into command line, and still be able to open a GUI just in case using startx. Trouble is, in the terminal mode I can't seem to get a connection using my wireless card (eth1). I tried the following sequence from root:

ifconfig eth1 192.168.1.67 netmask 255.255.255.0 broadcast 192.168.1.255
ifconfig eth1 down
dhclient -r eth1
ifconfig eth1 up
iwconfig eth1 essid "wirelessnetwork"
iwconfig eth1 mode Managed
dhclient eth1

Am I missing something here? The device does work, since I am able to use it when I am in xfce.

---

### Post by pytheas22 on 2009-04-16
It looks like you're not telling it which gateway to use.  I think it needs to know this before it can route traffic successfully.  Try adding in a command like
```

sudo route add default gw 192.168.1.1 eth1
```

(Assuming 192.168.1.1 is your gateway; also I'm not positive on the syntax for the route command, so check its man page if you get an error.)

You should also use iwconfig to tell it which channel and mode to use.  Depending on which driver you're using, it might not be necessary to specify this information, but it can't hurt:
```

iwconfig eth1 essid "wirelessnetwork" channel 1 mode managed
```

(Your channel is any number between 1 and 13; if you don't know which channel your router is on, look at the output of the 'sudo iwlist scan' command.)

You may also need to run the *iwconfig eth1...* command before you bring the interface up with *ifconfig eth1 up* rather than after, but again, this can vary from driver to driver.

Otherwise, it looks like you've got everything covered and the connection should work, provided the static IP configuration you're giving it is valid.

---

### Post by Chesamo on 2009-04-17
It... doesn't work. Here's the output:

```
# route add default gw 192.168.1.1 *[I checked the man pages, this is the correct syntax]*
SIOADDRT: No such process

root@ltop:~# ifconfig eth1 192.168.1.21 netmask 255.255.255.0 broadcast 192.168.1.255

root@ltop:~# iwconfig eth1 essid "wirelessnetwork" channel 1 mode managed

root@ltop:~# dhclient -r eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:d8:66:e6
Sending on   LPF/eth1/00:02:8a:d8:66:e6
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address

root@ltop:~# dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:d8:66:e6
Sending on   LPF/eth1/00:02:8a:d8:66:e6
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No working leases in persistent database - sleeping.

root@ltop:~#
```

What's strange is that when I use startx and then log out of X, the configuration magically fixes itself. I don't want to log into X every time I use this machine, though.

And it's frustrating, because I had it working before - I just don't know *how*.

---

### Post by pytheas22 on 2009-04-17
Does your wireless connection use static IP or dynamic?  In the output you posted above, it looks like you're trying to get a dynamic address via dhclient, but are also trying to set a static IP with ifconfig.  This doesn't work; you can only have one or the other.  Unless your router is manually configured to use static IPs, you probably need to use dynamic.

Try rebooting, then running these commands (without any of the others):
```

sudo iwconfig eth1 essid "wirelessnetwork" channel 1 mode managed
sudo dhclient eth1
```

If that doesn't work, please post the output of:
```

sudo iwlist scan
```

and tell me the name of the network you're trying to connect to.

---

### Post by Chesamo on 2009-04-17
I'll try that when I get home - the wired connection here at work makes it unnecessary for me to set up wireless.

---

### Post by Chesamo on 2009-04-17
```
root@ltop:~# iwconfig eth1 essid "wirelessnetwork" channel 1 mode managed

root@ltop:~# dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:d8:66:e6
Sending on   LPF/eth1/00:02:8a:d8:66:e6
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.42 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.42 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS recieved.
Trying recorded lease 192.168.1.42
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 recieved, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.42
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 recieved, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

root@ltop:~# iwlist eth1 scan
eth1	Scan completed :
	Cell 01 - Address: 00:1F:33:F1:27:83
		ESSID:"wirelessnetwork"
		Mode:Master
		Frequency:2.412 GHz (Channel 1)
		Quality:60/100 Signal level=-65 dBm noise level:-95 dBm
		Encryption key:off
		Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
		Extra:bcn_int:100
	Cell 02 - Address: 00:18:01:E7:80:DD
		ESSID:"RCU81"
		Mode:Master
		Frequency:2.437 GHz (Channel 6)
		Quality:10/100 Signal level=-90 dBm noise level:-95 dBm
		Encryption key:on
		Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6Mb/s
			9Mb/s; 12 Mb/s; 18 Mb/s
		Extra:bcn_int:100
```
I had iwlist target eth1 because I can't see all of the text if I have it scan both interfaces (blank space saying "This interface does not support scanning" from eth0 pushes the scan results of eth1 off the screen).

---

### Post by pytheas22 on 2009-04-17
That's kind of weird.  It definitely works if you're using the GUI?  The only other thing I can think of is to set the rate--this also shouldn't matter, but I guess it can't hurt.  We can also break the different arguments down into individual commands, in case for some reason your driver likes it better that way.  Try:
```

sudo iwconfig eth1 rate 1M
sudo iwconfig eth1 channel 1
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 essid "wirelessnetwork"
sudo dhclient eth1
```

That really should work, provided your router is serving dyanmic IPs.

If it still fails, please post the output of:
```

lshw -C Network
lspci -nn
cat /etc/network/interfaces
```

---

### Post by Chesamo on 2009-04-19
Okay, this is very annoying...

It worked once, then I rebooted to test it and it failed again.

```
# lshw -C Network
  *-network:0 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:d8:66:e6
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 module=airo multicast=yes wireless=IEEE 802.11-DS
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:c2:74:01
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:6e:2a:e8:82:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)

# cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by chili555 on 2009-04-19
Please check post #2 here: [http://ubuntuforums.org/showthread.php?t=826233&highlight=airo](http://ubuntuforums.org/showthread.php?t=826233&highlight=airo)

---

### Post by Chesamo on 2009-04-19
After blacklisting those modules, I still have the same problem.

Oh, Christ. I believe I should have mentioned I'm using 9.04 RC. Does this effect anything?

---

### Post by pytheas22 on 2009-04-19
I think the problem may be that your wireless interface is simply down--I notice that 'lshw -C Network' lists it as 'DISABLED'.  Try running these commands:

```
sudo ifconfig eth1 up
sudo iwconfig eth1 rate 1M
sudo iwconfig eth1 channel 1
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 essid "wirelessnetwork"
sudo dhclient eth1
```

The first command will ensure the interface is up before trying to connect (also, note that the first command contains 'ifconfig', not 'iwconfig'--it's not a typo).

---

### Post by Chesamo on 2009-04-20
I did try that, actually. I also noticed that the interface was listed as "Disabled".

Didn't help :(

Should I just say "screw it" and use X every time I need to use the 'Tubes? Everything I'm doing is *right*, it's just not working.

---

### Post by pytheas22 on 2009-04-20
Maybe.  I don't know what else could be wrong, other than that you possibly just don't have a strong enough signal for the connection to work every time (I assume you've tried connecting multiple times, however, always with the same results).

---

### Post by chili555 on 2009-04-20
Sometimes 'DISABLED' means the hardware switch or key combination on that laptop have killed the wireless radio. However, that's inconsistent with being able to scan and dhclient. Nonetheless, I'd love to see:```
sudo cat /var/log/messages | grep -i kill
sudo cat /var/log/messages | grep eth1
```

---

### Post by SuperSonic4 on 2009-04-20
Shouldn't a wireless connection be wlan0 instead of eth0?

wicd is a good wireless controller though

---

### Post by kevdog on 2009-04-20
DISABLED could be for a number of reasons.  The best thing would be to check the system log(s) for an idea of what is failing.  For example checking dmesg | less may be a start.  There are also hard and soft reset switches as chili was alluding to, however usually if you can get a iwlist scan result, this means at least the driver is loaded and functional.  I would definitely ensure you are using channel 1 -- however in my experience I've really never had to channel lock unless using kismet or something.

---

