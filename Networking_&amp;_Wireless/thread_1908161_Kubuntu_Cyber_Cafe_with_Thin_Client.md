---
title: "Kubuntu Cyber Cafe with Thin Client"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by herasmus on 2012-01-12
Hi,
 
             I have a cyber cafe project in Africa. I'm thinking using the NC600W multi-sers with Kubuntu and I'm wondering if anybody use the NC600W or any other thin client with Kubuntu or Ubuntu before and how can I setup the Computer to get it work?
 
 
Please help.

---

### Post by CongoJim on 2012-01-20
I set up a classroom in the DRC using one good desktop and 10 mixed computers running off it as thin clients. The computers were basically junk but when connected to the decent server you'd think they were new. Back to your query, I used LTSP for the setup [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) and it was fairly simple.  

I may be wrong but since you need no OS on the client I should imagine you can use your NC600w with an Ubuntu server.

---

### Post by herasmus on 2012-01-30
Thanks [CongoJim]("http://ubuntuforums.org/member.php?u=52641") for you explanation. What I'm doing now is to install a little cybercafe lab in my house just to test 4 NC600W devices that I ordered online that I will probably get in the next two weeks. As for the server itself I'm thinking have a system Unite with a duo core processor, 16 Giga of RAM and 1TB of Hard drive because the main cybercafe in Africa will contains 30 to 35 workstations and I hope with such specification of the server I will not have any problem to display some videos.

---

### Post by SeijiSensei on 2012-01-30
I'd be sure the server and any switches or other networking devices support Gigabit Ethernet.  You can get away with 100BaseT to the workstations, but the connection from the server to a switch or concentrator needs to run at Gig speeds if you want to stream video to 35 workstations.  In fact you might need to partition the network into three or four physical segments with separate switches and multiple Gig ethernet adapters on the server.

---

### Post by herasmus on 2012-02-01
Thanks SeijiSensei for your advice. For the VGA card do you have suggestion? 
Also I'm wondering if it is good idea to setup the Cyber with Wireless network or wired network since the NC600W supports both.
 
Thanks

---

