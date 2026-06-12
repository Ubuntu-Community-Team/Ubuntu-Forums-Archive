---
title: "ubuntu thinks firewall is up, but it's not"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by ellymayh on 2013-04-06
during installation ubuntu disconnects from the internet, claims can't connect because firewall is up. computer is dual boot and windows partition connects with no problem, no firewall problem. how do I convince ubuntu that connecting is safe

---

### Post by glln0v on 2013-04-07
Hi, ellymayh,

can you run this in a Terminal and report what output it gives you:```
sudo ufw status verbose
```

---

