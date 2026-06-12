---
title: "WUSB600N v1 install help on 10.04 please!"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by mrl72 on 2011-01-06
Hi all -

Well, I've been trying now for 2 days to get my WUSB600N v1 adapter installed on 10.04. I'm a bit of a noob but have been able to follow some posts on here on getting it set up. This is what I've done:

Installed the Ralink RT2870 drivers.
Changed the config.mk to enable some parameters.
Compiled and installed.
Added some entries to blacklist.conf.
Updated network/interfaces to include my wpa settings and passphrase.
Restarted/rebooted/reinstalled about 100 times!

Here's what happens:

iwconfig shows wlan0 with an ESSID:"" and Nickname: "RT2870STA"

iwlist wlan0 scan shows my router fine (although does not show Cell 02 which should be the 5GHZ range).

So basically it's not connecting to my router. Not sure if I missed any steps. Will gladly provide some extra output if needed. Pulling my hair out over this now ready to throw the adapter in the trash lol.

Cheers.

---

### Post by PatchesTheCaveman on 2011-01-07
If *iwlist* is showing your router, NetworkManager is probably to blame.  That's the program that drives the network icon on your top panel and manages your network connection.  A lot of people find that *wicd*, an alternative network management program, works a lot better.  To give it a shot, open a terminal and run these commands:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

---

### Post by mrl72 on 2011-01-07
Thanks for the response. It ended up being a conflicting driver (RT2800?) causing the problem. I added it to the blacklist and all seemed to work, that is work periodically..

The problem I have with this now is two fold:

1) It still will not connect to my 5GHZ network, even though signal seems strong and I can connect from my laptop to my N router from the same room.

2) It periodically stops working. I have to log in using my keyboard and restart the network service.

Any tips on fixing the above?

Much appreciated.

---

