---
title: "how to change the local IP to be treated as remote"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by palexof on 2011-09-07
Hello


I would like to bypass my local IP to be treated as a remote one. For example my IP is 192.168.2.1. If I disconnect my network and execute ping 192.168.2.1 it would still return the packets successfully, because it doesn’t go outside local. This is undesired behaviour and I want to change it. 
  I can imagine one solution being setting up an external proxy e.g. in /etc/environment. Anyway I want to avoid setting up a proxy. Is there another alternative?  
Which config file do I have to change (I don't have gui) ?

   
  Thanks in Advance!

---

### Post by Beacon11 on 2011-09-07
Unfortunately the local network is just that-- a local network. It doesn't care whether or not the network is connected to another network (e.g. the internet). May I ask what you're trying to do?

---

### Post by haqking on 2011-09-07
> **Beacon11 said:**
> Unfortunately the local network is just that-- a local network. It doesn't care whether or not the network is connected to another network (e.g. the internet). May I ask what you're trying to do?

+1

What do you want to change it to do ?

in what scenario would you need to be disconnected from a network and ping yourself and not get a response from the stack ?

I dont really understand you request or need ?

---

### Post by redmk2 on 2011-09-07
> **haqking said:**
> ..
It actually resolves to 127.x.x.x anyways and will always ping itself.


I assume that you are referring to the OP's statement > If I disconnect my network and execute ping 192.168.2.1 it would still return the packets successfully, because it doesn’t go outside local. 

Pinging a private IP (i.e. 192.168.2.1) will not resolve to any 127.0.0.0/8 address.  Typically these are 2 different interfaces (lo and eth*n*), but even if they were not; one IP address doesn't resolve to another via ping.

---

### Post by haqking on 2011-09-07
> **redmk2 said:**
> I assume that you are referring to the OP's statement 

Pinging a private IP (i.e. 192.168.2.1) will not resolve to any 127.0.0.0/8 address.  Typically these are 2 different interfaces (lo and eth*n*), but even if they were not; one IP address doesn't resolve to another via ping.

sorry didnt explain myself and shouldnt of used the word resolve.  I was meaning it in the sense of pinging himself

i dont understand what he is asking to be honest, he wants to ping his own ip address when not connected to the network and for it to not ping the IP address? LOL

im confused ;-)

---

### Post by palexof on 2011-09-08
Hello again
   
  Thank you very much for the participation! 
   
  So I guess I will have to explain further. The ping was only serving the example because I thought there was a simple solution through some specific setting and wanted to keep it short. 
   
  Actually I am using the Perls Module WWW::Mechanize in order to simulate a web browser, which tries to log in on a web server (running on the same machine) and checks if there is network connectivity, if everything with the log-in process is OK, if the users can log in etc. 
  As long as I have a proxy set up as an env var in /etc/environment and the network connectivity suddenly disappears – it works like charm: The program detects there is a problem and starts some specific automatic procedures in attempt to solve the problem.
   
  The problem is that I have to remove the proxy and when I do that, it can not detect the network problem any more, because it executes the connection locally, and although the network is gone, it still connects and logs in to the server.

---

### Post by redmk2 on 2011-09-08
> **palexof said:**
> Hello again
   
  Thank you very much for the participation! 
   
  So I guess I will have to explain further. The ping was only serving the example because I thought there was a simple solution through some specific setting and wanted to keep it short. 
   
  Actually I am using the Perls Module WWW::Mechanize in order to simulate a web browser, which tries to log in on a web server (running on the same machine) and checks if there is network connectivity, if everything with the log-in process is OK, if the users can log in etc. 
  As long as I have a proxy set up as an env var in /etc/environment and the network connectivity suddenly disappears – it works like charm: The program detects there is a problem and starts some specific automatic procedures in attempt to solve the problem.
  
  The problem is that I have to remove the proxy and when I do that, it can not detect the network problem any more, because it executes the connection locally, and although the network is gone, it still connects and logs in to the server.

The answer is pretty clear now that we can see what you are really attempting to do.

If you wish to simulate a *Host Unreachable * situation using a single local host, you need to create that situation by downing the interface on the that local host.  This would simulate a remote host on the network that was malfunctioning, powered off or disconnected.

---

### Post by palexof on 2011-09-09
> **redmk2 said:**
> The answer is pretty clear now that we can see what you are really attempting to do.

If you wish to simulate a *Host Unreachable * situation using a single local host, you need to create that situation by downing the interface on the that local host.  This would simulate a remote host on the network that was malfunctioning, powered off or disconnected.

 Unfortunately this is not the answer. Beside the fact that it is too obvious to miss, this solution is not feasible for my situation due to numerous reasons. To name a few:
  First of all _there are no_ remote hosts – everything is being done on / by the same host. 
  Secondly – I don’t want to simulate a network disconnection. As I previously said I am simulating a user connecting to the server in order to find out if there are any problems and by that I don’t mean only problems regarding the network connectivity. And then I want to take specific actions automatically if something is wrong (e.g. the network is gone).

  I really need the behaviour which I previously named: treating the local IP as a remote one and routing it through the gateway instead of executing the connection locally. There should be a way to do this. This is UNIX after all!

---

### Post by haqking on 2011-09-09
> **palexof said:**
> Unfortunately this is not the answer. Beside the fact that it is too obvious to miss, this solution is not feasible for my situation due to numerous reasons. To name a few:
  First of all _there are no_ remote hosts &#8211; everything is being done on / by the same host. 
  Secondly &#8211; I don&#8217;t want to simulate a network disconnection. As I previously said I am simulating a user connecting to the server in order to find out if there are any problems and by that I don&#8217;t mean only problems regarding the network connectivity. And then I want to take specific actions automatically if something is wrong (e.g. the network is gone).

  I really need the behaviour which I previously named: treating the local IP as a remote one and routing it through the gateway instead of executing the connection locally. There should be a way to do this. This is UNIX after all!


