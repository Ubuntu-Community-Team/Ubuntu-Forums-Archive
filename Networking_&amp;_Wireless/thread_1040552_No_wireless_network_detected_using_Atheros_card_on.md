---
title: "No wireless network detected using Atheros card on Acer Aspire 5050 laptop."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Absinthe Minded on 2009-01-15
Hello all,

I've got a new install of Hardy 8.04 on my lappy. wicd is installed but cannot find my wireless network. Router is set to broadcast address, and my other lappy (running Vista), connects fine.

Hardware drivers lists ATI driver and the two more:
Atheros Hardware Access Layer (HAL)
and
Support for Atheros 802.11 wireless LAN cards.

All are enabled.

I've tried this with two different wireless networks and it picks up neither of them.

I must be missing something and would appreciate some help!

Thanks,
Nick.

---

### Post by Absinthe Minded on 2009-01-16
OK, so I just made a clean install of 8.10 to see if that would fix it - but nothing!

Any ideas, please?

---

### Post by Absinthe Minded on 2009-02-06
OK, I fixed it by myself, with the help from [this page]("http://ubuntuforums.org/showthread.php?t=798485").

Here's the code I used in case you're too impatient to read the above page:

```
wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
```

```
sudo ./madwifi.sh
```

---

