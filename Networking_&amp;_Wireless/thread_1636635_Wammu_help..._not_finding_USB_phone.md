---
title: "Wammu help... not finding USB phone"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by Evil-Ernie on 2010-12-03
Got a Sony Ericsson K800i which I tether by USB. I'm having trouble finding the port for the config file, I have used HWINFO and I can see my phone but on the 'Linux.sysfs_path' parameter it doesnt state which tty I am on.

Anybody have any suggestions as I would really like to be able to read my sms messages on my system while hooked up.

---

### Post by alexfish on 2010-12-03
Hi

does this help

Code:

[COLOR=Blue]dmesg | grep -e "modem" -e "tty"


[/COLOR]

---

### Post by Evil-Ernie on 2010-12-07
Just spotted your reply, I will try it tonight and let you know. :)

---

