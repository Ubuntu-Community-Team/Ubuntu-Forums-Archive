---
title: "Wireless card activated, but no internet"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by evandec on 2006-05-31
I went through all the stuff on the ubuntu trouble shooting guid to no avail. 

I instaled my wireless card and got it going fine. It is activated and can see a wireless network with good (85/90%) strength. However when I open firefox and try to go to a website all i get is 

[wuote] looking for nyt.com [/quote}

where nyt.com can be any website and it never downloads the website.

Whats up?

---

### Post by jml on 2006-05-31
If Ubuntu lists your wireless card and the card "sees" the networks that means that you do not have a hardware issue, but a software, (usually a configuration) issue.  As a first attempt, disable all encryption on the wireless access point and your laptop.  Reboot the laptop and see if you can connect.  If you can, then its probably a problem with your encryption settings.  First off, Ubuntu does not support WPA PSK encryption.  If you need that type of encryption, you will need to download, install and configure an application called wpa_supplicant.  I think its located in the Universe repository.  Ubuntu does support WEP.

If you still can't connect, try deactivating the wired ethernet connection, or the modem connection, then reboot and try again.  Linux distros don't handle multiple active network devises very well.  Hope this helps.

Joe

---

### Post by Nonno Bassotto on 2006-05-31
Can you browse the net otherwise, say with a lan cable?
Often this kind of problem is related to lack of DNS service. Waht am I talking about? Usually we refer to sites using the URLs (like [www.google.com)](www.google.com)), which are understandable to humans. But internet is organized differently: every server is identified by his IP address (something like 192.134.252.110). So when you type [www.google.com](www.google.com) in your browser, it sends a request to a server to translate this into a sequence of numbers. This server is called a DNS (Domain Name Service) server. You have to have the IP address of one available in order to browse the net.
Usually your provider will have some servers. You can easily find some DNS server address by searching something like "your_provider dns server" on google.
To check if the problem is what I think, open System--> Administration--> Network Tools, go the tab Ping, put one of this addresses you found and click ok. If the test works, then the problem is probably what I said (if it doesn't say some packet are lost, then it worked).
Now for the solution (if this is the case). You have to set this address. Open System--> Administration--> Network, go the DNS tab and add one or more of the addresses you have found. This way you should be able to browse. It is possible that your router (if you have one) will replace the address you set at fixed time intervals. In this case you have to set the DNS server address in your router (usually routers are configurable by a browser interface).
Hope this helps you.

---

### Post by JackAcid on 2006-06-01
I am having a similar problem. Ubuntu sees my wireless card and I can access SOME internet sites. for example I can listen to interner radio and some of my bookmarks in firefox come up with no problem, but I cannot get to google, gmail, yahoo. other websites come up but only after several minutes. this seems to affect evolution since I am trying to connect to my gmail account and the weather widgets in the tool bar.
I should mention this is the qwest wireless modem (actiontec) at my farm. I have had no such trouble at my main isp (verizon) using my netgear router. nor did I have trouble using my brothers wireless (sorry, don't know his ISP).
does anybody have a clue what is happening. I would do a google search, but the connection times out or I get a message saying something like "www.google.com could not be found" 

Help????

Update!
I started reading other posts about  slow wireless and different fixes for the problems. I tried editing my /etc/resolv.conf file and commented out the router ip and everything now works, however I have tried editing this file before and when I shut down my laptop, or rather when I restart my laptop the old broken configuration is what I get.
Is there any way to make the edits to the resolv.conf "permanent"?

Thanks!

---

