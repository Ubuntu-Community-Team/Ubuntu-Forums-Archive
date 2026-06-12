---
title: "help connecting to a windows xp network"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by LincIVXX on 2008-12-09
Hi, I have had quite a bit of experience with Windows, but I'm completely new to Linux. My computer is hooked into a Windows network at my workplace, I am using Ubuntu 8.10 and my router is a Linksys. My Network Manager reads the connection as Auto ethO, and says I am connected to it but when I open Firefox it will only load the Ubuntu startup page and google. Google searches work but if I click on links they will not load. :confused:  I searched for a different browser in Synaptic and was going to use Epiphany but it said it was not compatible with an I386 system.  I haven't been able to successfully download any packages using synaptic but the live cd I created gives me a few packages. Any help would be very appreciated, this is a very confusing problem.

---

### Post by MagnumGI on 2008-12-09
If you can ping other hosts in the network, then your network connection is OK. Try pinging your gateway.

If successful, then you are probably having issues resolving domain names. Try to ping [www.google.ca](www.google.ca). If the URL doesn't resolve to an IP, then you've found your problem.

Check /etc/resolve.conf, and make sure it is updated with your name servers IP. You should have an entry like the one below. Just make sure it contains the IP of your domain name server

nameserver 10.1.0.10

---

### Post by LincIVXX on 2008-12-09
Okay, I type in my gateway and it came back 100% successful, when i typed in [www.google.ca](www.google.ca) it took awhile but eventually read 100% successful too, it gave me the IP address 74.125.95.103. I tried to update the file that you told me too anyways and it said the packet could not be found. :confused: Any more ideas? Could it be Firefox?

---

### Post by MagnumGI on 2008-12-10
Hmmm... the only other thing that comes to mind is an incorrect proxy setting within firefox. I'm forget how (I been using chrome for so long), but I know you can set firefox to connect to a proxy. Check this out, because you should not have a proxy address set for firefox, unless of course you are actually using one.

---

### Post by LincIVXX on 2008-12-10
Thanks for your help I will try that tonight when I get to my store. Hopefully it will work, and I seem to remember fooling around with something proxy related the other day so I pray that is the problem. 


Linc

---

### Post by superprash2003 on 2008-12-10
its mostly a dns issue.. use opendns servers - 208.67.222.222 and 208.67.220.220 ..

---

