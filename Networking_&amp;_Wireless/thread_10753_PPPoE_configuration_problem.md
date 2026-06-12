---
title: "PPPoE configuration problem"
date: 2005-01-11
forum: Networking &amp; Wireless
---

### Post by king_arthur on 2005-01-11
Hi everybody. I have posted this very same thread somewhere else on the forum but perhaps the title wasn't pointing to the real problem and got no comments. Will try again here.
=============================================

I want internet access trough aDSL + modem connection. Problem is that modem is remote and I can only reach with WiFi connection.

If I use pppoeconf it starts investigating my available nic's and , when found, checks for the modem. After having set up the modem step by step and quit pppoeconf, I am left with an error message from pppd winging that wlan0 is an unknown device for rp-pppoe.so 
(and no Internet connection, of course)

Please note that WiFi access is working OK and I can communicate on the home LAN.

PS the most frustrating part of the story is that with Win-XP it all works no problem, setting up two separate connections on the same (WiFi) NIC is easy: one for WLAN and one for aDSL modem. :cry: 

Hope somebody can help

Pieter

---

### Post by hardcandy on 2005-01-11
What brand is the wireless? What driver/module are you using?

---

### Post by hardcandy on 2005-01-11
It really sounds as if the wifi driver/module is working partially, enough to get a local connection. Is it set for ad hoc connection (one wireless to another wireless card) or infrastructure (all wireless cards connect to a gateway/router)?

---

### Post by king_arthur on 2005-01-11
[QUOTE=hardcandy]Is it set for ad hoc connection (one wireless to another wireless card) or infrastructure (all wireless cards connect to a gateway/router)?[/QUOTE]
   First of all, thanks for replying hardcandy.
   I suppose you are relating to the Ubuntu picture, not Win-XP.
 The set up was done by getting a dynamic IP from the wireless router I guess it's the latter (i.e. infrastructure). Setting ip manually however, shouldn't really make a difference IMHO.
   
  If I try iwconfig I can see IP is 192.168.1.2 and that's given by the router and BTW you may get a more complete picture [here.]("http://pjl.ath.cx/index.php?p=293")

---

### Post by hardcandy on 2005-01-11
I'm not quite sure about the problem, the more I read the more confused I make myself. 
1. With the setup you have now, you can connect to the modem AND to other computers? 
2. Even though you can connect to the modem and set it up via it's setup screen, you get a warning message that the modem or the wifi card is not found? Which is not found? 
3. Is there an ethernet connection on this computer as well as a wifi connection? Is the ethernet connection turned off? "sudo /sbin/ifconfig eth0 down"
4. Last question, is this wireless dsl modem just a modem or a modem gateway? Why would windows need two separate connections if the modem is handing out ip addresses and the modem was routing traffic? What brand modem, wireless card?

---

### Post by king_arthur on 2005-01-11
hardcandy,
            
              OK, well, I understand we often have a clear picture but fail to bring it over :D
               
               I'll try first to clarify by answering your questions one by one:
  
 

[list=1]
[*]The answer is yes. The WiFi router provides that.
[*]I did not say something is "not found". If you are familiar with pppoeconf, you will know it first looks for your NICs. Having found one or more (two in my case), it will ask you a confimation and look if there is a DSL modem connected to any of them. In my case nothing is connected to eth0 so the first scan finds nothing. The second NIC scan, done over WiFi finds a modem and asks for parameters such as name and password provided by your ISP and all the usual stuff like starting ppp at boot and so on. Finally, when the program quits and the blue Debian interface turns off, I can read a message on the terminal telling me that _pppd could not find unknown device Wlan0._ That's it. Obviously no internet is available.
[*]There is a ethernet card available indeed (eth0), and I didn't bother turning it off (I may as well remove it) but didn't think it could interfere with anything as at my place it was working all right. (WiFi connection)
[*]The modem is a modem only, connected to a WiFi router. It's supplied by Italian Telecom, I don't know the brand but, frankly, I don't think it matters though, you must know it's connected with ethernet cable to the WiFi router.Don't know the make of the WiFi card either. It's Taiwanese, Realtek 8010L chip or something like that.
[/list]Having said the above, pls note that without touching anything, just starting from a different partition, a out-of-the-box Win-XP install, setup by a newbie works.
               Very, very disappointing for both, him and myself.... :-&
               
    As I tried to explain on [the post]("http://pjl.ath.cx/index.php?p=293") I referenced you, at home my setup is different as my WiFi base is connected to aDSL modem/router. I have a web interface to that one and can setup so that the router takes care also of maintaining the aDSL connection. In that case, my Airport Express base is simply acting as a bridge but can also work as a router. The latter, pretty much the same as at my friend's place.
               
               Hope this sheds some light on the setup I am trying to get into gear :D

---

### Post by hardcandy on 2005-01-11
OK, the modem is not supposed to be doing anything because it has a wifi router between it and  the computer. The modem should already be set up and open to the internet.  Any pppoe configuring is bewteen the wifi router and the modem and that seems to be working OK, Forget about pppoe on the computer, this is a basic networking problem. "sbin /sbin/iwlist"  show anything? Basically you want to set up a wireless connection with dhcp through your networking config tool under Computer-->Network. You could turn off WEP on the router  to make the setup a little esier and then turn it back on after everything is working OK.

---

