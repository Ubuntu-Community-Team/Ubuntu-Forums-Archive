---
title: "iptables magic"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by namelessone on 2009-05-29
I am trying to take port 53 (dns) traffic and let it travel across eth0 (wan interface) and eth1(lan interface).

I want to use iptables, but I really don't know what I am doing. I have googled and done man iptables, but it really isn't helping me much. I have looked at many posts in the forums, but most of them are along the lines of, "type this command. it works. it's magic. don't ask questions."

I was hoping someone could not just tell me the *hows* of port forwarding with iptables, but also explain to me (or direct me to a website that explains) the *whys* of the commands I will have to type into my terminal.

---

### Post by dragos_iliescu_2005 on 2009-05-29
Using iptables directly can be confusing. Why you not using Firestarter. It is very simple and easy to use. Just install it from synaptic

---

### Post by ajgreeny on 2009-05-29
I found firestarter a bit too confusing and suggest you also look at gufw.  It lets you open and close ports as you wish extremely simply.

---

### Post by iponeverything on 2009-05-29
I am not clear on what you trying to do.  Is the nameserver going to running on private ip address on the lan segment attached to eth1?

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables")

---

### Post by doas777 on 2009-05-29
> **ajgreeny said:**
> I found firestarter a bit too confusing and suggest you also look at gufw.  It lets you open and close ports as you wish extremely simply.

really? I've always found firestarter to be childish, but gufw provides almost no benefit as a userspace tool. it's not a bad 1-time config tool, but without any monitoring capability I can't really test the results of a change in realtime.

regardless firestarter is out of date, and shouldn't really be used anymore. still, if your having trouble with it, then I suggest this excelent book on basic firewall theory: [http://oreilly.com/catalog/9781565928718/](http://oreilly.com/catalog/9781565928718/)

Firewalls are too complicated for a simple tool to work. IPTables is not complicated because it wants to be, the job is just complex.

---

### Post by doas777 on 2009-05-29
are you setting up and internal DNS server? if so use forwarders rather than port forwarding

---

### Post by namelessone on 2009-05-29
> **dragos_iliescu_2005 said:**
> Using iptables directly can be confusing. Why you not using Firestarter. It is very simple and easy to use. Just install it from synaptic

I would love to use a tool like firestarter, but you see, firestarter requires a graphical user interface. Servers don't have one of those.

Clarification: The server is a captive portal. all port 80 traffic is routed through a modified wifidog gateway (which manipulates iptables) and tinyproxy.

In order for it to work, though, I need machines to be able to do direct dns lookups. so i figure i need port 53 traffic to be able to traverse from eth1 to eth0 and vice versa.

eth0 is connected to a modem. my isp provides the dns servers. eth1 is connected to lan and provides dhcp.

---

### Post by doas777 on 2009-05-29
> **namelessone said:**
> I would love to use a tool like firestarter, but you see, firestarter requires a graphical user interface. Servers don't have one of those.

Clarification: The server is a captive portal. all port 80 traffic is routed through a modified wifidog gateway (which manipulates iptables) and tinyproxy.

In order for it to work, though, I need machines to be able to do direct dns lookups. so i figure i need port 53 traffic to be able to traverse from eth1 to eth0 and vice versa.

eth0 is connected to a modem. my isp provides the dns servers. eth1 is connected to lan and provides dhcp.


then you probably want to use the ufw interface rather than going straight to IPTables.
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

---

### Post by namelessone on 2009-05-29
> **doas777 said:**
> then you probably want to use the ufw interface rather than going straight to IPTables.
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

Yeah, I was looking at ufw, but I was having a hard time understanding how it worked. From looking at the configuration files, it looked really complex.

As I mentioned earlier, I prefer knowing how things work as opposed to "magic" commands :D Do you have any suggestions where I can look for documentation to learn how to use this tool? my normal methods of google searching seem to be failing me

thanks!

---

### Post by doas777 on 2009-05-29
> **namelessone said:**
> Yeah, I was looking at ufw, but I was having a hard time understanding how it worked. From looking at the configuration files, it looked really complex.

As I mentioned earlier, I prefer knowing how things work as opposed to "magic" commands :D Do you have any suggestions where I can look for documentation to learn how to use this tool? my normal methods of google searching seem to be failing me

thanks!

well, IPTables and UFW are both too big for me to want to learn them all at once, so i usually learn systems like these a few commands at a time.

