---
title: "Configuring squid from webmin"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by shekeine on 2009-07-25
:confused:Hello Everyone, i am a new Linux user and have had a lot of difficulty configuring squid for my cybercafe where am forced to use windows on the server owing to the ease of setting up proxy services on it, all the clients run jaunty.I have windows xp alongside ubuntu 9.04 on the server so am trying to set up squid so that i can get rid of windows from it.I tried editing squid.conf (using the help section on squid.org) but i kept messing up and getting error messages so i got webmin and still i have not had any success. Through webmin i have been trying to configure squid as per the instructions in the "Book of webmin here;([http://swelltech.com/support/pdfs/webminguide.pdf](http://swelltech.com/support/pdfs/webminguide.pdf))
in the "squid proxy" section.Summarily I input the client ip range 192.168.0.1-192.168.0.255 in the new acl created under "client adress option"as instructed.The port number is set to 3128(default) and set to allow all ip`s requests forwarded to it.I then added a Proxy restriction defining the acl I had created with the above ip range and moved it above the "Deny all" line,and applied the changes(accepted without any fuss) then restarted squid,it restarts perfectly. I then set the browser proxy settings on the clients accordingly;(http proxy=192.168.0.1(server) while port=3128-default) for all protocols.The subnet mask on all computers is set to;255.255.255.0(in the gnome network manager) However when i try to connect from any of the clients i get this;could not connect to proxy server;access is denied;opera browser) while in fire fox i get;firefox is configured to use a proxy server that is refusing connections...etc)
And thats where I have been stuck the entire week...someone please help me out here...

---

### Post by ericab on 2009-07-25
set the default policy's allowed clients for web access to allow for the most common clients.

in firefox, you need to *un-check* SOCKS proxy. squid isnt a socks proxy.

---

### Post by shekeine on 2009-07-30
Well uninstalled squid, deleted squid.conf and started all over again.This time though i used the 10.0.0.1-10.0.0.8 ip range instead of 192.168.0.1-255.I set proxy port to 6588,this works on windows for the same ip range.i then unchecked the socks proxy thing from Firefox on the clients...but am still stuck.When i launch firefox, say to access Google, i don't get "access denied" like before.the page starts loading;"connecting to www.google.co.ke" but nothing comes through at all.Eventually Firefox returns;(could not locate remote server).Now what could be the problem here?
   Opera also returns the same message,not access denied like before(by the way whats the equivalent of uncheckingsocks proxy in opera?).My internet connection is fine though..the clients connect just ok when the server is on windows and pages load fine..i can also access the internet from the server so its not a connectivity issue.

---

