---
title: "broadband error in 10.04"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by mark'V' on 2010-11-06
hi
i've configured my pc using **'sudo pppoeconf'** and it worked fine, but when i rebooted my pc and tried to connect using **'pon dsl-provider'** it says **'Error: *only* members of the '*dip*' group can use this command'**.
I've added myself to the group and tried to connect but to no use.
Im able to connect in windows without any issues.
Please help me.... Thanx in advance.

---

### Post by karthick87 on 2010-11-06
Use sudo infront of your command

```
sudo pon dsl-provider
```or

add your user to the group dip and dialout

```

sudo gpasswd -a <username> dip
sudo gpasswd -a <username> dialout
```Now you can run the command without sudo..Hope it helps.!

---

