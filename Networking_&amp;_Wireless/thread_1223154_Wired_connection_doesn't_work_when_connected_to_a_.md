---
title: "Wired connection doesn't work when connected to a router."
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by DaftPyramid on 2009-07-25
UPDATED

Hi,

I just bought my first ever router (Linksys WRT54G2), and I am having some troubles with installation.

I hooked the router up appropriately (I think), and the computer connects to the router (Network Manager say's "connected"), but I cannot connect to the modem (DSL). Even if I have the modem turned off, the network manager still says I'm connected. If the modem us turned on, I still get no internet connection. 

I called Linksys, and (surprise!) they don't support Linux. The lady did tell me, however, that it sounds like the IP address of my modem and the IP address of the router are conflicting. She says I need to change the IP address of the router. Does that make any sense?

As you can surely tell, I am not very well versed in wireless internet. Any help would be greatly appreciated.

Thanks in advance.

---

### Post by LookTJ on 2009-07-25
Can you ping your router?
```
ping 192.168.1.1
```

If so, the connection to the router is not at fault.  

You may need to call your ISP.  It may be that the MAC address of the router is having conflicts with another computer/router in the ISP's network.

but if not, post the output of both
```
sudo ifconfig
```and
```
sudo route
```

:)

---

### Post by DaftPyramid on 2009-07-25
Thanks for the reply. 

I hate to waste your very genuine and helpful comment, but I fear my idiocy may have changed the problem. I discovered and fixed a small wiring issue, but a similar problem persists.

Now the computer connects to the router, but it seems unaware of the modem's existence. Even if I have my modem turned off, Ubuntu says that I am connected, so long as the router is on. Even if I turn the modem on, I still don't get a connection (even though Ubuntu says I'm connected).

Would running the commands you gave me still help? I'd like to verify, because running those commands would involve disconnecting the internet again and rewiring everything. 

Thanks again.

---

### Post by LookTJ on 2009-07-25
Did you plug the modem into the WAN port of the router? If so, that's good.

What type of modem do you have? Did you buy it yourself or is it rented from the ISP.

could you ping google.com with the modem on? If not, something's wrong.

Does the Internet work when you plug your modem into your computer? If so, then the MAC address of the router is having conflicts with someone else router/computer or anyone in your ISP's network

It's best to contact your ISP(Yes I know most ISPs don't support Linux)

:)

---

### Post by DaftPyramid on 2009-07-25
Yikes, I didn't understand most of that. 

Currently the router is unplugged and my modem is connected directly to the computer like normal.

When I hook up the router, I plug the modem into the socket labled "internet" and plug the computer in the socket labeled "1".

The modem is a Westell that was supplied by Verizon when I first ordered Verizon DSL.

Not exactly sure what it means to "ping" google.com, sorry.

Yes, the internet works when I plug the modem into my computer. 

I have a feeling that contacting the ISP is not going to do much good...

Thanks for your help.

---

### Post by LookTJ on 2009-07-25
> **DaftPyramid said:**
>  I have a feeling that contacting the ISP is not going to do much good...

Thanks for your help.
The setup is okay as far I can tell

what it means to ping google.com is it means that your computer is requesting google.com to reply to your computer.

Call your ISP, tell them about your new router you bought, and then tell them that the modem won't connect to the internet while plugged into the router. Give them the router's mac address(if they request it/Or you ask them to check the MAC address). It's worth a try

A MAC address is a NIC(network card) hardware address. MAC addresses on routers are usually on the bottom.

Hopefully you gain insight from this post :) 

I wish you all the best.

---

### Post by DaftPyramid on 2009-07-25
OK, but just to clarify...

Is it normal that the network manager states that I'm connected, even though the modem is turned off? I figured that would depend on whether my modem was turned on/off, like normal.

---

### Post by martinbaselier on 2009-07-25
Your modem probably is a modem/router (a router with a built in modem), running a dhcp server. Your other router has probably a dhcp server running too. For the setup to work, you would need to configure your second router as a bridge. 

Ubuntu says it's connected when it gets a dhcp address. Wetter it's connected to the internet or not doesn't matter, that's what the modem/router is for. 

Since this is os independent, but it's about setting up the router correctly, you could ask this question to linksys. It's probably in the manual too. And if you don't understand a term, you can look it up on wikipedia.

---

### Post by DaftPyramid on 2009-07-25
Thanks for the response, but I'm sorry, none of that made any sense. Could you please proof-read and clarify your comment?

---

### Post by martinbaselier on 2009-07-26
I can't say it any clearer. 

These wiki articles explain the terms:

