---
title: "Wireless Problems"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by wheelsjr on 2013-06-19
Thanks for clicking my link I understand there are a vast amount of these sort of threads on this forum if you could just hang on with me here it would be much appreciated.
I have a Cisco wireless adapter for my XP computer, this adapter picks up wireless on my Windows partition very well, with no problems. But on my Ubuntu partition it realizes I have it plugged in but can't connect to the network. Thus far I have gone to the terminal and from reading a few other threads typed in nm-tool, and it says it's setting it up, and says the name of my wifi network. This will go on and on, and so I have no access to the internet on that partition I have left it for hours on end with no avail, if anyone could help me out it would be great.

---

### Post by praseodym on 2013-06-20
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
```

---

