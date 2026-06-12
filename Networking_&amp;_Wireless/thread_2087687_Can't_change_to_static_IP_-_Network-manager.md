---
title: "Can't change to static IP - Network-manager"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by Peternielsen5 on 2012-11-24
I would like to perform a basic network change on my Ubuntu 12 Desktop installation, that is to change my IP address from auto to static.

However I'm not allowed to accept the changes - I've tried hitting enter after injecting the gateway IP to no avail.
I get no error/ warning messages - the OK button is simply greyed out. 

What the heck am I missing :confused:

---

### Post by NikTh on 2012-11-24
Hi , 
I'm not sure for that , but maybe you have to open the network-manager as a root ? 
```
gksudo nm-connection-editor
``` 
try it. 
Keep in mind that, if you want to set a static IP , you have to set ,network mask and getaway also.
Thanks

---

### Post by chili555 on 2012-11-24
> **Peternielsen5 said:**
> I would like to perform a basic network change on my Ubuntu 12 Desktop installation, that is to change my IP address from auto to static.

However I'm not allowed to accept the changes - I've tried hitting enter after injecting the gateway IP to no avail.
I get no error/ warning messages - the OK button is simply greyed out. 

What the heck am I missing :confused:Is the button greyed out after you add DNS nameservers?

---

### Post by Peternielsen5 on 2012-11-25
Found the culprit.

It was a IP address formatting issue if address contains double zeros '00'

Wrong/not accepted format: xx.00.xx.xx
Correct/ accepted format: xx.0.xx.xx

---

