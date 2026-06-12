---
title: "Can't enable wireless?"
date: 2010-10-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SmoothFreeze on 2010-10-10
I can't enable wireless on my maverick meerkat. Anyone have problems, or is it just me?? The "Enable Wireless" option is greyed out.

---

### Post by florus on 2010-10-10
My wireless has worked perfectly since I installed alpha3. Ditto wireless broadband dongles from Vodafone and T-mobile.

---

### Post by xircon on 2010-10-10
May not be this, but try this:
```
cat /var/lib/NetworkManager/NetworkManager.state
```

Check everything says true, if not edit the file, save and reboot.

---

### Post by SmoothFreeze on 2010-10-10
> **xircon said:**
> May not be this, but try this:
```
cat /var/lib/NetworkManager/NetworkManager.state
```

Check everything says true, if not edit the file, save and reboot.

I can open the file, but I can't edit it! Help?

---

### Post by rapiertg on 2010-10-10
If you have the option try loading another kernel. On my netbook wifi is not working with 2.6.35, but if i boot it with 2.6.32 everything is ok.

---

### Post by SmoothFreeze on 2010-10-10
> **rapiertg said:**
> If you have the option try loading another kernel. On my netbook wifi is not working with 2.6.35, but if i boot it with 2.6.32 everything is ok.

How exactly do I do that?

---

