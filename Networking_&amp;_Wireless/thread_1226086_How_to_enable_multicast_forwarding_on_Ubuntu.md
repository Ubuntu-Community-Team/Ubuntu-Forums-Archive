---
title: "How to enable multicast forwarding on Ubuntu"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by johnseamus on 2009-07-29
hi, ive tried many ways to enable multicast forwarding bt it still wun work..can some guru here giv me some advice on how to do it? it seems dat i cant change the mc_forwarding file in the sys.net.ipv4.conf.all dir since its read-onli...any suggestions? thanks

---

### Post by NoReflex on 2009-07-29
I don't know how to enable multicast forwarding but if you say you must edit mc_forwarding and it's read-only you should probably edit it as root.
```
sudo nano filename
```

Best wishes,
NoReflex

---

### Post by burkas on 2009-07-29
gksudo gedit if you want to open it in gnome ;)

---

### Post by johnseamus on 2009-07-29
nope it doesnt work, the file is read onli bt my kernel already has multicast enable i just wanna change this file's value frm 0 to 1...

---

### Post by NoReflex on 2009-07-30
Go to the file location and type ls -la to find out ownership information and file permissions of mc_forwarding.

NoReflex

---