[http://en.wikipedia.org/wiki/DSL_modem](http://en.wikipedia.org/wiki/DSL_modem)
[http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)
[http://en.wikipedia.org/wiki/Dhcp](http://en.wikipedia.org/wiki/Dhcp)
[http://en.wikipedia.org/wiki/Network_bridge](http://en.wikipedia.org/wiki/Network_bridge)

---

### Post by DaftPyramid on 2009-07-26
Your English is somewhat broken. 

I need instructions here. One person is telling me to ask my ISP about my router's MAC address, and another is telling me to make my _______ (either modem or router) into a bridge.

---

### Post by cariboo on 2009-07-26
I would suggest you log on to the router management interface and ckeck the status tab. You should see what your external ip address is as well as the dns server addresses. When checking the staus page youshould see something like the screenshot. I obscured my external ip address and my isp's gateway address.

---

### Post by lisati on 2009-07-26
> **DaftPyramid said:**
> Thanks for the response, but I'm sorry, none of that made any sense. Could you please proof-read and clarify your comment?
Some modems come with features that let them do some of the same work that routers do. 

It is possible that you might need to tinker with the settings a bit more. To cut a potentially long story short, you might have to connect direct to the modem, get the setup working, then add your router and run its setup utility again.

---

### Post by DaftPyramid on 2009-07-26
Cariboo,

How do I log into the router management interface? What do I do with that information once I have it?

lisati,

Any ideas about what settings I need to change?

---

### Post by martinbaselier on 2009-07-26
[http://192.168.1.1](http://192.168.1.1) 
is the address of your linksys WRT54G router, according to the manual.(page 20)

Leave the User Name field empty, and enter admin in lowercase letters in the Password field.

---

### Post by DaftPyramid on 2009-07-26
Thanks.

What manual are you talking about?

I still don't know what to do with the information I gather there.

---

### Post by martinbaselier on 2009-07-26
I just used google and searched for WRT54G manual.

[http://74.125.77.132/search?q=cache:FX-voFoqsDMJ:77.100.103.108/public/reference/wrt54g_ug.pdf+wrt54g+manual&cd=1&hl=en&ct=clnk](http://74.125.77.132/search?q=cache:FX-voFoqsDMJ:77.100.103.108/public/reference/wrt54g_ug.pdf+wrt54g+manual&cd=1&hl=en&ct=clnk)

To be able to set up a router, you need some basic understanding of network technology. I gave you the wikipedia links, which explain them.

---

### Post by DaftPyramid on 2009-07-26
Those articles aren't going to help me solve my problem much. I just need instruction.

---

### Post by martinbaselier on 2009-07-26
[http://www.google.com/search?q=WRT54G+setup+as+a+bridge](http://www.google.com/search?q=WRT54G+setup+as+a+bridge)
[http://www.wi-fiplanet.com/tutorials/article.php/3639271](http://www.wi-fiplanet.com/tutorials/article.php/3639271)

---

### Post by DaftPyramid on 2009-07-26
Everything so far is Windows/Mac specific, including the WRT54G manual.

---

### Post by DaftPyramid on 2009-07-26
Should I follow this: [http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3687](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3687)

---

### Post by DaftPyramid on 2009-07-26
Is this what you mean by "bridging?" Should I follow this procuedure?

[http://www.dslreports.com/faq/13600](http://www.dslreports.com/faq/13600)

Please, I need instruction.

---

### Post by martinbaselier on 2009-07-26
That's a guide for setting up the router in combination with a DSL-modem, a real DSL-modem, and not a router with a modem built in.
edit: I meant the first guide you posted. 

What did you have to do to setup the your internet. Did you just plugin the cable and it worked? Or did you have to setup a PPPOE connection in the networkmanager?

The setup of the router itself has nothing to do with your operating system.

---

### Post by DaftPyramid on 2009-07-26
When I first started using this modem, I was using Windows. There was an installation disk, so I have no idea whether or not it would have worked by just plugging it in. When I switched to Linux, I didn't need any setup, it just worked. 

Should I follow the "How do I use a router with the Westell 6100?" guide? (That's the modem that I use).

When I go to 192.168.1.1 I get a settings interface. Would any helpful information be in there?

---

### Post by martinbaselier on 2009-07-26
This means you have a router with a built in modem, as I suspected. It has a DHCP server running on it, otherwise you would have had to setup your box. 

You would need to setup the router, to receive an ip via dhcp, which should be the default. If you check the manual (at least the pdf I gave you a link to), it explains each setting on the router. Most routers also have a built in help function, with explanations. 

First you must make sure the router connects to the internet. Normally there is a reset option on the router. So if you did something wrong and you can't reach it anymore, you can always reset it back to factory defaults. 

The "How do I use a router with the Westell 6100?" would probably be a good start.

---

### Post by DaftPyramid on 2009-07-26
So I'm *not* using PPPOE?

---

### Post by DaftPyramid on 2009-07-26
According to my modem settings interface, I *am* using PPPOE.

---

### Post by LookTJ on 2009-07-26
If you want to use your wrt router, you most likely will have set the modem in bridged mode.

If you don't know what bridged mode, call your ISP and they will set it for you :)


:)

---

### Post by DaftPyramid on 2009-07-26
Success! I used that guide to put my modem in bridge mode, and I am currently browsing the internet with the router installed. Now to see if the wireless works...

---

### Post by DaftPyramid on 2009-07-26
Super success!

Wireless internet is up and running.

Now... how do I set a password...

---

### Post by LookTJ on 2009-07-27
On the wrt? 

What password? A Wifi password or a web gui password?

To set a wifi password,

go to [http://192.168.1.1](http://192.168.1.1)

(Assuming default factory state)the username is blank, the password is admin

Go to wireless tab, then go to security sub-tab, and setup a WPA2 password there.

:)

To set the wrt password,

You would need look under administration/management tab. The rest should be obvious

:)

Don't be afraid to ask if you don't know where to go.

---

### Post by martinbaselier on 2009-07-27
> 
According to my modem settings interface, I am using PPPOE.

Of course you are, it's the most used protocol for DSL connections. It's setup on your router with the modem built in though and not on the machine which connects to it.

---

