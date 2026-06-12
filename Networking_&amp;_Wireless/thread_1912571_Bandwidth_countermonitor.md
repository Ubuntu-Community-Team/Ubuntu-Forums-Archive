---
title: "Bandwidth counter/monitor?"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by wujj123456 on 2012-01-20
Is it possible to retrieve the "Total received" or "Total sent" numbers from the gnome-system-monitor from command line? Or are there other tools/packages that can record and output the total data usage?

The motivation is that I want to monitor my bandwidth usage every hour or so. If I have some command line tool to access this information, I can write a script to save the numbers and collapse the data. 

Since gnome-system-monitor is already monitoring this, I'd prefer not to use additional daemons just for this purpose. (I saw Network Tools providing the same data. So I guess the such daemon already exists and probably I only need to find out the command to access the data I want. )

---

### Post by wujj123456 on 2012-01-20
OK. I was so dumb. Solved. How did I forget the most obvious solution: ifconfig. 

For data received:
ifconfig eth0 | grep "RX bytes" | awk '{print $2}' | awk -F':' '{print $2}'
For data sent:
ifconfig eth0 | grep "RX bytes" | awk '{print $6}' | awk -F':' '{print $2}'

---

