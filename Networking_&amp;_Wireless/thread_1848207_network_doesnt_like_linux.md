---
title: "network doesnt like linux?"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by NERDMAN! on 2011-09-22
i seem to have quite a vexing issue here, neither my phone (android) or my laptop (ubuntu 10.04) will allow me to access hotmail, or any other msn related webpage, nor will it let me sign into messenger from any app at all.
everything else seems to work just fine.

now the vexing part, it all runs perfectly fine on my fathers windows pc.

i'm on a wifi connection using a asus WL-520GC wireless router and an iconnect access 621 adsl2+ modem on a westnet plan. its been doing this for quite a while now and usually power cycling the modem and router would fix it temporarily. now it seems this no longer works. i have power cycled the modem and router 6 times tonight, to no avail. i'm starting to think it might be either a serious misconfiguration somewhere, or possibly time for a new router. i figured seeing as i have next to zero networking knowledge i should ask for a second opinion before spending money on a router that might have the same issue.

---

### Post by varunendra on 2011-09-24
I can suggest two quick things which can be easily verified without changing anything:

[LIST=1]
[*]Check whether the connection works fine from a Live CD,
[*]Check whether it works from a Live CD _on your father's computer_.
[/LIST]
One more thing - check whether the DNS IPs are same on your computer and your father's (in Windows).

---

### Post by NERDMAN! on 2011-10-06
may i ask where in ubuntu i would find the dns settings?
i found it in windows, but it eludes me in ubuntu.

---

### Post by varunendra on 2011-10-06
> **NERDMAN! said:**
> may i ask where in ubuntu i would find the dns settings?
i found it in windows, but it eludes me in ubuntu.
It is noted as plain text in **/etc/resolv.conf** file. Quickest way to view it:
```
cat /etc/resolv.conf
```

---

