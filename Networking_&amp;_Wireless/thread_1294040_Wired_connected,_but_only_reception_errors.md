---
title: "Wired connected, but only reception errors"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by chatter4eto on 2009-10-17
Well the title says almost all of it...

Had a big crash on my laptop (Fujitsu Siemens Amilo L6825) and tried to install Win (a few versions of XP), but with no success. A month back i met a huge Ubuntu fan, who adviced me to try install Ubuntu on it. So now I'm growing to LOVE this OS! 

Instalation completed (Jaunty Jackalope 9.04), but had problems with the Open Office... So format, reinstall, everything works fine, but... had problems with the NetworkManager - it didn't recognise wired connections. Maybe the problem was, that I installed the OS while connected to a different network (using a wired connection). At home I tried a few things, but no success. Removed NetworkManager and installed WICD (v1.5.9) and it recognised the cable, the connection. But as problems don't come alone I cannot recieve packages?!? Everything is set - IP, Netmask, Gateway and DNS, even the MAC address was recognised by my internet provider...
 Looked at Network Tools - 288 packages transmitted, but on the received it's a 0 with 29 reception errors. Only way of trying the connection was Mozilla's Firefox and the Network Tool.

Any suggestions?

---

### Post by chatter4eto on 2009-10-18
Bump

---

### Post by jward3010 on 2009-10-18
Are you set up through PPPoE?

---

### Post by chatter4eto on 2009-10-18
I am not familiar with most networks and protocols (had a bad teacher at school)... Could you give me some more info where i can look it up?

Else ifconfig shows (I ensure the IP is correct):
eth0      Link encap:Ethernet  HWaddr 00:03:0d:13:94:a0  
          inet addr:_xx.xx.xx.xx_  Bcast:10.10.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1740 (1.7 KB)  TX bytes:1740 (1.7 KB)

It doesn't show any receipt errors because i'm only allowed to use 1 cable (because of inet provider tarif), but if it was there would be packages send, but none received.

Strange thing is the connection works on a WinXP desktop with only this configurations. 

Just ask what info you need!

---

### Post by chatter4eto on 2009-10-18
Quick addition: I'm using Ethernet with Static IP

---

### Post by jward3010 on 2009-10-18
I'd actually appreciate your IP address as well. Don't worry, we can't decipher anything from a private address like 10.10.10.X, maybe only from a public address but we're nice chaps and lassies anyway and wouldn't do a damn thing anyway (well I'm speaking for myself anyway).

And by the way your not set up with PPPoE, your on a standard private network by the looks of things.

Lastly could you give me the output of:
```
nm-tool
```

---

### Post by chatter4eto on 2009-10-18
Well I hope no "bad people" will come trying to mess up with an already messed up WinXP dektop :D IP 77.70.72.32

---

### Post by jward3010 on 2009-10-18
I can see where you're going wrong, your IP address is on a completely different subnet from the details you have provided above. "nm-tool" will really help here.

If you post the output of "nm-tool" in code tags, like so:
(code)output of nm-tool(/code)

Just change the normal brackets to square brackets, makes terminal output much easier to read.

---

### Post by chatter4eto on 2009-10-18
As i said before i deleted NetworkManager (had to reinstall it in order to purge it - i only had it removed the first time) and installed WICD.

It says
```
 The program 'nm-tool' is currently not installed. You can install it by typing:
sudo apt-get install network-manager
bash: nm-tool: command not found 
```

Strange thing is that the details are one and the same with the ones i use ATM on the desktop:
IP:77.70.72.32
Subnet Mask:255.255.255.0
Default Gateway:77.70.72.1
And DNS Servers: 89.190.209.253 and 89.190.209.254

---

### Post by jward3010 on 2009-10-18
Ah, indeed. No network-manager.

Do you mean Asynchronous Transfer mode? I'm not completely sure wicd supports it.

What kind of network setup do you have, what does your PC plug into, a standard DSL modem / router or ATM hardware?

---

### Post by chatter4eto on 2009-10-18
The connection is LAN based, so i suppose it is an integrated in the Intel mainboard LAN card.

In fact there's a router, which is set up by the provider for the entire entry of the block.

