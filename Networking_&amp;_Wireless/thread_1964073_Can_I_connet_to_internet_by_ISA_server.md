---
title: "Can I connet to internet by ISA server?"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by ubun2os on 2012-04-23
hi for all
we have LAN network at our work. a pc that installed win server 2003 has ADSL internet. and many pc must have been had internet and ones is my pc.
i installed ubuntu 11.10. can i use internet from ISA server(win server2003)
what config is need for me and ISA?

---

### Post by haqking on 2012-04-23
> **ubun2os said:**
> hi for all
we have LAN network at our work. a pc that installed win server 2003 has ADSL internet. and many pc must have been had internet and ones is my pc.
i installed ubuntu 11.10. can i use internet from ISA server(win server2003)
what config is need for me and ISA?

enter your ISA box as the proxy.

Then whoever administers your ISA needs to allow you through , you need to speak to your network/ISA admin

---

### Post by ubun2os on 2012-04-23
> Then whoever administers your ISA needs to allow you through ;, you need to speak to your network/ISA admini am ISA admin. how to config ISA? is need any config in my ubuntu?

---

### Post by haqking on 2012-04-23
> **ubun2os said:**
> i am ISA admin. how to config ISA? is need any config in my ubuntu?

If you are ISA admin and you dont know how to configure it you have lots of issues ;-)

whatever your ISA server address is is the address you need for your linux proxy.

Depending on what *buntu you have depends how you enter it, either from a graphical DE or specified in the /etc/network/interfaces entry for the given interface.

---

### Post by ubun2os on 2012-04-25
> **haqking said:**
> If you are ISA admin and you dont know how to configure it you have lots of issues ;-)

whatever your ISA server address is is the address you need for your linux proxy.

Depending on what *buntu you have depends how you enter it, either from a graphical DE or specified in the /etc/network/interfaces entry for the given interface.
i haven't installed ISA in server yet. i would like install ubuntu on my pc and are there any problems between ubuntu and ISA server?

if i set up firefox browser proxy to IP server, my ubuntu would have been internet?
OR
how to edit /etc/network/interfaces?

---

### Post by haqking on 2012-04-25
> **ubun2os said:**
> i haven't installed ISA in server yet. i would like install ubuntu on my pc and are there any problems between ubuntu and ISA server?

if i set up firefox browser proxy to IP server, my ubuntu would have been internet?
OR
how to edit /etc/network/interfaces?

If you setup ISA properly then yes.

But why use ISA, why not use Squid.

ISA is primarily for windows network and clients

There is no ISA client for Linux, or at least there never used to be, you can make it a secure NAT client and you will have to configure apps etc for the proxy, not all support it however

---

### Post by ubun2os on 2012-04-25
> But why use ISA, why not use Squid.yes of course. i live any linux think and software. can i install Squid in windows XP and can i use internet on ubuntu from Internet server?

---

### Post by haqking on 2012-04-25
> **ubun2os said:**
> yes of course. i live any linux think and software. can i install Squid in windows XP and can i use internet on ubuntu from Internet server?

I dont understand what you are asking ?

Anyways [http://www.squid-cache.org/Download/](http://www.squid-cache.org/Download/) you can get a windows binary.

To answer question whatever your proxy is then yes ubuntu can use it but you need to be able to allow it to use that proxy and configure ubuntu to use it either globally or app by app basis.

Peace

---

