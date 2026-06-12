---
title: "Wired connection not working, tried everything"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by Golzy on 2011-08-23
I recently installed 11.04 on my PC (was running 9.04), and beforehand "tried it out" and networking was fine. I could access the internet no problem.

I then ran the install, and fully formatted my HDD (i have 1 HDD for the OS and another for storage)

It crashed halfway thorough, so no problem, i just re-formatted the hardrive and installed.

However, It didnt connect to the internet, I literally tried every single forum looking for the solution, including editing the Network interface file.

After a bit of digging I found my user privileges did not allow me to connect to ethernet, and randomly use audio devices.

SO, no problem I checked the boxes, but it still wont connect to the ethernet now, and it was fine before, tried re-installing twice with full format, but still doesnt work.

Help would be greatly appreciated as I cannot do anything without it, posting this from work.

---

### Post by lmarmisa on 2011-08-23
Hi Golzy,

Welcome to the Ubuntu Forums. :-D

Are you able to connect to the internet if you boot into an Ubuntu 11.04 (or 10.10) Live CD / USB?. Select the option Try Ubuntu.

---

### Post by Golzy on 2011-08-23
No, not since the first time, I checked the privileges when i "tried" it again, and the internet connection boxes were unchecked, so i checked them, disabled networking in applet, and re-enable, but still nothing.

---

### Post by lmarmisa on 2011-08-23
> **Golzy said:**
> No, not since the first time, I checked the privileges when i "tried" it again, and the internet connection boxes were unchecked, so i checked them, disabled networking in applet, and re-enable, but still nothing.

I do not know if I understand you.

An Ubuntu Live CD has no persistence. So, that means that, when you boot into it, you get an standard initial configuration. In the case of the Ethernet interface, an automatic DHCP configuration is supposed that exists in your LAN. This standard configuration works fine with many routers and modems (95% or even more).

I understand that when you tried an Ubuntu 11.04 Live CD for the first time, you did not detect any problems in relation with your network and therefore you decided to do a fresh install of Ubuntu 11.04.

But, you have checked that, after each new installation, you are not able to connect to the internet.

Is this summary correct?.

Best regards,

Luis

---

### Post by praseodym on 2011-08-23
Can you post the following terminal outputs:

```
uname -a
lspci -nnk | grep -iA2 net
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
lsmod
```
How do you want to connect? Router plus modem or only with modem?

---

### Post by Golzy on 2011-08-23
Sorry, I should have written better English.

Yes I have tried again using the try Ubuntu option booting from the CD. However, I get the same problem as when I do a fresh install.

Even on the Try Ubuntu option it doesnt have all the Admin user privileges.

---

### Post by Golzy on 2011-08-23
> **praseodym said:**
> Can you post the following terminal outputs:

```
uname -a
lspci -nnk | grep -iA2 net
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
lsmod
```How do you want to connect? Router plus modem or only with modem?

I will post in 3 hours when I am on my lunch from work. 

I have an ethernet card (cant recall which one), and through a router. I tried it again this morning with no other connections, including wireless devices.

---

### Post by lmarmisa on 2011-08-23
> **Golzy said:**
> Sorry, I should have written better English.

Yes I have tried again using the try Ubuntu option booting from the CD. However, I get the same problem as when I do a fresh install.

Even on the Try Ubuntu option it doesnt have all the Admin user privileges.

Your English is perfect. On the contrary, my English is really awful, but I am too old to improve it. :-(

I would recommend to type two more commands to those proposed by praseodym. Please, post the results of:

```

nm-tool
ping -c4 8.8.4.4

```

---

### Post by Golzy on 2011-08-23
Will post as soon as I get home, might take a while though!

---

### Post by lmarmisa on 2011-08-23
If you download the ISO image file of a previous version of Ubuntu and burn a CD with it, you will be able to check if your network problems are present in that version.

This link is a repository of Ubuntu 10.10:

[http://www.mirrorservice.org/sites/releases.ubuntu.com/10.10/](http://www.mirrorservice.org/sites/releases.ubuntu.com/10.10/)

I recommend to download the file **ubuntu-10.10-desktop-i386.iso**.

If you prefer Ubuntu 10.04 LTS, use this link:

[http://www.mirrorservice.org/sites/releases.ubuntu.com/10.04.3/](http://www.mirrorservice.org/sites/releases.ubuntu.com/10.04.3/)

The file to download would be **ubuntu-10.04.3-desktop-i386.iso**.

I recommend to boot into a Ubuntu Live CD of one of these previous versions and then check if you have connection to the internet.

---

### Post by Tortu16 on 2012-07-04
I have the same problem but in HP pavilion g6 (AMD version) and Ubuntu 12.04 LTS. Ethernet and wireless both work when booting from live CD, but from HD installed Ubuntu. Please help.

---

### Post by wildmanne39 on 2012-07-05
Hi, this is an old thread so it has been closed, please start a new one.
Thanks

---

