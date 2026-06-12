---
title: "How to Disable ipv6 in Ubuntu 9.10?"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by a.malcolm.stanley@gmail on 2009-10-31
In this thread, [http://ubuntuforums.org/showthread.php?t=1036068](http://ubuntuforums.org/showthread.php?t=1036068) ,
I identify by log entries that DHCP is failing during wireless network setup, causing a loop asking for the WEP password for the connection...

Google indicates this may be caused by presence of ipv6 DHCP calls which are incompatible with the wireless router software. FTR, I am using a stock unmodified verizon fios router.

I would like to test this theory by disabling ipv6 on the wireless link and seeing if ipv4-only dhcp transactions are successful.

I cannot find current instructions on how to do so; 
help would be appreciated.

Without this step I cannot enter an accurate bug report and help the community by eliminating this issue through identification of root cause.

Thanks all.

---

### Post by slask on 2009-10-31
I turned off IPv6 in Ubuntu 9.10 by adding "ipv6.disable=1" in kernel boot option. (GRUB_CMDLINE_LINUX_DEFAULT string in /etc/default/grub).

---

### Post by Sinsemila on 2009-10-31
Does that mean the line would look like this?
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" ipv6.disable=1
I haven't saved and updated yet until I'm sure how to do it.

---

### Post by eden159 on 2009-10-31
Take a look at this: [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)

---

### Post by Sinsemila on 2009-10-31
Thanks, lucky I waited as I had it wrong in the above post.

---

### Post by vasiauvi on 2009-10-31
Hy,
is strange but on my system there isn't /etc/default/grub 
but maybe this is working :
```
gedit /etc/sysctl.conf
``` and add this line net.ipv6.conf.all.disable_ipv6 = 1 
after that reboot!
Hope is working!

---

### Post by a.malcolm.stanley@gmail on 2009-11-01
so I followed the instructions and disabled IP V6 in the GRUB config.

which is why I am confused by this log fragment:

```
Nov  1 20:26:36 marquesas NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '7LQ21'.
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Nov  1 20:26:36 marquesas NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Nov  1 20:26:36 marquesas dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  1 20:26:36 marquesas dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  1 20:26:36 marquesas dhclient: All rights reserved.
Nov  1 20:26:36 marquesas dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  1 20:26:36 marquesas dhclient:
Nov  1 20:26:36 marquesas NetworkManager: <info>  dhclient started with pid 2117
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1) Beginning IP6 addrconf.
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Nov  1 20:26:36 marquesas dhclient: Listening on LPF/eth1/00:12:f0:00:b6:ae
Nov  1 20:26:36 marquesas dhclient: Sending on   LPF/eth1/00:12:f0:00:b6:ae
Nov  1 20:26:36 marquesas dhclient: Sending on   Socket/fallback
Nov  1 20:26:36 marquesas NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Nov  1 20:26:37 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov  1 20:26:40 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov  1 20:26:43 marquesas dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  1 20:26:47 marquesas NetworkManager: <info>  Device 'eth1' IP6 addrconf timed out or failed.
Nov  1 20:26:47 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Nov  1 20:26:47 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) started...
Nov  1 20:26:47 marquesas NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
Nov  1 20:26:47 marquesas NetworkManager: <info>  Activation (eth1) failed for access point (7LQ21)
Nov  1 20:26:47 marquesas NetworkManager: <info>  Marking connection 'Auto 7LQ21' invalid.
Nov  1 20:26:47 marquesas NetworkManager: <info>  Activation (eth1) failed.
Nov  1 20:26:47 marquesas NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) complete.
Nov  1 20:26:47 marquesas NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Nov  1 20:26:47 marquesas NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Nov  1 20:26:47 marquesas NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 2117
Nov  1 20:26:47 marquesas wpa_supplicant[1238]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```specifically, this line is confusing me:

```
Nov  1 20:26:36 marquesas NetworkManager: <info>  Activation (eth1) Beginning IP6 addrconf.
```if IP V6 is disabled, why is DHCP6 address config performing an IPV6 address config?

Anybody have any idea how to get DHCP to back off to an IPV4 config?

---

### Post by uniden9 on 2009-11-02
I question the ipv6.disable=1 kernel parameter actually does anything as well. I guess the only way to remove ipv6 for sure is to compile your own kernel with out it.  I hate going down that road, but sometimes its required.

Justin

---

### Post by TheForumTroll on 2009-11-02
> **vasiauvi said:**
> Hy,
is strange but on my system there isn't /etc/default/grub 
but maybe this is working :


If you upgraded then you still use the old grub. Then it's /boot/grub/menu.lst

---

### Post by vasiauvi on 2009-11-02
> **TheForumTroll said:**
> If you upgraded then you still use the old grub. Then it's /boot/grub/menu.lst
Ahhh...ok, I understand!
Thanks!

---

