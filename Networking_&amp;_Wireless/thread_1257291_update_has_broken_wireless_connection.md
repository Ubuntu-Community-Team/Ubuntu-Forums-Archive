---
title: "update has broken wireless connection"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by trundlenut on 2009-09-03
Earlier this evening I installed a couple of updates (libnss3-1d and python-gobject).  After I restarted the machine I can no longer connect to my wireless network.

The wireless card seems to be functioning OK, it can see the networks and tries to connect but it fails when authenticating with my router.

Looking through dmesg I get a load of lines saying:
```
eth1: Lucent/agere firmware doesn't support manual roaming
```

A search has revealed that libnss is related to security standards and I suspect that this may be the cause of the problems.  I have tried to roll back to the earlier version of the library but there isn't the option in Synaptic.

The wireless card is a Hermes 1 toshiba mini pci card using the orinoco driver.

Any ideas?

---

### Post by trundlenut on 2009-09-04
Bumpty Bump

---

### Post by crf on 2009-09-21
Hi, I see this too, on an elderly computer running Karmic Koala and using a vaio pcwa-c100 cardbus pc card. The orinoco driver is loaded. The card is working, and can see the router. But it will spin its wheels trying and failing to connect. It often wants my password (though the connection details, with password, is saved). (It all works while the computer runs an old Ubuntu live-cd, and Karmic runs ok when the computer uses a cable ethernet connection card.)

Unfortunately, I have no idea how to solve the wireless connection issue.

```
chris@paqsaq:/etc/dhcp3$ sudo lshw -c network
 *-network
      description: PCWA-C100
      product: Version 01.01
      vendor: Sony Corporation
      physical id: 0
      slot: Socket 0
      resources: irq:3
 *-network
      description: Wireless interface
      physical id: 2
      logical name: eth1
      serial: 08:00:aa:0a:42:aa
      capabilities: ethernet physical wireless
      configuration: broadcast=yes driver=orinoco driverversion=0.15
firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
```

---

### Post by crf on 2009-09-21
While running the ubuntu 6.04 cd, the firmware was different.

```
ubuntu@ubuntu:/tmp/test/home/chris$ sudo lshw -C network   
*-network
     description: PCWA-C100
     product: Version 01.01
     vendor: Sony Corporation
     physical id: 0
     slot: Socket 0
     resources: irq:3
 *-network
     description: Wireless interface
     physical id: 2
     logical name: eth0
     serial: 08:00:46:0a:42:2f
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=orinoco
driverversion=0.15rc3 firmware=Lucent/Agere 6.04 ip=192.168.0.103
link=yes multicast=yes wireless=IEEE 802.11b
```

Is modern ubuntu setting the card to use the right firmware?

---

### Post by crf on 2009-09-22
Well, it is now working again. And lshw reports it using 
configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.04

---

### Post by trundlenut on 2009-09-22
As far as I know the different version of the firmware is to enable WPA to work.  Prior to the 2.6.28 kernel you couln't easily get WPA encryption then a revised driver was included in the kernel.

Did you change anything to get it to work?  I just restored my machine with a backup I had from a week earlier and then didn't install the libnss update.  So at the moment it works and the firmware is reported as version 9.48.

---

### Post by crf on 2009-09-22
I didn't change anything to get it work. Although I have been updating using an ethernet pccard. I have libnss3-1d installed.
 
It doesn't resume properly after hibernating though. It looks like something crashes upon resume (after looking for firmware). Network manager applet said I was connected to wireless, but it wasn't connected. I used the network manager applet to disconnect from wireless, then had to pccardctl eject and insert. It then revived and is working okay.

