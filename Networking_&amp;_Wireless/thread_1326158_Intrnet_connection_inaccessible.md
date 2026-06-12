---
title: "Intrnet connection inaccessible"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Techieskull on 2009-11-14
[SIZE=3][COLOR=black]I'm a new user of Ubuntu. I requested the Ubuntu 9.10 cd online and got it in around 3 weeks. I've chosen the 'Install over windows' option for my use right now. The version of windows being 'Windows 7'. The problem is that I'm unable to connect to the internet. I'm using LAN cord to connect to my modem. The 'Network Manager' tht the user manual talks about, is not to be found yet. When I click on the 'Network' icon on the top right portion of the panel, it shows that 'autoeth0' is connected but when I open firefox and try to open any website, the 'Server not found' comes up on the firefox window. Thus I'm not able to surf the web.[/COLOR][/SIZE]
[SIZE=3]Please suggest me something to solve this.[/SIZE]

---

### Post by Techieskull on 2009-11-14
Please help me out !!!!!!!!!!

---

### Post by viralmeme on 2009-11-14
> **Techieskull said:**
> [SIZE=3][COLOR=black].. I've chosen the 'Install over windows' option for my use right now. The versin of windows being 'Windows 7'. The problem is that I'm unable to connect to the internet. ..[/COLOR][/SIZE][SIZE=3][/SIZE]
There's you problem, why not do a standard dual boot option ? [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by Techieskull on 2009-11-14
I'm using the standard dual boot option, i suppose. When I start the system, it gives the option to boot Windows or Ubuntu at boot time only.

---

### Post by Iowan on 2009-11-14
> **Techieskull said:**
> The [COLOR="Red"]'Network Manager'[/COLOR] tht the user manual talks about, is not to be found yet. When I click on the [COLOR="Red"]'Network'[/COLOR] icon on the top right portion of the panel,
You found it... From a terminal, check **ifconfig -a** to verify the interface (*probably* eth0) has an IP address. Next, check contents of */etc/resolv.conf* to see if nameservers are listed.

---

### Post by Techieskull on 2009-11-14
I acted upon both of your advices. The ip address is also there and the nameservers are also listed in the file you mentioned. but still the problem remains unsolved.

---

### Post by RedSingularity on 2009-11-14
Try pining a well know site such as google.  Try this in terminal.........

ping -c 5 [www.google.com](www.google.com)

---

### Post by Iowan on 2009-11-15
I forgot to mention "valid" IP address. If it ends up with a 169.254.X.X (avahi) address, it is probably in a subnet by itself - and won't talk to the modem.

---

