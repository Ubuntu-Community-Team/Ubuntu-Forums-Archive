---
title: "one local machine unreachable"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by okhowaboutthisusername on 2010-09-02
running 10.4

I have a Mac OS X laptop that I cannot connect to (ping, ssh, etc.) from my Ubuntu box. Another local Mac can be communicated with just fine. Oddly, I can ping the Ubuntu box from the laptop.

/etc/hosts on Ubuntu has the Mac as:
192.168.1.5 poseidon

On poseidon, the Network panel also shows 192.168.1.5

Although I doubted it would make a difference, I made sure to try booting the laptop first. As expected, there was no difference.

Can anyone suggest a reason this is happening? Or things to try?

---

### Post by BkkBonanza on 2010-09-02
Sounds offhand like firewalling issues. Make sure any firewall on that MAC laptop is disabled before testing. Being able to ping out but not in is typical when a firewall is blocking inbound traffic.

---

### Post by okhowaboutthisusername on 2010-09-03
Sorry, I should have mentioned that the firewall on the Mac was disabled. I also didn't have the "Remote Login" service enabled and so just tried that and now can ssh to the laptop. I still can't ping it but that's not so important. I would like to figure out what the issue is, though.

---

### Post by Iowan on 2010-09-03
Pinging by name or IP (or both?)

---

