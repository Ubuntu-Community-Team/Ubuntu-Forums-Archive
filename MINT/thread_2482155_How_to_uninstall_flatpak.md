---
title: "How to uninstall flatpak"
date: 2022-12-21
forum: MINT
---

### Post by f23948 on 2022-12-21
I don't use Software Manager very often, is that looks safe to uninstall flatpak in terminal? I am using Linux Mint Cinnamon edition 21.1

```
sudo apt-get remove --autoremove flatpak
sudo apt-get purge flatpak
```

---

### Post by Tadaen_Sylvermane on 2022-12-21
I think Mint avoids snap and flatpak in general. I'd run a ```
flatpack list
``` to see what if any you have to replace with non flatpak alternatives before dumping it though.

*EDIT*

You can run those apt-get in one shot with just apt.

```
apt --purge autoremove flatpak
```

---

