---
title: "No network connection after system update"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by mpilting on 2012-02-18
I have a Toshiba Satellite a215 laptop with an Atheros AR5001 wifi adapter. On it is a clean install of xubuntu 10.04. The wireless card worked perfectly immediately after installing xubuntu. I updated the system using Update Manager, restarted the computer, and now the computer can't connect to the network. Mousing over the network icon shows "No network connection". Left-clicking on it shows both Wired Network and Wireless Networks are disconnected and grayed-out. Right-clicking on network icon shows both Enable Networking and Enable Wireless are checked. lspci in terminal window shows my wireless card is still there.

I opened the file "NetworkManager.state" in var/lib/NetworkManager and it shows everything is set to true.

The reason I put xubuntu on this computer is because I had the exact same problem in ubuntu 10.04. I'd been using ubuntu for weeks, then updated it a few days ago and lost the network connection upon restarting the machine. It appears both ubuntu and xubuntu suddenly have the same issue. 

My theory is that one of the recent updates made to ubuntu/xubuntu has caused the problem. That would make sense, considering I'd been running ubuntu for weeks with no problems and upon the most most recent update, lost the connection. This same thing happened with xubuntu just today.

Anyone have any ideas?

---

### Post by cpk011 on 2012-04-26
I experienced the same problem. I installed Ubuntu 10.04 and the wired network worked fine. Like you, I I updated the system using Update Manager and then I had no more wired connection. 
 
Is there a way to roll back the update?

---

