---
title: "Ubuntu12 server 32bit"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by Spetsnaz on 2013-05-29
So I am having this problem with the Ubuntu issue networking.
It seems I can't ping google dns at all.
[COLOR=#000000][FONT=Tahoma]I can ping the openDNS server but DHCP DNS servers 8.8.8.8 and 8.8.4.4
[/FONT][/COLOR][ATTACH=CONFIG]243235[/ATTACH][ATTACH=CONFIG]243236[/ATTACH][ATTACH=CONFIG]243237[/ATTACH]

---

### Post by linuxtechguy on 2013-05-29
Then I would say there is a firewall blocking it somewhere.

---

### Post by Spetsnaz on 2013-05-29
This is a KVM VPS 
its all default and mininal OS that was installed and I tried with other KVM vps and i could ping to 8.8.8.8

---

### Post by sanderj on 2013-05-29
You can run

```
mtr -nrc2 8.8.8.8
```

to see where the path is blocked.

---

### Post by Spetsnaz on 2013-05-29
[ATTACH=CONFIG]243252[/ATTACH]
This is what I get

---

### Post by Spetsnaz on 2013-05-30
I am still facing this issue.

---

### Post by sanderj on 2013-05-31
(When you post pictures instead if text, it's harder for me to analyze)

Your mtr shows a few hops (good), but only 178.32.135.233 (which is ash-1-6k.va.us, but registered in France). It is hard to say what is going on.. I don't think it is a firewall on your own system.

I would try out mtr's to other destinations, and see if that works.

---

### Post by Spetsnaz on 2013-05-31
Sanderj I am using KVM and I can't copy and paste
[IMG]http://spetsnazhost.com/screenshots/SSoOw.png[/IMG]

---

### Post by sanderj on 2013-05-31
Have you asked your VPS provider about the 8.8.8.8 problem?

---

### Post by Spetsnaz on 2013-05-31
I am the VPS provider.

---

### Post by sanderj on 2013-05-31
You are the VPS provider?! LOL!

Then I would do this:

On the host, can you ping and mtr 8.8.8.8?
On another VPS, can you ping and mtr 8.8.8.8?
If you create a new, fresh VPS, can you ping and mtr 8.8.8.8?

---

### Post by Spetsnaz on 2013-05-31
Yeah I know
I have 3 dedis running on KVM, to be honest I really don't like KVM and preffer OpenVZ since this never happens on OpenVZ.

But I have destroyed this vps and created it again and on CentOs and debian and ubuntu and i faced the same problem.

I got curious and tried to ping with other vps on the same node and it was reachable so I checked the mac address of the ip to confirm it was correct and there was nothing wrong, so i just re-create the vps on a different ip and it seems like the problem got fixed.


So I am not sure how to set this thread as resolved as I am not even sure what went wrong.

---

