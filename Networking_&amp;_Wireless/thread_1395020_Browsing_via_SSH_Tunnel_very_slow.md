---
title: "Browsing via SSH Tunnel very slow"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by f00fyf00f3r on 2010-01-31
Browsing via SSH Tunnel very slow

When browsing in firefox at work via proxy through ssh on my 8.04 server the speed is near dial up. I have compression enabled, tried restarting ssh, and rebooting the server but it remains so sluggish. At home the connection is quick but the speed is lost in translation once I ssh in. I also tried adding "UseDNS no" to the ssh config but that did not help with the slow login or any other speed issues. Just wondering if anyone has any ideas why the speed degrades so badly, browsing on the work network is pretty fast.

---

### Post by falconindy on 2010-01-31
Because you're limited by the crippled upload of your server at home. If your ISP gives you a 256kb upload, that's the absolute maximum you'll ever see over the proxy.

---

### Post by f00fyf00f3r on 2010-02-06
Hmm, I've done faster up speed than that over ftp transfers, etc.

[[IMG]http://www.speedtest.net/result/708119326.png[/IMG]](http://www.speedtest.net)

---

### Post by calvolson on 2010-12-29
This appears to be the same type of issue I'm having. 
I'm connecting from work to one of my home machines currently running windows server 2008 with mobassh installed on it. The ssh tunnel speeds are just fine. 
I'm trying to make the switch to Ubuntu. On a separate machine I've got 10.10 installed and am able to connect, but the speed is painfully slow.  I've copied a friend's ssh_config and sshd_config files, who does the same thing without any speed issues, to see if I had something in there that was messing it up, but it's still slow. The 2k8 box continues to work fine.  Any thoughts? This linux noob will appreciate any feedback.

---

### Post by Lividity on 2011-02-09
ok I had the same issue it was very anonying. I actually switched to chrome for a short time until I could get firefox running faster. The issue is with the firefox settings. In your address bar type "about:config" this will allow you to change your firefox settings. 

network.http.max-connections;42
network.http.max-connections-per-server;0
network.http.max-persistent-connections-per-proxy;0
network.http.max-persistent-connections-per-server;0
network.http.pipelining;true
network.http.pipelining.maxrequests;0
network.http.pipelining.ssl;true
network.http.proxy.pipelining;true

Change your preferences and you will see a tremendous jump in speed. I can't tell the difference between routing the traffic through my home line and the proxy. The speed is greatly improved. Enjoy.

---

### Post by AintJoe on 2011-05-11
> **Lividity said:**
> ok I had the same issue it was very anonying. I actually switched to chrome for a short time until I could get firefox running faster. The issue is with the firefox settings. In your address bar type "about:config" this will allow you to change your firefox settings. 

network.http.max-connections;42
network.http.max-connections-per-server;0
network.http.max-persistent-connections-per-proxy;0
network.http.max-persistent-connections-per-server;0
network.http.pipelining;true
network.http.pipelining.maxrequests;0
network.http.pipelining.ssl;true
network.http.proxy.pipelining;true

Change your preferences and you will see a tremendous jump in speed. I can't tell the difference between routing the traffic through my home line and the proxy. The speed is greatly improved. Enjoy.

I just had this problem in both Chrome and Firefox. These tweaks fixed Firefox, but I haven't figure out how to fix Chrome yet.

---

