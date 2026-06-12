---
title: "Networking Problem - Help Needed."
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by xenex79 on 2013-05-25
Hi I'm having an issue with networking that I would love to get solved, here's the scenario.

I have a freshly installed Ubuntu 13.04 server in one room that connects to the network by cable via a router located in another room, I then have another box (Win7) in the same room as the server that connects to a spare nic on the server, both of these machines are headless, I connect to the server to control it using either Webmin and/or SmarTTY from a wireless laptop, I use the same laptop to connect to the Win7 box using VNC, this all worked fine until I decided to reinstall my server.

My issue is that before I decided to setup my server box again I previously had the Win7 machine able to show on the network through the server without it needing a second cable going directly to the router, I cannot remember how I was able to get that setup but I probably read it on the net somewhere and it's been as long that I cannot for the life of me track down how to get this configuration to work again, If I can remember correctly I think it had something to do with bridged connections but unfortunately I have not remembered how It was achieved in the first place.

Any help in getting this setup to work again would be much appreciated.

---

### Post by Iowan on 2013-05-25
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a Wiki page on Internet Connection Sharing. 
Just to cover bases, [here]("https://help.ubuntu.com/13.04/serverguide/network-configuration.html#bridging") is a Server Guide article on bridging.

---

### Post by xenex79 on 2013-05-25
I managed to get it working just 10min before your reply but thanks anyway, thanks for the links 10/10 for the effort \\:D/
```
[COLOR=#333333][FONT=monospace]sudo apt-get install bridge-utils[/FONT][/COLOR]
```
This was indeed the element I was missing, although I don't think the way I have set the bridge up is proper or at all orthodox but for now it works, I'll check those links more in-depth later but at first glance neither one seems to specifically mention my scenario but I'm sure the technique is probably related and in there somewhere.

---