Edit by ATM i meant at the moment on the desktop pc.
The internet provider i am using is having a router installed to support some of the appartments in the block, who are using his services, with internet. Might the problem lie in the router (first attempts to connect the laptop to the internet were a week ago, so if there was an error with the router it should have been solved long ago)?

---

### Post by chatter4eto on 2009-10-18
Bump

---

### Post by jward3010 on 2009-10-18
> **chatter4eto said:**
> Strange thing is that the details are one and the same with the ones i use ATM on the desktop:
IP:77.70.72.32
Subnet Mask:255.255.255.0
Default Gateway:77.70.72.1
And DNS Servers: 89.190.209.253 and 89.190.209.254

I don't think you've put the information in the same as on Windows. A previous post says you have a broadcast domain of 10.10.10.**255**, this should be 77.70.72.**255**.

Paste the output of "ifconfig -a" and show all info. I think this is a simple address error.

---

### Post by jward3010 on 2009-10-18
> **chatter4eto said:**
> In fact there's a router, which is set up by the provider for the entire entry of the block.

I find it odd that you use a public address behind a router, behind the apartments main router, sometimes it can work, technically it shouldn't and regardless, it's unsafe. Can you set wicd to DHCP and, let it get an address (if it does) and then retry internet.

---

### Post by chatter4eto on 2009-10-18
/etc/network/interfaces/ shows:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 77.70.72.32
	netmask 255.255.255.0
	network 10.10.10.0
	broadcast 10.10.10.255
	gateway 77.70.72.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 89.190.209.253
	dns-search amiloto

```

and the ifconfig -a shows:

```

