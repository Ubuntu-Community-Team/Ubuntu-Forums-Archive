---
title: "DNS for Temporary Internal LAN only"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by shelzmike on 2010-12-06
Hello - 

I am currently working with a cloning project using FOG on Ubuntu 10.10 (Desktop). While there is certainly a learning curve, all seems to be going well.

For the initial project, I have this "cloning network" isolated completely. Meaning, it is not connected to my main network/domain switch - FOG is handling the DHCP, I have a dedicated managed switch handling the routing between the FOG server and the client clones. 

The main problem I am having is that Ubuntu is not able to resolve the hostnames of the client computers.

I know this is because I do not have DNS setup on my Ubuntu PC. 

What is the best route to take in order to resolve this? Can I use bind9 to take care of it, or is that too complicated for what I need it to do?

Mike

---

### Post by endotherm on 2010-12-06
well static dns seems like it would be a right pain in this usecase. how dynamic is your naming (will you have a completely differant batch of 20 names each day)?are you trying to give names to all hosts, or just a few specific ones like your fog server?

---

### Post by shelzmike on 2010-12-06
Hmm, it is not very dynamic I do not suppose and this will only be used for this initial project to start with. For the next couple of weeks I will be using the FOG server and its clients off our main network; however, after that I will be putting FOG on our main network to use as a backup imaging solution. 

For the time being, my clones will only have hostnames like ACS-0001-LT, ACS-0002-LT, etc. 

Isn't there a config file that I can change what domain Ubuntu resolves on? Could I just create a workgroup and have it listed that way? I am not sure which file that I am referring to though, I need to do a little bit more research. 

Thanks.

Mike

---

### Post by endotherm on 2010-12-06
ok, bind might not be too much of a bear then. yeah, you can always change what DNS server the client resolves against via network manager, so thats no huge worry.

here is a good starting point for working with bind:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by shelzmike on 2010-12-06
Any good tut's on bind that you know of? I have found a couple, but they are mostly the whole kit n' kaboodle, if you know what I mean. I find it hard to weed through some of the not-needed, to get to the needed for my situation. I will see what I can do! Thanks again!

Mike

---

### Post by SeijiSensei on 2010-12-06
If you're only dealing with a couple dozen hosts, and this is a temporary thing, I'd just add them all to /etc/hosts and copy it to all the machines.  [Windows]("http://en.wikipedia.org/wiki/Hosts_%28file%29") supports the hosts file as well.

---

