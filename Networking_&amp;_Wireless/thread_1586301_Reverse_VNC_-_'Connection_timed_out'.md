---
title: "Reverse VNC - 'Connection timed out'"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by JaJaBinks on 2010-10-01
I am trying to establish a reverse VNC connection between my desktop PC (client), and a laptop (server). Both are running Ubuntu 10.04.

I am following [https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC") , and have installed vnc4viewer on PC, and x11vnc on laptop.
PC router is configured to forward ports 5500, 5800, 5900
following is executed on pc ```
vncviewer -listen 
``` responds with; **"Listening on port 5500"**
my public ip is determined from [http://www.whatismyip.com/]("http://www.whatismyip.com/") and the following executed on laptop ```
x11vnc -connect *mypublicip*
``` The response from this is
**"Making connection to client on host** *mypublicip* **port 5500"**, then
**"connection failed: connection time out**
**reverse_connect :** *mypublicip*** failed"**
:confused:
Any help with this would be appreciated.
N.B the laptop (server) is communicating with the internet via a Telstra mobile broadband device, hence the need for a _reverse_ vnc connection.

Thanks

---

### Post by krunge on 2010-10-01
On the laptop what do you get if you try to connect to, say, google:

```

x11vnc -connect www.google.com:80
...
01/10/2010 21:52:36 Making connection to client on host www.google.com port 80
01/10/2010 21:52:36   other clients:
01/10/2010 21:52:36 incr accepted_client=1 for 72.14.204.103:80  sock=5
01/10/2010 21:52:36 reverse_connect: www.google.com:80/72.14.204.103 OK
01/10/2010 21:52:36 reverse_connect: turning on auth for 72.14.204.103
01/10/2010 21:52:36 rfbProcessClientProtocolVersion: not a valid RFB client: HTTP/1.0 400

```
Does it show it connecting for you? (as the above does)

What if you use a port different from 80?  Does port 5500 and others get through? (you can use the above to test, just point it to a known server.)

Can you turn on logging on your router to see if there are connection attempts on port 5500?

---

### Post by JaJaBinks on 2010-10-01
Thank you.
Yes, I can connect to google and other servers through port 80, but not 5500
not sure how to turn on logging in router, but will have look.

---

