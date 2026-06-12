---
title: "Internet connection sharing with only 1 ethernet card, is it possible?"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by hito1 on 2006-04-22
Hi there, can someone answer me this?

 Here is the situation: 
   I have 3 computers in a LAN (mine, my fahter's and my sister's), all of them using WinXP. 
   All the comps are connected to a hub, an adsl modem is also connected to the hub.
   My computer is the one connected to the internet through the adsl modem, I share the connection with the other two by using a small proxy software.
   There is only one Network card in my comp., which is linked to the hub.

  Here is the problem:
   I want to install Ubuntu 6.06 in my comp., and I'd want to share internet connection in a similar way (my comp. gets connected and share with the two others).
   I ran LiveCD, and installed firestarter to share the connection, as advised in another thread - but Firestarter complains about having the two networks at the same device (don't remember the actual terms). 
   
  Here is the question:
   Apparently I have to have 2 network cards for sharing internet connection using Ubuntu, is that true???

  Many thanks!

---

### Post by johnny2211 on 2006-04-22
How is the adsl modem conected? Is it usb to your pc or network cable to the hub?

---

### Post by hito1 on 2006-04-22
[QUOTE=johnny2211]How is the adsl modem conected? Is it usb to your pc or network cable to the hub?[/QUOTE]

Network cable to the hub.

---

### Post by johnny2211 on 2006-04-22
OK. So you have two options now:

1. If the ADSL modem you have supports PPPOE and you can configure it to be on the internet all the time and act as a DHCP server and a router. All of your pc's can get to the internet whenever they want to.

2. You have to configure your ubuntu pc to use PPPOE and dial the internet using the ADSL modem. (This is what your windows did before) And your ubuntu pc will then be DHCP server and a router.

Of course 1. being the better solution:cool: 

What is you ADSL modem make and model?

---

### Post by hito1 on 2006-04-22
[QUOTE=johnny2211]OK. So you have two options now:

1. If the ADSL modem you have supports PPPOE and you can configure it to be on the internet all the time and act as a DHCP server and a router. All of your pc's can get to the internet whenever they want to.

2. You have to configure your ubuntu pc to use PPPOE and dial the internet using the ADSL modem. (This is what your windows did before) And your ubuntu pc will then be DHCP server and a router.

Of course 1. being the better solution:cool: 

What is you ADSL modem make and model?[/QUOTE]

Speedstream 5200

No 1 option was suggested to me before, I'm reticent about it because I fear ruining the modem in the process. Can you tell me more about it?

---

### Post by johnny2211 on 2006-04-22
I looked your modem up on the internet and it really does support the first option. I can't tell you how to set it up because it's different from ISP to ISP. But what I can tell you is to definetly get someone set it up for you. It will be worth it:-) Or you can even try doing it by yourself. You can't ruin the modem, because you are not burning anything new into it, just changing the settings. 

Ofcourse you could set the settings so that you wouldn't be able to log into it again or loose the internet connection. Even then people that know how to set it up can get it back easily.

Basicly what it is all about is:

Your adsl modem (which is a router and not a modem:-) will be the one dialing the internet (it is a small computer afterall runing linux:-). It will be a DHCP server and all the pc-s in your network will get the network settings from him as soon as you connect them to the network. I've been doing this for a long time now, and believe me it's easy so go find someone who can do it and have a great Ubuntu experience:D

---

### Post by mips on 2006-04-22
Go for johnny2211s Option 1. It is the best and easiest method to do this.

Who is your ISP, weblink please ? From this I should be able to give you all the settings you will need.

---

### Post by adamkane on 2006-04-22
You might want to purchase an affordable Netgear router. This will simplify the configuration greatly.

Just a suggestion. Time saved is worth the £50.

---

### Post by mips on 2006-04-23
[QUOTE=adamkane]You might want to purchase an affordable Netgear router. This will simplify the configuration greatly.

Just a suggestion. Time saved is worth the £50.[/QUOTE]

He already has a router, just has to configure it. No need to spend more money.

---

### Post by adamkane on 2006-04-23
Configuring a separate router is easier/safer than trying to configure his modem and making Ubuntu work as a sharing device. 

Buy a cheap router, and your life becomes greatly simplified.

It's just a suggestion.

---

### Post by mips on 2006-04-24
[QUOTE=adamkane]Configuring a separate router is easier/safer than trying to configure his modem and making Ubuntu work as a sharing device. 

Buy a cheap router, and your life becomes greatly simplified.

It's just a suggestion.[/QUOTE]

He already has a router, no point to buy another & waste money. It has a integrated modem. He just calls it a modem.

No need to make ubuntu a sharing device. The router will perform this function via the hub.

---

### Post by hito1 on 2006-04-24
Wow, thanks for all the feed back. There is even a quarrel about who is the most helpful :)! (the buy a router solution is out of question right now, I'm already buying a DVD bruner, so my expenses are pretty tight, sorry, adamkane, heheheh)

Ok, the router seems to be the easiest solution, but right now I'm having trouble doing it, the standard IP used to access this kind of modem/router doesn't work on mine, I'll have to figure a way around, but it will probably demand more time than I can afford right now (I just can't wait to install ubuntu, hehehehe). So I'd like to go back to the original question, is it possible to share the internet connection like I do with winxp + proxy software + only 1 ethernet card?

