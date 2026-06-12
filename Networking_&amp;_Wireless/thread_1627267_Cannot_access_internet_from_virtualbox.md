---
title: "Cannot access internet from virtualbox"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by noelraxit1 on 2010-11-21
Hi Guys

I have an issue my host os is ubuntu 10.10 and i've installed bt4 in virtualbox and i am not able to access internet from my guest os. NAT and Bridged dint work. can anyone give me a suggestion please. 

Thank you

with Regards
Noel

---

### Post by Amente on 2010-11-21
Do you have network(even if not with the internet) access for your guest os?

---

### Post by noelraxit1 on 2010-11-21
yes i hav...

---

### Post by Amente on 2010-11-21
Then the problem is with your host OS sharing its Internet connection to the Guest.So what you should do is go to the configuration of your network in System-->Preferences-->NetworkConnections 
 select the network and edit its IPv4 method to Shared to other computers.Restart your PC and it should work,if not then probably I will try to find other solutions.

---

