---
title: "Access personal server outside of LAN"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by Altay_H on 2009-01-20
I cannot connect to a personal server I set up. What's interesting is that I can connect to it from the LAN using its non-local IP address. However, I cannot seem to connect to it from anywhere else.

Here's how my server is set up:
My entire home has a single Ethernet cable that goes directly into our router. Every device in the house is connected to the router. My server is on a static (local) IP address. The router is configured to forward the necessary ports to my server. So, when I tested out my connection, I was able to connect to my server from another computer on the same local area network using my non-local IP address (the IP address assigned to my router by my ISP). However, when I try to connect to my IP address from a computer that is not on my LAN using my non-local IP address, I receive an error like this:

```

10061 - Connection refused
The server you are attempting to access has refused the connection with the gateway. This usually results from trying to connect to a service that is inactive on the server.

```

I can connect to my server from my LAN using the router's IP address, but I can't connect to it from outside of my LAN using the router's IP address. Does anyone know what I'm doing wrong? Could there be some sort of setting I missed that's necessary to make my router "public?"

---

### Post by bgerlich on 2009-01-20
Is it an external IP for sure? Maybe your network is behind ISP's NAT ? Also, try some non standard port like from 50000-60000 range, maybe your ISP is filtering your connections ...

---

### Post by cariboo on 2009-01-20
Go to [canyouseeme]("http://www.canyouseeme.org/") and check to make sure your ISP isn't blocking any services.

Jim

---

### Post by Altay_H on 2009-01-22
> **cariboo907 said:**
> Go to [canyouseeme]("http://www.canyouseeme.org/") and check to make sure your ISP isn't blocking any services.

Jim
I tried that. It gave me an error stating the reason as "Connection timed out." Any idea whether that means it's blocked or not? I tried it from a different LAN (which shouldn't allow connections), and I received the error reason "Connection refused." Obviously my connection isn't working, but it's timing out rather than being refused.

Oh, by the way, I only tried port 22 which I'm trying to use to SSH into my server. I have it set up to require a private key. Would that affect the result?

---

### Post by superprash2003 on 2009-01-23
try this online port scanner to see if port 5900 and port 22 is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by Coreigh on 2009-01-23
Additionally the server may not accept connection *originating* from outside the LAN. I know you connected to it using the IP of the router, but your system still sees it as a request coming from inside the LAN. I am not sure about where this is configured. /etc/hosts.allow or /etc/hosts.deny ?
or the smb.conf ?

anyone?

---

### Post by Iowan on 2009-01-23
Something seems wrong if the local computers can access the server via router's external address... Maybe I'm just confused. :confused:

Or maybe the router is...

---

### Post by pillar2012 on 2009-01-26
I am having the same problem (connection refused).  Although I don't have the external router connection issues that the original poster is.

I feel like I have tried everything.  I have checked to make sure that sshd is running, that firewall is down, that I am port forwarding, checked the logs for sshd and the hosts.allow and hosts.deny, the log messages etc.

Maybe I overlooked something but when I try to connect externally (outside of my LAN) I am getting connection refused.  Locally I can connect fine and transfer files from my desktop to my laptop all the time.  Yet, I want to be able to ssh into my desktop when I am working at school etc.

Anyone have any other suggestions for me?  I feel completely stumped.
I have a DSL modem that is then connected to a wireless router.  I have gone into both of them and messed with a bunch of the configurations (portforwarding etc).

I really want to get this working.  Thanks in advance for anyone's suggestions.

---

### Post by pillar2012 on 2009-01-26
Okay I figured it out and am posting here for others.

My setup consisted of a modem (which also has router capabilities like port forwarding etc) which was connected to the dsl line one side and connected to my wireless router on the other.  To troubleshoot you should connect to the internet directly through your modem (disable your router).

Then, make sure you have dynamic dns enables and port forwarding setup and point to your machine's ip address.  Go to canyouseeme.org
and make sure that port 22 (or whatever port you are using) is available.

Once this is done you now know that your service (ssh) is available.  If this didn't work make sure you have disables your firewall as well.  If the firewall was the problem you will have to make sure you set it up so it can accept packets for your port.

Now...here is the tricky part.  On my wireless router it comes with DDNS as well.  I have mine disabled on the router.  Also, the modem will see the IP address of your router as something like 192.168.0.2 (or similar).  I have my port forwarding on the modem setup to forward to this IP.  Then in the router make sure you are forwarding port 22 to your server's IP.  Then you should be set to go.  If you try to connect from the outside while inside of your server's network it may not work.  To test, I logged into my school's network from home and then back into my network from school and it worked.

Hope this helps some people.

---

### Post by pillar2012 on 2009-01-26
Just to clarify my last post.  After I was done connecting to the internet directly via my modem I then hooked it back up to my router and continued troubleshotting from there since I knew the problem was happening between my modem and the router.  So basically, make sure that your modem and router are talking to each other properly.

---

### Post by Altay_H on 2009-03-01
Sorry I haven't posted back for a while, but since I only have physical access to my server during breaks I was unable to try out much. I recently was on break and attempted to get my server working.


> **superprash2003 said:**
> try this online port scanner to see if port 5900 and port 22 is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)
I called my ISP and found out that ports 1-1024 are blocked. I'm now using only ports above 1024 and port-scanner confirmed that they're open.


Right now I'd just like to get SSH working. I know it was working when I tried it back on my LAN. I'm using the same settings and the same port, but it's just hanging. It says it's reading the configuration data, then applying the options, then connecting. Then the connection times out.

If port-scanner tells me the port is open and I know I have the same settings that were working over my LAN, what could be wrong? Thanks for any help.



> **cariboo907 said:**
> Go to [canyouseeme]("http://www.canyouseeme.org/") and check to make sure your ISP isn't blocking any services.
I just tried this out again, and it told me "Connection refused" for every port I tried. I'm assuming this means my client computer cannot connect to itself, which it shouldn't be able to anyway. If it actually means my client computer cannot send information over these ports that might be a problem. Does anyone know?

---

