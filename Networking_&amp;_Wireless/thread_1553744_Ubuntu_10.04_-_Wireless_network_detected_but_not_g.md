---
title: "Ubuntu 10.04 - Wireless network detected but not getting connected"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by nikhilsista on 2010-08-15
Hello All,

I've installed Ubuntu 10.04 32 bit version(dual OS) on my 64 bit Pentium core2 duo 2.2GHz processor. Everything seems to be working fine except it's not getting connected to wireless network, although it's detected the network :(.

It was working fine(got connected to wireless network) when I had installed the same OS via virtual machine.

I've gone through a lot of threads from many forums but none helped me fixing the problem. Appreciate if anyone could help me fixing this issue.

PS: I'm new to Linux & Ubuntu.

---

### Post by Thomas Garman on 2010-08-15
It isn't clear what the problem is.  Are you trying to get a network connection in the virtual machine?  If so, then are you using Sun Virtual Box?  If so, then are you using the PUEL version or the OSE version?  If you are not using the PUEL version then you cannot install guest additions and so you are probably not getting connected because of that.

If you are using VMware then its a totally different story.

---

### Post by nikhilsista on 2010-08-15
Hey Thomas,

Thank you for the quick turn around.

Initially, when i installed ubuntu 10.04 using virtual machine, the OS was able to detect and connect to the wireless network(I was able to access internet). However, when i scrapped it and freshly installed ubuntu 10.04 as a dual OS, the OS was able to detect the wireless network but not getting connected to internet.

Here are the scenarios :

1. OS with Virtual Machine - wireless network got detected and also connected (able to access internet)

2. OS as a dual OS - wireless network detected but is not getting connected to the network(not able to access internet)

I hope this clears the ambiguity.

---

### Post by xircon on 2010-08-15
Virtual machines do not use their own wireless connections, they "bridge" to the host operating system's connection.  Think "bridge" is the correct term:D

So if this is a fresh install, what make and model of wireless card do you have?

---

### Post by nikhilsista on 2010-08-16
Not really sure how do i get it. However, i used the following command to obtain the details. Please go through the following snippet and let me know if this could be of some help. If this is not request you to kindly let me know the command to get the required details.

nikhil@nikhil-laptop:~$ lspci -nn | grep -E 'Ethernet|Network'
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)

---

### Post by xircon on 2010-08-16
Nikhil,

Search for "Intel Corporation PRO/Wireless 5100 AGN" (with the quotes) using the search box for the forum, there are masses of references, all saying there is a problem with this card e.g.

[http://ubuntuforums.org/showthread.php?t=1541806&highlight=Intel+Corporation+PRO/Wireless+5100+AGN]("http://ubuntuforums.org/showthread.php?t=1541806&highlight=Intel+Corporation+PRO/Wireless+5100+AGN")

You might get some useful info, sorry I can't help further.

Steve

---

### Post by nikhilsista on 2010-08-17
Steve,

Apparently, the problem reported in the thread you posted is totally different from what I've encountered. In my case, it's displaying the wireless network but is not getting connected.

---

### Post by nogueira13 on 2010-08-17
Hi [nikhilsista]("http://ubuntuforums.org/member.php?u=1130361"), I have a similar problem with my Laptop Dell Inspiron 15, 64 bits, but not with vistual machine, but in real mode. I get connection with a wireless with a weak signal, but the connectio nis very unstable, connecting and interconnecting sequentially. When the signal is strong it remains connected. But the problem is that, when I boot by windows 7, in the same position at home, with the same weak signal, I keep connected all the time. The same happens when I use my Tablet Nokia N810, in the same position at home and with the same weak signal of the wireless router near home. Does someone could help me?

---

### Post by nikhilsista on 2010-08-17
Yippee !!! I'm finally able to connect to wireless Network now !:popcorn:

@Steve - Like i said it's not the problem with the card whatsoever ! Had that the issue been with the card, it wouldn't have got connected through Virtual Machine as well in the first place.

Anyway, Appreciate your time ! ):P:D

---

### Post by xircon on 2010-08-17
Well done!! What did you do? It might help someone else.

---

### Post by nikhilsista on 2010-08-17
@ nogueira13 - I'm new to ubuntu as well ! However, I've come across similar issue(Unstable connection) being reported in one of the threads. Look up for the thread, it could be of some help to you. 

My apologies that I couldn't be of much help to you :)

---

### Post by JEIhrig on 2010-08-31
nikhilsista,

What did you do? I have the exact same problem with my edimax nMax wireless card.

I am able to detect my router, and it even asked me for my WPA2 encryption key (Which I triple checked was correct), it tries to connect but never does.

---

