---
title: "connecting to WRT54GX4"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by reckless2k2 on 2006-02-23
I have an Atheros based wifi card that had no issue connecting to any other access point except for the recent purchase of the new Linksys WRT54GX4 (SRX400). I can not associate with the AP even standing right next to it. I'm using the stock madwifi drivers in Ubuntu and am wondering if I need to recompile with a newer version because of soemthing specific to this router. Any help would be appreciated.

---

### Post by reckless2k2 on 2006-03-01
Am I in the wrong forum for this question?

---

### Post by Lambert on 2006-03-01
If you can connect to other routers there's nothing wrong with your driver as it's functioning. so no you don't have to recompile a newer driver.

There is one other user recently who posted about this router and took his router back. He could connect but had other problems. After some searching found there's a lot of problems  with firmware. Is this your problem? don't know but it's not the driver. It's some breakdown in the two devices being able to talk to each other.

You'll just need to check all your network settings to make sure they match up?

Can you scan for the router and see it?

sudo iwlist ath0 scan

Can you associate with router and just not get an ip? Post output of iwconfig

---

### Post by alfermp on 2008-04-23
I have the same router on my house Linksys WRT54GX4 and i can not get connection. In my Mother office i have Linksys WRT54G and i can get connection. I can get connection on McDonalds, StarkBuck and other places too but no in my house with Linksys WRT54GX4. I try to change the security connection from MAC Filter to WPA an dWeb but nothing i can not get connection. I use Hardy:(

---

### Post by sportman1280 on 2008-05-04
Same issue.  Have tried multiple computers on the same router.  Hardy just doesnt connect. It worked great before the upgrade.... er

---

### Post by sportman1280 on 2008-05-05
Can no one help?

---

