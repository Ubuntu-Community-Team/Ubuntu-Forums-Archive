---
title: "medibuntu problems"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Payteer on 2008-05-07
Just got this while updating anyone know why?

[http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by bapoumba on 2008-05-07
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add
```
should fix your problems :)

---

### Post by Payteer on 2008-05-07
This is what I get.
gpg: can't open `': No such file or directory

---

### Post by bapoumba on 2008-05-07
I'm sorry, there is a typo, a **-** missing at the end:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

:redface:

---

### Post by Payteer on 2008-05-21
Thanks, that worked.

---

### Post by Nopposan on 2008-08-12
Thanks, folks, but it didn't work for me.  I get:
```
gpg: no valid OpenPGP data found
```

Any ideas as to why?

---

