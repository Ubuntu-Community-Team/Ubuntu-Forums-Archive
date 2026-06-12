---
title: "Spend 8hrs so far - Network UNCLAIMED - Ralink 2500"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by rationalthinker1 on 2011-06-06
Hello, I've spend about 8hrs trying to solve this, by looking at other thread and googling it. And I am about to give up on Ubuntu because any OS is useless without internet.

How do I 'claim' this network? Please note that I have no internet on this machine but have a labtop with Win7 to transfer files.


Thank You.

---

### Post by Joe of loath on 2011-06-06
I don't understand what you mean by 'network unclaimed'. Do you mean it won't connect?

---

### Post by rationalthinker1 on 2011-06-06
Sorry, when I put this in terminal: "lshw -c network" my Ralink 2500 is stated as unclaimed.

lshw -C network
returned

*-network UNCLAIMED

---

### Post by chili555 on 2011-06-06
FYI, 'Unclaimed' means no driver has associated with it and created a useful interface that can connect. Let's figure out what driver it wants. Please post the part here that relates to your Ralink wireless:```
lspci -nn
```

---

### Post by rationalthinker1 on 2011-06-08
Okay, I finally solved it. Another 8hr put into it. I simply reinstalled Ubuntu.

How to work Rt2500
- in windows, go to device manager and look up the .sys file that that device uses. ex. rt2500.sys. Search rt2500.* in Windows and save it into a USB.
- In Ubuntu, install Wireless driver installer and ndiswrapper.
- in Ubuntu, go to terminal and type in lshw -c network and see what driver it uses. ex. rt2500pci
- go to /etc/modprobe.d/blacklist.conf and add "blacklist rt2500pci" and save.
- add rt2500 driver with the program above.
- restart

---

