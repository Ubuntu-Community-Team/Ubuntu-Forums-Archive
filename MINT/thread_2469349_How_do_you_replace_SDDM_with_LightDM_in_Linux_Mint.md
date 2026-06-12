---
title: "How do you replace SDDM with LightDM in Linux Mint?"
date: 2021-11-26
forum: MINT
---

### Post by mgnr4 on 2021-11-26
How do you replace SDDM with LightDM in Linux Mint 20.2 Cinnamon?
You are given an option when installing KDE to choose between SDDM and LightDM, however i choosed LightDM and i want to use SDDM instead. :(

Correct me if this is not understandable enough because i installed Linux yesterday.

---

### Post by coffeecat on 2021-11-26
*Thread moved to **Mint** sub-forum*

---

### Post by guiverc on 2021-11-26
```
sudo dpkg-reconfigure sddm
```

FYI: you can use `lightdm` instead of `sddm` in that command; as it'll result in the same thing - ie. you're asked to pick one of the choices again.

Note:  that's what I'd do on a Ubuntu system (*such as my own Lubuntu; I can't imagine it differs with Linux Mint; I've not used it in years*)

---

### Post by KBar on 2021-11-26
> **guiverc said:**
> ```
sudo dpkg-reconfigure sddm
```

FYI: you can use `lightdm` instead of `sddm` in that command; as it'll result in the same thing - ie. you're asked to pick one of the choices again.

Note:  that's what I'd do on a Ubuntu system (*such as my own Lubuntu; I can't imagine it differs with Linux Mint; I've not used it in years*)

A bit off-topic, just want to ask/clarify. It technically should work on any .deb-based distribution, right?

---

