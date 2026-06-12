---
title: "email and MX related issues"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2010-04-05
Folks:
what does it mean when noslookup, set q=mx returns does not return a MX preference and mail exchanger listing? I am only getting the follwoing infromatino

primary name server =
responsible mail addr = 
serial = ####
refresh = ####
retry = #####
expire = ######
default TTL = #####

I am lost I do not understand this result with nslookup and set q=mx.

thanks.

---

### Post by mbehamin on 2010-04-06
Hi 
it means that your MX record is not conifugred in you name server or its configuration has problem. install syslogd and then tail it when you rebooting named service. it should be tell you some errors 

:) 
i recommend you to check my blog 
[http://blog.mehdibehamin.com/?p=113](http://blog.mehdibehamin.com/?p=113)

regards

---

### Post by e24ohm on 2010-04-19
> **mbehamin said:**
> Hi 
it means that your MX record is not conifugred in you name server or its configuration has problem. install syslogd and then tail it when you rebooting named service. it should be tell you some errors 

:) 
i recommend you to check my blog 
[http://blog.mehdibehamin.com/?p=113](http://blog.mehdibehamin.com/?p=113)

regards
Sorry for the late reply - I will try this...thanks.

---

