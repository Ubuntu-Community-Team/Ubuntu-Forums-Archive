---
title: "rt2860sta on 9.04 and 9.10 (Beta)"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by Snocrash on 2009-10-25
Hi All,

I have a little Acer Aspire I use as a combination Desktop/FTP server/Media server for my Xbox360. I had the same issue on 9.04 that I am having with the 9.10 beta. It uses an ralink chip for wireless and the rt2860sta module. I have a standard 802.11g router running WEP encryption. If I log in as a user and use the Network Manager applet to setup the connection. everything works fine. But since I am using this as a server and sometimes have to reboot remotely, this is a bit of a pain.

If I remove the Network Manager and set up the /etc/network/interfaces file to start networking at boot, the connection fails. After some poking around, this seems to be because no matter how I set up the config file, "sudo iwconfig" responds with "Key=off". Even if I try to force it with "sudo iwconfig ra0 key XXXXXXXXXXXXXX".

I know the system works because the connection works when Network Manager is intalled. So my question is how does the Network Manager get around this and set the WEP key? And how do I do the same without Network Manager installed??

Anyone have any ideas???


Thanks,

-Sno

---

### Post by Snocrash on 2009-10-25
Bump.

---

### Post by Snocrash on 2009-10-26
Figured it out. You need to remove all wireless information (SSID, key, mode, channel, etc.) from the /etc/network/interfaces file and list it ONLY in the /etc/wireless/RT2860STA/RT2860STA.dat file. If it is in both places, the connection will fail. At least that fixed it for me on 9.10.

Hope that helps anyone else out there with this problem.


Thanks,

Sno

---

