---
title: "Wireless connection lost - login fails despite all being correct - auth problem?"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by Harvey_Partridge on 2013-08-24
Thanks to a small child in the house, I have lost my wireless connection of long standing - since installation of ubuntu!
Same router still works with other computers. Same problem with other routers.

These messages appear in french ...

Authentification necessary for wireless network
Passwords or key codes are necessary for access to the wireless network "my-livebox"

Key:                       MILLIONSOFCONCEALEDHEXCODECHARACTERS
                     ¤ show the key
                                      cancel connect



pressing connect results in several minutes of unsuccessful connecting!! Repeat ...
pressing cancel results in several minutes of doing nothing! Repeat ...

I am running ubuntu 12.04 LTS on an ancient Fujitsu/Siemens Amilo

I strongly suspect that my user account is not authorised to authorise an internet connection, in the same way that when I try to edit files on my usb flash drives I fail due to lack of authority - I get around this with term and sudo cp

If there isn't a fix, is there a similar workaround?

I have separated my account from root account so that there are now two passwords to remember, but root is not allowed to open a session in gnome. So how do you sudo in gnome? Or better, how do you authorise users to access wifi and usb ports?

Harvey

---

### Post by Harvey_Partridge on 2013-08-26
Is there a more suitable forum for this query?

---

### Post by steeldriver on 2013-08-26
The kind of behavior you're describing (if I'm reading it correctly) is more typical of a wireless driver problem. If it was a matter of your user account permissions, then you would usually see a message to that effect (something like 'System policy prevents modification yada yada'). Wireless access point authentication problems (i.e. wrong wireless password) usually result in an error message as well. To help us diagnose please collect the following information from a terminal:

```

lspci -vnn | grep -e '\[0200\]' -e '\[0280\]'

sudo lshw -C network

ifconfig

```

You could also look for wireless-related messages in the dmesg log - assuming your wireless interface is called 'wlan0' (the ifconfig command above should tell you)

```
dmesg | grep wlan0
```

---

