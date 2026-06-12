---
title: "very poor eth0 performance"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Disabled20240622 on 2010-08-24
Using lucid on a Lenovo W510, I'm having to use wireless because the network performance is incredibly bad, a ping shows that the nslookup and each ping takes about five seconds to complete. Any clues?

---

### Post by prshah on 2010-08-24
> **BigglesPiP said:**
> network performance is incredibly bad


See [ Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution.

Summary hint: Change the MTU (to 1492, or so)

---

### Post by Disabled20240622 on 2010-08-24
That's not the issue I'm seeing and I can't change the MTU on our corporate network.

---

### Post by Disabled20240622 on 2010-08-24
Turned out to be a rogue DNS server entry.

---

