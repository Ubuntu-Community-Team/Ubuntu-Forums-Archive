---
title: "Ubuntu on VMWare cannot access internet on port 80"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by DonMarquardt on 2012-03-28
I just installed the latest VMWare player on my XP desktop and then installed Ubuntu. 10.04 using the instructions from [http://processors.wiki.ti.com/index.php/How_to_Build_a_Ubuntu_Linux_host_under_VMware](http://processors.wiki.ti.com/index.php/How_to_Build_a_Ubuntu_Linux_host_under_VMware). 

The installation went fine but when I use firefox, apt-get or wget I get "The Connection Has Timed out". :mad:

I can ping google.ca, nslookup google.ca works.

Suggestions?

Thanks

Don

---

### Post by cybpabeofm on 2012-03-28
Try tommorow the server might be down. If its a chronic problem then you might just have to update your repositorys

---

### Post by DonMarquardt on 2012-03-28
The server is running fine. If I ping google.ca I get a reply. If I start firefox and enter google.ca as the url I get a timeout. google.ca is not down as I can access it from the host windows box.

---

### Post by DonMarquardt on 2012-03-28
Another piece of information. I can access my adsl modem using firefox from my VMWARE Ubuntu.

---

### Post by DonMarquardt on 2012-03-28
This is resolved.

The network connection was set to bridged and I changed the setting to NAT and it worked.

:p

---

