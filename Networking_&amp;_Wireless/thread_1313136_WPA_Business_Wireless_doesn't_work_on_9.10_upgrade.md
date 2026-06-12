---
title: "WPA Business Wireless doesn't work on 9.10 upgrade some what"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by oliveira11670 on 2009-11-03
Hi,
i upgraded my 9.04 ubuntu on my asus 1000he to the 9.10, but the WPA business (MSCHAP) wireless access stoped working on the 9.10 as i use it to connect to the network at my university (Azores), the connect button gets shaded and doesn't let me connect. What should i do? Is there a way to solve this problem.

Regards,

Paulo Oliveira

---

### Post by covracer on 2009-11-03
This bug was reported during beta testing and nobody ever did anything about it. Not only TTLS/MSCHAP but also TLS is affected, and possibly all WPA2 methods. See [https://bugzilla.gnome.org/show_bug.cgi?id=590644](https://bugzilla.gnome.org/show_bug.cgi?id=590644) and [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/447145](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/447145). I too am affected and it's very frustrating.

---

### Post by covracer on 2009-11-04
Anyone else having this issue?

---

### Post by oliveira11670 on 2009-11-04
> **covracer said:**
> This bug was reported during beta testing and nobody ever did anything about it. Not only TTLS/MSCHAP but also TLS is affected, and possibly all WPA2 methods. See [https://bugzilla.gnome.org/show_bug.cgi?id=590644](https://bugzilla.gnome.org/show_bug.cgi?id=590644) and [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/447145](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/447145). I too am affected and it's very frustrating.

Gee, do you think they'll fix this bug? It's anoying that it worked in 9.04 and not in 9.10 where it is needed :S
Where should one submit the bug more?

regards,
Paulo

---

### Post by covracer on 2009-11-13
I was a bit hasty in putting the blame on NetworkManager. Turns out I had an expired certificate. It would be nice if NM could tell you that your certificate was outdated, and if it supported PKCS12 certs.

---

### Post by Yoann Juet on 2009-11-14
We are still facing this issue with WPA and WPA2 (Enterprise) at my university and the EDUcation ROAMing wireless network infrastructure ([http://www.eduroam.org](http://www.eduroam.org)). It seems related to the encryption key renewal frequency. According to friends, a workaround would be to configure manually wpasupplicant, then bypassing Network Manager.

---

