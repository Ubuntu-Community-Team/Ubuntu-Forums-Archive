---
title: "Connection Woes"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by Romppyy on 2006-03-05
First, let me say, Please be patient with me.  I'm a linux noob, so I don't know what I'm doing all that much, and I also may miss out on some fairly simple steps simple because I'm ignorant of them if you don't expressly tell me about them.

Now, I have a  Linksys WRT-54G router, and I'm trying to connect using a  WMP-54G PCI card (using the Broadcom chipset).  Using ndiswrapper and ndisgtk I was able to install the drivers for my card and get access to the router/internet.  I created an account for my little brother to use that has no administrative privledges.  When he was using his account he said that the internet suddenly cut out, and that the computer displayed a message saying there was no connection.  (Not sure about exact wording).  The internet and router are working, as I have access from another computer with WinXP on it.  I tried rebooting the computer, deactivating and reactivating the connection, and uninstalling/reinstalling the driver.  I checked to make sure that the essid and channel were correct (they are), and that the system recognizes the card (it does).

Finally, though I have absolutely no idea if this has relevance or not :rolleyes: I took a look at the daemon.log file.  At the time when the connection stopped working, there was an entry that said  "localhost -- MARK --".  This only occured when the connection stopped working, and there is no other mention of MARK that I can find in the log, nor was I able to find information about it on the internet.  Now, this may have absolutely nothing to do with my problem ;), but even if it doesn't have anything to do with my problem could you tell me what it is as I was not able to find that out.:mrgreen: 

Anyway, thanks a bunch in advance for helping me and putting up with my ineptitude ;) .  Also, sorry if the answer is right in front of my face.  *Big Grin*

---

### Post by Romppyy on 2006-03-05
Forgot to put this.........I put in "sudo dhclient wlan0" in terminal and got back this:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:41:12:a2:78
Sending on LPF/wlan0/00:0c:41:12:a2:78
Sending on Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received
Trying recorded lease 192.168.1.102
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
--- 192.168.1.1 ping statistics ---
1packet transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping

---

