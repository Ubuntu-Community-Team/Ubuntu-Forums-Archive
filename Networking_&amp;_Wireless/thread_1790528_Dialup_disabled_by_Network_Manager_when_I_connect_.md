---
title: "Dialup disabled by Network Manager when I connect ethernet/wireless"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by jamadagni on 2011-06-25
Hello. I'm running Kubuntu Natty. As I have no broadband connection at home [:(] I have to connect to the net via my Nokia C5 mobile phone and a Vodafone connection. Thankfully Natty automatically detects my phone when it is plugged in in the correct mode and using a wizard enables me to connect. (The "correct" mode is 'PC Suite', and NOT 'Connect PC to Web' which is apparently only valid for Windows, sheesh.) 

However, I also have an ethernet/wireless router connecting my two laptops and desktop via ethernet cable. 

The problem is that when I connect to my local home network via ethernet or wireless, the dialup mobile internet connection gets disabled. See the below behaviour when I disconnect and then reconnect my ethernet (similar thing happens for wireless too):

```

$ dmesg | tail
[   21.364609] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   21.377712] NFSD: starting 90-second grace period
[   22.383233] acer_wmi: Acer Laptop WMI Extras unloaded
[   28.389718] PPP BSD Compression module registered
[   28.429614] PPP Deflate Compression module registered
[  232.247075] r8169 0000:03:00.0: eth0: link up
[  232.247730] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  242.382351] eth0: no IPv6 routers present
[  329.914179] r8169 0000:03:00.0: eth0: link down
[  340.164564] r8169 0000:03:00.0: eth0: link up
$ tail /var/log/syslog
Jun 25 09:53:52 sarvajnatma NetworkManager[873]: <info> Scheduling stage 5
Jun 25 09:53:52 sarvajnatma NetworkManager[873]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 25 09:53:52 sarvajnatma NetworkManager[873]: <info> Done scheduling stage 5
Jun 25 09:53:52 sarvajnatma NetworkManager[873]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 25 09:53:52 sarvajnatma NetworkManager[873]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 25 09:53:53 sarvajnatma NetworkManager[873]: <info> Policy set 'Vodafone - Vodafone Connect' (ppp0) as default for IPv4 routing and DNS.
Jun 25 09:53:53 sarvajnatma NetworkManager[873]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun 25 09:53:53 sarvajnatma NetworkManager[873]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 25 09:53:53 sarvajnatma NetworkManager[873]: <info> Activation (eth0) successful, device activated.
Jun 25 09:53:53 sarvajnatma NetworkManager[873]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

```

The problem is evident in the line that says that the policy has been changed to choose the ethernet connection for IP4 routing and DNS when it is plugged in, probably because NM assumes that ethernet would give greater speeds than dialup. The problem is that my ethernet (and wireless) isn't connected to the internet at all but only the dialup is!

On the Kubuntu NM tray applet I find no option by which to change the default for IP4 routing and DNS back to my mobile internet connection.

Can anyone please help?

---

### Post by jamadagni on 2011-07-05
Those interested may look at the solution provided at [https://bugzilla.gnome.org/show_bug.cgi?id=653789](https://bugzilla.gnome.org/show_bug.cgi?id=653789)

---

