---
title: "intel 4965 agn wireless card not loaded"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2009-08-31
[INDENT][INDENT]I just installed a command line version of ubuntu jaunty on my laptop, which has an intel 4965 wireless agn card. Now, I don't know how to get the card to work. Under the desktop version of ubuntu, the card works out of the box, but with the command line only version, I guess the right module hasn't been loaded. How/where can I find the driver/module for this? In the desktop version, ndiswrapper wasn't even loaded at all in my system, so I know I don't need that for the card to function, but I don't have any other ideas. Thanks!
[/INDENT][/INDENT]

---

### Post by uylug on 2009-08-31
Check if your card is ready to be used:

```
ifconfig
```

```
iwconfig
```

If your interface is detected, check if you can see any wireless networks:

```
sudo iwlist scan


```

---

### Post by pythonscript on 2009-09-05
The card was working. For some reason, it didn't load on the first boot after install, but after I rebooted once, it's been working flawlessly. I installed wicd and never looked back. Thanks for the help!

---