Well its not UNIX it is Linux to be exact ;-)...semantics indeed but there are subtle differences, though for your point none to mention.

I still dont fully understand your question (perhaps i am being dumb or cant see something obvious...LOL)

The Local IP is deemed that by its binding to the NIC mac address and deemed local to the network through the subnet mask.

I dont see how you could achieve what you want ? but then i dont fully understand what you want either, sorry for the confusion.

As i dont completely understand your question i dont know if this helps, but is it something you could achieve by setting up a virtual / virtual machine as the remote you are attemtping to treat as local ?

I am confused ?. :???:

---

### Post by Vishal Agarwal on 2011-09-09
I think you can use the virtual interface; where you can assign the remote ip also. May be I could be wrong to understand your requirement.

---

### Post by palexof on 2011-09-09
Well thank you all for the replies. 


OK, I will try to explain it a bit further. So the WWW::Mechanize Module for Perl is actually a very nice tool for atomizing anything which has something to do with web browsing (although for now without Javascript support – unfortunately :( ) So when you are using it, it acts exactly like a web browser – hence simulates the user browsing experience – at least from the web server point of view :).
   
  So I have my host, with the IP – 192.168.2.203. It runs periodically a script from the crontab which says to the WWW::Mechanize – connect to 192.168.2.203 (thus to itself) identifying like a browser Firefox 5 and see what page would the user get in return and how would it look like and so on.
   
  Here comes the network problem – if the network suddenly disconnects (yes it happens and no I can’t influence that) it is still able to connect to itself through the process pictured above.This is unfortunate for me because as said I need to take specific automatic actions if this happens (the network problem).
   
  My first solution works very well – by setting up a proxy in the /etc/environment – it does exactly that what I want – it routes the connection through the proxy externally and doesn’t care that the IP is the one of the local machine, so if a network problem occurs – it detects it and executes the programmed actions.
   
  Now I come to the optimization. I have to remove the proxy – due to numerous reasons – one of them being that my solution is depending on some external component which I don’t posses the influence of. And here is the sad part – as long as I remove the proxy – the network problem can no longer be detected, because it executes the connection locally and misleadingly returns: Everything OK - the user has connected and the page returned was .... At the same time no user would actually be able to connect because of the network being down.
  

@Vishal Agarwal: your idea sounds like an interesting thing to try, but I don’t think I understand what you mean. Would you care to explain further how to do this? Thanks!

@haqking: Well it is really semantics - but the very core and the very idea of Linux is IMHO being a UNIX ;). Besides being free of course. To the other point - I've also considered this but no, I can't use a VM and it is the other way around - I am treating the local as a remote.

---

### Post by Dangertux on 2011-09-09
The best I can give you is this, and it's a little bit outside stretch, since what you're trying to do sort of negates the basic rules of TCP/IP :-/

Multiple interfaces, depending on what the networking issue is this might work for you, however if it is a WAN side connectivity issue it might not doing anything for you.

Multiple VM's , likely won't give you what you're looking for, but might.

Checking interface state, up or down... Run script based on that. Still might not work the way you want. 

Ultimately, you need to be a little more specific on what exactly you're trying to accomplish.

EDIT: Actually on thinking more about it... The reason the proxy is even working is different than what you think. It is failing because it can't reach the outside when the network is down, so it can't get back to the proxy.

So take that knowledge and apply it to the script, have it attempt to make outside connectivity over the network connection in some way (ping, or whatever) if it fails, you know the network interface is malfunctioning. Do your repairs... Just my 2 cents.

---

### Post by palexof on 2011-09-09
I don't know how to explain in more details what I do want to achieve - I thought I've already depicted it clear enough. Please ask if something was not clear.

Exactly that is the point: It is failing because it can't reach the outside when the network is down, so it can't get back to the proxy - but the whole thing is actually caused by the connection attempt to the local IP through the WWW-Mechanize Script in the first place. So I am really pretty sure it works as I explained.

I thought of course about this but I don't want to make outside connectivity over the network connection (e.g. ping), because this would be again relying on an external component. And worse enough I have neither knowledge nor any influence over the network.

---

### Post by Dangertux on 2011-09-09
Not necessarily true, since you're trying to test connectivity of a local interface, you could use a VM or virtual interface on the same network you control.

Also I did some research on WWW Mechanize. If I understand correctly it is essentially just a web spider. To be honest, if you're testing a website running locally things like that are designed to be run remotely. So it's going to take a little extra effort on your part.

I really don't see how you're going to do it without either

-- Utilizing the proxy method you're already doing
-- Using a VM
-- Using another interface
-- Using a virtual interface
-- Using another machine.

Or completely redesigning the script.

---

### Post by palexof on 2011-09-09
Well WWW-Mechanize can be used as a spider - yes, but is actually much more than that. It can automate virtually any user action on the web (excluding  parts with JavaScript/Flash).


> **Dangertux said:**
> 

-- Utilizing the proxy method you're already doing
-- Using a VM
-- Using another interface
-- Using a virtual interface
-- Using another machine.


Since I previously excluded the other, only points 3 and 4 would work for me. Regarding 4 (also proposed from Vishal Agarwal above), I am still waiting for his answer, because I don't have any experience with this kind of settings.

Thanks for the help!

---

