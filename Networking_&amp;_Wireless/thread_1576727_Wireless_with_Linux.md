---
title: "Wireless with Linux"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by ubuntu27 on 2010-09-17
Hello. 
I am about to contract an ISP so I could have wireless Internet at home.

It is my FIRST time that I will have a Wireless Internet, so, I would like to know what is it that I need to know to get it to work with my Linux Laptops properly.

From what I read, I need to ask the ISP how its Internet is configured.
But, none of the articles that I've read so far list what specific questions to ask. (They all assume that everyone is knowledgeable)



So, could you guys please tell me _what question to ask_ the "technician" who is going to install the wireless Internet? 


P.S: I have two laptops with Linux, and one Desktop with Windows.

---

### Post by metalf8801 on 2010-09-17
> **ubuntu27 said:**
> Hello. 
I am about to contract an ISP so I could have wireless Internet at home.

It is my FIRST time that I will have a Wireless Internet, so, I would like to know what is it that I need to know to get it to work with my Linux Laptops properly.

From what I read, I need to ask the ISP how its Internet is configured.
But, none of the articles that I've read so far list what specific questions to ask. (They all assume that everyone is knowledgeable)



So, could you guys please tell me _what question to ask_ the "technician" who is going to install the wireless Internet? 


P.S: I have two laptops with Linux, and one Desktop with Windows.

I would start by asking if they will even help you with your computers running GNU/Linux because some companies require Windows. Ask about what security protocol is being used by default and ask if they will set up the router to use WPA or WPA2 because you don't want WEP because its very easy to crack. 

Also you should make sure your wireless cards work properly with Ubuntu.

I hope this helps and good luck 
Dan 

PS By Wireless Internet you mean they (your ISP) are going to set up a wireless router for you right. As apposed to getting your internet service from a cellular company right?

---

### Post by ubuntu27 on 2010-09-17
I don't know how they are going to set up the wireless Internet. I might have to buy my own router.

Does the modem provide wireless or does the router do it? Confusion aroused since one of the ISP told me that if I don't want to rent a MODEM, I have to make sure to buy one that supports DSL.

This is all first time for me.

Does the ISP have to configure WAP? Can I do it?

Well, I doubt they support Linux. And I don't have a choice regarding ISP. There are only two ISP in my town. What a Oligopoly.


Thank you metalf8801.

---

### Post by metalf8801 on 2010-09-18
> **ubuntu27 said:**
> I don't know how they are going to set up the wireless Internet. I might have to buy my own router.

Does the modem provide wireless or does the router do it? Confusion aroused since one of the ISP told me that if I don't want to rent a MODEM, I have to make sure to buy one that supports DSL.

This is all first time for me.

Does the ISP have to configure WAP? Can I do it?

Well, I doubt they support Linux. And I don't have a choice regarding ISP. There are only two ISP in my town. What a Oligopoly.


Thank you metalf8801.

They will most likely set you up with a modem that has a built in router. 

They should set up some kind of encryption by default, but it will most like be WEP. However, you can change the encription later to wpa or wpa2. Just make sure they tell you the password to log into your modem/router using your web browser and what IP address you need to use to do that. For example most routers use the IP address 192.168.1.1 but not all of them. So you would type 192.168.1.1 into your browser then you will be asked for you users name and password then you will be able to make changes to how the router/modem is configured.

---

### Post by Hobgoblin on 2010-09-18
It most likely be one of two things.

They will provide a combined modem, router and wireless access point.  Or, you will have to buy your own and configure it to access their network.

If they provide it then they will provide the wireless key, all you need to do is tell your laptop to connect to the router and enter the provided key.  Most ISPs now provide routers set up with at least WPA protection, you may want to change a few things though.

If you buy your own it will come with instructions and will be set up with a default SSID and key, it would be best to change both of these along with the admin password (and user if possible).

But of course the first problem will be, does the wireless work on your laptops?

---

### Post by ubuntu27 on 2010-09-18
All right. They came. 
It seems that the modem is also a router.

They configured to use WEP.

My main laptop has no trouble connecting to the new network.
But, my other laptop cannot for some reason. (It does connect to any other access point).

So for now, those who want to use it has to connect with Ethernet.

It might be that they do now allow for more than one laptop...?


Thank you guys.

I took the note on how to login to configure the modem.

---

### Post by metalf8801 on 2010-09-21
> **ubuntu27 said:**
> All right. They came. 
It seems that the modem is also a router.

They configured to use WEP.

My main laptop has no trouble connecting to the new network.
But, my other laptop cannot for some reason. (It does connect to any other access point).

So for now, those who want to use it has to connect with Ethernet.

It might be that they do now allow for more than one laptop...?


Thank you guys.

I took the note on how to login to configure the modem.

The problem could be that they set up the router with MAC address recognition or that your wireless card has a problem with WEP and when your running Ubuntu 

What kind of wireless card do you have in your second laptop?

Oh what Internet Service Provider do you have?

---

