---
title: "I still can't open ports for torrents. I've tried everything (I Know of)."
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by Baltimora on 2010-03-25
Hi there people. Its not often I actually post something on a forum because I usually find an answer myself...but not this time. 2 days spent trawling the web has come up with nothing so here goes.

I've been using Ubuntu 9.10 now for 2 months and everything is going well apart from the fact that I can't get any ports open for using a bit torrent client. I have been using torrents for years with various Windows OS's so I am well versed with the entire process i.e. opening ports on the router, configuring firewalls, torrent client settings, static ip's and all that jazz. I've also tried using Upnp and I can see that I get a request from the torrent client on the right port but every time I hit the "Check Port" option, it comes back as saying not open. I've also used canyouseeme.org and the shields-up site and they keep telling me that the ports are all closed.

I've just updated the firmware on my router - no change. I've even tried a hard connection to just the modem (so not plugged in to my wireless router at all) and still no ports could be seen. I've just run a virus scan with clamtk and I'm clean.


Here are all my technical specs:

OS - Ubuntu 9.10 Karmic Koala
Firewall - I had been using Firestarter but uninstalled that and am now using Gufw which I have DISABLED. I've checked this by entering $ ufw status in the console.
Router - Linksys wrt160n (version 1)
Router firmware -[FONT=Verdana]DD-WRT v24-sp2 (10/10/09) voip (*SVN revision* 13064)[/FONT][FONT=Verdana]Wireless network card - Edimax [/FONT]RT2800 802.11n 
Torrent clients - I've tried Transmission and Deluge.


Any help greatly appreciated because I'm at my wits end.

---

### Post by gordintoronto on 2010-03-25
Funny, it never occurred to me that ports might be an issue when I started using Transmission.  Have you checked the processes in System Monitor?

Some ISPs block bittorrent transfers.  Any chance yours is one of them?

It's my understanding that Firestarter is not the actual firewall, it's just a graphical front-end.

---

### Post by Baltimora on 2010-03-25
> **gordintoronto said:**
> Funny, it never occurred to me that ports might be an issue when I started using Transmission.  Have you checked the processes in System Monitor?

Some ISPs block bittorrent transfers.  Any chance yours is one of them?

It's my understanding that Firestarter is not the actual firewall, it's just a graphical front-end.
I'm with Virgin and they don't block torrents.

I also realise that Firestarter and Gufw are just GUI's for iptables but I've got it disabled. This why I'm pulling my hair out :(

---

### Post by Grenage on 2010-03-25
How odd!

I'm also with Virgin, and currently using their usual supplied DG834 on DSL.  In my last house we had standard Virgin cable, but there were no issues there, either.

What port range are you using?  While I now only use rtorrent on my boxes, I've used Deluge without error.  Do any of your torrent clients have the ability to check that a port is open (I know deluge does)?

---

