---
title: "Extremely slow internet with Ubuntu, esp. DNS lookup times"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by jaygauthier on 2010-05-19
Hi all.  I just wanted to share with everyone a problem I was having, and how I eventually fixed it thanks to this post here by psyke83.

Internet browsing had been quite slow, and symptoms were consistent with slow DNS lookup times.  After searching for help online I came across this and it worked. Not sure whether this is more of a Ubuntu issue, or driver issue, or router issue, but manually setting the DNS servers fixed it as described below.

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9119483&postcount=51](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9119483&postcount=51)

> [LIST]
[*]Right-click on the Network Manager applet and choose Edit Connections.
[*]Edit your active internet connection, and go to the IPv4 Settings.
[*]Change 'Method' to 'Automatic (DHCP) addresses only'
[*]Enter into the 'DNS servers' field: 192.168.1.1
[*]Leave the 'Search domains' and 'DHCP client ID' entries blank.
[/LIST]

Restart your connection and let me know if it helps at all.

Note: to revert these settings, simply change the 'Method' back to 'DHCP'.


My system is a Dell 1012 netbook, with Atheros wireless (Ath9k driver), and it's a Belkin router. (Using Wifi, not wired.)

Thanks psyke83 :KS  Internet's now working as it should, nice and zippy~!

---

### Post by Jerryo100 on 2010-05-19
Is 192.168.1.1 your router's ip address? I came across the same post as I was having the same problem with very slow dns lookups and page not found errors, but using that ip address stopped any page from loading (Ubuntu was using my routers ip and one of AT&T's). What worked great for me was using the ip addresses generated at [http://www.dnsserverlist.org](http://www.dnsserverlist.org)

---

### Post by nanonils on 2010-08-08
> **jaygauthier said:**
> Hi all.  I just wanted to share with everyone a problem I was having, and how I eventually fixed it thanks to this post here by psyke83.

Internet browsing had been quite slow, and symptoms were consistent with slow DNS lookup times.  After searching for help online I came across this and it worked. Not sure whether this is more of a Ubuntu issue, or driver issue, or router issue, but manually setting the DNS servers fixed it as described below.

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9119483&postcount=51](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9119483&postcount=51)


Weirdest thing ever! You have just solved my WiFi troubles after many hours of tinkering with the driver ([http://ubuntuforums.org/showthread.php?t=1547049](http://ubuntuforums.org/showthread.php?t=1547049)). I felt so defeated I was close to buying Win7 and arrange a partition on that Compaq to make it usable again...

Thank you much!

---

