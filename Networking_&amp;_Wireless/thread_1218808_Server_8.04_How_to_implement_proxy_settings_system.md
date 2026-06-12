---
title: "Server 8.04 How to implement proxy settings system wide from command line"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by wayne0308 on 2009-07-21
Hi,

I was hoping you could help me with this. I have a system with ubuntu server 8.04 64bit installed for use as a file server. I'm in a university and there is a proxy server. 

There's no GUI installed (I'm still learning about linux) so I was wondering how do I input system wide proxy settings through the command line?

 Relevant info: 
I have root access. 
I was not the one who installed the operating system and the person who installed it didn't input the proxy settings during the installation. 
All other network settings are correct and we're set via DHCP.
I've looked around but all posts refer to inputting the settings on a user by user basis by putting the following at the bottom of the bash.bashrc file:
```
export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/
```
Any help would be much appreciated. Thanks!

---