### Post by adam814 on 2010-03-25
This is a shot in the dark, but are you trying to use ports under 1024?  AFAIK that will only work if the application listening on the port is running as root since low port numbers are reserved for system services.  I don't run anything as root I don't have a good reason to (and I don't have a good reason to run transmission as root).

---

### Post by Baltimora on 2010-03-25
> **Grenage said:**
> How odd!

I'm also with Virgin, and currently using their usual supplied DG834 on DSL.  In my last house we had standard Virgin cable, but there were no issues there, either.

What port range are you using?  While I now only use rtorrent on my boxes, I've used Deluge without error.  Do any of your torrent clients have the ability to check that a port is open (I know deluge does)?
I changed the default range so I'm just using port 65525. And yes, I have used the "Test Active Port" function in Deluge and it always comes up as closed. It is the same with Bit Transmission as well.

---

### Post by wojox on 2010-03-25
> **Baltimora said:**
> I changed the default range so I'm just using port 65525. And yes, I have used the "Test Active Port" function in Deluge and it always comes up as closed. It is the same with Bit Transmission as well.

Did you log into your router and port forward 65525

---

### Post by Baltimora on 2010-03-25
> **wojox said:**
> Did you log into your router and port forward 65525
Of course. I allowed UDP and TCP protocols and have set up a static ip address.

---

### Post by Grenage on 2010-03-25
I use 16370-16379, but it shouldn't make any difference unless the ports are down in the service range.

Are you having issues with any other forwarding, if you are forwarding anything else at all?  [s]You sound pretty switched on, but is it possible that the DHCP address that your machine received from the router is now different to the one it _was_ forwarding to?[/s] <- scrap that, after reading your next post.

I am out of suggestions.  If the router forwarding works fine on other OSs then we can rule that out.  Your ports and IP are static, so we can rule out error there.  The only thing that really leaves is a software firewall on the machine itself, but I have a pretty default Ubuntu install here and I'm not getting blocked.

---

### Post by Baltimora on 2010-03-25
> **Grenage said:**
> I use 16370-16379, but it shouldn't make any difference unless the ports are down in the service range.

Are you having issues with any other forwarding, if you are forwarding anything else at all?  [s]You sound pretty switched on, but is it possible that the DHCP address that your machine received from the router is now different to the one it _was_ forwarding to?[/s] <- scrap that, after reading your next post.

I am out of suggestions.  If the router forwarding works fine on other OSs then we can rule that out.  Your ports and IP are static, so we can rule out error there.  The only thing that really leaves is a software firewall on the machine itself, but I have a pretty default Ubuntu install here and I'm not getting blocked.
I don't use port forwarding for anything else other than bit torrents. As for DHCP - I've got 5 DHCP slots set from 192.168.1.80 - 192.168.1.84 for Playstation, iPhone etc and I've also set  a static ip of 192.168.1.100 so there shouldn't be a problem with that.

---

### Post by Baltimora on 2010-03-25
What really gets me is the fact that ports seem closed even when I just use the modem and not the router.

---

### Post by gordintoronto on 2010-03-25
Is there any possibility the very high port numbers can not be used?  Have you tried 4000, for example? Or even 16000 - low enough to flip the high-order bit.

---

### Post by Baltimora on 2010-03-26
I've tried a few different ports but alas no joy.

---

### Post by hatalar205 on 2010-03-26
As far as I have understood, your main problem is not about **downloading** but **sending data**, isn't it?

---

### Post by Baltimora on 2010-03-26
In a word, yes. Basically I can connect to seeders no problem but connecting to peers is hit n'miss. When there are lots of seeders i can still download at maximum capacity but if there is, for example, only one seed and several peers then download speed is mega pants. And as for when i just want to seed - its nigh on impossible.

---

### Post by hatalar205 on 2010-03-26
> **Baltimora said:**
> In a word, yes. Basically I can connect to seeders no problem but connecting to peers is hit n'miss. When there are lots of seeders i can still download at maximum capacity but if there is, for example, only one seed and several peers then download speed is mega pants. And as for when i just want to seed - its nigh on impossible.

Under Deluge settings. There is a choise "allow remote connections". Try it. But, it can cause some security problems. I was only in that way able to send data. And as a suggestion not try to seed lots of files on the same time.

---

### Post by Baltimora on 2010-03-26
I've tried the "allow remote connections" option for a while now and still no change. I also only ever have about 4 or 5 torrents on the go at the same time.

---

### Post by Baltimora on 2010-03-27
Bump.

---

### Post by Baltimora on 2010-03-30
Nothing a fresh install of Ubuntu couldn't fix. What a crappy solution though.

---

### Post by 98cwitr on 2010-03-30
having the same problem...I have been quick to conclude that it's my ISP (Time Warner) but after switching from Vuze to Transmission with a little improvement, I am assuming it's my network and/or machine.

I have allowed the port access via *iptables -i* commands, my "gateway" does not permit port forwarding or UPnP and now my PS3 keeps saying that "Network Cable us Disconnected" sporadically. It's really getting on my nerves. 

I am betting it's the equipment, but when I switched apps it improved...so I'm baffled. EVERY port I try to test says refused or closed, even when allowed through iptables

---

### Post by Grenage on 2010-03-30
What gateway do you have?  Is it possible to try an alternative router?

---

### Post by 98cwitr on 2010-03-30
Ambit, dont have another cable modem to test with. I do have my Netgear router, which supports PFing and UPnP, but can only set it up as a bridge and the protocols wont pass through the gateway. Im going to my girl's apt tonight (essentially same service) and ill see what kind of connection she gets when using transmission to weed out the ISP.

---

### Post by Chonnawonga on 2010-06-08
I'm having the same problem. Did you ever find a solution?

---

