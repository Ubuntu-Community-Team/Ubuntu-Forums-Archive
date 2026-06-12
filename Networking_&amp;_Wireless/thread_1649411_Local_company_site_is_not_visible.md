---
title: "Local company site is not visible"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by jeremycod on 2010-12-20
Hi,

I have the problem with Ubuntu to access the local site within my company network. This network has access to Internet, but the company's site does not have a public address. It is like "http:e-learning.local". I can access this site from any windows machine, but I can't access it from ubuntu. Only if I use IP address, I can access it. However, I have normal access to other sites on the Internet.

Do you have any suggestion how to solve this problem?

Thanks,
Zoran

---

### Post by grahammechanical on 2010-12-20
It is my guess that this company web site is only accessible from within the Company network. Someone like myself will not be able to access it using the Internet. Therefore, I guess that you, yourself, will not be able to access it from the Internet. I guess that you are using the Company network to access the Internet and then to access this local web site of the Company.

Could you not access this Company web site using the IP address (as you say you can) and then set it as a bookmark in the web browser? Then you may be able to connect to this web site by selecting the bookmark instead of typing in the IP address.

Regards

---

### Post by jeremycod on 2010-12-20
> **grahammechanical said:**
> It is my guess that this company web site is only accessible from within the Company network. Someone like myself will not be able to access it using the Internet. Therefore, I guess that you, yourself, will not be able to access it from the Internet. I guess that you are using the Company network to access the Internet and then to access this local web site of the Company.
That is exactly my case.

> **grahammechanical said:**
> 
Could you not access this Company web site using the IP address (as you say you can) and then set it as a bookmark in the web browser? Then you may be able to connect to this web site by selecting the bookmark instead of typing in the IP address.

It is not the problem in connecting to the web site. It contains Joomla site, which works fine in this way, using IP instead of symbolic address. However, site also contains Moodle learning platform and Moodle have it's own configuration settings containing home_url=http://elearning.local. 
If I open this site with IP address, next button or link click will redirect me to [http://elearning.local/something](http://elearning.local/something) and not to [http://10.10.10.10/something](http://10.10.10.10/something). Then Moodle can't appropriately find all resources it uses (css, images...) so the web page looks chaotic. 

Zoran

---

### Post by Barry53 on 2010-12-20
Jeremy,

Sounds like the Ubuntu box can't resolve e-learning.local to it's IP address. Perhaps adding e-learning.local to the /etc/hosts file might help.

---

### Post by ppv on 2010-12-20
The url in the first post does not have the two slashes that are there in a web address. Is this the case with just the post.

---

### Post by Boondoklife on 2010-12-20
The .local sounds like they are using mDNS to resolve names. Can you connect if you try 'elearning'?

If not then they should consider setting up a real dns server.

---

### Post by jeremycod on 2010-12-20
> **Barry53 said:**
> Jeremy,

Sounds like the Ubuntu box can't resolve e-learning.local to it's IP address. Perhaps adding e-learning.local to the /etc/hosts file might help.
Thanks. I will try this tomorrow morning as I'm at my home now.

---

### Post by jeremycod on 2010-12-20
> **Boondoklife said:**
> The .local sounds like they are using mDNS to resolve names.
I asked our network administrator about this. They are using Windows 2003 server integrated DNS server.

> **Boondoklife said:**
>  Can you connect if you try 'elearning'?
No I can't. We are using .local at the end as the part of the url. I asked our network administrator to map [http://elearning.local](http://elearning.local) with the IP address of the server hosting moodle. They decided to put local at the end of url, just because they wanted to make difference between local sites and sites from outside world, but they also could add anything else. It is not automatically added by mDNS or something else.

---

### Post by jeremycod on 2010-12-20
> **ppv said:**
> The url in the first post does not have the two slashes that are there in a web address. Is this the case with just the post.
Yes. Sorry for that. It was typo in the post.

---

### Post by Boondoklife on 2010-12-20
Are the windows machines enrolled in a domain and is it AD?

---

### Post by jeremycod on 2010-12-20
> **Boondoklife said:**
> Are the windows machines enrolled in a domain and is it AD?
No. The windows machines are not enroled in a domain. 
What is AD? Active directory? No. We don't use it. IP addresses are dynamically assigned to the machines. We don't use any proxy or something like that. I have dual boot (Windows and Ubuntu) on the same machine, and I have not configured anything for network access on any machine, neither in network settings neither in web browser. 
I have tried both Firefox and Chrome and it's the same. 
Ping elearning.local does not resolve host. 

Zoran

---

### Post by Boondoklife on 2010-12-20
can you post the output of
```
nslookup SERVERIP
```

Replace the SERVERIP with the ip of the elearning server.

---

### Post by grahammechanical on 2010-12-20
May I make another suggestion? It might be just as useless as my last suggestion. But here goes.

Try to bypass the company web page and go direct to the Moodle learning platform opening page. Use a Windows machine to find the url of the Moodle page. Past it as a link in a document. Then you can open that document and click on the link and it should load up the web browser and go to that url.

It think that this problem may be caused by the people who set up this learning program. They are not using conventional codes (addresses) for web pages. I suspect that the windows machines use a specially modified web browser to access these pages. 

Regards.

---

### Post by jeremycod on 2010-12-21
> **Boondoklife said:**
> can you post the output of
```
nslookup SERVERIP
```Replace the SERVERIP with the ip of the elearning server.

This is the output I got:
 
```
root@zoran-HP-EliteBook-8740w:~# nslookup 10.10.6.254
Server:        10.10.5.100
Address:    10.10.5.100#53

** server can't find 254.6.10.10.in-addr.arpa.: NXDOMAIN
```

---

### Post by jeremycod on 2010-12-21
Guys, 

Thank you all for your help in solving this problem. I solved it :D

> **Barry53 said:**
> Jeremy,

Sounds like the Ubuntu box can't resolve e-learning.local to it's IP address. Perhaps adding e-learning.local to the /etc/hosts file might help.

This was the solution. Thank you Barry.
Zoran

---

### Post by Boondoklife on 2010-12-21
Yea the /etc/hosts file will fix it but it is not a real solution. It looks like your DNS service is not working correctly as that should have been able to resolve to the host name. You may wanna talk to the admins as they might like to know that.

---