lubomir@amilo-l-ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:0d:13:94:a0  
          inet addr:77.70.72.32  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe13:94a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:128 dropped:0 overruns:0 frame:423
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17149 (17.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9240 (9.2 KB)  TX bytes:9240 (9.2 KB)

pan0      Link encap:Ethernet  HWaddr 52:88:73:1b:4a:66  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``` 

Tryed editing the /etc/network/interfaces broadcast entry to the one you said - 77.70.72.255 but it didn't work. I also used a found on some forum command line to restart something after the change:
```
sudo /etc/init.d/networking restart 
```

Could there be any restriction to access the internet? (I've set my user to have no restrictions in Users and Groups, but could there be any other restrictions, denying the access to received packages?)

> **jward3010 said:**
> I find it odd that you use a public address behind a router, behind the apartments main router, sometimes it can work, technically it shouldn't and regardless, it's unsafe. Can you set wicd to DHCP and, let it get an address (if it does) and then retry internet.

I think I couldnt say it clear :) The whole entrance uses 1 router with different public IP's behind them. I have no roters at home at the moment, as i want first to configure the internet connection on the laptop and then "upgrade" my tariff to 2 IP's, as my current is set to 1 IP at a time.
 The provider said that DHCP is not available so I assume that (just to say again - i have minimum knowledge of networks) the IP addresses are somehow coded in the router...

---

### Post by jward3010 on 2009-10-19
To be honest I'm finding it hard to understand your network, it sounds weird although I've come across them.

This is how your interfaces file should work to be feasibly correct:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 77.70.72.32
	netmask 255.255.255.0
	network *77.70.72.0*
	broadcast *77.70.72.255*
	gateway 77.70.72.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 89.190.209.253
	dns-search amiloto
```

I've highlighted in Italics what needs to be changed. The previous entries of the 10.10.10.0 network are incorrect and wont work on a completely different subnet of 77.70...

There's another file to put in DNS server addresses (/etc/resolv.conf or /etc/network/resolv.conf, something like that), it's not often done in "interfaces", I'll try and find out. You might look in those two locations in the mean time.

---

### Post by jward3010 on 2009-10-19
> **chatter4eto said:**
> 
Tryed editing the /etc/network/interfaces broadcast entry to the one you said - 77.70.72.255 but it didn't work. I also used a found on some forum command line to restart something after the change:
```
sudo /etc/init.d/networking restart 
```

It has to work, the previous entries are incorrect. The 77 network and the 10 network are two completely different things, I also think your interfaces file has too much info in it.

> **chatter4eto said:**
> Could there be any restriction to access the internet? (I've set my user to have no restrictions in Users and Groups, but could there be any other restrictions, denying the access to received packages?)
No, there are no restrictions whatsoever placed on users in terms of using the net, only restrictions on the apps that want to use them and whether you have to run them as root. So I'd say change those settings back.


> **chatter4eto said:**
> I think I couldnt say it clear :) The whole entrance uses 1 router with different public IP's behind them. I have no roters at home at the moment, as i want first to configure the internet connection on the laptop and then "upgrade" my tariff to 2 IP's, as my current is set to 1 IP at a time.

How do you test your connection then if you've no connection to the internet, or are you using the apartments connection and how does that all work (do you know?)?

---

### Post by jward3010 on 2009-10-19
Also have a read of this: [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by chatter4eto on 2009-10-19
> **jward3010 said:**
> How do you test your connection then if you've no connection to the internet, or are you using the apartments connection and how does that all work (do you know?)?

I use my apartments connection for tests (plug out of PC, plug in the laptop) as I have only one cable and am not willing to buy a router before I am convinced the laptop can access the inet.
As for how its working, I cant explain it, but can give you the facts:
-one (or maybe two) router for the block entrance;
-one cable leading into my flat;
-the internet provider recognises if the computer attached has a connection (suppose because of the packages send), and if the MAC address has changed;
-strange thing is that the first time i tryed to connect and called the provider to open a new MAC address slot they said, that everything is fine on their side and i should have a fully working connection :confused: 

I'm now gonna test the new parameters you told me, will bring feedback no matter the results :P

---

### Post by chatter4eto on 2009-10-19
I tryed but nothing changed (even after a down/up of eth0, and a restart with cable plugged in). 

After looking up a few commands (showing details, that can be seen in Network Tools, such as Active Network Services, Routing Table Information, Devices, etc) I decided to reinstall Ubuntu with the home cable plugged in and entering all the connection settings (at the previous install i wasnt home, but did the install with a connection from another cable).

Then, if the network works, I'll tell the differences, so we'd knew what the problem was, or, I'd have to start the whole search from the beginning :D

---

### Post by jward3010 on 2009-10-19
Alright see how you get on, I'm pretty sure this is a network issue and not an Ubuntu one. Are you on a college campus by any chance?

---

### Post by chatter4eto on 2009-10-19
Last update:
-the provider's call operator was so kind to enlighten me, that they do not support linux... Maybe it is explaned by that whole router thing (there are big amounts of cross win&linux networks with problems)... Nevertheless tryed to connect and (no this isnt a happy ending).

I guess i'll somehow install Windows on the laptop too and use the Ubuntu at public networks.

I'm sorry for your lost time (in fact i've learned a LOT for networks :) )
I've you're planning a visit to Bulgaria keep in mind, that you've got a few beers on my account :)

---

### Post by chatter4eto on 2009-10-19
> **jward3010 said:**
> Alright see how you get on, I'm pretty sure this is a network issue and not an Ubuntu one. Are you on a college campus by any chance?

Actually no, I'm not on a college campus, but the first and only time I had a connection was via a university network :)

I haven't quit to try solve the issue, but it's taking me too much of my time (and with 2 jobs + university it is a bit difficult). I took a look at the provider's forum. A few people have also been trying to establish a connection with linux, and Ubuntu in particular, too. If anyone of them comes up with a solution there, I promise to post it here.

PS Don't forget to remind me about the beers.

---

### Post by jward3010 on 2009-10-20
> **chatter4eto said:**
> Last update:
-the provider's call operator was so kind to enlighten me, that they do not support linux... Maybe it is explaned by that whole router thing (there are big amounts of cross win&linux networks with problems)... Nevertheless tryed to connect and (no this isnt a happy ending).

That PISSES me off! Sorry for exploding, but networking standards are just that - STANDARD. There should be no such thing as incompatibility between systems that support the same protocols. It's all TCP/IP for Crap's sake! Thats shocking. Did they say in what way it's incompatible with Linux, I mean do you have to install a little app in Windows to do stuff or what - do you know of course?

> **chatter4eto said:**
> I'm sorry for your lost time (in fact i've learned a LOT for networks :) )
I've you're planning a visit to Bulgaria keep in mind, that you've got a few beers on my account :)

