---
title: "Rhythmbox + DAAP"
date: 2010-12-08
forum: Multimedia Software
---

### Post by WG- on 2010-12-08
I have a QNAP TS-410, homeserver, I have DAAP enabled at this server and the router forwards the correct port, 3689. 

Now since a while Rhythmbox can't connect anymore (at school or home) to my server by DAAP. When I add a DAAP share: "<My IP>:3689" or the local address (when I'm home) "10.0.0.4:3689" Rhythmbox tells it can't find the host. 

This however strange because when I'm home Rhythmbox auto-detects the DAAP from the server.

Anyone has an idea what is happening and why I can't connect to my server with DAAP by entering my own IP or local IP address but still can find the DAAP share automatically.

---

### Post by WG- on 2010-12-08
I (think I) found out the problem.

In the past I had to type the host:port when connecting to a DAAP share within Rhythmbox. Now I figured out that when doing that it doesn't work. However when you only fill in the host Rhythmbox connects to the DAAP share.

Most likely Rhythmbox had hence a update in which they just paste the port of DAAP (3689) now behind the host so you don't have to type it in anymore.

---

