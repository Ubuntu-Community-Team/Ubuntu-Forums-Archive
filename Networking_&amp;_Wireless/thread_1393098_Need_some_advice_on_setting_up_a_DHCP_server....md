---
title: "Need some advice on setting up a DHCP server..."
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Theoutdoorsman on 2010-01-28
I'm considering setting up a DHCP server for home use. But before I attempt this, I'm wandering if it will benefit the throughput of my home network (assuming the server will cache frequently visited web pages). The only equipment that I have on hand is my access point, a wireless router, and three client computers, with another pc I'd like to use as a server. Is it possible to do this without a static ip address from my isp, and the equipment I have? Before anyone asks, "Why all the trouble?", I just want to gain some experience and familiarize myself with networking. At the same time, I want to get the most out of my home network by limiting the bandwidth on two of the client pc's and allocating more for use with my office computer. This is just a brainstorm at the moment. If it would be worth the time and effort spent, I'd make it happen. I'm open for any suggestions. Go easy on me..... ;)

---

### Post by rogue_0111 on 2010-01-28
Sure use something like [dyndns]("http://www.dyndns.com/"). And these links should get you going:

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_192.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_192.html)


Be patient
--

---

### Post by Iowan on 2010-01-28
Check [DNSMasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html") - it's in the repo's.

---

### Post by Theoutdoorsman on 2010-01-29
Looks like I have some reading to do.... thanks for the links!!!

A few more question, If I may.....

Prior to setting this up, let me make sure I understand how the topology should look. The server is to be connected to the Access Point (incoming high speed service with an RJ-45 connector in my case). Then, to the server who will need an additional NIC installed from which to listen on. The wireless router will be connected to this "added NIC". 

This is correct.....?

Many thanks for your help with this!!!

---

### Post by Theoutdoorsman on 2010-01-29
< bump >

---

### Post by Iowan on 2010-01-29
I'm still a wireless rookie - but what you describe *seems* right. The router will probably need some configuration to pass along requests - or it could probably be set up as a DHCP server.

---

### Post by rogue_0111 on 2010-01-29
> **Theoutdoorsman said:**
> Looks like I have some reading to do.... thanks for the links!!!

A few more question, If I may.....

Prior to setting this up, let me make sure I understand how the topology should look.

Many thanks for your help with this!!!

[SIZE=4][B]
What it should look like.[/B][/SIZE]

[IMG]http://images.howtoforge.com/images/screenshots/556af08d5e43aa768260f9e589dc547f-3024.jpg[/IMG]

---

### Post by Theoutdoorsman on 2010-01-31
Well....... I'm not having any luck, at all, setting this up. The network topology was adjusted as mentioned above. Too, I followed the second link in message #2 above, to the "letter". I have access to the internet via my DHCP server, but can't connect either of my client computers to the router. Basically, I have a server connected to the access point, and a wireless router connected to the second NIC that was installed in the server. (Putting the server in place was the only change I've made to my network.) Can anyone assist with this problem? Your help would be most appreciated. Here's a few quick notes:


1) I received the word (fail) during the installation of "dhcp server". However, I'm 
    really not sure at what point this was displayed.

2) I am using the Live CD, Ubuntu 9.04. 



Let me know what additional information you'd like and I will get it for you. Please inform me of any information that might need to be "hidden" on this public forum, such as MAC addresses and so forth. I'm nowhere near as savy as some. Not that I have anything worth seeing or stealing, but I would certainly feel better knowing I haven't invited trouble.... :-) ..... Thanks in advance for any and all help with this.

---

### Post by Iowan on 2010-01-31
I haven't used the Live CD often, but I'm not sure how you'd save configuration settings, etc. The DHCP server will fail if there's a configuration problem. A likely source is not having the (serving) interface addressed in the subnet.

---

### Post by Theoutdoorsman on 2010-01-31
If I log out and back on, won't that suffice?

---

### Post by theozzlives on 2010-01-31
Any respectable router will act as a DHCP server.

---

### Post by Theoutdoorsman on 2010-01-31
Theozzlives..... The purpose of including the DHCP server, in my configuration, is to simply cache url's visited so as to speed up my existing internet service and help reduce the overall use of bandwidth. It is shared with 2 client pc's who's users tend to utilize a lot of my bandwidth. I'd like to limit the percentage of bandwidth that is allocated to these two machines, and also learn a little bit along the way about networking. This is more of a learning experience than anything. I have a laptop that I'd like to connect later, but I'll work on that after I get the network up. If I can get it up. Right now, I'm not having any luck with it. If anyone can help, I'd sure appreciate it. Thanks.

---

