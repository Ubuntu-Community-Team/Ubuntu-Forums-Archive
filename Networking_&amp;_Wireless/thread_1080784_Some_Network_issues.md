---
title: "Some Network issues"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Jdallen5 on 2009-02-25
Hi

I'm using Gutsy Gibbon

I have a rather odd problem I've been working on.

My desktop has no way of connecting to the internet where it is, so I decided to hook it to my mac and share the wireless internet connection.  Its not working, but I don't think its the mac end.  I've gotten it to work on the windows portion of the desktop, but the Ubuntu side is having trouble seeing other computers on the network. 

I know this isn't a mac forum, so I don't expect you to know much about that side, but the reason I think its the Linux end that is causing the trouble is that when I ping the linux computer (from the mac) I get a response.  When I ping the mac, I do not get a response.  It says Destination host unreachable.  For some reason, it doesn't recognize that its connected to a network

The mac's firewall has been disabled, so my question is, is there a firewall built into Ubuntu that may be interfering?  Am I missing a driver perhaps?

Anyway, if this is all gibberish let me know.  I'll try to explain better.

Thanks in advance for any info :p

---

### Post by Iowan on 2009-02-25
I'm still running Gutsy... 
I don't remember it coming with firewall. How did you connect the two - crossover cable? Are the networks set up similarly - subnets, addresses,gateways...?

---

### Post by Jdallen5 on 2009-02-25
I'm connecting them via direct ethernet cable.  I have the mac settup to split the wireless connection.  I honestly don't know whats really going on on the mac end.  Most of it is done through the preference pane.  The reason I feel it may be ubuntu is that I was able to get a connection on the windows partition of the computer but not the linux partition.  

Sorry I'm not being more help- is there a specific config file I can find to show you?  

Also, I was messing around for a while with making a web server on the linux side.  Is it possible that that might be interfereing?  Its apache2.  

On a side note, I can see my linux page's default web page from the mac, but I can't see the mac's default webpage which I know is currently active.

---

### Post by Iowan on 2009-02-25
I'm not sure about the Mac (having never touched one), but ordinarily computer-computer requires a crossover cable - or you can use standard cables from both machines to a hub or switch.

---

### Post by Jdallen5 on 2009-02-25
I read up on the crossover-cable and that looks like it may do the trick.  I think the problem is that both machines are trying to do the talking, and the ethernet cable can only go one way.

I'm not sure if its luck that I got the Win XP to work using the same method or if there is a way to get the linux machine to sit back(I tried turning off apache2 but that didn't work).  At any rate, I'll try the crossover method, and if that doesn't work I'll break down and get a USB wireless card...  

yeah, I'm cheap-  Thanks for the help

---

