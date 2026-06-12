---
title: "ubuntu file / print server and internet access"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by fourthofjuly on 2009-12-30
hi,  we plan to setup ubuntu file and print server in our school using ebox-platform... it will act as a pdc for xp/vista clients... users will have roaming profiles... 

we have an old P4 machine with single NIC...

our computer consultant is (obviously) not in favour of this scheme, so we are taking a huge risk since we have very little knowhow about linux server and  networking... therefore using ebox...

please see the attached drawing of our network... at present only the server is not present in our network... our ISP's gateway is 192.168.1.1...

now, this is what we want...
a) all XP/Vista clients including laptop users should login to the ebox server for file and print...



b) all client machines should have internet access, but use restricted to only "staff" users...

our question is...
1) do we need to setup the firewall or should we have separate subnets for internet and LAN?

2) also, can we use dhcp to lease ip addresses to all client machines?

please advise...

---

### Post by fourthofjuly on 2010-01-01
anyone, please?

---

### Post by foolano on 2010-01-01
*a) all XP/Vista clients including laptop users should login to the ebox server for file and print..*.

Nop problem with that. You will have to add each computer to the domain though. Printers can't be a bit tricky. If you have a network printer you should experience less issues.

[I]
b) all client machines should have internet access, but use restricted to only "staff" users...[/I]

It depends on what you want to restrict and how you want to do it. If you are using users and groups, and you are as you need them for PDC/roaming thing. You can define internet browsing profiles per group. Please take a look at eBox's doc regarding this:

[http://doc.ebox-platform.com/en/proxy.html#web-content-filter](http://doc.ebox-platform.com/en/proxy.html#web-content-filter)


our question is...

[I]1) do we need to setup the firewall or should we have separate subnets for internet and LAN?
[/I]

It depends on your scenario. Take a look at this link:

[http://trac.ebox-platform.com/wiki/Document/HowTo/SetUpNetworkScenario](http://trac.ebox-platform.com/wiki/Document/HowTo/SetUpNetworkScenario)

*2) also, can we use dhcp to lease ip addresses to all client machines?*

No problem with that.

I would like to add a couple of things. 

eBox is already being used in schools successfully in scenarios that will likely be like yours. 

If you use roaming profiles, keep in mind that depending on the use of the desktop, it can use a lot of bandwidth. If that's your case you will have to tweak what is stored remotely and what not.

And of course, there's an eBox forum where you can post your questions too:

[http://forum.ebox-platform.com](http://forum.ebox-platform.com)

Hope this helps

---

