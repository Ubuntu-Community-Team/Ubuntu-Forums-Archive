---
title: "What is for &quot;Search domains:&quot; field in NetworkManager?"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by nodnolse1 on 2010-09-04
I searched over the INTERNET but I can't get an exhaustive description of that function ("Search domains:"). Are you able to explain to me what it is for?
Thanks

---

### Post by clrg on 2010-09-04
Could you please post a screenshot? I don't know where you found that feature.

---

### Post by procras on 2010-09-04
man resolv.conf

---

### Post by apmcd47 on 2010-09-04
Your company may have a domain:

```
mycompany.com
```

But it may be a large company, so each department may have its own village (sub-network), each with its own sub-domain:
```

hr.mycompany.com
pr.mycompany.com
it.mycompany.com
research.mycompany.com
marketing.mycompany.com

```
Your computer may be *mycomputer.marketing.mycompany.com* and the department server is *mkserver.marketing.mycompany.com* but thanks to the way DNS is set up you are in *marketing.mycompany.com* and can access the server simply as *mkserver*. But you use the server *prserver.pr.mycompany.com* a lot, not to mention *mainserver.mycompany.com*, and don't want to type in the full address each time. Search domains allows the other sub domains plus the main domain to be searched as though they are your local domain. So you may have this in your search domain:
```
marketing.mycompany.com
mycompany.com
hr.mycompany.com
pr.mycompany.com
it.mycompany.com
research.mycompany.com

```
Now the full domain name is needed if there is a clash of names as in *john.pr.mycompany.com* and *john.it.mycompany.com*

I hope that answers your question.

Andrew

---

### Post by nodnolse1 on 2010-09-06
Thank you to all that have tried to explain the function. I have understood that for soho w/o a domain it is better to leave the field blank. Thank you again, Paolo

---

