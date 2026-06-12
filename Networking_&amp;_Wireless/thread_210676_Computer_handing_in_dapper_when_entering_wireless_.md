---
title: "Computer handing in dapper when entering wireless properties.  Was fine in breezy."
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by jonboy99 on 2006-07-07
Title should be 'hanging' not handing.

Hi, am trying to use ndiswrapper in conjunction with a belkin f5d7050 with dapper.
This worked fine in breezy with the downloaded windows drivers.

However, in dapper, all seems to be well until I go into the networking administration window, an click on properties for the wireless card.

The spinny icon comes up for ever.  I can close the networking window but cannot load any other programs or shut the computer down - nothing happens when I click on the shutdown icon.

Exiting to console with ctrl-alt F1 works, but sudo reboot just causes a hard lock.

Is some inbuilt driver in dapper conflicting with ndiswrapper, or something else?  Have tried uninstalling ndiswrapper but makes no difference.

Have also tried completely fresh install - same thing.

:confused:

---

### Post by jonboy99 on 2006-07-07
Ok, am getting somewhere.   It appears it is dappers inbuilt drivers for the chipset that are causing it to hang.

It seems it may be the rt2500 or rt2570 modules that are the culprits:

jonboy99@ubuntu2000:~/Desktop/belkin$ modprobe -l | grep rt25
/lib/modules/2.6.15-23-386/kernel/drivers/usb/net/rt2570/rt2570.ko
/lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/rt2500/rt2500.ko


Now I have added these lines to /etc/modprobe.d/blacklist:

blacklist rt2570
blacklist rt2500

Are these correct to blacklist these modules?

The computer no longer hangs like it did on entering the networking screen but it still won't connect, so I feel i'm getting somewhere.

---

### Post by jonboy99 on 2006-07-07
Hmm, despite uninstalling ndiswrapper, my card still appears in networking, as eth1, so some other driver/module is still being loaded for it.

How an I find out which?

This is a copy of my syslog since unplugging and plugging in the device if it helps.  The chipset is a netgear net2280.

> only configuration source at position 4
Jul  7 13:29:46 localhost kernel: [4295024.095000] usb 3-1: USB disconnect, address 2
Jul  7 13:29:50 localhost gconfd (root-5302): GConf server is not in use, shutting down.
Jul  7 13:29:50 localhost gconfd (root-5302): Exiting
Jul  7 13:29:52 localhost gconfd (root-5324): starting (version 2.14.0), pid 5324 user 'root'
Jul  7 13:29:52 localhost gconfd (root-5324): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  7 13:29:52 localhost gconfd (root-5324): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul  7 13:29:52 localhost gconfd (root-5324): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  7 13:29:52 localhost gconfd (root-5324): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  7 13:29:52 localhost gconfd (root-5324): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  7 13:30:16 localhost kernel: [4295054.301000] usb 3-1: new high speed USB device using ehci_hcd and address 4
Jul  7 13:30:16 localhost kernel: [4295054.415000] islusb: suitable configuration found for net2280 + PCI device

---

### Post by jonboy99 on 2006-07-07
Aaargh, found a module called net2280 which surely had to be the right one!  But no, it was still there in networking despite no ndiswrapper installed, and still didn't work.:evil:

---

### Post by luxerama on 2006-07-07
I had/have the same problem with my belkin wirless dongle(rt2500). I also tried to solve the problem with ndiswrapper without sucess. What I did in the end is to enter the network details through the interface but not activate it. To activate it you have to do it via the console by typing "sudo ifup rausb0/wlan0(or whichever extension your wlan device has)". Hope that helps.

---

