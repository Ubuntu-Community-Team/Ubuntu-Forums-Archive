---
title: "Help using Ndiswrapper."
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by ken_pachi on 2009-09-01
Trying to get my wireless sorted out via Ndiswrapper. So far i've managed to downloaded it, but trying to extract it by using the tar command is a no go. I also can't seem to place it in the src directory. Also, i seem to have a problem changing users and logging as root. Anyone know an easy way to install ndiswrapper for a newb?

---

### Post by DFlame on 2009-09-01
Crack open a Terminal window and enter this:

```
sudo apt-get install ndisgtk
```

This will install the ndiswrapper tools and a GUI interface which appears as something like "Windows Drivers" under Administration or Settings.

---

### Post by ken_pachi on 2009-09-05
Oddly, my laptop (which has ubuntu on it) can connect to the internet wirelessly. I guess it must be the wireless card in my PC. Also, how come i can't switch user to root? Whenever i try, it asks me for my login and password, but when i type my log in and password, nothing happens.

---

### Post by uylug on 2009-09-05
> **ken_pachi said:**
> Oddly, my laptop (which has ubuntu on it) can connect to the internet wirelessly. I guess it must be the wireless card in my PC. Also, how come i can't switch user to root? Whenever i try, it asks me for my login and password, but when i type my log in and password, nothing happens.

You can't login graphically using root. Also, the root account is by default, disabled on Ubuntu. There are several guides on how to enable the root account but we can't give you any links or anything, as it is against the forum rules.

---

