---
title: "ssh question remote location"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Eremis on 2010-12-28
Hi everyone,

I have a quick ssh question...

I live in a college dorm but have a desktop at home  with ubuntu + ssh server...
When I visit home and I want to connect to my desktop I just type:

```

ssh 192.168.1.95 

```
192.168.1.95 --> my desktop on my dsl wireless router...

So I was wondering if I want to connect from my college dorm, what ip whould I have to connect to?

While being home I tried typing:
```

ssh myDesktopInternetIP 

```
myDesktopInternetIP --> Ip that I got from "whatismyip.com"

but doing this resulted in:
```

ssh: connect to host myDesktopInternetIP port 22: Connection refused

```

So how would I connect to my desktop from remote location?

---

### Post by spiky001 on 2010-12-28
I take it that at collage you are on there network, if so I doubt if they forward the ssh port22, the other thing is if they do forward the ssh port it might not be on port 22.
  You would have to ask the IT department about it.
  Sorry not much help.

---

### Post by frenzy_usa on 2010-12-28
There are three things you'll need to do for this to work.

1) Get a free host name from [dyndns.com]("http://www.dyndns.com") or [zoneedit.com]("http://www.zoneedit.com"). There are others but never checked into any of them.

2) Setup port forwarding on the router at your house. The steps to do this vary depending on who made your router.  You also might have to change settings on the cable/dsl modem supplied by your ISP.

4) Install a dynamic dns client to automatically update the ip address associated with your selected host name.

Once the above steps are completed, you can connect to your server at home from any where there is an Internet connection using the host name from step 1 instead of trying to remember a string of numbers.

---

### Post by Eremis on 2010-12-28
Solved a few of my own questions, just look at post below....

---

### Post by Eremis on 2010-12-28
I found where "port forwarding on my router is, I just dont know what to fill in the blanks (for ssh), I attached a picture...

---

### Post by frenzy_usa on 2010-12-28
Thanks for the screen shot. It's a big help.

**Service name:** Enter what ever helps you to remember why you setup this port forwarding rule
**Global Port Range:** The port you want to connect to from the internet
**Base Host Port:** The port that your ssh server is listening to
**Protocal:** Set to TCP

---

### Post by HiFiJive on 2010-12-28
What is your internet service provider? Do you have admin access to the router? 

Port forwarding basically tells your router what ip & port to forward inbound traffic.

---

### Post by Eremis on 2010-12-28
so for the range can i put 22-22 (since ssh in on 22)?

---

### Post by Eremis on 2010-12-28
so for ssh it should be like this:
Service name: my ssh server
Global Port Range: 22 - 22
Base Host Port: 22
Protocal: TCP

right?

I know its recommended to change the default 22 to something else...
Just one more question, will DynDNS interfere with security/online privacy, since I have a static name....?

---

### Post by Eremis on 2010-12-28
When I try to enable it it asks me a new question (attachment)
If I want dynamic or host...

When I choose host it asks me for host ip adress...
So I need dynamic?

---

### Post by frenzy_usa on 2010-12-28
Select host.  Host ip address is the address assigned to your ssh server.

---

### Post by Eremis on 2010-12-28
how do I get that address?

---

### Post by frenzy_usa on 2010-12-28
> **Eremis said:**
> how do I get that address?

It's the ip address you use to connect to the server when your at home.

I.E.
```
ssh 192.168.1.95
```

---

### Post by Eremis on 2010-12-28
picture attached

---

### Post by Eremis on 2010-12-28
still will not let me connect...
When I do:

ssh XXXXXXXXXX.dyndns-home.com

I get:
ssh: connect to host XXXXXXXXXX.dyndns-home.com port 22: Connection refused

XXXXXXXXXX being the name i set up with DynDNS

---

### Post by Eremis on 2010-12-28
I tried doing this on both my laptop and server(desktop)

---

### Post by frenzy_usa on 2010-12-28
In your last screenshot enter the ip address of the ssh server. I'm curious as to the options listed for 'Host Device'?

Is the dyndns client installed?

If not you will need to log into your account at dyndns.com and manually update the ip address that your ISP assigned to you (the wan ip of the modem).

Edit: I had to wait about an hour till I could login using my dyndns host name

---

### Post by Eremis on 2010-12-28
Here's step by step what I did, this might help you,

1. Went to my router ip
2. Configured port forwarding on port 22

(Shown in screenshots step by step)

3. Set up free DynDNS from [www.dyndns.com/](www.dyndns.com/)
4. tried to connecting to server (my desktop) with:
```

ssh thegiventomename

```

I get:
ssh: connect to host thegiventomename port 22: Connection refused


BTW linux-machine is my server, but i entered the ip anyways... it replaced the ip with linux-machine

---

### Post by Eremis on 2010-12-28
final screenshot...

---

### Post by Eremis on 2010-12-28
here's how my DynDNS page looks like...

---

### Post by Eremis on 2010-12-28
Do you think everything is right? Is it just a matter of time?

---

### Post by frenzy_usa on 2010-12-28
Everything looks right.  Can you tell if the ssh port forwarding rule has been enabled on the router?

---

### Post by Eremis on 2010-12-28
Not really just by viewing screenshot 6...

I also used nmap on my desktop with the results below:

```

desktop:~$ nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-12-28 20:55 EST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.17 seconds
desktop:~$ 


```

This means that 22 is opened, but is it forwarded?
How would I find out?

---

### Post by Eremis on 2010-12-28
if I use this website: [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)
and test port 22, it says that it's open, but once again does it mean it's forwarding?

---

### Post by Eremis on 2010-12-28
when I try to telnet on my laptop 
telnet WanAdressOfDesktop 22

It says unable to connect, connection refused

Also when I ping the DynDNS name on my laptop, I get a responce, so that means the domain name is working,
however the ssh is not...

---

### Post by frenzy_usa on 2010-12-28
> **Eremis said:**
> when I try to telnet on my laptop 
telnet WanAdressOfDesktop 22

It says unable to connect, connection refused...

Is the laptop on the same network as the ssh server? If it is, you won't be able to connect using the wan address.

Ask a friend to try from their house or ask a neighbor if you can use their computer to test.

---

### Post by Eremis on 2010-12-28
yes its on the same network, why cant I connect then, just curious....

ok I will try to get a friend to do it, and post back with results...

---

### Post by Eremis on 2010-12-28
yeah it works!!!!!!!!!!

Thanks a lot and have a great New Year!!!!

---

