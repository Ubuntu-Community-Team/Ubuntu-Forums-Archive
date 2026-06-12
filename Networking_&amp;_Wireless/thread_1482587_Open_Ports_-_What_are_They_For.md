---
title: "Open Ports - What are They For"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by Jason Cook on 2010-05-13
I have a few open ports and am wondering what they are for. The ports are: 631, 5800, 5900, 17500, 36801, 37950, 39554, 46318, 53910.

I have some info on some of the ports.

631: CUPS Administration
5800: in web browser I see "ISD 001.000" in plain text
5900: in web browser I see "RFB 003.008" in plain text
17500: 
36801: in web browser it askes for authentication, after cancelling "since I don't know passwords" it says "{"error":"unauthorized","reason":"Authentication required."}"
37950: in web browser it askes for authentication, after cancelling "since I don't know passwords" it says "{"error":"unauthorized","reason":"Authentication required."}"
39554: 
46318: 
53910:

---

### Post by arkham on 2010-05-13
If these things are on "standard" or at least recognized ports you can find them in /etc/services

For example:

```
cat /etc/services | grep 5900
vnc-server      5900/tcp    # VNC Server
vnc-server      5900/udp    # VNC Server

```
That should solve one of the mysteries for you.  In addition to that, lsof -i can be helpful to figure out which process owns the open listening port.  Another example (my machine is listening on various ports, here's a snippet):

```
sudo lsof -i | grep LISTEN

COMMAND    PID           USER   FD   TYPE     DEVICE SIZE/OFF   NODE NAME

httpd       27           root    3u  IPv6 0x08702940      0t0    TCP *:http (LISTEN)
httpd      109           _www    3u  IPv6 0x08702940      0t0    TCP *:http (LISTEN)
```

If it is a known port you get :http instead of 80 etc.

After that it's Google time :)

---

