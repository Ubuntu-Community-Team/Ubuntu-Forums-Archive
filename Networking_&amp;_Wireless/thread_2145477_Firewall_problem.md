---
title: "Firewall problem?"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by psionman on 2013-05-15
Hi

I'm trying to install [BubbleUpNp]("http://www.bubblesoftapps.com/bubbleupnpserver/") server on Ububtu 12.04

I've installed and started it but I get the message

[COLOR="#FF0000"]HTTP: ERROR: cannot reach external server to perform test: java.net.SocketTimeoutException: Read timed out[/COLOR]

The help suggests:

If "Server is reachable from Internet" is displayed, everything is fine and BubbleUPnP Server is ready to use for remote access.

Otherwise something is preventing the Internet to connect on the HTTP or HTTPS port. This will likely be a NAT or firewall issue. For example, if the public HTTP port is 58050 and the LAN IP Address displayed is 192.168.1.10

    Add a rule on your router to redirect connection on TCP port 58050 to LAN IP Address 192.168.1.10 on port 58050. You must use the same port for the redirection
    Add a rule on your firewall to allow incoming traffic on TCP port 58050 on the 192.168.1.10 machine
    For HTTPS access repeat the 2 steps above with the HTTPS port (58051 by default)

IMPORTANT: if you use HTTPS access, the HTTP port must still be open as it is still used for media streaming reque

 

How do I set about doing this?

---

### Post by psionman on 2013-05-16
Sorted thanks

---

