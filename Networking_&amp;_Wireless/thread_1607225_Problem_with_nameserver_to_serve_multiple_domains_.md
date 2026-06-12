---
title: "Problem with nameserver to serve multiple domains using bind9"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by brealmz on 2010-10-27
Hi to all
  Im a php programmer and a newbie in ubuntu and i need your help guys please. English is not my primary language and i apologize for any mistake in my grammar. 
  Basically here is my goal.

[LIST=1]
[*]  mydomain.ph(not real domain name) was registered on sole registrant of my cTLD(ph) and they does't allow wildcard  subdomain so i want to host it instead in my nameserver and allow wildcard. It was a requirement on my project.
[*]  I will resell domain names and use my reseller program api in registration. Their api seems doesnt allow modify dns record so im going to use my own nameserver instead.
[/LIST]
So far here is what i have for now.
    
    

[LIST=1]
[*]    I use one domain name for my NS. At my mynsdomain.info registrar i forward ns1.mynsdomain.info and ns1.mynsdomain.info at my two internet ip address respectively.
[*]  mydomain.ph was set to used ns1.mynsdomain.info and ns2.mynsdomain.info as NS. They require nameservers with IP so what i understand was it will try to connect directly into my IP.
[*] I installed bind9  on my server. below is my zones settings
[*] When i dig my-domain.ph it has an entry on my ANSWER SECTION using one of my internet IP but when i used internet(browser based) tools it  does not return anything and cannot be resolve into ip. My ns1.mynsdomain.info and ns2.mynsdomain.info resolved into their IP respectively
[/LIST]
    
Heres is my questions. If you have an answer to any of question please reply.  

[LIST=1]
[*] Am i closed or not or is it even achievable?
[*]What i understand was when mydomain.ph was set to used my own nameserver and my registrar will be no longer have an authority with mydomain.ph. My question was where will those registrant information when whois will suppose to reside? Forgive me but i am really new to this.
[*] Can anyone please point me to a right direction?
[/LIST]
named.conf.local
```
zone "mynsdomain.info" {
        type master;
        file "/etc/bind/mynsdomain.info.hosts";
        };
zone "mydomain.ph" {
        type master;
        file "/etc/bind/mydomain.ph.hosts";
        };
```mynsdomain.info.hosts

```
$ttl 38400
mynsdomain.info.    IN      SOA     ns1.mynsdomain.info. root.localhost. (
                        1288143560
                        10800
                        3600
                        604800
                        38400 )
mynsdomain.info.    IN      NS      ns1.mynsdomain.info.
mynsdomain.info.    IN      A       10.179.176.193
ns1.mynsdomain.info.        IN      A       10.179.176.193
mynsdomain.info.    IN      NS      ns2.mynsdomain.info.
ns2.mynsdomain.info.        IN      A       10.179.176.193
10.179.176.193.mynsdomain.info.     IN      PTR     ns1.mynsdomain.info.
10.179.176.193.mynsdomain.info.     IN      PTR     ns2.mynsdomain.info.
mynsdomain.info.    IN      HINFO   "Quad-Core AMD Opteron(tm) Processor 2374 HE, 748922 MHz" "Ubuntu 9.04 "
```mydomain.ph
```
$ttl 38400
mydomain.ph.        IN      SOA     ns1.mynsdomain.info. root.localhost. (
                        1288189718
                        10800
                        3600
                        604800
                        38400 )
mydomain.ph.        IN      NS      ns1.mynsdomain.info.
*.mydomain.ph.      IN      A       184.106.x.x
mydomain.ph.        IN      NS      ns2.mynsdomain.info.
```where 10.179.176.193 is my local address
I know some of you guys can come up with a solution at no time and i need your help cause im out of both money and time already. I thought this problem would be easy but it already took me 3 days finding an a solution.


Thanks

---

