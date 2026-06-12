---
title: "Wired connection stop working"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by rekkoo on 2010-10-25
Ubuntu 9.10. Everything works fine until yesterday when I cannot connect to network. My lan card is Realtek PCI and is present on system (i can read mac address and all settings). In connection manager I was try to set everything manually (IP, netmask, gateway and DNS) or leave automatic - without success. I am connected to router. Anyone with experience with resolving that problem? I don't want to feed "log-hungry" people because I hope that someone who know how to resolve ubuntu lan problem can help me (not someone who will want to try). I cannot connect manually because there is no option when I click on network icon (I can just uncheck connection, but that's all). I can't even access to my router (from computer with Ubuntu, because I can access from another computer). All logs shows lan card proper. Windows XP on the same computer booted from another HDD works fine.

---

### Post by BahBah on 2010-10-25
This is not a very technical reply, but I haven't found an answer to the problem I am having either. However, a recent kernel update stopped Network Manager automatically connecting to networks for me (this happened in vanilla 10.04 and 10.10). The only way for me to get it to work is to right click Network Manager untick Enable Networking, then retick it. Then it connects just fine, although this temporary fix has to be applied most reboots. I'm hoping the next kernel update fixes this. YMMV

---

### Post by rekkoo on 2010-10-25
That's totally crazy. Yesterday I was try everything and even after many restarts lan connection don't want to work. But today, when I want to check your method, Ubuntu starts with internet connection without any problems. I suspect then, that Ubuntu is operating system for believers and maniacs, not for regular users, and works only when you don't need it. :)

---

