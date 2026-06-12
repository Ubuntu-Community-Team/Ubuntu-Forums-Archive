---
title: "setting up ssh"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by nolsen01 on 2009-03-03
Hello all!

I am not a networking wiz (yet) so this will (hopefully) be pretty simple.

I set up SSH on my ubuntu desktop so that I can connect to it using my laptop from school.

I am using verizon FIOS and my desktop is connected wirelessly to a router that connects me to the internet. How can I connect to my desktop using SSH from outside the wireless network?

---

### Post by yawnzzzz on 2009-03-03
Here's kind of an overview.

When you're connected to the internet using a router, then the router is really the only thing that has an ip address to the outside world. So you need to determine that ip address.

When you're connected to your router, click this link:
[http://www.ip-adress.com/](http://www.ip-adress.com/)

It will tell you your 'public' IP address. This is the same for every computer connected to your router, and this is the IP address that you'll need to SSH into when you're not at home.

When you SSH in to that public IP address, your router will be confused on what computer on your network that you want to connect to. So, how this is handled is thru port forwarding. For example with SSH, the default port is 22.  You need to tell your router to connect your SSH (port 22) client to your desktop.

To set this up, you need to connect to your router's configuration settings. You normally do this by typing the IP Address of your router into a webbrowser. Once you've connected, look for an area called port forwarding. It will likely ask for a few bits of information.  A name (ex. SSH), port range (ex. 22-22), 'private' ip address of your desktop (ex. 192.168.1.100), and possibly a checkbox to enable/disable that should be enabled.

The 'private' ip address is probably the one you're using to connect when you're on your own network.

---

### Post by terazen on 2009-03-03
Also if your public ip changes then you'll want to use dynamic dns.

---

