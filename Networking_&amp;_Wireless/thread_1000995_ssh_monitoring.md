---
title: "ssh monitoring"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by markusfarkus on 2008-12-03
I tried searching, but didn't find anything helpful. I have an ssh server at home and I want to make sure that it doesn't get hacked. So I am wondering what the easiest way to have an automated monitoring service for ssh. I basically want an email sent out to me telling me all of the valid or invalid authentication attempts. 

Suggestions are welcome.

---

### Post by jonobr on 2008-12-03
HEllo


I would check you /etc/syslog.conf

You should check where your auth.log records records are stored.
Typically its in /var/log

The only thing I can recommend then is to set up a cron job to parse the file and look for occurrences of sshd etc.....

(you should see entries when you do cat /var/log/auth.log | grep ssh )
You can further refine your grep and stick it in a bash script to output to a file,
cat /var/log/auth.log| grep ssh > my_ssh_log.log

That done you need to then email it to your self.
This would require you to (IMO) use the SMTP server on your ubuntu server, and given your slightly concerned about hacks or access , opening up and using port 25 for mail is a bad idea.
That means you would have to integrate to an external mail server, which again I would not recommend.

I would instead recommend you use something like rsync to automatically copy across the latest file produced and store it in some directory on your machine.

Hope it was some small bit useful

---

### Post by markusfarkus on 2008-12-03
Actually that is very helpful, and should be pretty easy to setup. You are probably right about opening up smtp traffic. So I'll probably just securely transfer the file somewhere that I will remember to look at it.

Great thanks,

I just checked the log and I have only had this machine up for 1 day (not even) and I already have an IP address trying to get in. I have a bunch of root failures from an identical IP address. 

Maybe I should ask if there are any additional security measures I should take beyond the standard Openssh.

---

### Post by jonobr on 2008-12-03
Hello


Im no security expert but I would be security conscious, that being said I would recommend the following,

1) Disable unneeded services, an open service you don't need is a possible entry method for bad people
2) Keep up to date with security patches and forums which discuss security topics
3) Have a good firewall in place or expand on  the inbuilt firewall you already have on your system -iptables, heres a link
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
4) Tread carefully with 1 and 3 for denying services, if you dont know what something is, investigate and ask around for peoples adive, you may stop some service you need from working.
5) IF other people will be using the system, do the usual admin task of password enforcement, aging and pw complexity
6) If your system is mission critical - invite friends, family and the tech savvy you know and trust to hack it and exploit it, there are also tools out there to help you see if your system has an loopholes (nmap would be one example
7) Dont get excited about probes when you have hardened your system. There are programs which just do port scans on IP addresses, so you going to see this from time to time, and often. Once you are protected and you logs look clean your in good shape.


Cheers

---

### Post by markusfarkus on 2008-12-03
Wow, again thanks that is very helpful. I also found denyhosts which is going to make me feel a whole lot safer. 

So my setup is a home network. The machine is already behind a router that denies all incoming traffic except those that I explicitly allow ssh and some web stuff so 22 and 80. 

But the denyhosts is simple aptitude install denyhosts and the default is pretty good, though I made a few changes. It automatically adds IP addresses to /etc/hosts.deny based on the number of denied ssh attempts from a single IP. Pretty awesome program. I am already blocking 5 IPs.

---

### Post by jonobr on 2008-12-03
Cool , sounds like your in good shape, the previous will be good when you go one to own your own large ISO:p

---

### Post by troutbum13 on 2008-12-04
you may also want to change the default ssh port to something other than 22, and use shared key authentication and disable password authentication.  

you could also create a separate user for ssh sessions that is not a sudoer and/or has limited access.

hth:D

---

### Post by markusfarkus on 2008-12-04
That is good info as well. I am really considering going to key based authentication, but I don't know that I want to change the port. I like defaults in general.

---

