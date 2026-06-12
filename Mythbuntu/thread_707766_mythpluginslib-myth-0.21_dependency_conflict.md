---
title: "mythplugins/lib-myth-0.21 dependency conflict"
date: 2008-02-25
forum: Mythbuntu
---

### Post by SuperDodge on 2008-02-25
I am trying to make a new master backend/frontend combo system.  I need the input groups feature so I am attempting to install 0.21 using the weekly autobuilds.

When I attempt to install lib-myth-0.21 it requires libfaad0 as a dependency.  When I attempt to install mythplugins it requires libfaad2-0 as a dependency.

Apparently I cannot have both libfaad0 and libfaad2-0 installed at the same time.  These are both the same revision number from the same mythbuntu repository.

What gives? Do mythbuntu's own weekly builds actually conflict with one another?

---

### Post by superm1 on 2008-02-26
This will be fixed in the next day or two.  It only affects amd64.

---

### Post by SuperDodge on 2008-02-26
> **superm1 said:**
> This will be fixed in the next day or two.  It only affects amd64.

Thanks Mario.  I can certainly go a couple of days without my plugins I just wanted to make sure someone was aware of this and it wasn't just a stupid newb (me) screwing stuff up...

---

### Post by wombo on 2008-02-27
I did a 'apt-get dist-upgrade' and then it allowed me to continue

---

### Post by SuperDodge on 2008-02-27
Thanks for the tip but I don't think it will work for me as this is a fresh install of ubuntu and mythtv.  If I am incorrect in that assumption please let me know.

---

### Post by superm1 on 2008-02-27
Plugins are fixed now, and you should be able to.

---

### Post by SuperDodge on 2008-02-28
it worked just fine.  Thanks!

---

