---
title: "Creating a network bridge"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by ltrobertcole on 2009-08-30
I am very new to this. I just installed ubuntu on my netbook and I need to create a network bridge because the wireless adapter on my desktop is dieing. So I need the internet connection from my netbook to transfer over to my desktop. I know windows xp had network bridge basically built right in all you had to do was select two connection then right click and select bridge. I was wondering if it was that easy on here also or am I required to download something?

---

### Post by aesis05401 on 2009-08-30
Hello, 

Can you provide more details?  I read your post and it sounds like you are wanting to use the laptop as an access point (either wireless or wired).  Am I misunderstanding?

---

### Post by ltrobertcole on 2009-08-30
I really don't know how to word this and I am sorry for that. My netbook is wireless and I want to connect a Ethernet cord to my desktop because my desktop has no Internet connection. So in other words I want my desktop to take the internet connection from my netbook.

---

### Post by aesis05401 on 2009-08-30
> **ltrobertcole said:**
> I really don't know how to word this and I am sorry for that. My netbook is wireless and I want to connect a Ethernet cord to my desktop because my desktop has no Internet connection. So in other words I want my desktop to take the internet connection from my netbook.

Are you in possession of a cross-over ethernet cable?  [http://en.wikipedia.org/wiki/Ethernet_crossover_cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

---

### Post by ltrobertcole on 2009-08-30
Yes I have one.

---

### Post by aesis05401 on 2009-08-30
> **ltrobertcole said:**
> Yes I have one.

Ok, 

ICS is an acronym for internet connection sharing used in the following link.  The details of your setup will vary a little because one of your cards is a wireless card, but this tutorial should be customizable to your needs: [https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

Long story short, your Linux installation has all the software on board to act as a router, you just need to get the configuration in place.  On your laptop the wired and wireless connections need to be placed into different subnets, then you create a forwarding rule between the subnets.  Can you read through the linked information and post back here with questions?

---

### Post by ltrobertcole on 2009-08-31
Yes I will look at it when I get home. I am at college right now.

---

