---
title: "Help me with multimedia support in Ubuntu 9.10..."
date: 2009-11-21
forum: Multimedia Software
---

### Post by phenomFX on 2009-11-21
Could anyone help me, guide me to install full multimedia support in Ubuntu 9.10 Karmic?

Thank you very much guys !!



          phenomFX

---

### Post by Uncle Spellbinder on 2009-11-21
This is what I did....

add this to your sources.list:

```
#### Medibuntu - http://www.medibuntu.org/ 
deb http://packages.medibuntu.org/ karmic free non-free
```

in terminal do: 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then:
```
sudo apt-get install ubuntu-restricted-extras
```

and 
```
sudo apt-get install libdvdcss2
```

---

