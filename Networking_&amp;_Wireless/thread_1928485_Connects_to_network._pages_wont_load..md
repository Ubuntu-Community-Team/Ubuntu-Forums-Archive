---
title: "Connects to network. pages wont load."
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by Chasmo on 2012-02-20
I changed my wireless card and it finds my network and has a good connection but the browsers wont load the pages. I am sure there is a simple fix but I can't find it. Here is the content of the page that comes up....


This webpage is not available
The server at [www.google.com](www.google.com) can't be found, because the DNS lookup failed. DNS is the network service that translates a website's name to its Internet address. This error is most often caused by having no connection to the Internet or a misconfigured network. It can also be caused by an unresponsive DNS server or a firewall preventing Chromium from accessing the network.
Here are some suggestions:
Reload this webpage later.
Check your Internet connection. Restart any router, modem, or other network devices you may be using.
Check your DNS settings. Contact your network administrator if you're not sure what this means.
Try disabling network prediction by following these steps: Go to the wrench menu > Preferences > Under the Hood and deselect "Predict network actions to improve page load performance." If this does not resolve the issue, we recommend selecting this option again for improved performance.
Add Chromium as a permitted program in your firewall's or antivirus software's settings. If it is already a permitted program, try deleting it from the list of permitted programs and adding it again.
If you use a proxy server, check your proxy settings or contact your network administrator to make sure the proxy server is working. If you don't believe you should be using a proxy server, adjust your proxy settings: Go to the wrench menu > Preferences > Under the Hood > Change Proxy Settings... and make sure your configuration is set to "no proxy" or "direct."
Error 105 (net::ERR_NAME_NOT_RESOLVED): Unable to resolve the server's DNS address.

---

### Post by Lisiano on 2012-02-20
Seems that you either manually set a DNS server or your default one (router/ISP) is failing. Try opening a terminal (Ctrl+Alt+T) and typing this ```
ping google.com
```If it pings, then it's Chromium acting up, if not, your system wide DNS settings are wrong/broken. If the later, go to the network manager (The wifi indicator -> Settings -> Wireless -> Edit -> IPv4 -> DNS and input 8.8.8.8 first and your router IP after, seperated by a comma so if your router IP is 192.168.1.1then it should look like this ```
8.8.8.8, 192.168.1.1
```

8.8.8.8 is the public Google DNS.

---

### Post by Chasmo on 2012-02-20
I am not sure what you mean by if it pings. I put in the code "ping google.com" and terminal is still outputting as I write.

---

### Post by Chasmo on 2012-02-20
when I click on the wifi Icon my network name shows up twice, one is set to auto connect and it does not work. when I clicked on the other it works. can I remove the one that is not working?

---

### Post by Chasmo on 2012-02-20
I found that my network was listed twice. I went in to edit vpn connections and deleted one of them. then I reloaded the page and it worked. then I rebooted the computer and it loaded the right network and it works fine. Solved.

---

### Post by Lisiano on 2012-02-20
Ah, sorry I wasn't that much of help to you.
"Pings" means you get a reply from a ping and not a Timeout. For example
```
lisiano@Lisiano-Ubuntu:~$ ping google.com
PING google.com (173.194.67.113) 56(84) bytes of data.
64 bytes from wi-in-f113.1e100.net (173.194.67.113): icmp_req=1 ttl=49 time=42.3 ms
^C
--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 42.379/42.379/42.379/0.000 ms
```
This is what would've happened if you couldn't ping Google.```
lisiano@Lisiano-Ubuntu:~$ ping google.com
ping: unknown host google.com
```

Also to stop a program executed in a terminal you need to press Ctrl+C. Sorry that I forgot to mention that.


Anyway, glad it got resolved.

---

### Post by Chasmo on 2012-02-20
Thanks for your help. You got me to looking and I happened to find the right thing.

---

