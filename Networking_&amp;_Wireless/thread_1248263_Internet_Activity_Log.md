---
title: "Internet Activity Log"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by hackerseraph on 2009-08-24
Is there any application that can let me log all internet activity incoming and outgoing? I googled around and came up with nothing >_>
Thanks

---

### Post by PeEllAvaj on 2009-08-24
Are you looking for something like wireshark (sudo apt-get install wireshark) that has can capture all of the packets into and out of your machine? Or are you looking for something more specific?

---

### Post by aesis05401 on 2009-08-24
You can log by implementing a firewall logging rule.  The very powerful and customizable iptables firewall is included in your install.  

You can get an idea about your options by reading a brief tutorial on iptables, and here is a pretty concise how-to written by one of the mods of this board:_[http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")._

 Does this help?

---

### Post by hackerseraph on 2009-08-24
> **PeEllAvaj said:**
> Are you looking for something like wireshark (sudo apt-get install wireshark) that has can capture all of the packets into and out of your machine? Or are you looking for something more specific?

This is pretty much what I was looking for. I wanted to log internet addresses my computer goes out to, i was looking for it to say things like google.com, mail.yahoo.com for a project Im doing in class so me and a large bunch of my buddies are gonna collect raw data and see what we browse over a 2 week period :]

---

