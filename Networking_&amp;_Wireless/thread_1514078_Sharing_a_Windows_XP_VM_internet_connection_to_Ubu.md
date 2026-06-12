---
title: "Sharing a Windows XP VM internet connection to Ubuntu"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by Alan502 on 2010-06-20
Hi,
I'm trying to share the internet connection of my Windows XP Virtual Machine (virtualbox) to Ubuntu. I know it sounds weird, but what happens is that i'm using a 3G modem to connect to the internet and 3G connections are still very unstable with ubuntu's network manager. Fortunately, the modem works a lot better with my Virtual Machine. I have already set up a "host only" network between my Windows XP guest and my Ubuntu host and i can they can ping each other but i still can't share the connection of my virtual machine. I already selected "share this connection" on win xp but i think i still have to configure something on ubuntu for it to work. The interface Ubuntu uses is vboxnet0 (not eth0).

Please help me guys!! i couldn't get much help at the virtualbox forum :P but it might be a problem with the gateway or something. This is the last thing to do before i can get rid of my Windows XP partition, please!

---

### Post by sanderj on 2010-06-20
Reading [http://en.wikipedia.org/wiki/Internet_Connection_Sharing](http://en.wikipedia.org/wiki/Internet_Connection_Sharing) , I guess the ICS host is a DHCP-server and Internet-gateway doing NAT.

So, your linux system should only listen and be connected to the Windows machine, not to a LAN or modem/router on your LAN. Have you taken care of that?
Does your Linux-system do DHCP-client? If so, does it get an IP address from the Windows machine?

---

### Post by Alan502 on 2010-06-20
Sorry for taking so long to reply

Actually, the host and the guest are not connected through NAT. Virtualbox has an option named "Host-only network" that they say creates a network between the host and the virtual machine; and i'm connected to it through the vboxnet0 interface. Virtualbox has a dhcp and both my VM and ubuntu get their ip adresses from it.

---

### Post by sanderj on 2010-06-21
> **Alan502 said:**
> Sorry for taking so long to reply

Actually, the host and the guest are not connected through NAT. Virtualbox has an option named "Host-only network" that they say creates a network between the host and the virtual machine; and i'm connected to it through the vboxnet0 interface. Virtualbox has a dhcp and both my VM and ubuntu get their ip adresses from it.

Exactly: that's not correct: Ubuntu should get it's IP address from the Windows XP doing ICS.

---

