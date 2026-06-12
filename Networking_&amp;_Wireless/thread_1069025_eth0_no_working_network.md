---
title: "eth0 no working network"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by DualJazz on 2009-02-13
Hello, I have recently installed Kubuntu through Wubi using a Live CD.

Although problems have occured, I have had this problem with both Kubuntu and Ubuntu. It appears no internet is actually working, even though a wired eth0 device is recognised.

I am using a ADSL modem which connects my pc through a network cable. My motherboard is abit SG-95 with SIS190 Gigabyte Ethernet port. (built on motherboard)

This internet works flawlessly on Windows XP with no special configuration. The ADSL gives me a autoconfig ip.

The problem is no network is actually working. It is recognised in Kubuntu and Ubuntu but for example when I go onto the internet, Google can load easily but when I search something and click on the link, the page is always still loading and nothing is appearing. This is also happens when I type in the address too. "xyz contacted, waiting for reply" is shown in the web browser for Kubuntu and Ubuntu. Network manager is not loading either!

Please help me with this problem, thank you.

---

### Post by st33l on 2009-05-20
yes i do have the same problem too and im using asus p5sd2-vm motherboard with hte aforementioned ethernet adapter...it was a relief when finaly a linux distro detected my adapter..but this problem is makin it harder

---

### Post by st33l on 2009-05-22
please somebody help...wat info would u like to have im desperately lookin for a solution..i can connect to google..im able to ping etc

---

### Post by mrog on 2009-05-22
If you can ping IP addresses, eth0 is working. You state that the default google page loads but it might just be cached. This looks like a DNS issue. So here are the questions:

Is there anything in syslog that indicates a network failure (there might not be)?

What are the contents of /etc/resolv.conf? If that file indicates one or more nameservers, do they have the same addresses as on the Windows computer?

Some ISPs require that you go to a specific start page when you first connect a new computer through their service, is this required in your case.

Some ISPs will only allow access from one computer. They restrict access by recording the MAC address of the nic card. Have they or do they do this?

---

### Post by superprash2003 on 2009-05-22
post output of ifconfig from the terminal

---

### Post by hpasi on 2011-05-09
I have the same problem that you experienced, with the last 3 released versions of Ubuntu. Can you tell me if you finally could solve the problem, and in that case, how?
 
Thank you in advance 
 
Hector

---

### Post by jorritTyb on 2011-05-25
I have a similar problem. In my dmesg.txt I can constantly see things like:


> 
[    5.844707] r8169 0000:03:00.0: eth0: link down
[    5.845136] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.462225] r8169 0000:03:00.0: eth0: link up
[    7.462619] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


It appears that the connection is intermittently lost.

Greetings,

---