There was no lost time whatsoever, I learn lots from this stuff, so you're more than welcome.

A Budvar if you wouldn't mind!

---

### Post by chatter4eto on 2009-10-20
Actually the only thing they said is that they dont support Linux OSs. At first I thought like you. Is it so hard to configure a network? But then, as i wrote before, i found the provider's forum where there were some threads about connecting from a linux pc. 

The provider actually began a massive expand three years ago, buying other LAN net providers, so it could be they dont support a Linux helpdesk. Or it may depend whether the previous owner of the network was supporting linux. Or it could be that to some reasons the new provider is trying to unify the network properties, so they prefer to support only windows at the cost of all linux users (who at my calculation should be around 5% or not more that 10% of all the users, connected to this provider)

In fact the provider is right to do so. As an economy student I can tell you, that he provides a service like almost no other bulgarian clientrelated company. He offers a very good service, smiling faces at all his paydesks, a SMSbased warning system for free (your payday comes, your connection might slow down from 5 to 6am) and many many other features. 

In Bulgaria such a service is an EXCEPTION. Almost every service provider (including restaurants, coffee shops, tax desks, administration) reckons that you are bound to pay. They could not even imagine that if they loose you as a customer, they'd soon have no salary (its the result of socialism).
So in my view the provider preffers not to allow linux systems before they have set and tested whether their network connects linux without problems :)

---

### Post by jward3010 on 2009-10-20
What bugs me is there's nothing to supporting Linux. It's networking, like you say, there's nothing OS specific about networking, certainly not anymore. Their system is something akin to having a particular brand of screws that only screw into a particular brand of wood (and as you talk about economics thats a particular bone i'd pick with capitalism in a big way, proprietarness, patenting, closed ideas - the opposite of Ubuntu). I think they have no experience with Linux and are afraid to try and offer support as they wouldn't know what to do. Basically I'm thinkin' that all this will work on your Ubuntu machine, maybe it's a proxy thing, a particular Windows app that registers MAC addresses, I don't know. Either way it's disgraceful.

To say that there right to do so, in my opinion, is wrong, even from an economics point of view. I might say from an economics point that they would be reluctant if Linux had completely separate protocols and they needed to invest a huge amount of money to support it, but they don't. It's a standard TCP/IP network carried over DSL, ATM, PPPoE - whatever it is it's supported by Linux. Linux and UNIX created it in fact, all those years ago. The worlds DNS servers and routers (the backbone of the web) run on some variant of UNIX or Linux whether open source or proprietary. There's NOTHING the Linux world doesn't know about networks.

So in economics terms the extras you mention above are fluff and forms of PR, I hate to be harsh but you have to understand there is no difference in networking terms between Windows and Linux, or Mac, or SunMicrosystems, or iPod touch's or anything else in the world that can connect to the internet. You should in fact complain even if they are the "exception".

---

### Post by chatter4eto on 2009-10-27
OK, here's some feedback.

Actually the provider hasn't restricted Linux in the network - he doesn't support connectivity issues on linux systems via the call operators.

A network administrator heard me out (or read my thread in the forum actually :P ) and assigned a technician to come take a look at the cable (his theory was that the cable or its connector could be damaged so if the laptop's lan card was too old and thus weaker at transmitting the signal (as opposed to the desktop with a newer and stronger lan card).

At this time i was installing a netgear wireless dongle to try out if there are any OS restrictions on connecting to the inet i might accidentaly turned on. Tried it at a cafe with free WiFi and it worked.

Today was the day. The technician came, took a look at the cable, tried with a router - nothing, but the fact that the router augmented (google translator came up with that word :D ) the signal. The techie suggested I'd take a look at my Lan card. So I had to look for drivers...

The ethernet controller is National Semiconductor Corp. DP83815 (listed by both Hardinfo and lspci). I found a site, there were both linux (2.6 kernel) and winxp drivers. Tried out both - and none worked, both can be found [here]("http://www.national.com/analog/interface/macphyter2#windows") . The linux gives a lot of errors in terminal, the win doesnt include a .sys file for every .inf file... Any suggestions?

---

