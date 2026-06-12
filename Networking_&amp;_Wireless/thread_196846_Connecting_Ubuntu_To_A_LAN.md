---
title: "Connecting Ubuntu To A LAN"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by StormKitty on 2006-06-14
Greetings.

I have just installed Ubuntu on one of my machines I have in my home. I am trying to connect this machine to my homes LAN. I am having problems finding out how to do this.

The LAN consists of 5 computers. 4 are running Windows 2000, the one I'm trying to connect is on Ubuntu 6.06, dual booted with Windows 2000. I have a wireless router/modem for my DSL and laptop, and a and another router for the 5 computers. All of the computers are set up to obtain their IP address's automatically, as well as the DNS server address automatically.

How do I get the Ubuntu computer to connect to the network?
I am very new to Linux, and jujst trying it out for the first time.

---

### Post by jrobinson5 on 2006-06-14
From reading your post, I take it you're connecting it wired, you've already installed ubuntu 6.06 dapper drake, plugged in the cable, and when you open firefox it doesn't work. Correct me if I'm wrong. If I'm right, then click System>Administration>Networking, enter your password, click on "Ethernet Connection", click properties, check "enable this connection", and set the drop-down box to "DHCP." If it works or doesn't work let me know.

---

### Post by StormKitty on 2006-06-14
I have tried this, and it hasn't worked.

And yes, that is exactly what I did.

---

### Post by StormKitty on 2006-06-14
Alright. It is working now. I Disabled, then Re-Enabled the ethernet card, and now it is working!

---

### Post by jrobinson5 on 2006-06-14
So do you have to disable and reenable the ethernet card after each boot?

---