### Post by king_arthur on 2005-01-11
hardcandy,
   
   not so sure what to say, you might be right but to me networking seems OK...
   
 Anyway, I would be more than happy to try any suggestion coming up from this forum but as for now I can't do anything. The computer is out of reach till Sunday.:shock:
   
   Up to then, I'll have to wait but in any case I would like to have some* strategy* ready.
   
 As often the case with computers, it's becoming a matter of principle (and pride) to get the damn thing working better than under Win-XP! ](*,)

---

### Post by hardcandy on 2005-01-11
See the wireless local network is doing good because the wifi router is handling the network. When you go to try and set up PPOe on the computer, naturally it cannot find the modem since it is behind the wifi router. Call the friend up and ask him to reboot Ubuntu and see if the web browser can connect to the internet.

---

### Post by king_arthur on 2005-01-11
[QUOTE=hardcandy]When you go to try and set up PPOe on the computer, naturally it cannot find the modem since it is behind the wifi router...[/QUOTE]This is actually not true. The pppoeconf utility finds the modem and writes a configuration.
   Trouble starts after this, when pppd tries to take control of the modem.
    
    To my opinion, the problem is within the script in **rp-pppoe.so** that does not accept Wlan0 as a valid interface. (It is expecting  ethx instead)
    
    Sunday I will check also this option and post here the results accordingly

---

### Post by hardcandy on 2005-01-11
Ok, I have a Bellsouth Westell ADSL modem. I have a Linksys wireless gateway/router connected to the Westell ADSL modem with Cat5 cable. My 4 computers never deal with the modem. They get their IP addresses,etc from the Linksys gateway/router. As far as they are concerned, both with wireless and wired connection, the Linksys gateway/router is their ticket to the world outside. 
The Linksys gateway/router uses PPPOe to connect to the modem. 
Now if your computer is somehow seeing the modem behind a wireless router/gateway, something is wrong. > you must know it's connected with ethernet cable to the WiFi router and if the computer is seeing a "modem", I'm wondering if it is not seeing another computer with a wireless card because it is in "ad-hoc" mode (which means it will connect to other computers since a wireless gateway/router is supposed to not be present). I would check the settings and make sure the wireless card is in "infrastructure" mode (which means it knows to look for a gateway/router).

---

### Post by king_arthur on 2005-01-12
hardcandy,
    
    thank you very much again for your reply.
    
    I realize that this WiFi stuff si quite complex and as I am fairly new to it I'll need to do some more reading. :)
    To deepen my knowledge I am starting with the [Linux Wirelesss how-to]("http://www.faqs.org/docs/Linux-HOWTO/Wireless-HOWTO.html#ss3.2") and hopefully, by next Sunday I'll understand enough to solve the issue or, at least, return here with correct answers.
    
 One more question: could you tell me the difference between a wireless point and a wireless router? I am suspecting that the WiFi device my friend is using to connect the aDSL modem is not a router...
    
    More about this soon, 
    
    cheers

---

### Post by hardcandy on 2005-01-12
A router can be a gateway and a gateway (wireless access point) can be a router. It's really sort of a name game. 
A gateway connects one network (your home network) to another network (the internet). A router takes packets from one machine and sends them to another machine. 
If your friends wireless access point has a setup screen and it is the only "router" in his network, see if there is an option to choose "gateway" or "router". Set his to "gateway". 
A good link with comprehensive home networking info and good wireless setup info:
[http://compnetworking.about.com/od/homenetworking/](http://compnetworking.about.com/od/homenetworking/)

---

### Post by king_arthur on 2005-01-30
Well, it took me a while to get hold of the problem but now that my WiFi networking is working fine, I though it was time to give something back to the community I got so much from.. [img]http://www.ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]
    
 Basically, it appears that Warty probably needed a more recent or advanced pppoe package. I found it (the source) at the RoaringPenguin and, once compiled the rp-pppoe I was given a simple but fully functional Graphic interface (with blinking, coloured leds as well as bistream graph) which could get all the various parameters and take care of starting and stopping the aDSL connection through WiFi. 
     Nice. Find it [here]("http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php") 
 Actually, I also posted a question to the package developer/mantainer David F. Skoll who sent me a reply the day after pointing me into the right direction. Linux is a great community!
     
 Having finally connected the main computer to the internet I was only half away as I needed LAN support. I simply created a wlan0:0 virtual interface to my WiFi NIC to obtain this, hence allow one other computer (my friend's 11 years old brat) to surf the internet using the Ubuntu-box as a gateway/router.
     
 On the internet I found a script named "routing" which I installed into /etc/inet.d/routing in order to setup the netmasking and NAT routines necessary to allow access to the outher world from the LAN. I tested it at my place with the iMac and it worked surprisingly well.
     
 To make networking setup easier for the computers connected to the LAN, I installed from "Universe" a Ubuntu/Debian package named dnsmasq: that wiil take care of all domain name resolving on behalf of the connected clients and makes it trivial to setup other computers as gateway and DNS will have the same ip of the Linux-box. (on this sub-network that is 192.168.2.1) 
     This can be done simply with "apt-get install dnsmasq". The beauty of Linux and Debian!
     
     Now, making the above setup permanent and starting it automatically is just a matter of two simple steps: 
  
 

[list=1]
[*]writing the NIC configuration in /etc/networking/interfaces
[*]running "update-rc.d **routing** defaults" to create the necessary symlinks for the script at the various runlevels.
[/list]That's all there is folks! As usual, when you know how-to, with Linux things get real easy.[img]http://www.ubuntuforums.org/images/smilies/eusa_clap.gif[/img]
     
     Hope this post is written in a way you can uderstand and find usefull...

---

