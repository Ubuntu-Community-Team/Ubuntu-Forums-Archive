---
title: "Has anyone tried to have wired Ethernet &amp; Wireless working together?"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by dcstar on 2006-02-13
Has anybody successfully used ifenslave to get simultaneous operation of a wired Ethernet and Wireless connection?

[http://ubuntuforums.org/showpost.php?p=728419&postcount=17](http://ubuntuforums.org/showpost.php?p=728419&postcount=17)

---

### Post by mips on 2006-02-13
I replied to the linked thread by mistake but here goes anyway.

I haven't tried it but in theory it should work. Why don't you give it a bash ? I would if my AP wasn't in for repairs 
 
 I would advise thought that that you don't run any of the interfaces at speeds higher than the lowest common denominator. For 54Mb/s wireless & 100Mb/s I would run at 10Mb/s. For 11Mb/s wireless I would try to run both interfaces at round about 5Mb/s. you can always play with these values while using a sniffer to see if you are experiencing layer 2 problems.
 
 Why ? Wireless has a lot of overhead so it performs worse. If you have different speed interfaces you are going to receive out of sync frames which could be very problematic.

---

### Post by dcstar on 2006-02-13
[QUOTE=mips]I replied to the linked thread by mistake but here goes anyway.

I haven't tried it but in theory it should work. Why don't you give it a bash ? I would if my AP wasn't in for repairs 
 
 I would advise thought that that you don't run any of the interfaces at speeds higher than the lowest common denominator. For 54Mb/s wireless & 100Mb/s I would run at 10Mb/s. For 11Mb/s wireless I would try to run both interfaces at round about 5Mb/s. you can always play with these values while using a sniffer to see if you are experiencing layer 2 problems.
 
 Why ? Wireless has a lot of overhead so it performs worse. If you have different speed interfaces you are going to receive out of sync frames which could be very problematic.[/QUOTE]
In theory the data rate of the two links would be the average of both of them, (packets are supposedly shared on a round-robin basis).

The TCP layer should just see the one logical link as working at that rate.

I posted the question for the purposes of seeing if someone had tried it, I don't have a wireless AP myself so I can't do the work!

And it may be useful for those people with wireless who want to also use a wired connection by just plugging it in (without having to do anything else).

---

### Post by mips on 2006-02-13
[QUOTE=dcstar]In theory the data rate of the two links would be the average of both of them, (packets are supposedly shared on a round-robin basis).

The TCP layer should just see the one logical link as working at that rate.
.[/QUOTE]

Just keep in mind that before they become packets they are ethernet frames. If it is a round robin method then you are defeating the purpose of NIC bonding. NIC bonding effectively doubles your throughput and does not provide an average of interfaces. Data gets transferred over both interfaces simultaniously as they are seen as one logical interface.

Come to think of it this might not work as both ends of the link need to support it.

---

