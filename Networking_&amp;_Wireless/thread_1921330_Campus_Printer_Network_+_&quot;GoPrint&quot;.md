---
title: "Campus Printer Network + &quot;GoPrint&quot;"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by hotbeef on 2012-02-06
I am trying to get access to the printers at my campus through my laptop running Ubuntu. The windows machines they provide for students are setup to print to a few big network printers (which I'm guessing is a windows print server, but I don't know how to tell), but everything is piped through printing management software called [GoPrint]("http://www.goprint.com/") that is running on these windows machines. I looked around their website, and they mention supporting 'linux' a few times, but I dont know if that is for linux clients or a linux print server.

Not only am I having trouble finding these printers through System-Administration-Printers-Add Network Printer (I don't even know which protocol I should be using), I am also concerned that this print management software will cause problems with printing off my Ubuntu Laptop.

So far, after poking around on the windows machines, all the information I've been able to find for the main public printer is:

```
 \\syprint.pcc.edu\SYLIBQ1

HP universal Printing PCL 6
```I am a total novice when it comes to Ubuntu and networking in general, so I will apologize if I say something stupid or if I don't know what I'm talking about.

Any suggestions?

---

### Post by praseodym on 2012-02-06
Type

[http://localhost:631](http://localhost:631)

in your browser and try to setup the printer(s) with CUPS:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by hotbeef on 2012-02-06
Ah, i was able to connect to it through samba and instructions provided by the campus for adding a printer in macOsX. yay. 

solved.

---