Thanks again, guys!

---

### Post by souki on 2006-04-24
[QUOTE=hito1]is it possible to share the internet connection like I do with winxp + proxy software + only 1 ethernet card?[/QUOTE]
if you are looking for a proxy software on linux, there is "squid", but this will only work for http and ftp traffic. and you will have to set up the others hosts to access internet through the proxy.

you can also set up your linux host to act as a gateway (you can attach several addresses to one ethernet card), I don't recommand you this since it's much more diificult than setting up your router

the best solution, as said before in previous posts, is to set up your router

---

### Post by hito1 on 2006-04-25
Did it! :) Changed the modem into a router! :)

That raises some questions, though:

1. What kind of differences will I experience now that I'm behind a router? Is it just the port-forwarding need? or there is something else, like authentication issues?

2. How can I configure my internet under ubuntu, it's not the pppoeconf anymore is it? (the router acts like a DHCP server)

3. Now that my connection have to pick up an IP from the DHCP server, will I have issues with my local network? (previously, the machines were assigned static IPs)

Thanks, guys! Can't wait to install Ubuntu!!!!! :D

---

### Post by mips on 2006-04-25
[QUOTE=hito1]Did it! :) Changed the modem into a router! :)

That raises some questions, though:

1. What kind of differences will I experience now that I'm behind a router? Is it just the port-forwarding need? or there is something else, like authentication issues?

2. How can I configure my internet under ubuntu, it's not the pppoeconf anymore is it? (the router acts like a DHCP server)

3. Now that my connection have to pick up an IP from the DHCP server, will I have issues with my local network? (previously, the machines were assigned static IPs)

Thanks, guys! Can't wait to install Ubuntu!!!!! :D[/QUOTE]

1. Not much. Only certain apps might require port forwarding. The router now does the authentication/login where you PC previously did it.

2. No you don't need pppoe anymore on any of your pc's. Just get a ip via dhcp or configure all your pc's with static addresses. Make sure the subnet/mask/gateway etc is specified correctly if you go the static route. Think it is done under system-administration-networking, cant really remember as I use kubuntu.

3. No really. It is not advisable to run dhcp & static configurations on the same lan as it could lead to address conflicts (unless you reserve certain addresses). So make all the pc's static or dhcp but not a mixture of both.

---

### Post by hito1 on 2006-04-25
[QUOTE=mips]
3. No really. It is not advisable to run dhcp & static configurations on the same lan as it could lead to address conflicts (unless you reserve certain addresses). So make all the pc's static or dhcp but not a mixture of both.[/QUOTE]

Another question (please don't kill me, hehehe):

when setting alocal network, does one computer remember other computer's name or ip? I mean, I had a shared folder in my comp., did my sister's computer used to see it as "hito\share" or "192.168.0.2\share"? If it were "192.168.0.2\share" will I have to make the network again?


Many Thanks!!

---

### Post by mips on 2006-04-25
[QUOTE=hito1]Another question (please don't kill me, hehehe):

when setting alocal network, does one computer remember other computer's name or ip? I mean, I had a shared folder in my comp., did my sister's computer used to see it as "hito\share" or "192.168.0.2\share"? If it were "192.168.0.2\share" will I have to make the network again?


Many Thanks!![/QUOTE]


Not sure to be honest. If you keep all the pc's ips the same then nothing should change. pcs store IP/MAC information in a ARP table.

---

### Post by hito1 on 2006-04-25
That's ok, you already helped a lot. :)

Many thanks again!

---

### Post by Slim Odds on 2006-04-25
[QUOTE=mips]He already has a router, no point to buy another & waste money. It has a integrated modem. He just calls it a modem.

No need to make ubuntu a sharing device. The router will perform this function via the hub.[/QUOTE]

He said he has a Speedstream 5200. That is just a modem, not a router.

---

### Post by mips on 2006-04-26
[QUOTE=Slim Odds]He said he has a Speedstream 5200. That is just a modem, not a route.[/QUOTE]

Sorry but you are wrong. It can function as both. The majority of them are shipped as 'modems' (More the 5100 than 5200).

You can access it via the web interface and change it over to a 'router' with a few mouse clicks.

If you don't believe me then go read the documentation on their website...

As a general rule of thumb, if it says it is a adsl device and it has a Ethernet port then you can be pretty certain you have a router, not always but most of the time. The factory configures it for 'bridged' mode and sell it to companies like sbc etc. This way sbc gets to bundle their own dialer/pppoe/marketing/advertising software crap with it and lock you into their network.

Don't always believe what you are told or read on the box ;)

---

### Post by hito1 on 2006-04-26
It can work as a router. It's doing it right now :).

---

### Post by mips on 2006-04-26
[QUOTE=hito1]It can work as a router. It's doing it right now :).[/QUOTE]

Thanks for confirming that ;)

---

### Post by Slim Odds on 2006-04-27
[QUOTE=hito1]It can work as a router. It's doing it right now :).[/QUOTE]

I stand corrected. 

This gives me some ideas as I have a SpeedStream 5100 and Netgear router/wireless access point.

I may do a little network reconfiguration. :twisted:

---

