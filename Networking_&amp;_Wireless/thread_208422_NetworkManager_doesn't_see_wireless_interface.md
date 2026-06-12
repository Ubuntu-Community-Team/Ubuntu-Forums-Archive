---
title: "NetworkManager doesn't see wireless interface"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by Rob_H on 2006-07-03
Hi. I just successfully set up a Linksys WPC54GS card with NdisWrapper under Dapper. It works fine, but now I want to enable WPA security on my network. After searching the forum, it sounds like all I need to do is install "network-manager-gnome". I've done that, and rebooted. But when I click on the Network Manager applet, the only connection that shows up is my wired ethernet connection, which is grayed out. (It's not plugged in.) There is no wireless network option listed.

Meanwhile, my wireless card continues to function, since I haven't enabled WPA yet. So how do I get NM to see my wireless connection? Is there a way to configure the set of interfaces visible to NM?

Thanks!

---

### Post by spd106 on 2006-07-03
You need to make sure that you have removed the configuration lines for the wireless interface (usually wlan0 or ath0) in the /etc/network/interfaces file. Then reboot (easiest way) and nm should be up and running.

---

### Post by Rob_H on 2006-07-03
I tried this, but it seemed to have no effect on Network Manager. I even tried removing all of the interfaces (except "lo") and still no change in NM after a reboot. Any other ideas?

---

### Post by kperkins on 2006-07-03
Go to System > Administration > Networking
(Type in your passowrd)
Check and see if, under Wireless connection, it says "The interface eth* is not configured."
If that's not what it says, ie. the interface is configured, then highlight it, click on properties, and uncheck the where it says "Enable this connection". Click ok, and close that window, and then OK to close the network settings window.
Your wireless should be seen by networkmanager now.
If this doesn't help, I'm stymied.

---

### Post by Rob_H on 2006-07-03
Thanks for your suggestions. I tried disabling the connection as you described, rebooted, removed all entries from /etc/network/interfaces again, rebooted, but still no change.

If I plug a network cable into my wired Ethernet port, NM does detect that okay. But no matter what I do, it won't see the wireless. Could it have something to do with the fact that I'm using NdisWrapper?

---

### Post by Matt0001 on 2006-07-04
I had the same problem--my wireless connection worked just fine, but the Network Manager icon in the notification area kept telling me there was no network connection. The icon just sat there and I saw it as just a little annoyace.  It finally annoyed me enough this morning to search through the forums and I found this thread.

Deleting the configuration lines in etc/networking/interfaces worked for me. 

And now that Network Manager is doing its thing, I'm learning how really handy it is.

---

### Post by ubunturules on 2006-07-04
Go into networking and deconfigure your etho connection.

```
sudo gedit /etc/network/interfaces
```

comment out anything that has to do with your essid but all of the lo and inet stuff.

---

### Post by spdlimit120 on 2006-08-10
Thanks for these posts, really helped me out!

---

### Post by Reb on 2006-08-10
That didn't work for me, but 'sudo /etc/init.d/dbus restart' did (that restarts NetworkManager daemon and dispatcher).

---

### Post by mattydee on 2006-12-20
> **Reb said:**
> That didn't work for me, but 'sudo /etc/init.d/dbus restart' did (that restarts NetworkManager daemon and dispatcher).

That did it for me too! 
:D

---

