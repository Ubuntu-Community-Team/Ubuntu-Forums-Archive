---
title: "D-link DWL-G122 drivers"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by Mortesins93 on 2010-08-14
Hello,
I was wondering where to find the drivers for my D-link adapter. It says on the box that it has Linux support, what does that mean? I have already used it without any drivers and it works for a bit but after a week or something it doesn't work anymore (it is connected to the network but no download). What should I do? Would installing the drivers solve the problem?
Thanks in advance

---

### Post by Kerubu on 2010-08-14
Linux can handle most devices without any special drivers simply because devices have to comply with a hardware structure that is independent of anyone manufacturer. If you're connecting to your network then it's likely that your device is working. I've no experience of USB network adapters so see if this works :

ifconfig

If you know how to bring up a terminal window (applications -> Accessories -> terminal window) you can try pinging a website :

ping -c 5 [www.yahoo.com](www.yahoo.com)

---

### Post by Mortesins93 on 2010-08-15
Ok thanks i'll try that even though if i get a connection i don't need to ping any server. So now my question is why every month or so ti doesn't download a thing. I mean i have installed my xubuntu 9.10 in January or something and I got this problem twice since May. So what could the problem be? On my windows partition I don't have this problem, once it is connected to the wireless network it downloads fine. Could the problem be the network applet? I have another computer with ubuntu 8.10 with the same adapter which had this problem only once but i found out it was a problem with the internet service so I can say it never had the problem i have on my xubuntu, so can the problem be my OS? I mean could switching to ubuntu 10.04 with GNOME solve my problem?
Another question: I would like to try to put the same configurations (for example frequency, network passphrase and stuff like that) that the dlink drivers for windows automatically put to make my adapter work, how do I do that? I mean my network applet doesn't have all does configurations available to fill in, where do I find them?

---

### Post by Mortesins93 on 2010-12-24
So I installed ndiswrapper and loaded the windows drivers. For now everything has been working fine.

---

