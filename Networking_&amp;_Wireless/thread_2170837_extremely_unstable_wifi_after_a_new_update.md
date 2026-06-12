---
title: "extremely unstable wifi after a new update"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by zariskij on 2013-08-27
Hi, I've been using dell xps13 (intel centrinos advanced-N 6235) for half a year, and the wifi works fine (with 11n_disable=1). However, after a recent apt-get upgrade (I don't remember what was updated, but it was a quick one), my wifi becomes basically unusable. It connects sucessfully, but freezes roughly after 10 seconds and will come back to normal after 10-20 seconds, and then freezes after 10 seconds again, and so on. Any idea what is going on? Thanks!

By the way, it shouldn't a problem with the wifi signal, since another laptop with windows 7 has no problem at all.

---

### Post by zariskij on 2013-08-27
update: something weird happened. I searched the web and tried several possible solutions including installing backports and reinstalling dnsmasq. But it turned out that nothing worked. Then I felt desperate and uninstalled backports. After reboot, suddenly the wifi works fine again ... I have no idea what happened. I'll see if the problem persists. 

By the way, does anyone know whether the n-card bug in iwlwifi has been fixed or not? Do I still have to add 11n_disable = 1?

---

### Post by chili555 on 2013-08-27
> By the way, does anyone know whether the n-card bug in iwlwifi has been fixed or not?Nope.> Do I still have to add 11n_disable = 1? Possibly. Some card and router combinations, including mine, work fine. Most don't. I suggest you try without it and see. You obviously know how to replace it if needed.

---

