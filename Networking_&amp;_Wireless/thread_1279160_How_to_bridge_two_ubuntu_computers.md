---
title: "How to bridge two ubuntu computers?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by Gogeden on 2009-09-30
I just wanted to know how I go about doing this. I read an ubuntu guide on this but I didn't quite understand it. Please help, thanks! ^_^

---

### Post by fishy6969 on 2009-09-30
Can you expand a bit on what you mean by 'bridge'? What exactly are you trying to acheive?

---

### Post by Gogeden on 2009-09-30
I mean bridging them so that I can have internet access on the one that doesn't already have any internet connection. I'm working on a dekstop with Jaunty on it and I want to get all the updates, codecs, apps, etc. for it ^_^

---

### Post by lukeiamyourfather on 2009-09-30
> **Gogeden said:**
> I mean bridging them so that I can have internet access on the one that doesn't already have any internet connection. I'm working on a dekstop with Jaunty on it and I want to get all the updates, codecs, apps, etc. for it ^_^

The real solution here is to get a router.

---

### Post by fishy6969 on 2009-09-30
Sorry - a few more questions

How are you connecting to the internet?
Is it with a wireless router?
Are the computers physically near each other?

---

### Post by Gogeden on 2009-09-30
I have a switch. Would that work?

---

### Post by Gogeden on 2009-09-30
I'm connecting to the web via my laptop which hops on a wireless router
And yes my laptop and the desktop are about a foot near each other.

---

### Post by amsum on 2009-09-30
> **Gogeden said:**
> I have a switch. Would that work?

If yours is Static IP, switch will not work. Switch works only with Dynamic IP. However, you can configure your static IP in router and can connect to internet on both the computers.

---

### Post by amsum on 2009-09-30
> **Gogeden said:**
> I'm connecting to the web via my laptop which hops on a wireless router
And yes my laptop and the desktop are about a foot near each other.

sorry to miss this one. Since you already have wireless router, you can directly connect your both computers (laptop and desktop) with router to surf the internet.

---

### Post by Gogeden on 2009-09-30
I don't have a wireless card in my desktop...

---

### Post by oldfred on 2009-09-30
Even on my laptop I find updates run a lot quicker if I use an ethernet cable to connect to my router rather than wireless. It just works better. Wireless is fine when I am not near router but big downloads are slow.

---

### Post by amsum on 2009-09-30
> **Gogeden said:**
> I don't have a wireless card in my desktop...

I believe most of the wireless routers have ethernet ports too. You can connect to it with ethernet cable. If there is no ethernet port, then can you tell me which router model you have?

---

### Post by Gogeden on 2009-09-30
I just want to learn how to bridge 2 computers. I could care less about hooking it up via a wireless router. I want my laptop to be connected to the Desktop I am working on via Ethernet and then my laptop will connect to a wireless router (In this case the town's wireless connection) So my laptop will act as a nexus between the desktop and wireless router so there is internet on the desktop. If that makes any sense...


Wireless Router>Laptop>Desktop

^_^

---

### Post by motorcity909 on 2009-09-30
I think the router should act as the nexus you're looking for.  Then both machines connected to it with ethernet cables.  The router will share the internet connection with both machines.

---

### Post by amsum on 2009-09-30
I am not of much help then. I am still learning all these stuffs and would love to see the solution. Hope somebody comes up with easy solution fo rthis one.

---

### Post by amsum on 2009-09-30
> **motorcity909 said:**
> I think the router should act as the nexus you're looking for.  Then both machines connected to it with ethernet cables.  The router will share the internet connection with both machines.

you got him wrong. his primary objective is not to get internet in both the computers rather he wants to learn how to bridge two computers. its more of a Bridge How-To.

---

### Post by motorcity909 on 2009-09-30
Fair enough.  Back to the crowd then for more answers!

---

### Post by Gogeden on 2009-09-30
How will the router act as nexus when I don't even own the router. It's the towns router.


The router will send data out, which will then be sent THROUGH my laptop and then will go through the ethernet cable thus give the desktop internet access. The only way the desktop will get any kind of network activity is via it's Ethernet NIC (I think that's redundant). It's a VERY old desktop but yet is still pretty powerful... It's a buddy's desktop, not mine. I'm just rebuilding and setting it up for him and stuff ^_^

---

### Post by Ergo on 2009-10-01
I did this once 5 years ago.  I am unsure all of the software tools, but I can physically get you set up.  The key to this is called a crossover cable.  It is a network cable that has one of the twisted pair reversed.  You can then physically connect the laptop to the desktop.  Once the cable is in place, the laptop is the gateway to the internet (the laptop is in all reality a router for the desktop).  I used IP tables back then.  The desktop and laptop will be connected on the same local network and can share files.  The desktop will be able to share the laptops internet connection.

---

### Post by Gogeden on 2009-10-01
Alright cool. I did Cisco back in high school for about a month or two and I learned how to make my own Ethernet cable. So i'll do that then. Thanks! ^_^

---

