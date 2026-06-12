---
title: "No internet access through the school proxy only for ubuntu users"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by thusi87 on 2011-06-11
I have been using ubuntu for my college work for some time, and suddenly last week for ubuntu users in a specific Department/building lost the ability to connect to the internet through the school proxy.

The problem seems to have effected only our department/building and the network guys are offering no real help since there are no problems connecting to internet from ubuntu in any other location than our building. 

What is so annoying is even its the same computer we have internet if we use Windows but no internet for ubuntu. 

When using ubuntu the DHCP server automatically assigns IP's just as before, and we can reach the Default gateway using ping, but cant reach the proxy server. When we ping the proxy we get a message saying it refuses a connection. When using firefox or chrome we get the same message when we try to browse <proxy server not available>. 

Please do share any thing of you can think of a reason or a way to handle this. The network guys says that the only change they did recently is to activate ipv6. But i fail to see how this can become a problem.

---

### Post by superduperlinuxperson on 2011-06-12
look at your proxy settings (search for it)

---

### Post by thusi87 on 2011-06-13
Proxy settings are fine. Even if the proxy is not set according to my knowledge we should be able to ping the proxy.

---

### Post by superduperlinuxperson on 2011-06-13
very strange

---

### Post by josephmills on 2011-06-13
try using a random macaddress and can you log into the routers? what is going on with wireshark is it picking up beacon frames?

---

### Post by SeijiSensei on 2011-06-13
Do you get the same IP address using both Windows and Linux?  In Windows, type "ipconfig /all" in a command prompt to see your IP information; in Linux use "ifconfig" at the prompt.

---

### Post by thusi87 on 2011-06-13
> **josephmills said:**
> try using a random macaddress and can you log into the routers? what is going on with wireshark is it picking up beacon frames?

Will you be kind to explain what you mean by the first statement? There is a place to put a "Device Mac address" and a "cloned mac address" under network manager->edit Connections-> Auto Ethernet . Are we supposed to put our device mac address there? currently there is nothing in the spaces. 

I will try to learn about wireshark and see if i can analyze and put a result here by tomorrow. 

thanks. :)

---

### Post by thusi87 on 2011-06-13
> **SeijiSensei said:**
> Do you get the same IP address using both Windows and Linux?  In Windows, type "ipconfig /all" in a command prompt to see your IP information; in Linux use "ifconfig" at the prompt.

actually we can assign the same address if we want to. By the way there is another shocking discovery. I can ping the default gateway, but when I ping the proxy server there is a error from the default gateway saying that the destination is unreachable. 

Please do help.. thanks.

---

### Post by thusi87 on 2011-06-13
[http://dl.dropbox.com/u/8279462/capture](http://dl.dropbox.com/u/8279462/capture)

I have done a ping to the proxy and captured the packets as you suggested. Please be kind enough to go through the file. Thanks.

---

