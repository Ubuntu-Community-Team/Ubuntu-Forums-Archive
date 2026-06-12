---
title: "How can I confirm that the firewall is on in KDE?"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by Rytron on 2010-10-31
Hi.

I am using Linux Mint 9 KDE. I launched Guarddog.
How can I confirm that firewall is on and secure?

Thanks.

---

### Post by SeijiSensei on 2010-10-31
Go to another computer on the Internet and run **nmap** against your computer's IP address.  nmap is in the Ubuntu repositories.  There's also a Windows version at [www.insecure.org](www.insecure.org).

---

### Post by spiky001 on 2010-10-31
+1 SeijiSensei  here is nmap online [http://nmap-online.com/](http://nmap-online.com/) that will scan your external ip

---

### Post by Rytron on 2010-11-01
Hi guys.

I just use internet at home.
Is there another way to verify? Could someone else try Guarddog and tell me how to set it up properly? Or is it just a matter of starting Guarddog for the first time and then it is setup?

Thanks.

---

### Post by Rytron on 2010-11-07
I have got used to Guarddog now. You must go to Protocol tab and, under default network zones, select Internet. From there select the items you will need such as HTTP,HTTPS, SSH, DNS.

---

