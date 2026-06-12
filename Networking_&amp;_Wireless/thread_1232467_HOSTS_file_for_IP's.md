---
title: "HOSTS file for IP's"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by natbob1 on 2009-08-05
Is there a file similar in function to the HOSTS file which can redirect an IP to a different IP rather then redirect a hostname to an IP?

Thanks,

natbob1

---

### Post by jonobr on 2009-08-05
Hello

Your /etc/nsswitch.conf  file maps the lookup order for host name.

Its usually 
hosts:      files     dns


This means it looks at its hosts file first and then if no response goes to the dns to resolve.


You control the hosts file on your system, so if you have a hostname on dns and on the hosts file and if the ip addresses are difference,. it will take the one from the host file first.

Not sure why you would want to do that though???

---

