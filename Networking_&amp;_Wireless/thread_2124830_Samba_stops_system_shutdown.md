---
title: "Samba stops system shutdown"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by mike acker on 2013-03-12
snce i started using Samba again I now have a system shutdown problem: system shuts down to a point but hangs with UBUNTU displayed in the center of the screen.

this is a zombie state: i have to kill it with the power switch

i think it's because it is waiting on an inactive and incomplete event, specifically: one of the windows systems probably still has a connection ...

has anyone run into this ?

---

### Post by bab1 on 2013-03-12
...sure have.  Try unmounting the Samba share and see if the system shuts down cleanly.

---

### Post by mike acker on 2013-03-12
> **bab1 said:**
> ...sure have.  Try unmounting the Samba share and see if the system shuts down cleanly.

thanks. before I try that though i want to check and be sure my daughter has completely logged off windows before she goes home.  i'll post more results here when i test this

---

