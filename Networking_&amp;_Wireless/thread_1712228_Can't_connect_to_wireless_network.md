---
title: "Can't connect to wireless network"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by orrymr on 2011-03-22
Hey all, my wireless card seems to be working fine in that it's picking up my wireless network, but I cannot connect to it. After some time it simply times out. Here is what is in my syslog:

grep -ie wlan -ie ndis /var/log/syslog returns 
> 
Mar 22 17:30:00 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Mar 22 17:30:00 ubuntu NetworkManager[987]: <info> (wlan0): supplicant connection state: completed -> disconnected
Mar 22 17:30:00 ubuntu NetworkManager[987]: <info> (wlan0): supplicant connection state: disconnected -> associated
Mar 22 17:30:00 ubuntu NetworkManager[987]: <info> (wlan0): supplicant connection state: associated -> 4-way handshake
Mar 22 17:30:00 ubuntu NetworkManager[987]: <info> (wlan0): supplicant connection state: 4-way handshake -> group handshake
Mar 22 17:30:00 ubuntu NetworkManager[987]: <info> (wlan0): supplicant connection state: group handshake -> completed
Mar 22 17:30:09 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Mar 22 17:30:20 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Mar 22 17:30:34 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Mar 22 17:30:38 ubuntu NetworkManager[987]: <warn> (wlan0): DHCPv4 request timed out.
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1723
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Mar 22 17:30:38 ubuntu NetworkManager[987]: <warn> Activation (wlan0) failed for access point (NETGEAR)
Mar 22 17:30:38 ubuntu NetworkManager[987]: <warn> Activation (wlan0) failed.
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Mar 22 17:30:38 ubuntu NetworkManager[987]: <info> (wlan0): deactivating device (reason: 0).


Any help would be very much appreciated.

---

### Post by colio on 2011-03-22
You're not using a Broadcom 43XX card by any chance are you?

---

### Post by orrymr on 2011-03-22
No, Netgear wg311v3

---

### Post by colio on 2011-03-22
I was having a similar problem when I upgraded my router.  I switched the wifi card driver and the problem went away.  I'm not familiar with any Netgear issues but you might try looking for an updated driver.

---

### Post by orrymr on 2011-03-22
Hmmm, I've actually only tried the win2k driver using ndiswrapper - thanks for the advice, I'll give it a shot!

---

### Post by orrymr on 2011-03-22
Aaah! Awesome! If I could reach across the internet and hug you I would! You have no idea how long its taken me to get this wireless story sorted; this was simply the latest in a long line of problems. The signal strength isn't very strong though, but I'll try experiment with other drivers. The Windows XP one works whilst the 2k one doesn't. I've yet to experiment with the 98 and ME drivers.

Thanks again for the advice

---