you want to allow DNS, which operates on UDP 53 (in both directions since it's connectionless, eg. UDP). here is a rule to do just that:
```
[B][B]sudo ufw allow 53/UDP
[/B][/B]
```*sudo* runs your app as admin.
*ufw *is the app you are running
*allow *indicates the rule action (allow/deny/reject)
*53/UDP* is the port number you are setting the rule for (0-65535/UDP/TCP/ICMP/etc) 


Now what exactly are you trying to do on a high level? why do you want to port forward DNS traffic?

---

### Post by iponeverything on 2009-05-30
I made a series of modifications to wifidog myself. 

- put in a manual useradd
- removed email signup
- added a "this a restricted network" splash as the first screen
and several other things.

I have to say that wifidog is nice piece of code. After all the work I did, they ended up opting for nocat.. IMO a mistake, but what can you do..

What I did was put a couple of caching nameservers on the local segment and had them bypass the wifidog box completely. It is fairly trivial though to add some rules to wifidog box to have the all traffic coming from and going to the local caching server bypass all the rules setup by wifidog.

The link that put in previous post is very short (about as short as it gets) howto on iptables. I have found that the best way to pick it up is to play around with them a bit. I you have specific requirement like that one that I describe above, I or any number people folks can kick out a rule or two for you.

---

### Post by namelessone on 2009-05-30
iponeverything, that's pretty much exactly what I was trying to do: let dns traffic bypass wifidog. I can make a guess at the rules I would make to do this from my attempts to learn iptables...but I don't know if this would work:

```
sudo iptables -A INPUT -i eth0 -p tcp --dport 53 -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 53 -j DNAT -to-destination $INTIP:53
```

$INTIP=my internal lan subnet

Does that sound about right? I'm really not sure about that second command...mainly because I'm not sure what DNAT is and i can't remember if dns traffic is udp or tcp :)

---

### Post by dragos_iliescu_2005 on 2009-05-30
> **namelessone said:**
> I would love to use a tool like firestarter, but you see, firestarter requires a graphical user interface. Servers don't have one of those.

Clarification: The server is a captive portal. all port 80 traffic is routed through a modified wifidog gateway (which manipulates iptables) and tinyproxy.

In order for it to work, though, I need machines to be able to do direct dns lookups. so i figure i need port 53 traffic to be able to traverse from eth1 to eth0 and vice versa.

eth0 is connected to a modem. my isp provides the dns servers. eth1 is connected to lan and provides dhcp.



Then you may use webmin to setup your firewall - iptables or whatever you want to use for this purpose.

---

### Post by iponeverything on 2009-06-02
> **namelessone said:**
> iponeverything, that's pretty much exactly what I was trying to do: let dns traffic bypass wifidog. I can make a guess at the rules I would make to do this from my attempts to learn iptables...but I don't know if this would work:

```
sudo iptables -A INPUT -i eth0 -p tcp --dport 53 -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 53 -j DNAT -to-destination $INTIP:53
```

$INTIP=my internal lan subnet

Does that sound about right? I'm really not sure about that second command...mainly because I'm not sure what DNAT is and i can't remember if dns traffic is udp or tcp :)

DNS uses both tcp and udp depending on the size of the records involved. The below rule should allow the internal DNS traffice to pass unmolested. 

```
iptables -t nat -I POSTROUTING -p tcp --dport 53  -s  $INTIP  -j MASQUERADE
iptables -t nat -I POSTROUTING -p udp --dport 53  -s  $INTIP  -j MASQUERADE
```

---

### Post by namelessone on 2009-06-03
thanks, iponeverything, that code seems to do the trick!

I am curious, though. Why do you use -I POSTROUTING? what is the significance of that part of the command?

---

### Post by iponeverything on 2009-06-04
Use PREROUTING if your changing the destination address (DNAT)
and POSTROUTING if your changing the source address. (SNAT)

In your case, you want your DNS packets to pass out through the wifidog machine -- assuming the address of the external interface as the source on the way out (SNAT) . When the response is received, the source address of the packet is changed back and it is passed on to the internal machine.

-I is insert the rule at the top the chain 
-A is to append the rule to the end of the chain

We want -I because the rules are evaluated from the top down, therefore this rule won't get pre-empted by something else that you might have in your POSTROUTING chain that I didn't know about.

---

### Post by theDaveTheRave on 2009-06-04
Hi all.

I don't know where else to ask this so I'm hoping you will be able to point me in the correct direction.

I remember reading somewhere that all ports are "open" as standard on an  ubuntu box (or was it closed? I can't find that thread anymore!).

So I've downloaded an [NCBI Blast]("http://blast.ncbi.nlm.nih.gov/Blast.cgi") software and it wants to communicate on specified ports.

As I live in france I have a ADSL from Darty (using the DartyBoxV2). I have apparently "dissabled" all my firewalls (once I get this working I will re-enable them with the required info).

But I still get errors returned from the NCBI server saying that some of my ports aren't "open".

From what I can tell the request for the information is sent out on one port, and results returned on another (which kinda makes sense). But if all my ports are "open" by default (as I seem to recall they are) then why does the server report an error message back to me saying that I need to open specified ports!?

I have used wireshark and I can now see that this is a message coming from the NCBI server (it may also be incorported into the software as an error message? I'm not sure) as initially I wasn't convinced the messages where going out correctly?

Maybe I haven't got my router correctly setup, so if there is anyone out there with knowledge of this router I would be eternally gratefull for assistance 'written in english' as I must be doing something very wrong for it to continue to not work!

thanks in advance.

David

---

### Post by iponeverything on 2009-06-04
The default configuration of Ubuntu is quite secure -- Not in the sense that all the ports are closed, but in the sense that nothing is listening on any of the ports. Generally speaking though -- almost no one these days has their box on an external address -- so, it really does not matter if services are running on your machine or not, as they would not be accessible from the Internet at large without special configuration on the device that is connected to the Internet. 

That said. Is the machine connected directly to Internet with a public IP address -- or is behind another device. If it latter the source problems may be the inability of the device in question to properly handle the protocol that the application is using. To see if you do have any rules in place on your machine run the command:

iptables -L -n

Also keep in mind that a non-root user can only bind a service to ports above 1024.

---

### Post by theDaveTheRave on 2009-06-05
iponeverything.

You may have hit on something there....

The other night I thought I had removed all restrictions on my wireless router, but I found out when I tried to join the ubuntu-beginners irc that I couldn't connect... as the port wasn't correctly forwarded!

So I've temporarily dissabled the router's firewall, and the irc now works. However the stuff I am running from the NCBI doesn't seem to be getting through to my system?

I've tried using wireshark (as suggested somewhere else) to confirm what ports messages are coming and going on.

This investigation leads me to believe that outbound communication is on a different port to the response. Which I kinda guess makes some sort of sense, as if they sent responses on the same port they would block any more incoming requests - is that correct?.

how do I determine if the router box is unable to pass the response protocol through to my laptop? I obviously can't hook in directly to internet as I don't have the correct type of connector in the back of my laptop... 

or do I? I know that the router plugs into the telphone socked via a special adapter with a standard ethernet cable. How do I set my pc / laptop to communicate directly with my ISP rather than use the router box to connect? I guess I need a special bit of software but what is it called?

Thanks for your help

David

---

### Post by iponeverything on 2009-06-05
It does not appear to be overly complex.

this link:

[http://www.ncbi.nlm.nih.gov/staff/tao/URLAPI/netblast.html#2.2](http://www.ncbi.nlm.nih.gov/staff/tao/URLAPI/netblast.html#2.2)

references:

```
Table 3. Firewall Ports Needed by BLAST Client for NCBI Connection
IP Address	Port Number
130.14.29.112 	5861
130.14.29.112 	5862
130.14.29.112 	5863 
```

I checked and Ports 5861, 5862 and 5863 closed on 130.14.29.112

perhaps the document is out of date.

look over these:

[http://www.ncbi.nlm.nih.gov/Sequin/QuickGuide/sequin.htm](http://www.ncbi.nlm.nih.gov/Sequin/QuickGuide/sequin.htm)
[http://www.ncbi.nlm.nih.gov/IEB/ToolBox/NETWORK/firewall.html](http://www.ncbi.nlm.nih.gov/IEB/ToolBox/NETWORK/firewall.html)

In the above doc has a reference to this:

[http://www.ncbi.nlm.nih.gov/IEB/ToolBox/NETWORK/fwd_check.cgi](http://www.ncbi.nlm.nih.gov/IEB/ToolBox/NETWORK/fwd_check.cgi)

which gives the following:

```
Checking connections to NCBI Firewall Daemons as of Jun 05 2009 17:40 GMT:
130.14.29.112:5860	RESERVED
130.14.29.112:5861	RESERVED
130.14.29.112:5862	RESERVED
130.14.29.112:5863	RESERVED
130.14.29.112:5864	OK	
130.14.29.112:5865	OK	
130.14.29.112:5866	RESERVED
130.14.29.112:5867	OK	
130.14.29.112:5868	OK	
130.14.29.112:5869	OK	
130.14.29.112:5870	RESERVED
```

The "OK"s are open ports that will accept client connection.
To test them from command line do:

```
telnet 130.14.29.112 5864

```

and when it connects, just enter test and hit return.

What are the ports that your client is trying to connect to?

---

### Post by theDaveTheRave on 2009-06-08
> **iponeverything said:**
> 
What are the ports that your client is trying to connect to?

As I say, when I wireshark and run the downloaded software the outbound messages do seem to be passing via the open ports, but I get a strange error message reporting that I need to have a problem on ports 4460 to 4560.

I've been reading through the API for the program and I don't find anything that actually specifies the port to use (I expected it to be hard coded, but it may be in a setting file that I have missed?).

either way the message comes back from the server saying that my ports are not accessable, but I have turned off the firewall on my router and so I should be listening on ALL ports?

I can confirm that when I have the firewall turned on I can't connect to the ubuntu irc channel (even though I feel that I have the correct port forwarding info in the router's table), but if I turn off the firewall it works fine to the ubuntu irc. But I still get this strange response from the software.

I think I need to send the NCBI a message and see what they say.

cheers for you help, do you have any other suggestions?

i didn't find wireshark veryhelpfull, way too much information, and when I used iptraf I didn't get the information I was expecting... although I need to try it again from home with the firewall turned off!!

I will keep investigating but currently I send the query to the web page (all 900 of them in a single file) and then just download all the results. which takes a while to perform. I wanted to use this other system as apparently it is "quicker" and sends the requests on another server, and so reducing the load on their server.

David

---

