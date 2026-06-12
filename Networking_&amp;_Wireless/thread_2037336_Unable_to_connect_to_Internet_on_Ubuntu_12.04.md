---
title: "Unable to connect to Internet on Ubuntu 12.04"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by kifetew on 2012-08-04
Hello,

I have ubuntu 12.04 running on a toshiba satellite laptop and all was fine until (I don't know what I did or installed which updates) all of a sudden I cannot connect to the Internet (either via wired or wireless means). I am able to connect to the adsl modem both via wired and wireless (and change settings). I have also tried to use an external USB wireless key but still no Internet.

I have a windows 7 system (dual-boot) on the same machine and it works just fine.

Does anyone have any idea as to what might be the problem.
Thanks

---

### Post by praseodym on 2012-08-04
Uninstall the package "resolvconf", and reboot.

Check:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Finnicella on 2012-08-04
Did you turn off the wireless switch on windows?
If you did it, go in windows and turn on the switch.
Sorry for my english. :)

---

### Post by ranger1021994 on 2012-08-04
You can try this :
1) Go to network manager
2) Click on Wired or Wireless
3) Select your connection
4) Go to IPv4 settings
5) If your method is Automatic(DHCP) then Change it to Manual and enter information or do the vice versa (ie. change manual to automatic)

PS:Manual settings can be obtained from your ISP

---

### Post by kifetew on 2012-08-05
hi all,

thanks for all the responses! It turns out that the problem was related to DNS resolution. In the /etc/resove.conf file there were entries describing the name information of the network I use at the office. I changed the settings to that of my home router and I was able to access the Internet. However, I don't know why that happened and whether I will need to change it back when I'm in the office. 
May be I'll try the solution proposed by praseodym to remove resovconf and see what happens.

Thanks again!

---

