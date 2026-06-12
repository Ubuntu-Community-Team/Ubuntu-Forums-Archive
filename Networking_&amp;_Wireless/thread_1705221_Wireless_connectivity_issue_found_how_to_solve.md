---
title: "Wireless connectivity issue found how to solve"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by slair on 2011-03-11
> 
i know notting of the tux.

ok i think i found why my wireless card isn't detected (i ither have no driver or the wrong one) I was wondering what solution should i seek. i've seen some STA and ndw"something", and ofcourse b43 diver solutions
i've been at this for a while and keep running into walls, my head literally hurts.

any help will be appreciated n sorry for yet another "i can't connect to the net post"

Sys info: Laptop --> HP Pavilion DV6500
[wubi]Ubuntu 10.10


[QUOTE]
dmesg
[   14.499703] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   14.499709] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
[   14.499712] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/user](http://wireless.kernel.org/en/user)

[COLOR=Red]b43-fwcutter is located on the Ubuntu install media under ../pool/main/b/b43-fwcutter/ and patch is located under ../pool/main/p/patch/ or both in the official repositories online. 

**can't find such a file[/COLOR]

repositories downloaded and moved to home file
terminal output at step 2

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo: b43-fwcutter: command not found

also i searched for b43-fwcutter and wansn't found anywhere


ilist scan wlan0
No command 'ilist' found, did you mean:
 Command 'slist' from package 'ncpfs' (universe)
 Command 'klist' from package 'heimdal-clients' (universe)
 Command 'klist' from package 'krb5-user' (main)
 Command 'iwlist' from package 'wireless-tools' (main)
 Command 'flist' from package 'nmh' (universe)
ilist: command not found
shain@ubuntu:~$ lsb_release -d
Description:    Ubuntu 10.10
shain@ubuntu:~$ uname -mr
2.6.35-22-generic x86_64
shain@ubuntu:~$ $ sudo /etc/init.d/networking restart
$: command not found
shain@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 

lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

iwconfig
*-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:b1:24:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg


lsmod
b43                   187931  0

lshw -C network
*-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:b1:24:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg



[/QUOTE]

I got it but... i get the feeling i broke something in the process

0:followed[ WiFiDocsDriverbcm43xx-no Internet Internet]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28AND%29%7C%28ManufacturerModel%29#b43%20-%20No%20Internet%20access")

1:command b43-fwcutter wouldn't run so i assumed it wasn't installed. googled it and got it.
2:step 2. returned an error, can remember what it was, didn't pay much attention to it, since for the first time the b43-fwcutter didn't return an error
3:moved to step 3 stuff got extracted and instantly the exclamation mark vanished

---

