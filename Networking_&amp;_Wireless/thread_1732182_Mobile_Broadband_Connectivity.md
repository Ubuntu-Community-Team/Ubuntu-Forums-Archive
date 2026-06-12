---
title: "Mobile Broadband Connectivity"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by pcsel on 2011-04-17
Hi all,

I have a problem similar to this thread:

[http://ubuntuforums.org/showthread.php?t=1714540&highlight=mobile+broadband]("http://ubuntuforums.org/showthread.php?t=1714540&highlight=mobile+broadband") 

Same device and same service provider.(ZTE K3570-Z on Vodafone)  Running 10.04 Dream Studio. I get pretty much the same responses to the previous thread.. My connection has never worked however. If I click on the Network Applet I can see the "Vodafone UK UMTS" Connection there and it also says available, however it is greyed out and cannot be selected and I can see a signal on it.

If I create a connection.. say for GSM or UMTS then the greyed out connection (the one created automatically also changes to GSM or UMTS) but is still greyed out. The new connection just comes up with the pop up "GSM Disconnected" when I click it.

Anyone any ideas please.

Thanks

Paul

---

### Post by pcsel on 2011-04-18
Anyone???:)

---

### Post by chinmaya_n on 2011-06-25
same problem here....
[http://ubuntuforums.org/showthread.php?t=1789426&highlight=K3570-Z](http://ubuntuforums.org/showthread.php?t=1789426&highlight=K3570-Z)

---

### Post by jamadagni on 2011-06-25
Disconnect your mobile broadband device and reconnect it and immediately go to terminal and do the following commands **dmesg | tail** and **tail /var/log/syslog**.

---