Log from upon resuming from a suspend to disk, and later bringing up connection:
```

Sep 22 08:17:50 paqsaq kernel: [ 7218.723305] eth1: Attempting to download firmware agere_sta_fw.bin
Sep 22 08:17:50 paqsaq kernel: [ 7218.723347] hermes_dld: AUX enable returned 0
Sep 22 08:17:50 paqsaq kernel: [ 7218.724297] hermes_dld: AUX disable returned 0
Sep 22 08:17:50 paqsaq kernel: [ 7218.724312] hermes_dld: Actual PDA length 998, Max allowed 1000
Sep 22 08:17:50 paqsaq kernel: [ 7218.724327] eth1: Read PDA returned 0
Sep 22 08:17:50 paqsaq kernel: [ 7218.724460] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
Sep 22 08:22:03 paqsaq kernel: [ 7218.935647] eth1: Cannot find firmware agere_sta_fw.bin
Sep 22 08:22:03 paqsaq kernel: [ 7218.935675] eth1: Error -2 re-initializing firmware
Sep 22 08:22:03 paqsaq kernel: [ 7218.935696] PM: Device 0.0 failed to resume: error -5
Sep 22 08:22:03 paqsaq kernel: [ 7471.153712] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
Sep 22 08:22:03 paqsaq kernel: [ 7472.208295] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Sep 22 08:22:03 paqsaq kernel: [ 7472.208629] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
Sep 22 08:22:03 paqsaq kernel: [ 7472.298701] eth0: Hardware identity 0001:0001:0004:0000
Sep 22 08:22:03 paqsaq kernel: [ 7472.298826] eth0: Station identity  001f:0001:0006:0004
Sep 22 08:22:03 paqsaq kernel: [ 7472.298845] eth0: Firmware determined as Lucent/Agere 6.04
Sep 22 08:22:03 paqsaq kernel: [ 7472.299136] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
Sep 22 08:22:03 paqsaq kernel: [ 7472.408894] eth0: Attempting to download firmware agere_sta_fw.bin
Sep 22 08:22:03 paqsaq kernel: [ 7472.408935] hermes_dld: AUX enable returned 0
Sep 22 08:22:03 paqsaq kernel: [ 7472.409841] hermes_dld: AUX disable returned 0
Sep 22 08:22:03 paqsaq kernel: [ 7472.409855] hermes_dld: Actual PDA length 998, Max allowed 1000
Sep 22 08:22:03 paqsaq kernel: [ 7472.409869] eth0: Read PDA returned 0
Sep 22 08:22:03 paqsaq kernel: [ 7472.409889] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
Sep 22 08:22:03 paqsaq kernel: [ 7472.450075] eth0: Cannot find firmware agere_sta_fw.bin
Sep 22 08:22:03 paqsaq kernel: [ 7472.450165] eth0: Hardware identity 0001:0001:0004:0000
Sep 22 08:22:03 paqsaq kernel: [ 7472.450285] eth0: Station identity  001f:0001:0006:0004
Sep 22 08:22:03 paqsaq kernel: [ 7472.450304] eth0: Firmware determined as Lucent/Agere 6.04
Sep 22 08:22:03 paqsaq kernel: [ 7472.450318] eth0: Ad-hoc demo mode supported
Sep 22 08:22:03 paqsaq kernel: [ 7472.450331] eth0: WEP supported, 104-bit key
Sep 22 08:22:03 paqsaq kernel: [ 7472.450454] eth0: MAC address 08:00:46:0a:42:2f
Sep 22 08:22:03 paqsaq kernel: [ 7472.450559] eth0: Station name "HERMES I"
Sep 22 08:22:03 paqsaq kernel: [ 7472.451106] eth0: ready
Sep 22 08:22:52 paqsaq kernel: [ 7472.455286] eth0: orinoco_cs at 0.0, irq 3, io 0x0180-0x01bf
Sep 22 08:22:52 paqsaq kernel: [ 7472.828053] udev: renamed network interface eth0 to eth1
Sep 22 08:22:52 paqsaq kernel: [ 7472.840395] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 22 08:22:52 paqsaq kernel: [ 7472.964495] eth1: New link status: Disconnected (0002)
Sep 22 08:22:52 paqsaq kernel: [ 7505.198074] eth1: Lucent/Agere firmware doesn't support manual roaming
Sep 22 08:22:52 paqsaq kernel: [ 7510.442212] eth1: Lucent/Agere firmware doesn't support manual roaming
Sep 22 08:22:52 paqsaq kernel: [ 7510.548454] eth1: New link status: Connected (0001)
Sep 22 08:22:52 paqsaq kernel: [ 7510.548699] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

```

---

### Post by trundlenut on 2009-09-22
are you connecting using WEP or WPA?

---

### Post by crf on 2009-09-22
Wep

(When it wasn't working, I did try disabling all encryption on the router -- that still didn't help)

---

### Post by crf on 2009-09-22
do you use network manager and nm-connection-editor and networkmanager applet, or gnome-network-admin, or neither?

---

### Post by tienhn on 2009-09-22
I experience the same thing. My wireless using WPA encryption is no long making connection. How do I back out the update?

---

### Post by crf on 2009-09-22
Start Synaptic, go to the libnss3-1d package, and from the package menu, choose force version.

---

### Post by trundlenut on 2009-09-23
I was using wicd but I changed it over last night to networkmanager because I need to connect to a VPN.

I think you will find you might not be able to connect to any WPA encrypted networks as the newer firmware is needed to make that card work.  I originally started using wicd because I found networkmanager to be a bit flaky at maintaining WPA connections, seems alright now though.

---

### Post by trundlenut on 2009-09-23
> **crf said:**
> Start Synaptic, go to the libnss3-1d package, and from the package menu, choose force version.

I tried this originally but I found that the previous version was not available only a much earlier version.

---

### Post by onthenarrowpath on 2009-09-27
I can confirm the problem: Since the last update, I cannot connect to wireless anymore, showing the symthoms already described: Networks are found, but the connection is not established, always asking for passwords it already knows. I'll try to downgrade, I guess...

---

### Post by crf on 2010-01-13
I wonder if this problem is related to dhcp. I had this problem happen again on a newly reinstalled system, even after removing network manager. But once i ran dhclient, it connected.

Something to try, if this problem is still happening to anyone else.

---

### Post by Martin Hecht on 2011-01-22
I have seen again on Ubuntu 10.04 LTS the dmesg entry:
 eth1: Lucent/Agere firmware doesn't support manual roaming
 I have a Dell TrueMobile 1150 Series PC Card and tried to connect to a  hidden WEP encrypted WLAN with shared key. It has found the network but  couldn't log in neither with network manger nor with wicd. However, by  means of iwconfig I could connect to the network without any problems.  As a quick hack I added the following commands to my rc.local (well,  should be placed better somewhere in the networking scripts ...)


 iwconfig eth1 essid my-essid
iiwconfig eth1 mode managed
iwconfig eth1 key myhexkey
iwconfig eth1 key restricted
dhclient eth1


so, the dhcp client is one thing, but already before, something with the key exchange failed.

---

### Post by Martin Hecht on 2011-01-25
here the better way to do this, add to /etc/network/interfaces the following lines:

auto eth1
iface eth1 inet dhcp
            wireless yes
            wireless-mode managed
            wireless-essid my-essid
            wireless-key restricted myhexkey

(on the lines starting with "wireless" there should be a tab or some blank characters at the beginning)

---

