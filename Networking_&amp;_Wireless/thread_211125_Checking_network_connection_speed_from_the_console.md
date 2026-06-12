---
title: "Checking network connection speed from the console"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by wykd on 2006-07-07
I recently installed a Realtek RTL8169-based PCI Gigabit networking card into my server, which is running Ubuntu 6.06 Server Edition. 

The card appears to have been configured fine with the drivers built into Ubuntu, but I do not know how to tell if it is actually getting 1000Mbit/s speeds from the console. The last gigabit card I used with Ubuntu only run at 100Mbit, so I am concerned about this one. 

Thanks for the help!

---

### Post by Dr. Nick on 2006-07-07
Try this from the terminal

```
 sudo mii-tool
``` 
Also remember to get a 1000Mbit speed you need a 1000Mbit hub/router/switch I do believe. If you have a 100Mbit switch you wont run at 1000

---

