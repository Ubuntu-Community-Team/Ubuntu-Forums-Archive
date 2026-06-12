---
title: "&quot;404 Not Found&quot; error messages on developer.nokia.com website"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by akhil520c on 2011-08-13
Hi,

I have been facing this issue for months now, just didn't get down to do anything about it till now.

When I try accessing the site [http://developer.nokia.com](http://developer.nokia.com), Firefox automatically changes the address to [http://**www](http://**www)**.developer.nokia.com and I get the Chinese version of the website, and am not able to change it back to English, using the drop-down option on the site itself.

Now, this may sound like an issue with the site, but let me give you some background info, and what steps I have tried:

1. On the terminal, when I ping developer.nokia.com, I get the IP address of the site ( 62.61.69.88 ) and using this IP address, the English version of the site loads on Firefox. The problem is, if I try navigating through the links on the site, I get the "404 Not Found" error message (eg: "The requested URL /Resources/Library/Symbian_Design_Guidelines/ was not found on this server") because many links have "**www**.developer.nokia.com" prefixed in them.

2. When I ping [www.developer.nokia.com]("http://www.developer.nokia.com"), I get the response from [www.developer.nokia.com.cn]("http://www.developer.nokia.com.cn") (203.212.5.44), which explains why the Chinese version of the site loads.

3. I disabled the DNS cache on Firefox ( version 3.6.18 )by adding the following integer entries to the about:config page:

a. network.dnsCacheExpiration=0
b. network.dnsCacheEntries=0

4. I flushed the DNS cache on the OS (Ubuntu 10.04 Lucid Lynx) using the command:

```
sudo /etc/init.d/dns-clean start
```5. Retarted the system.

Still face the same issue.

Is there any way to statically tell Ubuntu/Firefox to resolve all instances of [www.developer.nokia.com]("http://www.developer.nokia.com") to the fixed IP ( 62.61.69.88 ), or is there any other better way to fix this issue?

This issue doesn't occur when I use a different ISP for my internet connection (sharing my mobile phone's internet connection). I changed the DNS server IP addresses in the router to the OpenDNS IPs, but this issue persists.

Any help would be appreciated :-)

Thanks
akhil520c

---

### Post by akhil520c on 2011-08-17
Hi all,

Just found on the discussion forums on developer.nokia.com that this is an issue that's being caused by something at Nokia's end..something to do with export compliance/restrictions. 

[http://www.developer.nokia.com/Community/Discussion/showthread.php?87731-Download-Failure-of-Series-60-3rd-SDK&highlight=country+group](http://www.developer.nokia.com/Community/Discussion/showthread.php?87731-Download-Failure-of-Series-60-3rd-SDK&highlight=country+group)

Sorry for posting an issue that was, in this regard, not relevant, and hope it didn't inconvenience anyone.

Thanks all,
akhil520c

---

