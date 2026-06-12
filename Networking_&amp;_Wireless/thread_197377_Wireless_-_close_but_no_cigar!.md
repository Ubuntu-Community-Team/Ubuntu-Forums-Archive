---
title: "Wireless - close but no cigar!"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by Jaymoid on 2006-06-15
Hi, I feel I am sooo close to getting this sorted, but I'm quite new to linux so I feel I lack some vital knowledge that could put everything in place and get my wireless working! I shall give you all as much information as possible. 

I have a US robotics USR805422 USB adapter.

I have installed ndiswrapper, installed the driver, which all seems to work ok. ndiswrapper -l is as follows
```
Installed ndis drivers:
rsc4usb:    driver present, hardware present
```

Then I have ran:
  sudo depmod -a
  sudo modprobe ndiswrapper

/var/log/messages is giving me no errors thus far...

So I have tried to configure my network interface - which places the following in my /etc/network/interfaces:
```
iface eth1 inet static
address 192.168.0.41
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid <my essid>
wireless-key <my wep key>
```

When I click activate, it thinks about it for a while and these messages appear in /var/log/messages:
```
localhost kernel: [4295299.536000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

**Any ideas? All suggestions welcome.**:-({|= 

At the moment I think it could be because some other native wireless drivers are installed (I have no clue how to remove them?).

Anyway here is some additional information that may help come up with some ideas/solutions...

When I plug my usb device in this is what appears in /var/log/messages:
```
localhost kernel: [4296323.892000] usb 3-2: new high speed USB device using ehci_hcd and address 4
localhost kernel: [4296324.011000] islusb: No suitable configuration found, trying 3887 support
localhost kernel: [4296325.312000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

**lsusb** provides the following info:
```
Bus 003 Device 004: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
```

**lshw** provides the following:
```
 *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:c0:49:5c:b6:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.41 multicast=yes wireless=IEEE 802.11b
```

**iwconfig** provides the following:
```
eth1      IEEE 802.11b  ESSID:"p1g30n5tr33t"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**ifconfig** provides the following:
```
eth1      Link encap:Ethernet  HWaddr 00:C0:49:5C:B6:37
          inet addr:192.168.0.41  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

**Thanks in advance.**

James

---

### Post by Slicedbread on 2006-06-15
Did you did ndiswrapper -m? If you did do " sudo gedit /etc/modprobe.d/ndiswrapper" and change the alias to from wlan0 to eth1, that solved it for me.

Also check here [here]("http://ubuntuforums.org/showpost.php?p=1105667&postcount=218")

---

### Post by Jaymoid on 2006-06-15
Thanks for the reply: I have edited the file as you suggested, but I am still getting the same error when I try to change/activate the connection in the network settings dialog:
ADDRCONF(NETDEV_UP): eth1: link is not ready
in the /var/log/messages

and the iwconfig remains the same.

is there something I need to do after editing this file before I try to activate the connection?

---

### Post by dicecca112 on 2006-06-15
if you are using the default ndiswrapper that comes with drapper that might be your first problem.  It has never worked for me, ever.  Go download the newest ndiswrapper and follow the directions to install it, and try this all again.  This is the only way I have ever got wireless to work

---

### Post by Jaymoid on 2006-06-16
[QUOTE=dicecca112]if you are using the default ndiswrapper that comes with drapper that might be your first problem.  It has never worked for me, ever.  Go download the newest ndiswrapper and follow the directions to install it, and try this all again.  This is the only way I have ever got wireless to work[/QUOTE]

Hmm I am using the default driver but according to the list of devices with ndiswrapper, it should work (I amusing 1.8.0ubuntu2):
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#u](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#u)
```

USB: US ROBOTICS USR805422 802.11g Wireless USB Adapter

    * Chipset:Unknown
    * usbid: 0baf:0118
    * Driver: Official U.S. Robotics http://www.usr.com/support/5422/5422-files/USR5422-v1.0.1.18.exe rename the archive with a .zip extension, extract the files, then rename all of them to lower-case.
    * Other: Works perfect, also the radio, tested on Ubuntu 5.10 kernel 2.6.12, ndiswrapper 1.1-4ubuntu.
    * Bug: If the usb adapter is disconnected before the system shutdown the computer freeze, probably kernel panic
```

Also if ndiswrapper was not working then I would assume that this would not occur for ndiswrapper -l:
```
Installed ndis drivers:
rsc4usb:    driver present, hardware present
```

Thanks for the suggestion - I may download and compile the latest version but I think it should work with this version.

---

