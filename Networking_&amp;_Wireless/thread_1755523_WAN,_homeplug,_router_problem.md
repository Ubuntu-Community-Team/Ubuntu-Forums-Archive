---
title: "WAN, homeplug, router problem"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by Diderik From on 2011-05-11
Hi!

Hopefully someone can help me find the best solution. I get internet via a cable moden just behind the tv. Until now, I have kept all sorts of computer components under the tv. In my new apartment, there is a technical room in which I plan to stow all these things, but I need a fast connection between both the modem as well as the mediaplayer and the router in the technical room.


Present scenario:[FONT=Fixedsys]

                                                          [FONT=Courier New][SIZE=1]___________________________homeplug<------------> switch<------> NAS etc.
cable modem<-->router<----<
___________________________media player with switch<--->media player 2
     

[/SIZE][/FONT][/FONT]Wanted scenario:

[FONT=Fixedsys][FONT=Courier New][SIZE=1]cable modem<-->homeplug <------------------------->router<------->all sorts of stuff
                _______________|
__________media player with switch <---> media player 2[/SIZE][/FONT]
[/FONT]
It seems the modem must be connected to the WAN port of the router, but then I cannot get a connection back to media players. It tried using an ethernet spliter (something like this: [http://www.amazon.com/Cables-Go-2-Port-Splitter-Combiner/dp/B000Q5UMEI/ref=sr_1_7?ie=UTF8&s=electronics&qid=1215884619&sr=1-7](http://www.amazon.com/Cables-Go-2-Port-Splitter-Combiner/dp/B000Q5UMEI/ref=sr_1_7?ie=UTF8&s=electronics&qid=1215884619&sr=1-7)) over the homeplug, but -- as expected -- it did not work. Another option would be to get a usb-powered small router, but I only find wireless ones.

Does anyone have a suggestion? Is it possible to plug the modem into a switch, and then to the router for it to share the connection?

---

### Post by lz1dsb on 2011-05-11
I don't really get your scenario. What kind of network interface does your media player device has?
Basically you have a Cable modem which is directly connected to a router, right? Is this also a wireless router?

---

### Post by Cheesehead on 2011-05-11
According to your network sketch, it looks like your media players were behind the router, and now are still behind the same router. 

So if the media players don't connect anymore, that smells like a possible hardware fault to me. Have you checked for loose connections? Perhaps a bad cable? Or a port on the router?

---

### Post by Diderik From on 2011-05-11
Thanks for your answers. The router is wireless, yes, but that is irrelevant, I think. The media player has a standard interface like you'd expect to find on most media players. (They are a Sonos and a Popcorn Hour.:popcorn:) It is hard to explain, but it boils down to connecting my cable modem and my media player to my router via one ethernet cable (in this case substituted with a home plug). Is this at all possible without a translational gateway or some other extra box? I hope I'm a bit clearer.

---

### Post by lz1dsb on 2011-05-13
What kind of router it is? Does it have Ethernet inerfaces? How many? 
In general that's the idea of your home router, to aggregate the connections from your home devices into one connection to your provider.
If you are able to give me more detail, probably I can also get in a bit more details.


Cheers,
Boyan

---

### Post by Diderik From on 2011-05-18
Thank you for your answer, again! My router is a Netgear WNR-3500, it has 4 ethernet ports and one WAN port. The thing here is getting both WAN and ethernet over one cable... Anyway, I have decided to have my cable company add an extra outlet in my technical room. That way, I can circumvent this problem.

Thanks!

---

### Post by lz1dsb on 2011-05-18
> **Diderik From said:**
> The thing here is getting both WAN and ethernet over one cable... 
For those SOHO devices technically the WAN port and the LAN ports are the same. But the WAN port can only be used as a WAN port, you can't change that on the config. For the Linksys routers if you chnage the firmware to some of the freelly available variants, you have much more options including using the WAN port as a LAN port which is quite handy. 
For my Linksys router I'm using DD-WRT, which also supports many other vendors. I saw that your router is also supported:
[http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)
So this is another option you could use.
 
 
Cheers,
Boyan

---

