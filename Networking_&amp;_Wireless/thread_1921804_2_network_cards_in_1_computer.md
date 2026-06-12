---
title: "2 network cards in 1 computer"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by scpu1 on 2012-02-07
I have a computer that has 2 builtin network cards and a second computer with 1 network card. The first computer uses one nic to connect to the internet. I would like to use the other nic to connect to the other computer, but I am not sure how to configure this. In the end, I would like to be able to browse shared directories between both computers. Both systems use Ubuntu 11.10. How can I do this?

---

### Post by helgman on 2012-02-07
> **scpu1 said:**
> How can I do this?

If all you want is a connection between the two computers, let us call them computer A (connected to the Internet) and. If B is only going to talk to A then making the connection shouldn't be a problem:

1. Connect A and B via a physical connection
2. Configure [IP addresses]("http://en.wikipedia.org/wiki/Ip_address")
3. [Configure file sharing]("https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba_Server_Configuration_by_GUI")

So, here is the break down ...

1. For modern computers, just get an Ethernet cable (TP, UTP or whatever you like to call it) and connect the computers. This should work like a charm since modern network interface cards supporting the GigabitEthernet standard also supports [auto-MDIX]("http://en.wikipedia.org/wiki/Mdix#Auto-MDIX").

2. Here we run into a lot of theory about IP addresses and [subnetting]("http://en.wikipedia.org/wiki/Subnetting"). Hopefully this is not a problem. Just make sure that you don't use the same address space on the A-B network as you do on the A-Internet one. To be on the safe side. Look for the combination of [FONT="Courier New"]inet addr[/FONT] and [FONT="Courier New"]Mask[/FONT] when you run [FONT="Courier New"]ifconfig[/FONT]. If the command says that you use 192.168.1.x and 255.255.255.0, then, for the A-B network, you can use 192.168.y.x (and 255.255.255.0) where y is not the same as x (y != x).

More information on the actual configuration can be found [here]("https://help.ubuntu.com/community/NetworkManager0.7").

3. For step three the instructions are in the link above. Read the first few paragraphs carefully since indicate the easiest way to do it.

(If you decided that computer B needs access to the Internet, take a look at [this article]("https://help.ubuntu.com/community/Internet/ConnectionSharing").)

Let us know how you are doing.

Regards,
Helgman

---

### Post by scpu1 on 2012-02-07
Ok, I followed the instructions and networking is setup correctly. Thank you for that. As for file sharing. I noticed that Samba is for Windows networking. What if I want to make sure that it is only Unix/Linux based? How can I then share a folder between the two computers.

---

### Post by helgman on 2012-02-07
> **scpu1 said:**
> What if I want to make sure that it is only Unix/Linux based? How can I then share a folder between the two computers.

You could try [NFS]("http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29") if it's file sharing you want. If you just want to move files you can try SCP or SFTP (on top of SSH). But if I was going to do something like this, I'd go for SAMBA.

Regards,
Helgman

---

