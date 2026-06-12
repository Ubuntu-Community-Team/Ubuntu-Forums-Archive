---
title: "Can't start Amarok"
date: 2009-12-25
forum: Multimedia Software
---

### Post by eriqjaffe on 2009-12-25
...thought I'd give Amarok a whirl, as it's been a while.

```
sudo apt-get install amarok
```
seems to work fine, but when I run Amarok, I get this:

```
amarok: symbol lookup error: /usr/lib/libamaroklib.so.1: undefined symbol: _ZTIN6TagLib3MP44FileE
```
Any tips would be appreciated.

---

### Post by mc4man on 2009-12-26
Well you didn't mention what ubnutu you're running and where you got amarok (2..?)

The error is pointing to an incompatible version of libtag installed for the version of amarok you have ( probably libtag1c2a

So take a look at that

---

### Post by eriqjaffe on 2009-12-26
So I didn't...

I'm running Ubuntu 9.10, and the Amarok version is just the one from the regular repos (2.2.0-0ubuntu2).  As far as I can tell, I have the right version of libtag1c2a installed (1.6-2ubuntu2).

---

### Post by jonest1 on 2009-12-27
The only reference I found was in reference to somebody who installed a custom version of libtag.

Run 'ldd /usr/lib/libamaroklib.so.1 | grep libtag' and ensure the libtag which is being referenced is in /usr/lib.

The example I found had a custom installation in /usr/local/lib.

---

### Post by mc4man on 2009-12-27
If you upgraded from jaunty then maybe libtag-extras0 is still installed and causing an issue. ( should only have  libtag-extras1 installled

---

### Post by eriqjaffe on 2009-12-27
> **jonest1 said:**
> The only reference I found was in reference to somebody who installed a custom version of libtag.

Run 'ldd /usr/lib/libamaroklib.so.1 | grep libtag' and ensure the libtag which is being referenced is in /usr/lib.

The example I found had a custom installation in /usr/local/lib.Sure enough, that was it - I had libtag.so.1 in both /usr/lib and /usr/local/lib.  I ran 'sudo mv /usr/local/lib/libtag.so.1 /usr/local/lib/libtag1.so.1.bak' and now Amarok starts properly.  Thanks!

---

