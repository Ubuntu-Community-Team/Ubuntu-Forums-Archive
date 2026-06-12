---
title: "configure forwarded port"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by nadeendra on 2011-08-09
I have port forwarded Router using windows for local ip 192.168.1.10 and now I use Ubuntu. How can configure this forwarded port to use in Deluge torrent client  ?

---

### Post by Herman on 2011-08-09
:D I need to break up your question into two parts.

For the first part, if you are asking how you can access your router in Ubuntu I can help.

1. Run this command to find out the internal  IP address of the router in your LAN,
```
netstat -nr
```Your router's internal IP should appear under the 'Gateway' column.

2. Copy your router's internal IP address and paste it into the address bar in firefox or whatever web browser you use and click the 'go' button or hit 'enter' or whatever.
It should take you to your router's control panel login screen.

3. Log in with your username , often 'admin' by default, (consult your router's documentation), and password. Make appropriate changes to your router's configuration, (again consult your router's documentation as much as possible).

For the second part of your question, I'm not sure if you really need port forwarding to use Deluge, do you? I looked quickly in [Deluge's website]("http://deluge-torrent.org/")  and Deluge's FAQ there and I did not see where they say you need to use  port forwarding to enable Deluge to work. Maybe I didn't read well  enough and missed it. If you're not sure you really need port forwarding it would be better to  go into your router's control panel and cancel the port forwarding you  had set up when you used Windows. 
I use BitTorrent through the Transmission BitTorrent Client and that does not require any port forwarding. Port forwarding opens ports in your router's firewall and exposes all computers inside your LAN to potential attacks from the internet. Perhaps I'm wrong, but I would be thinking twice about using a BitTorrent client that requires port forwarding.
Maybe somebody who has experience with Deluge can correct me. :)

---

### Post by haqking on 2011-08-09
> **nadeendra said:**
> I have port forwarded Router using windows for local ip 192.168.1.10 and now I use Ubuntu. How can configure this forwarded port to use in Deluge torrent client  ?

as long as your ubuntu machine is using the same ip then just make sure you torrent client is using the port you used when you used windows.

example: if you used port 12345 in azureus in windows and this was the port you forwarded on your router then set deluge to use port 12345.

it depends what you mean by you set your router to port forward, as this should mean you specified a port to forward to your ip address.

same in ubuntu or any other OS, you set the app port to be the one on the router unless it uses the default

read here to see if you really need to do it at all [http://portforward.com/help/pfprogression.htm](http://portforward.com/help/pfprogression.htm)

---

