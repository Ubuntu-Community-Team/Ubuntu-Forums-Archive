---
title: "Can see wireless networks, can't connect."
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by gantis on 2009-08-23
[FONT=Tahoma]I am using an ASUS 1005 HA. The driver is installed and networks can be detected. When trying to connect to any wireless network, it can't. I've tried by booting the kernel with "pci=noacpi", didn't seem to work. Here is some info, let me know what else you might need.

> 
_iwconfig_

wmaster0 no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:"Mike"
Mode:Managed Frequency:2.462 GHz Access Point: 00:23:69:6B:2B:19
Bit Rate=24 Mb/s TxPower=
27 dBm
Retry min limit:7 RTS thr: off Fragment thr=2352 B
Power Managementff
Link Quality=84/100 Signal level:79
dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
pan0 no wireless extensions.


_sudo lshw -C network_


*network
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCIExpress)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wmaster0
version: 01
serial: 00:25:d3:09:85:db
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
*network
UNCLAIMED
description: Ethernet controller
product: Attansic Technology Corp.
vendor: Attansic Technology Corp.
physical id: 0
bus info: pci@0000:01:00.0
version: c0
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list
configuration: latency=0
*network
DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 92:1a:da:3c:88:f4
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes\
[/FONT]

---

### Post by gantis on 2009-08-23
*bump*

---

### Post by bapoumba on 2009-08-23
[http://ubuntuforums.org/showthread.php?t=1179951](http://ubuntuforums.org/showthread.php?t=1179951)

Please see here if it helps.

---

### Post by gantis on 2009-08-23
Thanks, that seemed to do the trick at first. Now it is not working again; "sudo apt-get install linux-backports-modules-jaunty" isn't curing now. Here is what I get when trying to run the command: ```
michael@michaelnetBook:~$
sudo aptget
install linuxbackportsmodulesjaunty
[sudo] password for michael:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
linuxbackportsmodules2.6.2815generic
linuxbackportsmodulesjauntygeneric
The following NEW packages will be installed:
linuxbackportsmodules2.6.2815generic
linuxbackportsmodulesjaunty
linuxbackportsmodulesjauntygeneric
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1288kB of archives.
After this operation, 4198kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com jauntyupdates/
main linuxbackportsmodules2.6.2815generic
2.6.2815.17
Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com jauntysecurity/
main linuxbackportsmodules2.6.2815generic
2.6.2815.17
Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jauntysecurity/
main linuxbackportsmodulesjauntygeneric
2.6.28.15.20
Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jauntysecurity/
main linuxbackportsmodulesjaunty
2.6.28.15.20
Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linuxbackportsmodules2.6.28/
linuxbackportsmodules2.6.2815generic_
2.6.2815.17_
i386.deb Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linuxmeta/
linuxbackportsmodulesjauntygeneric_
2.6.28.15.20_i386.deb Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linuxmeta/
linuxbackportsmodulesjaunty_
2.6.28.15.20_i386.deb Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run aptget
update or try with fixmissing?
michael@michaelnetBook:~$
```

---

### Post by bapoumba on 2009-08-24
Were you on a wired network when you tried this? 
And which ubuntu release are you using?

---

### Post by gantis on 2009-08-24
Na, I am using wireless and running 9.04. I have also installed all of the latest updates a few days ago before the wireless turned fussy. #-o

---

### Post by bapoumba on 2009-08-24
Do you have access to a wired connection? You won't be able to install anything if you do not have a net access.

---

### Post by ieBrazil on 2009-08-24
> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?t=1179951](http://ubuntuforums.org/showthread.php?t=1179951)

Please see here if it helps.



man, this is for Ubuntu jaunty; and what if I have a LTS, which is not jaunty?

---

### Post by bapoumba on 2009-08-24
> **ieBrazil said:**
> man, this is for Ubuntu jaunty; and what if I have a LTS, which is not jaunty?
Do you have the same hardware ?

> product: AR9285 Wireless Network Adapter (PCIExpress)

---

### Post by gantis on 2009-08-24
I do have access to a wired connection although I haven't tried to set it up with ubuntu, I did install the updates wirelessly a few days ago, but now it doesn't want to cooperate. Still, I can see the broadcasted networks, just not connect to any.

---

### Post by bapoumba on 2009-08-24
> **gantis said:**
> I do have access to a wired connection although I haven't tried to set it up with ubuntu, I did install the updates wirelessly a few days ago, but now it doesn't want to cooperate. Still, I can see the broadcasted networks, just not connect to any.
Ethernet connection will work for sure, and allow you to install the packages with the package manager, taking care of all the dependencies. Otherwise, you can download the package here from another computer and install it with dpkg, but it will be a pain to pull all the dependencies along:
[http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty](http://packages.ubuntu.com/jaunty/linux-backports-modules-jaunty)

---

### Post by gantis on 2009-08-24
Thanks. What dependencies would be appropriate for me to download? There is such a variety that I don't know where to begin looking. :-k

---

### Post by gantis on 2009-08-24
Okay, now it randomly started to connect, but it will disconnect at random then reconnect. (wireless) Any ideas?

---

