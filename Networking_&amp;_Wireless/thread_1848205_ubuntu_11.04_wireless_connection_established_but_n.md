---
title: "ubuntu 11.04 wireless connection established but no acces to the internet"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by Janara on 2011-09-22
):PHi All,
 
Got an issue with ubuntu 11.04 on my compaq presario cq60 320SA. 
The instalation get trough but I realized that I do not have the internet.
My wired and wireless connection is working but not in the correct way.
On ifconfig my wired (eth0) connection shows instead if an IP adress a MAC adress.
My wireless connection shows that is working and that the connection is established but unable to browse the internet. My network controller is Atheros and I thing that I might miss some drivers but at the minute I'm not able to do anything becasue my wired and wireless connection are not working. Please Help
 
Yesterday when I looked on the command rfkill list it shows me that nothing is blocked everything was on "NO".

---

### Post by praseodym on 2011-09-22
Hello,

please post the following terminal outputs:

```
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
rfkill list
uname -a
sudo iwlist scan
```
You can c/p the outputs in a .txt file and upload it.

---

### Post by Janara on 2011-09-23
Guys thank you very much the internet started to run on 10.04 but my wirless light is flashing (blue and orange) could you please advise how to fix it?  Cheers for you Help

---

