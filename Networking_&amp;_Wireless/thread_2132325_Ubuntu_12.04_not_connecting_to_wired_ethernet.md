---
title: "Ubuntu 12.04 not connecting to wired ethernet"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by n3m35i5 on 2013-04-04
[COLOR=#333333][FONT=Ubuntu]I just installed Ubuntu 12.04.02 alongside my Vista (didn't use wubi). On booting up, I configured my wired internet connection. It doesn't use DHCP, and uses a static private IP (given by my ISP) which by the use of NAT is assigned a public IP. I have entered all information like gateway, mask and DNS. Now when I startup Firefox and login to my ISP's router to connect, the internet speed is greatly reduced. My plan is for 256kbps and I get <10kBps. Also, the software center though doesn't show any error, doesn't update or install anything...Please help.[/FONT][/COLOR]

---

### Post by gordintoronto on 2013-04-04
Am I correct that you have a modem, but no router? If so, NAT doesn't enter into the equation.

---

### Post by Iowan on 2013-04-04
At one time (might still be the case) IPv6 could cause slowdowns. 
Tweaking MTU also sometimes helped.
(Getting old and rusty.)

---

### Post by n3m35i5 on 2013-04-05
> **gordintoronto said:**
> Am I correct that you have a modem, but no router? If so, NAT doesn't enter into the equation.
Actually, my ISP just provides a cable to my home, nothing else on my end. Since, my windows installation can access the net pretty well, so I am sure the problem lies with my Ubuntu config. And about the NAT, my ISP gave me a static private IP which gets translated to a public IP when I'm visiting the outside net, so I figured out there must be a NAT at their end.

---

### Post by gordintoronto on 2013-04-06
I think we need a lot more details in order to help you. Actual IP addresses, details of how and what you specified to set up the network connection.

I think you are saying the ISP runs Ethernet into your house. I have never heard of that type of setup. Also, your plan seems very slow.

---

### Post by n3m35i5 on 2013-04-11
> **gordintoronto said:**
> I think we need a lot more details in order to help you. Actual IP addresses, details of how and what you specified to set up the network connection.

I think you are saying the ISP runs Ethernet into your house. I have never heard of that type of setup. Also, your plan seems very slow.

Well, all the details you need are here:
[https://answers.launchpad.net/ubuntu/+question/225883](https://answers.launchpad.net/ubuntu/+question/225883)

---

