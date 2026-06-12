---
title: "is it possible to assigin to ip addresses to my computer? just to use them internally"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by legolas_w on 2009-08-04
Hi
Thank you for reading my post.
I am developing a server application for a client and thier server's ip address is 192.168.0.107. my computer IP address is not the same as their server ip address and eveytime I want to move the application to server and test it I must change the ip address to make it work.

Is there anyway like using the hosts file to assign two ip address to my computer? for example when I am trying to connect to 192.168.0.107 it connect me to 127.0.0.1?

Thanks

---

### Post by lyghtkruz on 2009-08-04
While it is possible to do what you are asking, I would advise against it as it may cause you to not be able to access your network or the Internet if the router/gateway is on a different subnet. 

My recommendation would be to develop the application with a configuration textbox or a config file which would hold the IP address of the server.

You have to keep in mind that if the server's IP address ever changes or they have to change servers all together, it would no longer be able to connect as it is always trying to connect to 192.168.0.7.

---

