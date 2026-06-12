---
title: "Cant start broadband connection"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by drunkenbrawler on 2010-02-11
Hello everyone,

I've been using Ubuntu/Kubuntu for some time now but i dont know any technical details. I am using Kubuntu 9.10 with Ubuntu desktop installed. The problem I am facing started a day ago.

I have used 
```
sudo pppoeconf
```
to setup my broadband internet connection. I have enabled it to setup connection at startup. Everything was working fine until from yesterday, the connection is not established. When I start the Firefox, I get message saying
> Server not Found

I tried using 
```
sudo pppoeconf
```
again but nothing happens.

My internet connection works good in Windows. 

Can anyone please help... Any help will bw greatly appreciated

---

### Post by kyletstrand on 2010-02-12
Are you connecting wirelessly or wired?  Is your IP static or DHCP? 

```
:~$ ifconfig
```

Post the results you are getting from this command as it will give an indication if Ubuntu's drivers are recognizing the modem or if they have any kind of connection.

Go to System > Preferences > Network Connections and check to see if the IPv4 settings are configured for DHCP for either ethernet or wireless connections, whatever you are using.

---

