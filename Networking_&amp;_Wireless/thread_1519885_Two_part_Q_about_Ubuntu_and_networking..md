---
title: "Two part Q about Ubuntu and networking."
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2010-06-28
First:

What does ifup and ifdown do?

Second:

My wireless and etheret are set up.  How come when I check the /etc/network/interfaces file, It just says:

```
auto lo
iface lo inet loopback
```

Shouldn't it reflect my network settings in Ubuntu network manager?

I just don't understand the networking in Ubuntu after 2 years of using it.

---

### Post by Iowan on 2010-06-28
It's enough to confuse a sane person - fortunately...8-[
Sometimes (after 5 years) I realize that what I thought I knew has changed...
Network Manager and */etc/network/interfaces* kinda compete for network control. NM stores its settings under */etc/NetworkManager*. At one time, settings in "interfaces" overrode NM... I'm not so sure anymore.

There are  multiple ways to share (Samba) files, too. Sometimes too many choices are not a good thing...

---

### Post by pepsifx357 on 2010-06-28
> **Iowan said:**
> Sometimes too many choices are not a good thing...

I agree with that statement.

---

