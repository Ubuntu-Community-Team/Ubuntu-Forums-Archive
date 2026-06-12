---
title: "creating a vpn connection"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by ekor on 2009-09-25
hi guys

i just started using ubuntu and i have a problem to create a vpn connection.
when i go to "configure vpn connection"
the " add " is shaded...is it an authorization problem ???????

plez help

eko

---

### Post by cgroza on 2009-09-25
Try hamachi ...you can find many tutorials on google....

---

### Post by scorp123 on 2009-09-25
> **ekor said:**
> when i go to "configure vpn connection"
the " add " is shaded... No, there are extra-modules that don't get installed by default. Only if those extra modules for NetworkManager are installed that "Add" button will become functional.

```
sudo apt-get install network-manager-openvpn network-manager-pptp network-manager-vpnc 
```

---

