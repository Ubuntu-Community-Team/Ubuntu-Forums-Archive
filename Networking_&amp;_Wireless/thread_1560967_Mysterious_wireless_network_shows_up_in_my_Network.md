---
title: "Mysterious wireless network shows up in my NetworkManager list."
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by ldt on 2010-08-22
When I search for “NetworkManager icons” I get about 250 posts so this newbie question may have been asked before. In the list of available wireless connections I see an unsecured connection called “hpsetup” which has an icon beside it that looks like a monitor broadcasting wireless waves.  
 

 1.) What does the “monitor” icon mean?
 

 When I try to connect to it I actually get a connection to my (secured) wireless router which also shows up in the list with its correct name. I'm worried that my wireless connected computer is somehow broadcasting itself and that other's within range are seeing it too as an unsecured connection.
 

 2.) Am I somehow inadvertently exposing my computer to the whole world to see?
 

 I'm running 64-bit Ubuntu 9.10
 

 Thanks.

---

### Post by ldt on 2010-08-25
A few days ago I asked a similar question and got zero replies. I thought it was a newbie question but now I'm not so sure. So let me re-phrase it and try again.
 

 I'm running 64-bit Ubuntu 9.10. I'm in a commercial area so when I click the NetworkManager icon I normally see 6-10 wireless networks. My own is a Linksys router secured with a randomly generated 40-bit password. Sometimes, but not always, I see an unsecured network (called “hpsetup” but that may not be important). The mysterious thing about it is that it has an icon beside it that looks like a computer monitor broadcasting wireless waves. When I connect to it I actually get a connection to my own secured network. As I said, sometimes it is there and sometimes it isn't, so I assume that it is due to some other router in the area and not mine. But I get the uneasy feeling that I'm being hacked but I don't know enough about networking to understand what is going on.
 

 Questions:
 What does the “wireless waves monitor” icon mean?
 Should I be worried about it?
 

 Thanks.

---

### Post by Iowan on 2010-08-25
Threads merged.
Generally a "bump" (not over once/day) will work as well as a new thread. :)

---

### Post by ldt on 2010-08-29
Here is another clue. The mysterious “hpsetup” wireless network was absent from the list for a couple of days but it is back now.  I disconnected my Linksys router so that my network connections were dead. I then tried to connect to the (unsecured) hpsetup network. Again it tried to connect to my private wireless but failed.
 

 Of the four computers on my LAN, two are WindowsXP. They are the only ones that could possibly be running any HP software. So I shut them down but the “hpsetup” network is still visible and it still connects to my personal (secured) wireless router.
 

 Actually, when I try to connect to ANY of the unsecured wireless networks in the list (many of which I know where they are coming from) I always get a connection to my personal secured network. Or at least that is what the NetworkManager says.
 

 So maybe the “wireless monitor” icon is nothing special. Just a thought – if there is a laptop in the vicinity with a 3G connection, like a Sprint USB connector, would that create a wireless network that would show up in the list? Could this be what the “wireless monitor” icon stands for?

---

### Post by conradin on 2010-08-29
I bet someone has a wireless printer you're detecting. Pinters have an amazing amount of network hardware these days including website hosts, network managers, boot agents and more. 

I recommend getting a firewall for any and all who use the networked devices. also, visit [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
to see what ports are looking like to uses across the net.

---

### Post by MattBD on 2010-08-29
I just Googled HPSETUP and came up with two possibilities:
1) It's a Hewlett Packard wireless printer. I found the following quote:
> Hewlett-Packard networked printers are usually configured to have an ad-hoc 
WiFi network with the SSID named "hpsetup".  This allows one to print to the 
printer by joining the ad-hoc network.  Of course, this assumes that the SW 
drivers have been installed onto the host computer.

The WiFi radio can be disabled via a configuration item in the printers 
embedded web server.  It is also disabled whenever the Ethernet cable is 
attached.
2) It's another computer broadcasting a viral SSID. What I read suggests that this results in them broadcasting as an ad-hoc access point.
Two resources I found about this were at [http://www.wlanbook.com/free-public-wifi-ssid/](http://www.wlanbook.com/free-public-wifi-ssid/) and [http://blogs.techrepublic.com.com/hiner/?p=602](http://blogs.techrepublic.com.com/hiner/?p=602)
EDIT - not actually a virus, apparently it's only viral in terms of how it spreads, and there's no actual payload. It's actually quite interesting how it happened!

---

### Post by ldt on 2010-08-30
Very interesting. The party next door that I suspect of having a wireless printer is not in but I will check with them eventually. But I'm pretty sure the wireless printer diagnosis is correct. All of the articles talk about how to delete this in Windows. I don't see any way of deleting this from my Ubuntu NetworkManager list and the documentation for it is pretty thin – mostly just installation and setup stuff. Any suggestions on how to get rid of this?

---

### Post by MattBD on 2010-08-30
I think you should be able to do it by right-clicking on NetworkManager, selecting Edit Connections and deleting the offending connection.

---

### Post by ldt on 2010-08-30
Yes, that works. My mistake was that I was trying a right click on the “hpsetup” that appeared in the list instead of the NetworkManager icon itself. Thanks so much for your help.
 

 By the way, when I edited the connections the “hpsetup” showed “never” for last connected. So I never did actually connect to it although I clicked on in several times.

---

