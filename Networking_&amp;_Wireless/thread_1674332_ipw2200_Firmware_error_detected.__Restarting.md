---
title: "ipw2200: Firmware error detected.  Restarting"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by Tim Waterman on 2011-01-23
I'm a Linux/Ubuntu noobie - installed Ubuntu 10.10 Netbook on my tablet PC this weekend - all good except.. WiFi keeps dropping out.

PC has Intel 2200BG adapter installed. AP has 11g only traffic selected.

I found a lot of similar posts regarding 2200BG, but I don't think I've seen any solutions yet.

A few bits of relevant info..

tim@Tablet:~$ ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  209190 2010-08-16 20:02 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2010-08-16 20:02 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2010-08-16 20:02 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2010-08-16 20:02 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2010-08-16 20:02 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2010-08-16 20:02 ipw2200-sniffer.fw
tim@Tablet:~$ 

tim@Tablet:~$ dmesg | grep ipw
[   25.936425] libipw: 802.11 data/management/control stack, git-1.1.13
[   25.936436] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.199441] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.199454] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.199710] ipw2200 0000:02:06.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   26.216292] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.943176] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[  582.020821] ipw2200: Firmware error detected.  Restarting.
[  590.641125] ipw2200: Firmware error detected.  Restarting.
[  etc etc...

What is the latest thinking on this problem?

Should I consider updating the ipw2200 driver/firmware??
If so, is there an idiots guide on how to do this?

Any help gratefully received...

---

### Post by chili555 on 2011-01-23
> AP has 11g only traffic selected.Does it drop if you change the router to autonegotiate the rate? That is, mixed B and G?

---

### Post by Tim Waterman on 2011-01-24
OK thanks Chili555 - tried this, but WiFi still dropping out.
What should I try next?
Thanks

---

### Post by chili555 on 2011-01-24
Please try installing linux-backports-modules-compat-wireless-2.6.36-maverick-generic through System > Administration > Synaptic. It evidently has a newer version of iwp2200 in it. You might also change the channel your router is on; perhaps you have some radio frequency interference from dimmers, cordless phones, microwaves, nearby ham radios, etc. I have the best luck on channel 11. 

Can you interrupt the boot process with the shift key and boot into an earlier kernel version? Is the behavior improved?

Last, you might look in:```
sudo cat /var/log/syslog | grep -e eth -e ipw
```See if there are any clues as to what is causing the drops aside from a firmware error. If the file is sparse, it has recently been archived and started fresh; look in syslog.1.

---

### Post by Tim Waterman on 2011-01-26
Couldn't find linux-backports-modules-compat-wireless-2.6.36-maverick-generic through System > Administration > Synaptic. found compat-wireless-2011-01-26 online and downloaded but unable to compile - gcc not installed

Linux Tablet 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
Netbook edition - installed via USB

sudo cat /var/log/syslog | grep -e eth -e ipw 
....
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> (eth1): device state change: 5 -> 6 (reason 0)
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> (eth1): device state change: 6 -> 4 (reason 0)
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1/wireless): connection 'Auto TimHome' has security, and secrets exist.  No new secrets needed.
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan 26 20:51:06 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan 26 20:51:07 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  associating -> associated
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  associated -> completed
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TimHome'.
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jan 26 20:51:08 Tablet dhclient: Listening on LPF/eth1/00:0e:35:9b:41:83
Jan 26 20:51:08 Tablet dhclient: Sending on   LPF/eth1/00:0e:35:9b:41:83
Jan 26 20:51:08 Tablet dhclient: DHCPREQUEST of 192.168.1.17 on eth1 to 255.255.255.255 port 67
Jan 26 20:51:08 Tablet NetworkManager[714]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jan 26 20:51:11 Tablet dhclient: DHCPREQUEST of 192.168.1.17 on eth1 to 255.255.255.255 port 67
Jan 26 20:51:11 Tablet NetworkManager[714]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Jan 26 20:51:11 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 26 20:51:11 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jan 26 20:51:11 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 26 20:51:11 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 26 20:51:11 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jan 26 20:51:11 Tablet avahi-daemon[712]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.17.
Jan 26 20:51:11 Tablet avahi-daemon[712]: New relevant interface eth1.IPv4 for mDNS.
Jan 26 20:51:11 Tablet avahi-daemon[712]: Registering new address record for 192.168.1.17 on eth1.IPv4.
Jan 26 20:51:12 Tablet NetworkManager[714]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Jan 26 20:51:12 Tablet NetworkManager[714]: <info> Policy set 'Auto TimHome' (eth1) as default for IPv4 routing and DNS.
Jan 26 20:51:12 Tablet NetworkManager[714]: <info> Activation (eth1) successful, device activated.
Jan 26 20:51:12 Tablet NetworkManager[714]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jan 26 20:52:02 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  completed -> disconnected
Jan 26 20:52:02 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan 26 20:52:03 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan 26 20:52:03 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  associating -> associated
Jan 26 20:52:03 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  associated -> completed
Jan 26 20:53:10 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  completed -> disconnected
Jan 26 20:53:10 Tablet NetworkManager[714]: <info> (eth1): supplicant connection state:  disconnected -> scanning

Thinking about buying a different wireless card to solve this!?
thanks..

---

### Post by andrew5859 on 2011-01-26
Are you on a home or business network.....if it's a home network, the subnet mask is wrong, it should be 255.255.255.0, this could be why your signal drops off....just a thought...cheers

Andrew

---

### Post by chili555 on 2011-01-26
> found compat-wireless-2011-01-26 online and downloaded but unable to compile - gcc not installedThat's probably the long way around. Let's reserve that for Plan B. With an internet connection, try:```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-`uname -r`
```Those tick marks are on the left side of my US keyboard on the same key with ~.

In your first post, you showed the size of the firmware files. Although mine are the exact same size, let's check their integrity with md5sum. Run this command:```
md5sum /lib/firmware/ipw2200*
```You are hoping for this result:```

045a46163341514ef17490c76bd0c858  /lib/firmware/ipw2200-bss.fw
44cdedc8d5a0eb727466ed982db97a53  /lib/firmware/ipw2200-ibss.fw
ebc70dce66f876695fa8852b8ff757ee  /lib/firmware/ipw2200-sniffer.fw
```Let us know if the sums are different.> .if it's a home network, the subnet mask is wrongI believe dhclient, which is called by Network Manager, uses x.255. I don't believe Tim can change it.

---

### Post by Tim Waterman on 2011-01-28
Excellent  chili555 - all installed OK - WiFi now stable !! - ipw2200 checksums match OK.
Thank you chili555..

---

