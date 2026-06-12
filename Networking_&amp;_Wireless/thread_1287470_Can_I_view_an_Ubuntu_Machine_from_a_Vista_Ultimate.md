---
title: "Can I view an Ubuntu Machine from a Vista Ultimate Machine?"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by Dafong on 2009-10-10
I have Ubuntu installed on one machine, I have checked it is connected to the internet, I can browse the web.

it must therefore be going through my Router.

However, when I am looking for it from my Windows Vista machine, it does not appear.
 
I am guessing this is a common problem, however my search threw up either thousands of results or none.
 
Was wondering if anyone could help me find the Ubuntu machine on my network as I am kinda new to both Win Vista ultimate and Ubuntu.

---

### Post by Dafong on 2009-10-10
I would add that I have always struggled to find my networks on the Vista machine from any other machine that wasn't running vista.

Thing is in windows, I know how to run a cmd, ipconfig, find the IP address of the machine in question, then return to the Vista machine and run a //IP ADDRESS which will bring up the machine on the network.

It still don't show up in any of Vista's network explorers, but that doesn't matter.
 
I don't know how to find the IP address of an Ubuntu machine.

---

### Post by Dafong on 2009-10-10
Ok found the IP address.

//IPADDRESS 
 
does not work to open up the network. I am guessing a firewall issue, but I don't know a way around it.

I am hoping that given the longevity of Linux/Ubuntu and the fact that windows operating systems are so common that this is at least possible?

---

### Post by ikt on 2009-10-10
So you are unable to ping/tracert to it?

---

### Post by rickyjones on 2009-10-10
> **Dafong said:**
> Ok found the IP address.

//IPADDRESS 
 
does not work to open up the network. I am guessing a firewall issue, but I don't know a way around it.

I am hoping that given the longevity of Linux/Ubuntu and the fact that windows operating systems are so common that this is at least possible?

1. The correct UNC path would \\IPADDRESS
2. Can you ping the IP address from your Vista computer?
3. Have you compared your Vista IP to the Ubuntu IP to make sure they are in the same subnet?
4. Is Samba installed on the Ubuntu PC?

Thanks,
Richard

---

### Post by Dafong on 2009-10-10
I was able to ping the IP addy, I wasn't able to tracert the IP addy, but that is more becuase I don't know how to, rather then there was any issue with tracert.
 
I also know i made the mistake with // instead of \\ it isn't a mistake i repeated while running the command, just while posting.
 
Yes they have the same addy, and subnet and default settings in the IP information.
 
I do not know if I have Samba installed, if it doesn't come with ubuntu 9.04 then no I don't, if it is bundled and loaded automatically then yes I probably do.
 
For the ping results:
 
4 packets sent, 4 received, 0 lost 0 
 
3ms roundtrip.

---

### Post by Dafong on 2009-10-10
Had a look at what Samba was, going through a 'how-to' guide at the moment.

---

### Post by Dafong on 2009-10-10
Ok after a bit of working, yep got that going.

Big thanks for the heads up about Samba and thanks to Stormbringer who wrote the how-to guide to Samba that took me through it.

---

