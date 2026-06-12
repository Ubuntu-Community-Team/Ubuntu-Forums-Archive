---
title: "IPtables, DNS and restoring"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by cbillson on 2012-12-04
Had a strange issue this morning. booted my test box without DNS available and firewall didnt establish.
 
I'm using IPtables, i have the output of iptables-save as a command in rc.local
 
iptables-restore < myfile.rules
 
now if you have an entry in there that is a domain name (my case ntp.ubuntu.com) it fails at that line as unable to resolve (when there is no DNS server available) and the box comes up with no firewall.
 
firstly is my method of restoring firewall rules the best way for what i want to achieve?
 
secondly, is this expected behaviour, and is there any way i can ensure that the default state is locked down, rather than wide open?
 
Thanks
Chris

---

### Post by SeijiSensei on 2012-12-04
The normal order of tasks at boot starts iptables before the network so there isn't a small window of opportunity for attackers.  As you discovered, that means you will not have DNS available when the rules are installed.  You can only use IP addresses in iptables rules unless you reorder the sequence of boot events.  I'd avoid that unless you really know what you are doing.

Here's the IP I get for ntp.ubuntu.com: 91.189.94.4.  

On servers, I run the ntpd daemon on the box itself.  You can then list the upstream servers in ntp.conf with domain names.

---

### Post by cbillson on 2012-12-04
> **SeijiSensei said:**
> The normal order of tasks at boot starts iptables before the network so there isn't a small window of opportunity for attackers. As you discovered, that means you will not have DNS available when the rules are installed. You can only use IP addresses in iptables rules unless you reorder the sequence of boot events. I'd avoid that unless you really know what you are doing.
 
Here's the IP I get for ntp.ubuntu.com: 91.189.94.4. 
 
On servers, I run the ntpd daemon on the box itself. You can then list the upstream servers in ntp.conf with domain names.
 
Thanks, two issues with this, firstly domains are dynamic so the domain may point to one IP one day, another the next.
 
second, i was already concious of this, when i added public IP's from the command line, I'm pretty sure it did a reverse DNS lookup and added a domain to the list.

---

### Post by SeijiSensei on 2012-12-05
> **cbillson said:**
> Thanks, two issues with this, firstly domains are dynamic so the domain may point to one IP one day, another the next.

What domains are you talking about here?  Whether the upstream servers have dynamic addressing?  Yes, a lot of NTP server names use round-robin DNS so the IPs may change over time.  Usually that's just for load-balancing purposes.  It's unlikely that the address I gave above won't still be offering NTP even if it's not the machine you get from a DNS query today.  Also that's a good reason to run ntpd on your server so t can handle the name-resolution of the upstream NTP servers while it's running.

If you run your own ntpd daemon, you do not need to worry about iptables rules.  The queries your server sends upstream will be handled by the regular iptables rules for "ESTABLISHED,RELATED" traffic.  You would only need to open ports in the firewall if other machines are using your server as their NTP provider.
 
> second, i was already concious of this, when i added public IP's from the command line, I'm pretty sure it did a reverse DNS lookup and added a domain to the list.

I don't know what you mean here.  Are we still talking about rules for NTP?

---

### Post by cbillson on 2012-12-05
> **SeijiSensei said:**
> What domains are you talking about here? Whether the upstream servers have dynamic addressing? Yes, a lot of NTP server names use round-robin DNS so the IPs may change over time. Usually that's just for load-balancing purposes. It's unlikely that the address I gave above won't still be offering NTP even if it's not the machine you get from a DNS query today. Also that's a good reason to run ntpd on your server so t can handle the name-resolution of the upstream NTP servers while it's running.
 
If you run your own ntpd daemon, you do not need to worry about iptables rules. The queries your server sends upstream will be handled by the regular iptables rules for "ESTABLISHED,RELATED" traffic. You would only need to open ports in the firewall if other machines are using your server as their NTP provider.
 
 
 
I don't know what you mean here. Are we still talking about rules for NTP?
 
I used the ntp rule as an example, but there are lots of sites who change their ip frequently, not just for load ballencing.
 
cant remember the exact command i used, but it was iptables with a whole load of parameters to add a rule for input/output etc and it took the IP and did a reverse lookup, when i did iptables-save the output had a domain name in ti.

---

### Post by Cheesehead on 2012-12-05
> **cbillson said:**
> cant remember the exact command i used, but it was iptables with a whole load of parameters to add a rule for input/output etc and it took the IP and did a reverse lookup, when i did iptables-save the output had a domain name in ti.

Sure, IPTables will do a DNS lookup if the service is available. But you cannot rely upon that availability during boot. After boot you can.

You can simply divide your IPTables script. Boot rules with addresses only, and post-boot supplemental rules that include names. Plenty of other strategies to deal with it.

---

### Post by cbillson on 2012-12-05
> **Cheesehead said:**
> Sure, IPTables will do a DNS lookup if the service is available. But you cannot rely upon that availability during boot. After boot you can.
 
You can simply divide your IPTables script. Boot rules with addresses only, and post-boot supplemental rules that include names. Plenty of other strategies to deal with it.
 
Thanks, like this idea a lot. where would i add the command so it is post boot?

---

### Post by SeijiSensei on 2012-12-05
You can add scripts and commands to /etc/rc.local.  That is the last script run during boot.

However you will need to be careful about what you put in each set of rules.  For instance, the pre-DNS rules cannot end with a generic DENY rule, since the rules you append in the post-DNS file will never be reached.  Using DENY as the default policy for the INPUT chain can help avoid this issue, since you don't need a final catch-all deny rule.

---

### Post by cbillson on 2012-12-06
> **SeijiSensei said:**
> You can add scripts and commands to /etc/rc.local. That is the last script run during boot.
 
However you will need to be careful about what you put in each set of rules. For instance, the pre-DNS rules cannot end with a generic DENY rule, since the rules you append in the post-DNS file will never be reached. Using DENY as the default policy for the INPUT chain can help avoid this issue, since you don't need a final catch-all deny rule.
 
 
Thanks, the box is fairly locked down, so my thoughts would be to have the pre-interface to be lock all but allow SSH and critical services. all other rules could come in with the second.
 
Another question however. my current 'firewall rules' come from the command iptables-restore < myrules and this is in rc.local - if you're suggesting this should be where i add my second set of rules, where ordinarily would you be adding your first set? or would i just use two lines in rc.local - ie
 
iptables-restore < lockdown
iptables-restore < rulesthatmightfail

---

