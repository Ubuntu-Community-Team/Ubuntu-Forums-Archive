---
title: "Cisco VPN-no DNS and no http"
date: 2005-02-27
forum: Networking &amp; Wireless
---

### Post by dnetwkguy on 2005-02-27
I have had Ubuntu Warty installed for about a week now. I am not new to Linux but new to Debian-based distros. I have installed Cisco's Easy-VPN client. The connection takes place but I do not appear to get DNS service and cannot http or https to servers on the remote network. I am able to successfully ping the remote nameserver and telnet or ssh to some routers I need access to.
I have tried the DNS solution on the Ubuntu Networking list but that did not resolve the issue. I now have a static address on my PC (behind a Linksys) and I have configured the DNS and nameservers in Networking.  This has not resolved the issue either. 
I am not having any issues with networking except for the VPN issues. Ubuntu runs great and access to the Internet and local net is perfect.

Any ideas?

Thanks

---

### Post by alastair on 2005-02-27
If you can ping the nameserver, then it should work.

Try access to DNS via the command line :

1) make sure ping works :

ping <IP address of nameserver>

2) Try a DNS lookup :

dig @<IP address of nameserver> [www.cisco.com](www.cisco.com)

---

### Post by dnetwkguy on 2005-02-27
Thanks. I have done both your suggestions. I am able to ping the nameserver by IP address only. I am not able to get a response from the nameserver using dig or nslookup. I was wondering if this had something to do with ports not being open.
Using Nmap I am showing these ports open:

68/tcp         open   dhcpclient
139/tcp       open   netbios-ssn
538/tcp       open   gdomap
32770/tcp   open   sometimes-rpc3

Is there something missing that I need to open?

Thanks,

---

### Post by codemonkey on 2005-03-01
I had a similar problem on my laptop and found that there's some conflict with certain network interface drivers.  I don't have that machine in front of me right now, so I don't remember the exact error messages, but check the output from dmesg.  If you are having the same problem as I am, you should see some errors indicating that packet sizes are too big:

[INDENT]...something I don't remember... XYZ > ABC[/INDENT] 

google for the error message, and you should find the same pages I did that helped me fix it.

In the end I found that my wireless card driver (prism2_cs) had a problem, but I was able to switch to the orinico_cs driver and that fixed the problem.  I hope you have some alternative driver available.

Sorry I can't be more specific, but the errors were pretty obvious in the dmesg output.

---

### Post by dnetwkguy on 2005-03-01
codemonkey, your solution worked! I swapped out my 3COM nic with a intel nic and everything worked. Thank you very much.

---

