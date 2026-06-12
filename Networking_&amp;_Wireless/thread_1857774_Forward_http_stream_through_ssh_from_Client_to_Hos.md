---
title: "Forward http stream through ssh from Client to Host."
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by DanRichNC on 2011-10-11
Hi,

This is my first new thread and I want to begin by thanking everyone who contributes here.  Many many questions that I've had have been answered by browsing these forums; however, I have not been able to find a solution to my current one.

I am using a desktop(Client) running 10.04 Lucid Lynx that is behind a hotel firewall. (me@desktop)  
I have a remote headless server(Host) also running 10.04. (you@server.dyndns-ip.com)

Both machines have ssh properly installed and I am able to connect to the server using a key.

The Client has a web-cam video feed that I am able to stream via http to port 8081.
I have confirmed this by opening a browser and navigating to 'http://localhost:8081/?action=stream'.

What I want to do is to be able to view my stream at 'http://server.dyndns-ip.com:8081/?action=stream' from anywhere.
This seems like a very trivial task, but it has stumped me.  I have tried many combinations of ssh port forwarding.  The server is behind a router that is directed to forward ports 22,80, and 8081.  This seems like a job for local port forwarding...but maybe I'm wrong.  My gut tells me this command should work, but it does not.  I have the camera streaming beforehand.

    me@desktop:~$ ssh -L 8081:localhost:8081 server.dyndns-ip.com
    bind: Address already in use
    channel_setup_fwd_listener: cannot listen to port: 8081
    Could not request local forwarding.
    Last login: Mon Oct 10 23:35:35 2011 from rrcs-24-172-71-10.midsouth.biz.rr.com
    you@server:~

If I execute the command first, I do not get a bind error; but then my streamer refuses to start up.
Does anyone have any ideas?

---

### Post by DanRichNC on 2011-10-13
Bump. 

Is there any information I can provide to help find a solution?

---

