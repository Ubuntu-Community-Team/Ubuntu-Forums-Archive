---
title: "seeking home LAN sharing &amp; interaction"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by SaintDanBert on 2010-12-27
I have several linux laptops and a desktop-server running Ubuntu Lucid. I also have Android(tm) and iPhone(tm) devices. All of these connect to my at-home LAN using wireless or wired ethernet through my home-LAN router+gateway and on through the cable modem. In addition, printers are network capable and deployed on the same at-home LAN.  All of that works.

Now I want these various and several computers to share files and services (web, print, media) with each other and interact with each other on this same at-home LAN. [color=green]Can someone point me to a HOWTO or similar application notes that discuss what I need to do?[/color]

[list]
[*]Since all of the at-home LAN devices use DHCP and get dynamic IP addresses, any /etc/hosts files that I create stop working when leases renew.
[*]I can configure "fixed IP address" settings, but then wifi roaming is a royal pain in the anatomy -- at least the ways I know how to do this.
[*]I can use the router+gateway to give a specific IP address to each hardware (MAC) address, but then when folks visit it is irksome to setup so that we might give or get the odd file or they might print the odd document.
[*]I vaguely remember that there was a way to generate dynamic "local network" host names or similar attached to dynamic "local network" IP addresses all under the control of DHCP-server and supporting utilities. I'm dashed if I can find anything about that other than really antique details.
[/list]
Once folks stop laughing at what I'm certain is a totally noob question, I hope that there is a solid HOWTO that just works out there and that some kind soul will tell me where to find it.

Merci d'avance,
~~~ 0;-Dan

PS/  I apologize in advance if this question has been asked and answered in the past. One must know enough to know what to search for and get meaningful results.  ~~~0;-/

---

### Post by misterbiskits on 2010-12-27
I for one am confused about what you are asking.
You want to share files between computers on the LAN?

---

### Post by Boondoklife on 2010-12-27
if you are worried about dhcp and being able to have a local dns to do name resolution, then get a router you can flash with dd-wrt firmware and setup dnsmasq to be your dhcp and dns. This will allow you to assign ips by mac and also resolve hostnames to those ips.

Now people that are not setup in the the mac/ip/hostname section will not be able to be referred to by name, but then again they are just visiting. they will be able to get to your devices by name however.

As an added bonus since you are running your own dns, you can do some awesome adblocking and site filtering which will speed up access tremendously.

I for example have a nas, wii, 2 laptops, and a windows mobile phone; all of the devices have their own names which are resolvable from any device that connects to my network.

---

### Post by SaintDanBert on 2010-12-28
obviously you have such a router with DD-WRT.  Which router hardware did you decide to use for this effort?

I've thought to do this for a while. There are loads of Linksys(tm) "blue boxes" available  for pennies through various salvage and recycle outlets, but found the matrix of hardware and firmware editions daunting in the time and headspace I had to devote to the effort. I'm not married to Linksys if other hardware works out better ... as in easier, less trouble, etc as well as technically.

Thanks,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-12-28
> **misterbiskits said:**
> I for one am confused about what you are asking. You want to share files between computers on the LAN?

"Share files" might as well be a euphemism akin to "walk across Asia."

There are dozens of ways that a linux box might share files with another linux box.  There are another dozen to share between linux and the internet. There is one way to share between win-dose boxes. There are a couple of ways to share between linux and win-dose. And that is just for moving files from place to place.

Next we add services -- backup, dropbox(tm), web pages, streaming audio, streaming video, calendar, contacts, printing, faxing, aggregation, etc -- all running on some hosts within the LAN and available to whatever participates in the LAN based on some access profile.

Next we add "observers" -- HDTV, phones, game consoles, net-storage, etc.

If I get papers that I think will be meaningful to my wife, I put them on her desk.  If I get e-papers, I'd like to deal with them in-house rather than send her email -- off the LAN, thru the ISP, back on the LAN -- or dropbox from me to cloud and back to her.

Does this 'splain my interests?
~~~ 0;-Dan

---

### Post by Boondoklife on 2010-12-28
The easiest way to pick a router is to look at what you need for wired speeds (10/100 or 10/100/1000) and wireless speeds (b/g/n) and then look through what you can get at your local retailers or even ebay (my preferred option).

Once you have a short list of routers that will do what you want, then just look here to see if they are compatible. [[LINK]("http://www.dd-wrt.com/site/support/router-database")]

If you are looking to have a central repository for files then look into a western digital mybook world edition II (Blue Ring) NAS. It will get you speeds of 4-8 MB/s for transfers and one option is dual 750GB drives in RAID 1 which means if one drive dies you can replace it and not loose data. It should be decently priced (sub $200 range easily). If you need a faster connection for say multiple HD transmission simultaneously, then you may want to look into a higher end NAS.

Now for transfers you may want to go with ftp when ever possible as it has a lower overhead then smb/samba/windows file sharing. I would however keep samba running and as an option as it does have a higher compatibility for straming and access than ftp in some cases.

---

### Post by SaintDanBert on 2011-01-06
while I'm tracking down hardware for DD-WRT or OPEN-WRT use, might I get some help with a related topic?

I have a road warrior laptop. How do I configure for this:

[list]
[*] At home, the DD-WRT dance will give me a fixed IP address, etc
[*] On the road, I'll need to dance DHCP with whatever access point I choose to use
[/list]

Many access points (AP) while "open" take one to an initial web page that requires end-user interaction -- usually EULA acceptance and similar. One example is my local hospital where they have open wifi for patient and non-staff use.

I don't mind a dance and interaction the first time I use such a site.
I want to store the configuration and re-use it ... without the need for me to remember any details -- each time I return to the same place.

Under win-doze, Lenovo has a helper application that permits me to store a large blog of network details under a name of my choice. At startup, this helper app feels the available network(s) matching with whatever is already on file. I can then configure automatic or manual selection of the matching network.

Under *-buntu, **wicd** comes close, but I cannot discover how to store any web page dance details for mostly automatic processing once a connection happens.

Suggestions please,
~~~ 0;-Dan

---

