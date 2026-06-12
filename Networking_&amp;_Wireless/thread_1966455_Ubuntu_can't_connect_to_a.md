---
title: "Ubuntu can't connect to a"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by NomadBal on 2012-04-27
Hi,
I recently installed Ubuntu on my laptop with wubi.
I can't connect to my wireless network, it find the modem but when i type the password he can't connect and suggests me to retype that.
I checked many times, and the password is right, so i don't know what it will be.
I hope to find help here, thanks!

Sorry for my bad english, i'm bad at typing :/

---

### Post by wildmanne39 on 2012-04-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

