---
title: "Need help using a pre-configured proxy file in ubuntu"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by ObiWanJakobi on 2010-02-13
In order to connect to the internet on my university, you must have a certain proxy set up. That is why they provide a pre-configured proxy file. I really need to know how to set this file up to work with ubuntu.
> function FindProxyForURL(url, host) 
{ 
if (isInNet(myIpAddress(), "10.2.0.0", "255.255.0.0")) 
return "PROXY 10.2.0.25:8080"; 
 
else 
return "DIRECT"; 
}
 
-this is the file.
 
Also if anyone could tell what I should enter into a manual proxy setup, I'd appreciate it. From what I understand this line
 
if (isInNet(myIpAddress(), "10.2.0.0", "255.255.0.0")) 
return "PROXY 10.2.0.25:8080"; 
 
means that if the ip-adress of this computer is connection to the specific network on my university, it must return to this proxy. And 10.2.0.25 is the proxy ip, while 8080 is the desired port number??

---

