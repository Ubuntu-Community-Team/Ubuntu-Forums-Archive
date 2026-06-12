---
title: "Upgrade from alpha version"
date: 2007-10-04
forum: Mythbuntu
---

### Post by llpamies on 2007-10-04
Is possible to upgrade my last mythbuntu alpha installation to the new beta ?

---

### Post by superm1 on 2007-10-04
Yes, but you may run into a few complications.

The general process should be
```

apt-get update
apt-get dist-upgrade
```

Reboot

```
mkdir ~/.config/autostart -p
```

Open up the control centre, turn off auto login.  Hit apply.  Turn on auto login, hit apply. 

Reboot


Hopefully that *should* be it :)

---

