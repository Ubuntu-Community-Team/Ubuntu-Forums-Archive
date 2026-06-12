---
title: "How Do You Set Up Wireless Security??"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by Plumtreed on 2009-05-29
I have wireless going ok but I don't seem to know how to effect any form of security.

When I go into NetworkManager via right-clicking the Icon and select edit; I find I can go through the motions of effecting security. It seems retrospective because when I re-select my wireless it shows with no encryption. If I check previous selections they show that they were encrypted????

Is it possible to effect encryption in this way and is it possible to save it?

---

### Post by Idefix82 on 2009-05-29
First you need to setup your router to have an encripted network. You can specify the password in the router settings. Then, if you try to connect to the network, the network manager will ask you for the password and will remember it, so you don't need to type it in every time you log in.

---

### Post by Plumtreed on 2009-05-29
> **Idefix82 said:**
> First you need to setup your router to have an encripted network. You can specify the password in the router settings. Then, if you try to connect to the network, the network manager will ask you for the password and will remember it, so you don't need to type it in every time you log in.

That makes sense!!!.........I'll have a go. Thanks for the 'heads-up':p

---

### Post by ixpl on 2009-05-29
With most routers you'll need to be connected via ethernet cable in order for the WPA settings to be saved. It is good to set a password to your routers setup page also. You can find your router setup page by right clicking the network manager icon and click on information, this will show your gateway address. Punch it into a web browser and your ready. This is also a good place and time to see all the other computers that have associated with your router. Check that the firewall is enabled with no port forwarding etc unless you want to connect to your computer remotely via internet. Then a simple scan from another network against your routers public IP will tell you how secure. MAC filtering is nice too.

---

### Post by Plumtreed on 2009-05-29
Thanks Ipxl & Idefix82, I'm having difficulty getting my head around this???

I actually have two routers or switches. I have a router hooked up to provide a 'home' wireless zone. It hooks directly to a router with lan only connections. This is our connection to a wirefree radio type broadband. It is a PPPoE connection.

I think I should have some security on the home wireless bit but It may not be necessary.

---

### Post by munky99999 on 2009-05-29
Ya the router itself has to be set to run those things. For example WPA2 or whatever. Then when you setup to connect to the router wirelessly; you insert those settings.

-disable ssid broadcasting
-WPA2
-mac address filtering

All of which needs to be done router side.

---

### Post by Plumtreed on 2009-05-31
Thanks for the guidance everybody! It all seems so easy now. I appreciate the 'kick-start'.

---

