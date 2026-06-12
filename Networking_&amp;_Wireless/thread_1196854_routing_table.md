---
title: "routing table"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by perpetuo on 2009-06-25
hello,
can anyone explain what's the meaning of '*' in the kernel IP routing table?
thanks

---

### Post by rdd37 on 2009-06-25
According to the manual:

"The output of the kernel routing table is organized in the following columns
       Destination
              The destination network or destination host.
       Gateway
              The gateway address or &#8217;*&#8217; if none set."


So... I take it to mean that a gateway address has not been set for that route entry..?

---

### Post by perpetuo on 2009-06-25
> **rdd37 said:**
> According to the manual:

"The output of the kernel routing table is organized in the following columns
       Destination
              The destination network or destination host.
       Gateway
              The gateway address or ’*’ if none set."


So... I take it to mean that a gateway address has not been set for that route entry..?

what manual are you refering?

---

### Post by rdd37 on 2009-06-25
'man route'
will provide the "manual" for the route command  ;)

---

### Post by perpetuo on 2009-06-25
> **rdd37 said:**
> 'man route'
will provide the "manual" for the route command  ;)

thanks!

---

