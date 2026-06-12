---
title: "no remote SSH in apartment complex"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by fordman1090 on 2012-01-23
I have open SSH set up on my desktop, which is connected directly to my router which is plugged into the ethernet port in the apartment complex. The Aprt's have a T1 service and some type of user management service that requires you to register the MAC address that you connect. 

Any ways, im running a SSH so i can remotely connect to the desktop. If i use whatsmyip.com i get what looks like an internet IP, but if i use pinky or look at my router it gives me a different ip. 

So far iv been able to connect to the desktop through my local lan and through the router/pinky ip as long as im on my router wifi. But any remote connections time out for both external IP's.

I know it has something to do with the Aprt's network, but what is the best way to get around this or is there something im forgetting?

Thanks for any suggestions.

---

### Post by Lars Noodén on 2012-01-23
You'll have to check to see if it is getting blocked by the appartment's network:

[http://canyouseeme.org/](http://canyouseeme.org/)

If it's blocked then you'll probably have to work out some arrangement with the network administrator to fix the mistake.

---

### Post by matt_symes on 2012-01-23
Hi

> Any ways, im running a SSH so i can remotely connect to the desktop. If i  use whatsmyip.com i get what looks like an internet IP, but if i use  pinky or look at my router it gives me a different ip. One address is lightly to be your LAN side address and is usually a class C address on the subnet 192.168.0.0/24, 192.168.1.0/24 or 10.0.0.0/24.

The other is going to be your external IP address. It is this you need to connect to from outside your LAN.

As Lars stated, check the port is open from the outside. You have also port forwarded on any router you may have in your apartment ?

Kind regards

---

### Post by fordman1090 on 2012-01-23
Sorry for the delayed reply, i havent been home so i couldnt really test my home ip. I tried "canyouseeme.org" and it return with

[I]I could not see your service on xx.xxx.xxx.xxx on port xxxx
Reason Connection timed out[/I]

I do have my personal router setup to forward the port to my desktop PC and my PC is set up to receive the port. I guess ill have to give my ISP a call and see what they say, which is kinda what i figured, but i was hoping there was an easy way around it.

Thanks for the help, ill give them a call and see what happens.

---

### Post by fordman1090 on 2012-01-24
Here's an update, sorry if its a little confusing and long,

I called my ISP and they said that they dont close any ports and the gave me the number of the company that manages the switches and networking services for apartment complex's. I called them and they said that they could give my router's mac address its own internet ip. This is where it got kinda strange. 

He looked up my account, but didnt see any active devices. So he added my routers default MAC(from the bottom of the router) with its own internet IP. The router still didnt show up. I made sure the the "use default MAC" option was selected in the router settings. But he still couldn't find it. But he did find a very similar MAC that wasn't registered to an account. It was in fact the same MAC that was grayed out in the "Custom MAC" option on my router and that my laptop was seeing as its gateway. He tried to add it to my account but it kept returning that it was already in use.

To get it working, i set the custom MAC to the default MAC that he had added to my account with its own ip. So right now my SSH is working great and the internet is even a little faster. 

Its still kinda strange to me that the routers own default MAC isnt right. Im not too worried about the MAC issues, i just thought it was kinda weird and interesting and that i would share it with yall. 

Thanks again

---

