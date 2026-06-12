---
title: "How do I make a network bridge between Wifi (internet) and Ethernet (network)?"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by TheOnlyMrK on 2009-10-13
I've been searching around Google for awhile now and all the info about network bridging on Ubuntu I could find was out of date and/or I couldn't understand it. So if I'm bad at searching or network bridging just isn't popular in the Ubuntu world I'm not sure.

Anyways, basically how my network goes is this... I have my laptop connected to my neighbors WiFi, it bridges the connection to the Ethernet card and the Ethernet plugs into my router, then my desktop, PS3, and so on connect to my router. The laptop is currently running Windows 7 64bit to bridge the connections and does fine but if not restarted every 3 to 4 days it starts to freeze up and lag my internet connection. Since the laptop is used for nothing but give internet to the rest of my house I wanted to put a less resource intensive operating system on it like Xubuntu, but the problem still remains, how do I create a network bridge from the WiFi card to the Ethernet card?

Also, would Ubuntu Server Edition be a better choice for this? I've never used the server edition so I have no clue what it is like or what all it can do. All the computer does is sit there and bridge connections, it's used for nothing else, so I just need a real light OS with nothing fancy, I just want to stick with the Ubuntu flavors as I'm still learning Linux.

AND, yes my neighbor knows I use his internet, me and him talked about that a long long time ago.

Edit: Forgot to add in, if anyone knows if network bridging is available on the PS3 too, please tell me, because I never use my PS3. We're out of money, can't afford games for it, so it just sits there and collects dust, I'd think a PS3 could handle running 24/7 better then a crappy Wal-Mart laptop that gets so hot I could bake a cake on the CPU (160F under medium to heavy load).

---

### Post by TheOnlyMrK on 2009-10-13
Well it is apparent after hours of searching the internet, and no replies here either, that Network Bridging is the one thing Linux can't do, or at least not WiFi-to-Ethernet, looks like Ethernet-to-Ethernet would be fine. Surprising since Windows XP, Vista, AND 7 can do it in two mouse clicks, wouldn't be surprised if Mac's could do it too but I dunno, I've never touched those things.

If I do ever find anything out about how to setup a bridge that works, gives you internet, doesn't require user interaction once setup, and doesn't randomly disconnect for no reason at all, like all the other ones I've found, I'll post it here for anyone it may be useful to.

---

### Post by Iowan on 2009-10-13
> **TheOnlyMrK said:**
> Well it is apparent after hours of searching the internet, and no replies here either... Four hours isn't an eternity (unless you're holding your breath...)
I see Karmic has [this]("http://manpages.ubuntu.com/manpages/karmic/en/man4/bridge.4freebsd.html") man page.  [Here]("https://help.ubuntu.com/community/VirtualBox/Networking") is another article I found - but can't claim to have read.
Fir Internet/connection sharing, there's [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page - with a [link ]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") to sharing wired via wireless (kinda backwards from what you need...)

---

### Post by ArielEnter on 2009-10-14
I'm kind of obsessive, and I worked in the following for about tow days in a row: I wanted to share the Internet I was getting from my wireless with another computer trough the the Ethernet using a crossover cable. As you said is super easy to do it on windows, and as easy to do it in Mac Os (I have a mac runing the tree OS :)
 Getting to make it work on Ubuntu was like a living hell. At the end today it's working but I don't know how it came out to work. Yesterday it wasn't working and today I turned on and is working, WTF? Any way since I don't know what made it work, all what I can do is give you some hints:
 

 1.- I download the bridge-utils.
 

 2.- Some thing that I believe was very important for me, was to find out the following: Usually in the right upper side of the screen there is a button to manege your network connections right?, if you right click on it you can chose to edit the connections. Once there, you will edit Auto eth0, in the tab where it says Ipv4, and you will chose Method: Share with other Computers. This way, your computer will work kind of a DNS server, and it will assign an IP to the other computer.
 

 That's all I can say for sure. I did a thousands of things, but I think I change every thing back to normal.
 This is the kind of things I did:
 

 1.-I change /etc/network/interfaces a lot but now I only have:
 auto lo 
 iface lo inet loopback
 So I don't think that made the trick.
 

 2.- I installed fire started a lot of times and did every thing that was suggested in the tutorials, but I uninsatlled back so I don't think that's it either.
 

 3.- I follow the tutorial using ipmasq and dnsmasq but after finishing I Uninstalled both packages.
 

 4.- I created a bash that is executed at the beginning of the system start up, that has the following code:  
 echo"Iniciando Bridge..." 
 /usr/sbin/brctl addbr br0 //creo el bridge 
 /usr/sbin/brctl addif br0 eth0 //agrego la eth0 y eth1 al bridge 
 /usr/sbin/brctl addif br0 eth1 
 /sbin/ifconfig eth0 0.0.0.0 //dejo la eth0 y eth1 sin ip asignado 
 /sbin/ifconfig eth1 0.0.0.0 
 /sbin/ifconfig br0 192.168.1.79 up //le asigno ip al bridge y levanto el #bridge con up //
 

But at the end I delete every thing by comment every thing with #.
 

 So If every thing supposedly came back to normal how come is working now? This thing doesn't make sense.
 

 All I can thing that may have made the trick is the following tutorial:  
 [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
 And don't forget my to other recommendations. I hope you get as lucky as I got. Good luck.

---

### Post by TheOnlyMrK on 2009-11-25
Update after over a month now...
Well now that a month has gone buy a few things have changed, major one being both my computers run Ubuntu 9.10 now (instead of Xubuntu 9.04) and my laptop and desktop now directly connect (instead of through my router).
I have found out that with no additional software installed by taking a guess from ArielEnter's step two in his post above mine that now all I have to do to make a network bridge is...
Right click the network icon,
click "Edit Connections...",
select the "Wired" tab,
select "Auto eth0",
click "Edit...",
select "IPv4 Settings" tab,
and change "Method" to "Shared to other computers",
Click "Apply" and you're done. Though I will note that after restarting both my desktop and laptop at the same time the internet will not work until I unplug and replug the Ethernet cord.

Thank you both to whoever added this fix to the latest Ubuntu version and to ArielEnter for showing me that setting otherwise I probably never would of found it. Now all I have to do is find something to use my GPS in Ubuntu and I can get rid of Windows forever.

---

### Post by ArielEnter on 2009-12-04
Jajajajajja, super funny. All what you had to do was what I describe in point number two. Jajajaja. I can't understand why all other tutorials are so confusing, you don't have to do all that. I'm going to have to start a new thread about this, is crazy.

---

### Post by seeker5528 on 2009-12-04
> **ArielEnter said:**
> I can't understand why all other tutorials are so confusing, you don't have to do all that.

If you search for help on setting up a network bridge, you get help on setting up a bridge. 

If all you actually want to do is share an internet connection, then you can ignore all that crap about setting up a bridge.

Later, Seeker

---

