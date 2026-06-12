---
title: "Please help examining NetworkManager syslog output (bcm43xx, WPA)"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Patsoe on 2006-06-04
Dear all,

I'm sooo close to getting my wireless connection working (I think...).

I'm using the bcm43xx driver with NetworkManager. My system has a Broadcom 4318 wlan chip, for which I obtained a firmware with fwcutter from an Acer driver ([from here]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip")). 

I am staying at a place where only a WPA-protected network is available. This makes troubleshooting my connection somewhat difficult.

Anyway, I can scan for networks, and can see the networks that I also see in WinXP. When I try to connect, NetworkManager correctly finds that a WPA-key is needed and asks me to enter it. Then, it tries to connect but stops after a minute.

I've extracted the output in /var/log/syslog to an attached file. I did a fresh system start, then tried to connect - then included only the messages since the restart. It's still 1200 lines... sorry. NetworkManager output starts at line 403.

I think there is something odd at the point where NetworkManager invokes wpa_supplicant (starting at line 484). Up to that point, everything is as I'd expect. But then it seems wpa_supplicant is dropping the connection to the accesspoint, and trying to scan for accesspoints? It keeps iterating this until NetworkManager cancels the whole operation after one minute trying.

I must admit I understand very little of the output. Please help me interpreting the problem. Many thanks in advance!

---

### Post by Patsoe on 2006-06-04
There's one more thing I noticed... the following message shows up repeatedly in /var/log/syslog:

```
Jun  4 14:05:53 localhost kernel: [  157.280463] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

```

but I have no idea if this has any relation to the problem... that is, it didn't show up in the 1200-odd lines of syslog I uploaded earlier.

---

### Post by Patsoe on 2006-06-05
I'm posting from my laptop over the WPA wireless connection now!

I decided to try the ndiswrapper driver and it worked in one go. NetworkManager (or wpa-supplicant) apparently plays nicer with ndiswrapper right now than with the bcm43xx driver, well for this machine anyway.

Now there's one thing I should still do ofcourse, and that's informing the bcm43xx developers of my troubles. The thing is, I don't know where the problem is, so I don't really know where to send my info...?

---

### Post by Emrysk on 2006-07-15
I've had very similar trouble, and I settled on ndiswrapper, too.  I plan on informing the [NetworkManager]("http://www.gnome.org/projects/NetworkManager/") developers instead--or, at least, their mailing list.

I'm glad you got it working in the end despite not having native drivers.  Users like you who'll go out of their way to help altruistic Open Source hackers are not in the majority.  If I could send you a brownie, I would, but instead I just wish you good luck.

Good luck.

---

### Post by Patsoe on 2006-07-15
Hi, thanks! And good luck to you too!

---

### Post by motin on 2006-09-19
Aha so here is the new thread. 

How do I know if I am using ndiswrapper or not? The NetworkManager connection info shows (or rather: showed - nowadays it doesnt show anything complaing that the glade file isnt there...) ipw2200 i believe. But is ndiswrapper a higher and or lower level driver than shown there?

I'd like to try out ndiswrapper as I am experiencing the same problem...

---

### Post by eltorodeoro on 2006-09-21
Patsoe,

Are you able to connect to non-encrypted networks?  I've got a card with the same chipset, and WPA works great, but the only way I can connect to an open network is by by-passing Network-Manager and configuring it through the basic gnome GUI - net-admin, i believe.  Then, when I want to connect back to my WPA network, I've got to unconfigure it to let NM do its thing.  I think a reboot is required somewhere in there.

Motin - I think if you do a **dmesg** it will show what driver your wireless interface is using.  Just look for the interface name in the output.

jc

---

