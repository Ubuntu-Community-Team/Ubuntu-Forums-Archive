---
title: "I can see my neighbors networks, but mine does not show up on the list.."
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by soundofbread on 2010-08-27
For some reason my network does not show up on the list of available networks, it is not a hidden network. And it is WP2 just like most of my neighbors networks are... I'm using a Linksys Wireless N Broadband Router.. (Model # WRT160N V2) 

I also have a Apple Airport Express, which when plugged in WILL show up on the list, but I am unable to connect to it.. It just keeps trying to establish a connection to it but never works..

I am using a custom build PC, and everything has been a breeze up until now... I am brand new to Linux (I just installed the lastest version of Xubuntu, Lucid Lynx 10.04)

Any ideas or suggestions?

Also, I am living at my parents house, and their router is the Lynksys (which is better than the apple router anyways) so I need to connect to that network and not my Apple router's network.

Please help me!

Thanks in advance if you take the time to reply.
-soundofbread

---

### Post by cycling-rod on 2010-08-27
Can you connect to the internet using an ethernet cable (wired)?
Is it possible that your security settings to enable a wireless connection to the internet is not set properly?
Which computer are you seeing your neighbours networks from?

---

### Post by soundofbread on 2010-08-27
I have not tried to connect wired in, I'm pretty certain I can, I just didn't want to lug my pc in over to the modem. I'll try that later after my classes are over.

Im not too sure what you mean by your second question.. we have 5 computers in the house and all of them can access the family network, and get the internet. We also have an iPod touch, and a Apple TV that are able to connect to the same network.

I can see my neighbors networks from every computer in the house, the one with Xubuntu freshly installed can see the neighbors networks as well, (including my apple router's network) but it does not see the family network (the linksys router)

When I try connecting to the apple router network, it just keeps trying to connect, and about every minute it brings up the window asking me to type in the password.. so i type it in, it tries to connect for a minute, repeat.

---

### Post by grahammechanical on 2010-08-27
When you are asked for a password to connect to a network, then Ubuntu will try to connect using the password that you have entered. If it is the wrong password, then you will be asked for a password again. There will not be any indication that you entered the wrong password. You need, not your log in password, but the router/modem wireless key (WPA-PSK). Once you get the password right Ubuntu network manager will remember it. It will also remember incorrect passwords.

As for not seeing a wireless network, Did you select More Networks from the list, a side menu should appear showing any other wireless networks. You might want to edit connections and get rid of those networks that are creating a long list.

Regards.

---

### Post by kerry_s on 2010-08-27
if it's not on the list treat it as a hidden wireless & manually enter the name.

---

### Post by soundofbread on 2010-08-28
I tried typing in the network name as a hidden network and it was unable to be found.

Yesterday I was able to connect to my Apple router, but the connection i was getting was only around 18 k/s which is extremely sad... (My other computer is getting 6.15 mb/s)

I really have no ideas on what else to try

---

### Post by hypocrite420 on 2013-04-13
> **soundofbread said:**
> I tried typing in the network name as a hidden network and it was unable to be found.

Yesterday I was able to connect to my Apple router, but the connection i was getting was only around 18 k/s which is extremely sad... (My other computer is getting 6.15 mb/s)

I really have no ideas on what else to try


[COLOR=#070F14][FONT=Verdana]It very simple the wirelss Standard. The Wifi has the latest 802.11 n standard your pc or laptop has the 802.11 b, g standard. So no problem. Go to your wifi change the wireless setting from 802.11 bgn to 802.11bg and your computer or laptops wirele[/FONT][/COLOR][COLOR=#070F14][FONT=Verdana]ss lan's wirless setting from 802.11 abg to 802.11 bg and if possible both the devices to channel 11. Best of luck and post the result. 

[http://www.tomshardware.com/forum/41998-43-wifi-neighbors-signal-mine](http://www.tomshardware.com/forum/41998-43-wifi-neighbors-signal-mine)
[/FONT][/COLOR]

---

