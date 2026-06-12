---
title: "Interesting Wireless Problem after Reinstall"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by Coda_ on 2010-11-25
I recently reinstalled 10.04. The wireless worked fine for a week or so, but not it cant get a connection for more than a few seconds. Ive downloaded Wicd, and after an eternity of trying to connect, it tells me that no IP address could be established. I can connect no problem when I plug in via Ethernet cable. Nothing when I try to use the wireless though.

---

### Post by grahammechanical on 2010-11-25
Are you aware of the wireless trouble shooting guide?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Try some of the checks in that guide.

Regards.

---

### Post by Hippytaff on 2010-11-25
If you have no luck with the guide please do
```

lscpi | grep -i net > Wireless.txt

```
```

iwconfig >> wireless.txt

```
and```
lshw -C network >> wireless.txt

```
and post the wireless.txt file here :-)
 
Might be worth trying
```

rfkill all

```
first :-)

---

