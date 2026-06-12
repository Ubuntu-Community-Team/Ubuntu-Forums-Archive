---
title: "dsl problem"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by saravanaspeed on 2009-06-23
:(i had a dsl connection working properly.Then on reading a book
i downloaded and installed firestarter.I run the wizard .At last it said no active connection.Now i cant connect using dsl.I removed fire stater .Still i cant connect.
         urgent

---

### Post by puppywhacker on 2009-06-23
firestarter is a GUI for iptables. you can flush the rules like this
```
sudo iptables -F
```

with -L you can list the rules that are still present
```
iptables -L 
```

---

