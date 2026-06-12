---
title: "Moblock issues"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by poho on 2009-01-07
Hi guys, was hoping to get some help here (running out of options)

Im using debian (so mostly ubuntu) and am trying to get moblock working for my, uh, legitimate torrents.

My network is set up like this:

I have a dsl modem/router connected to my debian box (the box is called liza).  liza has 2 nics in her, one from the router, the other to my internal network.  liza acts as a NAT box as well as dhcp and all the rest.  The external interface on liza (connected to the router) is 10.1.1.3 and the internal one is 192.168.0.1.

After a heap of messing around i got moblock installed and not completely killing my internet connectivity.  However now, it seems like my http traffic is being filtered by moblock  (even though traffic on one specific port is all i told it to filter - using moblock for torrents here).

Is there somethign i'd need to accept thru my 10.1.1.3 interface or white list with moblock??

Any help would be greatly appreciated

poho

---

### Post by jre on 2009-01-08
General answer: All traffic internet - your LAN goes through the FORWARD chain (moblock_fw). So if you want to block or whitelist traffic for the rest of your network this is where you have to look at.

The traffic to your Debian box is handled by INPUT and FORWARD (moblock_in and moblock_out).

For concrete help I need to know which traffic to which machines you want to have checked by MoBlock and which you want to not being checked.

---

### Post by jre on 2009-01-08
[deleted double post]

---

### Post by jre on 2009-01-08
[deleted double post]

---

### Post by poho on 2009-01-12
im trying only to moblock bitorrent traffic coming off the machine that moblock is installed on.  I think i have already played with the white forward bit, although ill double check it tonight and see how i go!

thanks

---

