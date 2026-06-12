---
title: "Setup recordings remotely from anywhere?"
date: 2010-08-15
forum: Mythbuntu
---

### Post by agentsmith23 on 2010-08-15
I am not sure if this is possible so hopefully someone here can inform me. I know with certain subscription DVR services you can remotely setup recordings. Say for example you are at work and you realize you forgot to setup a recording, is there a way to login remotely from any location to your own backend and schedule a recording? I realize you would more than likely need your networks public IP and also have your network configuredso you can access the individual machine also.

Is this possible?

---

### Post by SoFl W on 2010-08-15
Yes, with the correct skills it is possible.

---

### Post by uncle hammy on 2010-08-15
> **SoFl W said:**
> Yes, with the correct skills it is possible.
In useful terms...

You'd have to use Mythweb.  Assuming you have a public address to your home network (dyndns for example), the simple way is to forward port 80 to your myth backend machine.  Jut be sure to use the Mythbuntu Control Center to set security up for Mythweb.

You can also use ssh tunneling if you don't want to expose your Mythweb completely publicly.

---

### Post by agentsmith23 on 2010-08-17
ok so I have been messing around with mythtv for the last few days and I just can't seem to get remote access,  port 80 isn't blocked from what I get back using a port scanner, i have tried setting up mythweb from inside of mythbuntu control center and from the terminal, when installed from the terminal I can only access it from 127.0.1.1/mythweb, I get this message at the end of the install in the terminal:

"apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

when installed from the control center I can get to it by accessing 192.168.2.9/mythweb

what do I need to do to get access remotely?

---

### Post by larsolav on 2010-08-17
How is your internet setup? Do you have a modem (DSL or cable etc) and a router, or a combo modem/router? I have the latter from 2Wire.
This is what I did to access Mythweb remotely.
First I set up Mythweb password in the control center. Then I had to go to the 2Wire setup and direct port 80 to my mythbox. In the 2Wire setup I also could see my ISP provided IP number which I now use to access mythweb remotely (my ISP changes this number once in a while, so I need to re-check ever so often...)

Cheers!

---

### Post by nickrout on 2010-08-18
I would actually recommend ssh tunnelling rather than opening mythweb to the internet. Security can be breached and the last thing you want is some web searching spider to click on all your "delete" links!

But if you want to access it from the web without ssh tunnelling you can simply get your modem/router to forward port 80 to your backend. How you do that varies by router, but [http://portforward.com/](http://portforward.com/) has detailed instructions for many routers.

---

### Post by agentsmith23 on 2010-08-20
I finally got it resolved. For some reason I couldn't get the port forwarding to work across the two differnt subnets within my home network. So I switched my repeater to a bridged repeater so it could be on the same subnet as my main router and now everything works great!

---

### Post by nickrout on 2010-08-20
Do make sure you have a REAL good password.

---

### Post by twin--turbo on 2010-08-22
Don't port forward pot 80, think of an arbitrary port number between 10000 and 65535. then port forward that to port 80 on the server. 

That significantly reduces the amount of unwanted traffic.

TT

---

### Post by dad311 on 2010-08-26
For security, don't forward or open any ports on your home router unless absolutely necessary. Instead, setup a VPN using something like Neorouter.

Checkout Neorouter.com for install instructions.  Neorouter supports windows, mac and linux.


  Product Overview

NeoRouter is the ideal Remote Access and VPN solution for small businesses and home. It helps you manage and connect to all your computers from anywhere. It gracefully integrates Remote Access, File Sharing, Virtual Private Network, User and Access Management.

Many small businesses or homes have high-speed internet and multiple computers, and users are facing challenges like remote access, directory management and network security. To solve similar problems at large enterprises, skilled administrators can deploy very expensive and complex tools like VPN, domain controller and corporate firewall. But small business or home users do not have the right tools that fit their needs.

Our mission is to provide low-cost zero-configuration networking solutions for small businesses and homes. This is why we have built NeoRouter.

---

### Post by LowSky on 2010-08-26
I use teamviewer and mythweb. Its a great combo.

---

