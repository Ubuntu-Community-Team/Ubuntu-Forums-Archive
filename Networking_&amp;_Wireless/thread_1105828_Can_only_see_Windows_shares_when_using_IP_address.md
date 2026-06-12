---
title: "Can only see Windows shares when using IP address"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by mssever on 2009-03-25
I'm trying to hook into the network at the school where I teach. All machines except mine run XP. I can't see any machines from Nautilus (though other machines can see my shares). However, if I point Nautilus at smb://<ip-address>, I can see the relevant machine.

Also, possibly related: I've installed one of the printers (HO DeskJet 1125C) as a network printer (via Samba, of course). However, jobs sent to it don't actually print, though I get no error messages.

---

### Post by BkkBonanza on 2009-03-25
One thing you can do is put names in your /etc/hosts file to map to the ips. If there is a DNS server running on your lan then I think it should find names from that. If not then the hosts file works but is manual editing.

---

### Post by mssever on 2009-03-25
> **BkkBonaza said:**
> One thing you can do is put names in your /etc/hosts file to map to the ips. If there is a DNS server running on your lan then I think it should find names from that. If not then the hosts file works but is manual editing.
The IPs are not static. Besides, I shouldn't have to do anything like that, because Windows doesn't require a hosts file hack.

---

### Post by dmizer on 2009-03-25
You should be able to get the smb://servername to work with the following directions:

Edit /etc/nsswitch.conf and add "wins" to the hosts line (before dns) so it looks /something/ like this:
```
hosts:          files [COLOR="Red"]wins[/COLOR] dns mdns
```
Then install winbind:
```
sudo aptitude install winbind
```

This may or may not allow browsing via Nautilus.

---

### Post by nickmcg on 2009-03-25
I would suggest that you put wins at the end of the hosts line  - I found (with Jaunty) that I lost name resolution for the outside world unless wins was after dns

Nick

---

### Post by mssever on 2009-03-25
> **dmizer said:**
> You should be able to get the smb://servername to work with the following directions:

Edit /etc/nsswitch.conf and add "wins" to the hosts line (before dns) so it looks /something/ like this:
```
hosts:          files [COLOR=Red]wins[/COLOR] dns mdns
```Then install winbind:
```
sudo aptitude install winbind
```This may or may not allow browsing via Nautilus.
Thanks. That did the trick.

My printing problem is unresolved. However, it now appears that it's unrelated to my first problem, so I'll open a separate thread about it.

---

### Post by mssever on 2009-03-25
> **nickmcg said:**
> I would suggest that you put wins at the end of the hosts line  - I found (with Jaunty) that I lost name resolution for the outside world unless wins was after dns

Nick
I discovered something similar after making the change, having file sharing work, then being unable to resolve DNS. I think it has something to do with the [NOTFOUND=return] in nsswitch.conf (Intrepid in my case).

Here's my current file, which seems to work:
```
#hosts:          files mdns4_minimal wins [NOTFOUND=return] dns mdns4
hosts:          files mdns4_minimal wins dns mdns4
``` Though I must confess that I don't that the [NOTFOUND=return] might be doing that may be useful. The man page wasn't terribly helpful.

---

### Post by nickmcg on 2009-03-25
I agree about the [NOTFOUND=return] being the problem - you removed it, I just put wins the other side of it:)

It seems to work either way.

Nick

---

