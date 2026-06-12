---
title: "Network disconnected problem"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Foxfan100 on 2009-04-14
I have a Dell running XP and Ubuntu 8.10, which connects to the web via an Intel PRO/100 VE network adapter and then to a belkin N1 router in ethernet wired mode. It all works fine in XP, but when I reboot to Ubuntu, I get a "Network disconnected" message from time to time i.e. it works randomly, about 50/50. When I have the disconnected message, the status lights on the router are what they should be when connected. There are no hardware problems.
What I would like to know is how to reconnect the network in Ubuntu through software i.e. what commands or utilities are there which allow me to do this? Put even more simply, when I click on the network icon and it tells me "Network Disconnected", what do I do then?

---

### Post by chili555 on 2009-04-14
Please open a terminal and do:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig eth0 up
sudo dhclient eth0
```Did you connect? Do you stay connected?

Is this a desktop machine that never goes down to the cyber cafe? If so, I doubt you need Network Manager to manage your connection and to select from multiple available networks.

---

### Post by Foxfan100 on 2009-04-15
Thanks. Haven't tried it yet as working OK but will do and report back. You are correct that this is a go-nowhere desktop, so a range of network access options probably isn't needed.

---

### Post by Foxfan100 on 2009-04-15
Just tried it after restarting from XP with a good connection. Network Manager icon has red cross as if Disconnected but message is "Networking Disabled". Internet connection still up and running.

---

### Post by chili555 on 2009-04-15
That's good news. If your connection continues with no disconnects, let's make manual configuration, needed one time only, permanent and kick Network Mangler out for good.

---

### Post by Foxfan100 on 2009-09-13
> **chili555 said:**
> That's good news. If your connection continues with no disconnects, let's make manual configuration, needed one time only, permanent and kick Network Mangler out for good.

I still keep getting this problem sporadically, and it's a real nuisance.

My machine is set up to default GRUB boot to XP (for my own reasons) and I can restart, boot into Ubuntu and maintain my network connections via the Belkin N1 router used as a wired connection, perhaps 80% of the time.

Other times I boot to Ubuntu from XP and lose my connection, although the router lights tell me that it's OK.

Then  again, I can start my machine from new, boot to Ubuntu and get a connection. This time it's about 20%, with 80% failure.

I've tried disabling Network Manager from the startup apps, but this doesn't seem to make any difference. 

The irony is that because of this I'm trying solve a Linux problem via Ubuntu Forums, which I have to post to via XP because I lack a network connection under Linux! Crazy.

---

