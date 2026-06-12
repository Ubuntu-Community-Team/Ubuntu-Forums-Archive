---
title: "Questions on setting up VPN, optimizing server functions"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by tsunamikitsune on 2011-03-01
For a few months now, I've been running Ubuntu server on an old tower in my house. As sort of a hobby/pastime, I've been playing around with it to see what kind of magical things I could do with the power of networking. Thus far, I've:

-Set up a RAID in the server and used Samba to share the space with my housemates (who thoroughly enjoy streaming music and movies from it to their computers and my living room media center PC)
-Set up Torrentflux for more centralized torrenting (why waste power leaving our computers on all night when there's an always on server?)
-Set up a dedicated [Minecraft]("http://www.minecraft.net/") server
-Made said Minecraft server accessible from the internet with a DynDNS static URL
-And most recently, made music streaming available anywhere with Subsonic (albeit a little slow on our 3G phones)

Anyway, my next endeavor is to hopefully set up a VPN. Feel free to laugh me off the forums if I misunderstand the way such a thing works (I'm still learning a lot about this stuff), but the way I've read about it, it sounds like I can connect into the house's network from anywhere on the internet securely and much like I'm physically connected. Free to SSH into the server, maintain the router settings, manage my torrents, and browse the samba shares from the comfort of my not-home.

Hopefully I'm understanding this right, because it would be fantastic to do these things when I'm out of town (especially when something goes awry with the server or even my housemates' computers, since I'm the one they come crying to for help). I don't really have a clue how to start setting such a thing up, though, so any help (be it a link to a guide or personal instruction) would be greatly appreciated.

VPN help aside, I have some pretty dumb networking questions that may also get me laughed off these forums:

First off, how much difference does 10/100 megabit Ethernet and gigabit Ethernet make? Currently, my router only has 10/100 megabit ports. Does that mean that the server's network transfers will be slower than connected by a gigabit port? What about internet transfers? I assume the latter isn't going to get faster considering our service is 12 megabit, but I thought it would be worth asking.

Secondly, (in my head, I'm thinking this is a really silly question, but it might have some logic behind it) would it be possible to install a second ethernet card in the server and divide the load between internet and local network for better speeds? As in, one card handles all the music streaming and file transfers within the house's LAN, while the other card delegates off-site connections (like the Minecraft server and mobile music streaming)? If I'm just dreaming, feel free to wake me up. :P

Anyway, sorry for the wall of text, but I thought it better than opening a bunch of topics for different things. Any help is appreciated, as is any correction to my networking delusions. Thanks in advance!

---

