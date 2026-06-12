---
title: "IPCONFIG /displaydns Equivalent?"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by wizardfait on 2009-09-28
I'm in a class at college where-in we are using both Ubuntu and Windows. We are trying to see if Ubuntu has an equivalent to the Windows command "ipconfig /displaydns" where it will display all of the DNS names stored in the DNS cache, along with other information about them.

Would anyone be able to help us?

---

### Post by Bucky Ball on 2009-09-28
System->Admin->Network. Hit the DNS tab. They are listed there.

---

### Post by wizardfait on 2009-09-28
> **Bucky Ball said:**
> System->Admin->Network. Hit the DNS tab. They are listed there.

I'm sorry? All I have are a Devices, Ping, Netstat, Traceroute, Port Scan, Lookup, Finger, and Whois.

Might it be Netstat and "Routing Table Information"?

---

### Post by chili555 on 2009-09-28
Please open a terminal and do:```
cat /etc/resolv.conf
```

---

### Post by wizardfait on 2009-09-28
> **chili555 said:**
> Please open a terminal and do:```
cat /etc/resolv.conf
```

Are you asking me to paste it to you? Or is that supposed to be an answer? If that's supposed to be an answer, it isn't.

---

### Post by badger_fruit on 2009-09-28
> The **ipconfig /displaydns** command provides you with a means to view the contents of the DNS client resolver cache, which includes entries preloaded from the local Hosts file, as well as any recently obtained resource records for name queries resolved by the system. This information is used by the DNS Client service to quickly resolve frequently queried names before it queries its configured DNS servers.

source --> [http://technet.microsoft.com/en-us/library/cc758108%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc758108%28WS.10%29.aspx)

resolv.conf simply lists all the DNS servers that will be used by your Linux client PC.
However, there does not appear to be a unix alternative; the NSCD daemon seems to be the client resolver cache manager

```

bgrsvr-y:~ # service nscd status
Checking for Name Service Cache Daemon:                               running

```

There may be more info on this daemon by searching the old google.

---

### Post by i.r.id10t on 2009-09-28
> **wizardfait said:**
> Are you asking me to paste it to you? Or is that supposed to be an answer? If that's supposed to be an answer, it isn't.

No actually, that is the correct answer.

---

### Post by badger_fruit on 2009-09-28
> **i.r.id10t said:**
> No actually, that is the correct answer.

No, it's not ..
Windows ipconfig /displaydns shows a list of domains in the DNS cache, NOT a list of DNS servers ...

> 
C:\Documents and Settings\my.logon>ipconfig /displaydns

Windows IP Configuration

         digg.com
         ----------------------------------------
         Record Name . . . . . : digg.com
         Record Type . . . . . : 1
         Time To Live  . . . . : 536
         Data Length . . . . . : 4
         Section . . . . . . . : Answer
         A (Host) Record . . . : 64.191.203.30


         [www.kidscape.org.uk](www.kidscape.org.uk)
         ----------------------------------------
         Record Name . . . . . : [www.kidscape.org.uk](www.kidscape.org.uk)
         Record Type . . . . . : 1
         Time To Live  . . . . : 24263
         Data Length . . . . . : 4
         Section . . . . . . . : Answer
         A (Host) Record . . . : 213.171.219.35


         1.0.0.127.in-addr.arpa
         ----------------------------------------
         Record Name . . . . . : 1.0.0.127.in-addr.arpa.
         Record Type . . . . . : 12
         Time To Live  . . . . : 575995
         Data Length . . . . . : 4
         Section . . . . . . . : Answer
         PTR Record  . . . . . : localhost


         hotmail.com
         ----------------------------------------
         Record Name . . . . . : hotmail.com
         Record Type . . . . . : 1
         Time To Live  . . . . : 230
         Data Length . . . . . : 4
         Section . . . . . . . : Answer
         A (Host) Record . . . : 64.4.33.7


         Record Name . . . . . : hotmail.com
         Record Type . . . . . : 1
         Time To Live  . . . . : 230
         Data Length . . . . . : 4
         Section . . . . . . . : Answer
         A (Host) Record . . . : 64.4.32.7



         [www.google-analytics.com](www.google-analytics.com)
         ----------------------------------------
         Record Name . . . . . : [www.google-analytics.com](www.google-analytics.com)
         Record Type . . . . . : 5
         Time To Live  . . . . : 212
         Data Length . . . . . : 4
         Section . . . . . . . : Answer
         CNAME Record  . . . . : www-google-analytics.l.google.com


---

### Post by doas777 on 2009-09-28
it's an answer, just not one for the question you asked.

ubuntu does not do dns caching by default.

---

### Post by wizardfait on 2009-09-28
> **doas777 said:**
> it's an answer, just not one for the question you asked.

ubuntu does not do dns caching by default.

Alright, thank you. I didn't mean to make it sound arrogant by saying it WASN'T the answer... I merely meant as you said that it wasn't the answer I was looking for.

Is it merely Ubuntu that doesn't cache DNS, or is it a generic Linux thing?

---

### Post by doas777 on 2009-09-28
some more info:

[http://www.ubuntugeek.com/local-dns-cache-for-faster-browsing-on-ubuntu-machine.html](http://www.ubuntugeek.com/local-dns-cache-for-faster-browsing-on-ubuntu-machine.html)
[http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html](http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html)

---

### Post by wizardfait on 2009-09-28
Ahh, and thank you one more time! You've been quite helpful!

---

### Post by Bucky Ball on 2009-09-29
> **wizardfait said:**
> I'm sorry? All I have are a Devices, Ping, Netstat, Traceroute, Port Scan, Lookup, Finger, and Whois.

Might it be Netstat and "Routing Table Information"?

Not Network Tools, Network.

---

