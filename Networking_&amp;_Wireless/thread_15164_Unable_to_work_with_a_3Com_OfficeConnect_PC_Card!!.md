---
title: "Unable to work with a 3Com OfficeConnect PC Card!!"
date: 2005-02-12
forum: Networking &amp; Wireless
---

### Post by sharingan on 2005-02-12
hi!

this thing is driving me crazy... i'm trying to go wifi with a **3Com OfficeConnect  Wireless PC Card (3CRWE154G72)** with no sucess  :-( 

this card is supposed to work out of the box,  as listed in [prism54 supported cards](http://prism54.org/supported_cards.php), but this is what i get in /var/log/messages after plugging in the card and configuring the network interface:

```
Feb 12 17:35:19 localhost pci.agent[4776]:      prism54: loaded successfully
Feb 12 17:35:19 localhost kernel: Loaded prism54 driver, version 1.2
Feb 12 17:35:19 localhost kernel: PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Feb 12 17:35:19 localhost kernel: ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 5 (level, low) -> IRQ 5
feb 12 17:35:51 localhost gconfd (root-4852): comenzando (versión  2.8.1), pid 4852 usuario «root»
Feb 12 17:49:29 localhost kernel: eth1: timeout waiting for mgmt response
Feb 12 17:49:32 localhost last message repeated 3 times
Feb 12 17:49:32 localhost kernel: eth1: mgmt tx queue is still full
Feb 12 17:50:03 localhost last message repeated 90 times
Feb 12 17:51:04 localhost last message repeated 150 times
Feb 12 17:52:06 localhost last message repeated 155 times
Feb 12 17:53:08 localhost last message repeated 155 times
```

after that i tried with **ndiswrapper** following the [How To - Set up Ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)  guide in Ubuntu. 

first output was promising...

```
Feb 12 18:24:38 localhost kernel: ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
Feb 12 18:24:38 localhost kernel: PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Feb 12 18:24:38 localhost kernel: ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 5 (level, low) -> IRQ 5
Feb 12 18:24:38 localhost kernel: ndiswrapper: using irq 5
Feb 12 18:24:39 localhost kernel: ndiswrapper (NdisAcquireSpinLock:905): Windows driver trying to use uninitialized lock d376eb74, fixing it.
Feb 12 18:24:42 localhost kernel: 3c154g72.sys: probe of 0000:02:00.0 failed with error -22
Feb 12 18:24:42 localhost kernel: ndiswrapper: driver 3c154g72.sys (3Com,06/25/2004, 3.0.7.2) added
```

i thought this was going to work, but it didn't!!
this is what a got trying to start the interface:

```
sharingan@ubuntumovil:~ $ sudo ifup wlan0
Password:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0
```

did i make a bad wireless card choice or am i missing something?

i would really apreciate any help of tip... at least to know if i should get rid of the card and buy a new one.

thnx!!!

---

### Post by belch on 2005-02-24
i have the same problem.
I also tried with prism54 but it won't works.

Then i've found your thread, but i neither was able to succesfully load the
ndiswrapper.
When i modprobe ndiswrapper (from root) I get the following:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.11-rc3-mm2/misc/ndiswrapper.ko): Operation not permitted

i also tried the ubuntu-hoary kernel, but the result doesn't change.

BTW a month ago i had success to user the 3com Wireless 11 g card
from a LInux Kernel 2.6.10

Please, can any one help us?

---

### Post by sharingan on 2005-02-26
hi

i could finally manage to somehow configure this 3Com card. this is what i did:

[list=1]
[*]install ndiswrapper through synaptic. you can follow this [how-to](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)
[*]i read in a [german forum](http://www.ubuntuusers.de/wiki/treiber:netzwerk:netgear_wg511_china_einrichten) that there was a *conflict* between **prism54** and **ndiswrapper**, therefore i added a new line for the prism54 module in the hotplug blacklist ```
/etc/hotplug/blacklist
``` 
[*]finally, this the content of my [FONT=Courier New]/etc/network/interfaces[/FONT] file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
name Ethernet CardName

mapping hotplug
        script echo
        map wlan0

#auto wlan0
iface wlan0 inet dhcp
#iface wlan0 inet static
#       address 192.168.1.3
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.1
        wireless_essid YourESSID
        wireless_mode Managed
        wireless_channel 11
        wireless_rate auto
        name Wireless CardName
#       wireless_keymode restricted
#       wireless_key1
#      wireless_defaultkey 1
``` 
[/list]

anyway, the solution is far from being perfect, because sometimes ndiswrapper (or the windows driver, i don't know for sure) is not able to get the MAC address from the card i have to plug and unplug the card several time until it works. this is an strange behaviour, but at least it works.

hope my experience helps.

cheers!!

---

