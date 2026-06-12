---
title: "Unable to Automatically Reconnect to Wireless Connection, 12.04"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by odinbaal on 2012-04-14
Hi all,

I've done the required search on this and other forums but didn't find what I was looking for.

I have a wireless connection and everything is working fine. The only problem is that if I am disconnected for whatever reason (electricity outage, for example), the system does not re-connect automatically (unlike W7 on my dual boot machine). I get the "authentication required by wireless network" box which I have to accept (the passphrase is already there) and then I'm reconnected.

Thing is I keep my machine on at night when downloading and if I'm disconnected and I'm not there to click on the dialog box, I waste the whole night having downloaded very little.

Any settings I'm not aware of which automatically re-connect when the connection is dropped?

Note: The "Connect Automatically" and "Available to all Users" boxes are checked alright; using Network Manager.

(Ubuntu 12.04 beta, fully updated)

Thanks!

---

### Post by praseodym on 2012-04-14
Hi,

set the encryption mode to pure WPA2-AES if possible.

---

### Post by odinbaal on 2012-04-14
Thanks for the help, praseodym.

My encryption is initially set to "WPA & WPA2 Personal," and the only other options I have in network manager are:

None
WEP 40/128-bit
WEP 128-bit
LEAP
Dynamic WEP
WPA & WPA2 Enterprise

---

### Post by praseodym on 2012-04-15
You need to change it in your router interface: Connect via cable and type in the IP address of the router in your browser.

---

### Post by iyjian on 2012-04-15
hey, i am having the same problem as you. i suspect it is a bug in 12.04 LTS.

see 
[https://bugs.launchpad.net/ubuntu/+bug/974833](https://bugs.launchpad.net/ubuntu/+bug/974833)

[http://askubuntu.com/questions/101429/wireless-not-working-ubuntu-12-04](http://askubuntu.com/questions/101429/wireless-not-working-ubuntu-12-04)


what is the wireless network controller  of your computer? mine is "Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection".

---

### Post by odinbaal on 2012-04-15
Thanks.

Setting in router is initially WPA2 with encryption algorithm AES; I just checked.

---

### Post by praseodym on 2012-04-15
Ok, so please show:

> lspci -nnk | grep -iA2 net
iwconfig
lsmod
sudo iwlist scan

---

### Post by odinbaal on 2012-04-15
OK, new development:

I had an electricity cut (and back on again) just 15 minutes ago and, although I got the dialog box mentioned above in order to reconnect, the connection was up on its own.

So, it seems there is something with (maybe) Ubuntu authorization which turns up when the wireless goes off, but the network comes back on nonetheless, albeit with some delay. I'm writing this with the network on but with the "Authentication required by wireless network" still there. If I click on "Cancel" I still have my connection.

I hope this helps.

---

### Post by raymondvillain on 2012-04-18
> **praseodym said:**
> Ok, so please show:

I'm having the same problem.
What will the output of these commands tell me?

---

### Post by aapash on 2012-05-09
The following instructions resolved the issue in my case:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/975882/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/975882/comments/24)

---

