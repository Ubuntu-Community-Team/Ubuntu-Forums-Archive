---
title: "DNS server"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-07-17
I'm new for DNS server set up. I want to create DNS server in locally, because i have web server in my local machine, I allow local network user to access that machine using web server name(url) 
Please provide reference site or tutorial 

Thank you..

---

### Post by jasonsjunk on 2009-07-17
The easist way I have found to set up BIND is to use Webmin.  

A good how-to article can be found here.  [http://rimuhosting.com/support/bindviawebmin.jsp](http://rimuhosting.com/support/bindviawebmin.jsp)

Are you sure you need to run a DNS server?  If you have a FQDN (fully qualified domain name) then you can just use the DNS server from whoever you got your domain name through (GoDaddy for example).  The only reason for a home user to run a DNS server is if you have internal only domains that you only want accessible to your internal users.

---

### Post by mthalis on 2009-07-17
My web server should run locally and local users should have access that server using name without server ip that why i tink set up local dns server. Please any suggestion.

---

