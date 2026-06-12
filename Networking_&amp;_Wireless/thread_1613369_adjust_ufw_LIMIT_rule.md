---
title: "adjust ufw LIMIT rule"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by nerdy_kid on 2010-11-04
Hello, I need to adjust what exactly ufw LIMIT port# does.  I like the fact that the port is getting limited, but ufw overdoes it a bit. Is there a config file somewhere I can edit?  thanks.

---

### Post by nerdy_kid on 2010-11-05
bump...

---

### Post by nerdy_kid on 2010-11-06
bump....

---

### Post by nerdy_kid on 2010-11-07
bump

---

### Post by benju on 2011-01-13
hello nerdy_kid.

I don't know if you're still looking into this, but:

ufw rules are stored in a file called: *user.rules*

when you issue:

```
locate user.rules
```

the following comes up:

/lib/ufw/user.rules
/usr/share/ufw/user.rules
/usr/share/ufw/user.rules.md5sum
/usr/share/ufw/iptables/user.rules

I believe you must edit the */lib/ufw/user.rules* file. 
If you look inside (and have a current active limiting rule) you'll see the rule structure (I believe you need ...limit --limit 3/min...)

As far as *how* you must modify it, I honestly can't tell you as I haven't tinkered with this myself, it's up to you.
Test it in a Virtual Machine or non-critical hardware until you're sure you understand how it works (you don't want an accidental hole in your firewall) And when satisfied, apply it to the desired machine.

Disclaimer: I'm far from an expert and provide this tip to the best of my knowledge and with best intentions, use at your own risk.

cheers.

---

### Post by nerdy_kid on 2011-01-13
> **benju said:**
> hello nerdy_kid.

I don't know if you're still looking into this, but:

ufw rules are stored in a file called: *user.rules*

when you issue:

```
locate user.rules
```

the following comes up:

/lib/ufw/user.rules
/usr/share/ufw/user.rules
/usr/share/ufw/user.rules.md5sum
/usr/share/ufw/iptables/user.rules

I believe you must edit the */lib/ufw/user.rules* file. 
If you look inside (and have a current active limiting rule) you'll see the rule structure (I believe you need ...limit --limit 3/min...)

As far as *how* you must modify it, I honestly can't tell you as I haven't tinkered with this myself, it's up to you.
Test it in a Virtual Machine or non-critical hardware until you're sure you understand how it works (you don't want an accidental hole in your firewall) And when satisfied, apply it to the desired machine.

Disclaimer: I'm far from an expert and provide this tip to the best of my knowledge and with best intentions, use at your own risk.

cheers.

thats exactly what I was looking for, thanks!

---

