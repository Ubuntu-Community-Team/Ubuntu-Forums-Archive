---
title: "Block certain domains"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by bala150985 on 2012-02-03
Hi

I am running Ubuntu Desktop and I don't have a web proxy configured on my browser.  Is there some way by which I can add certain domains to a something like a file, so that my browsing habits will never accidentally visit those sites ?

I know that the answer is as simple as getting a proxy installed and making my browser to use it.  However can we do it without installing & using a proxy or changing the hosts file configuration ?

---

### Post by barong234 on 2012-02-03
you can use add-ons in firefox. There are plenty of them you can choose.. :)

---

### Post by jonobr on 2012-02-03
I may be reading the question wrong, but why dont you just put the domain in the host file and point to the loopback interface


i.e.

in /etc/hosts
place an entry like

```

127.0.0.1     test.domain.com
```
then when you go to test.domain.com it will "block"
You could do an NSlookup of the IP address and clock using ufw or iptables rules.

---

### Post by bala150985 on 2012-02-03
Hi Jonobr,

I was thinking exactly the same method which you said,  However I am planning to keep adding more domains and would it give a blocked message ? "This is blocked as it is present in the hosts file ?"

---

### Post by lisati on 2012-02-03
[Opendns]("http://www.opendns.com/") might be of some help.

---

### Post by jonobr on 2012-02-03
Hello

Im not really sure what your trying to do, but if you wanted, (maybe this is overkill) you could install apache, change the index.html from the usual apache message of "It works" to

> "You filthy person. Looking for gratification on websites like this will not only make you go blind but will also make your mother really disappointed with you. Your IP address has been recorded, we have taken your photograph and stolen your poodle.You will soon be visited by the thought police and moved to a re-education camp where you will be retrained to only visit websites that feature flowers and knitting, and youtube sites that show only episode of downton abbey and masterpiece theater."

Then when someone trys to visit that blocked website which has been defined in the host file to point to 127.0.0.1 they will get the above message

Cheers


PS- The message would be changeable in index.html so you would not have to go with what I wrote:P

---

### Post by bala150985 on 2012-02-03
Jonobr cool :-D

---

### Post by daenuli on 2013-03-05
then how to enty some message on that content??
the content just say error 404 when it is accessing..

---

