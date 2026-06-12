---
title: "STA driver not in use"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by eng.reem on 2010-01-26
hey i had a suffer installing broadcom b43 or the brodcom STA driver
i ended with STA in Hardware drivers i installed it and it's activated but not in use
and i still have no wireless connection 
i'm on ubuntu 9.10 

any help plz ?

---

### Post by bkratz on 2010-01-26
> **eng.reem said:**
> hey i had a suffer installing broadcom b43 or the brodcom STA driver
i ended with STA in Hardware drivers i installed it and it's activated but not in use
and i still have no wireless connection 
i'm on ubuntu 9.10 

any help plz ?

Could you go to the terminal ( Applications>>Accessories>>Terminal) and type in:

lspci  (that is LSPCI in lowercase)
and
sudo lshw -C network   (LSHW in lowercase)
and  copy paste the outputs back here

(Note the sudo command will require your password which will not be echoed, not even **, to the screen. Just press enter when put in.

---

