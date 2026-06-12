---
title: "dsl 502t router...bridge mode?"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by rahilm on 2010-03-11
hello.. i am looking for an ubuntu alternative to this : 

[http://broadbandforum.in/mtnl-broadband/46431-mtnl-broadband-shift-bridged-mode-d-link-dsl-502t/](http://broadbandforum.in/mtnl-broadband/46431-mtnl-broadband-shift-bridged-mode-d-link-dsl-502t/)

Can anybody help?

---

### Post by rahilm on 2010-03-12
bump

---

### Post by dineshs on 2010-03-12
You mean how to configure in PPPoe mode?Just select PPPoE/PPPoA in step 2.An additional field for username and password will appear.Just fill it and proceed

---

### Post by rahilm on 2010-03-13
> **dineshs said:**
> You mean how to configure in PPPoe mode?Just select PPPoE/PPPoA in step 2.An additional field for username and password will appear.Just fill it and proceed
No. I am trying to get a bridged connection. I currently have a pppoe connection. the site explains how to set up a bridge connection. but all steps are for windows..

---

### Post by dineshs on 2010-03-13
The modem configuration is same for any operating system ,but making a PPPoE dialler differs.So first open firefox , try 192.168.1.1 as the web address and configure modem as explained in that site.If you are not able to get this router page configure network .
Right click on the network icon on the right top and edit connection.Add a wired connection with IP 192.168.1.131 Mask 255.255.255.0  and gateway 192.168.1.1 then hit enter.Put DNS as 4.2.2.1 then apply
Once the modem is configured,Create PPPoE connection as in the link
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
You can also configure DSL by clicking the same network icon-edit connection-DSL-add-then give username and password and apply

---

