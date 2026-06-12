---
title: "If a hacker use my internet..?"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by xic816 on 2011-11-25
Hi guys,

If a hacker manages to get into my internet and does illegal things, would it then
look like I'm the one doing it or can it all be traced back to him?

Another thing I'm wondering about; If all computers on a network are shutdown but the router is still blinking does that mean someone is using it?

Thanks

---

### Post by sudodus on 2011-11-25
Have a look at this thread about security
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)[URL="http://ubuntuforums.org/showthread.php?t=1886575"]
[/URL]

---

### Post by sh4d0w808 on 2011-11-25
What type of internet connection do you have? Cable?

---

### Post by ghost on 2011-11-25
> **xic816 said:**
> 
If a hacker manages to get into my internet and does illegal things, would it then look like I'm the one doing it or can it all be traced back to him?

That depends if you have enough logging in your IP devices, such as your PC, Server, Router and FW. If you don't have any logging, then no, it can't be trace. But this also depends if the hacker is any good at cleaning up their track. They might have left some rootkit, or whatever, and then sometimes that can trace them back, if they didn't delete it before they get out.

And it does look like it is you. But then if you are not that good at that side of computing, I am sure your lawyer can argue that this is impossible. 

> **xic816 said:**
> 
Another thing I'm wondering about; If all computers on a network are shutdown but the router is still blinking does that mean someone is using it?
Thanks
It depends, but mostly if configure properly, then no.

---

### Post by haqking on 2011-11-25
If a cracker decides to use your internet and carry out malicious activities if in the event it is serious enough to warrant tracing then it could come back to your WAN interface, if he decides to launch the attack from your machine then it could come back to your machine.

The best thing to do is minimise the chances of someone using your network.

If you use wireless then use WPA at a minimium, WPA2 (enterprise if you have the facility) given the choice and use a complete 63 character key non dictionary word or phrase utitlising all available characters DO NOT USE WEP as it can be cracked very quickly.

Once your WIFI is protected then there are many steps to help increase the security of your machine and network which can be seen in the wiki linked to above and following:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Ensuring strong WIFI protection and taking to steps to limit the chances of somoneoe hijacking your machine through the various methods available to will help you to feel more comfortable.

Remember though as in my signature, nothing is 100% secure in a connected world.

Peace

---

### Post by xic816 on 2011-11-25
> **ghost said:**
> That depends if you have enough logging in your IP devices, such as your PC, Server, Router and FW. If you don't have any logging, then no, it can't be trace. But this also depends if the hacker is any good at cleaning up their track. They might have left some rootkit, or whatever, and then sometimes that can trace them back, if they didn't delete it before they get out.

And it does look like it is you. But then if you are not that good at that side of computing, I am sure your lawyer can argue that this is impossible. 


It depends, but mostly if configure properly, then no.

Thanks! ;)

---

### Post by haqking on 2011-11-25
> **ghost said:**
> That depends if you have enough logging in your IP devices, such as your PC, Server, Router and FW. If you don't have any logging, then no, it can't be trace. But this also depends if the hacker is any good at cleaning up their track. They might have left some rootkit, or whatever, and then sometimes that can trace them back, if they didn't delete it before they get out.

And it does look like it is you. But then if you are not that good at that side of computing, I am sure your lawyer can argue that this is impossible. 


It depends, but mostly if configure properly, then no.

Not having logging enabled locally on your own devices does not mean that a malicious attacker utilising your Internet connection cannot be traced to your network or machine, whether or not the attack is worthy of tracing is another matter, however tracing it back to a network or machine is not dependent on the local logs.

As for router activity if all machines are not connected then yes if there is activity you should check.  If no machines are connected yet you have wifi activity for example then you should check to see if someone other than your own machines are connected, if in doubt then turn off your router when not connected.

The lights are indicators of activity so if there is none you are aware of then check, internet light activity is probably OK as the ISP will often communicate with the router, however you should check if suspicious.

---

### Post by xic816 on 2011-11-25
> **haqking said:**
> If a cracker decides to use your internet and carry out malicious activities if in the event it is serious enough to warrant tracing then it could come back to your WAN interface, if he decides to launch the attack from your machine then it could come back to your machine.

The best thing to do is minimise the chances of someone using your network.

If you use wireless then use WPA at a minimium, WPA2 (enterprise if you have the facility) given the choice and use a complete 63 character key non dictionary word or phrase utitlising all available characters DO NOT USE WEP as it can be cracked very quickly.

Once your WIFI is protected then there are many steps to help increase the security of your machine and network which can be seen in the wiki linked to above and following:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Ensuring strong WIFI protection and taking to steps to limit the chances of somoneoe hijacking your machine through the various methods available to will help you to feel more comfortable.

Remember though as in my signature, nothing is 100% secure in a connected world.

Peace


"If a cracker decides to use your internet and carry out malicious  activities if in the event it is serious enough to warrant tracing then  it could come back to your WAN interface" 

Are you saying the hacker doesn't leave behind trace of any kind as the previous guys stated?

Thanks for reply

---

### Post by xic816 on 2011-11-25
> **xic816 said:**
> "If a cracker decides to use your internet and carry out malicious  activities if in the event it is serious enough to warrant tracing then  it could come back to your WAN interface" 

Are you saying the hacker doesn't leave behind trace of any kind as the previous guys stated?

Thanks for reply

U just answered it ^^; Thanks bro

---

### Post by joy23 on 2011-11-25
If a hacker is a pro there are very rare chances that he is going to leave a trace.:(

But if your devices are configured properly then catching hackers especially through cable is possible.

Still i do believe in hand of God:popcorn:

---

### Post by xic816 on 2011-11-25
What about the IP address, cant that easily be traced regardless?

---

### Post by haqking on 2011-11-25
There are no absolutes.

Take steps to secure your system within the confines of your usability and requirements, educate yourself reading the wiki above and the pages it links too.

Accept or mitigate the risks associated with internet use and sit back and enjoy a connected world.

The whys and wherefores of tracing a malicious attacker are so varied and involved.

Peace

---

### Post by xic816 on 2011-11-25
> **haqking said:**
> There are no absolutes.

Take steps to secure your system within the confines of your usability and requirements, educate yourself reading the wiki above and the pages it links too.

Accept or mitigate the risks associated with internet use and sit back and enjoy a connected world.

The whys and wherefores of tracing a malicious attacker are so varied and involved.

Peace

Well said, thx;)

---

### Post by mastablasta on 2011-11-25
problem is they can mask their IP address as your without even touching your computer. the suspicion could then fall on to you if they did their job.
 
that is why IP alone should be used to charge people with sharing etc.

---

### Post by sudodus on 2011-11-25
> **mastablasta said:**
> problem is they [COLOR=SeaGreen]can[/COLOR] mask their IP address as your without even touching your computer. the suspicion could then fall on to you if they did their job.
 
that is why IP alone [COLOR=SeaGreen]should[/COLOR] be used to charge people with sharing etc.
can or can't?
should or shouldn't?

---

### Post by xic816 on 2011-11-25
> **sudodus said:**
> can or can't?
should or shouldn't?

Yeah I noticed that as well, I guess he meant shouldn't

---

### Post by xic816 on 2011-11-25
Just to see if I understand the principle behind IP-addresses.
The router automatically generate an IP-address for each computer connecting
to the router. The addresses are usually 192.168.0.(2-9999), then my question is; 
Dosn't most computers on different networks have the same IP address? O.o
Ex:

Network 1: 2 computers -> IP = 0.2 and 0.3
Network 2: 3 computers -> IP = 0.2, 0.3 and 0.4

If this is so, why do I read articles about hackers being linked with IP?
Is there like a unique IP on each computer or something?

Thanks

---

### Post by haqking on 2011-11-25
> **xic816 said:**
> Just to see if I understand the principle behind IP-addresses.
The router automatically generate an IP-address for each computer connecting
to the router. The addresses are usually 192.168.0.(**2-9999**), then my question is; 
Dosn't most computers on different networks have the same IP address? O.o
Ex:

Network 1: 2 computers -> IP = 0.2 and 0.3
Network 2: 3 computers -> IP = 0.2, 0.3 and 0.4

If this is so, why do I read articles about hackers being linked with IP?
Is there like a unique IP on each computer or something?

Thanks

192.168 are part of a reserved address system for LAN usage usually in a NAT environment.

192 denoting a Class C, there are also class A and B. (and D and E) and this is IPv4 there is now IPv6

routable Internet IP addresses wont be in these ranges.

and the 2-9999 you quoted wont happen, it is 0-255 (where n-2) so 254 being the maximum usable address, 255 would be broadcast address

---

### Post by xic816 on 2011-11-25
> **haqking said:**
> 192.168 are part of a reserved address system for LAN usage usually in a NAT environment.

192 denoting a Class C, there are also class A and B. (and D and E) and this is IPv4 there is now IPv6

routable Internet IP addresses wont be in these ranges.

and the 2-9999 you quoted wont happen, it is 0-255 (where n-2) so 254 being the maximum usable address, 255 would be broadcast address

Yeah okey, but what does that means in terms of tracing the IP?
U said "routable Internet IP addresses wont be in these ranges", can you elaborate?

---

### Post by haqking on 2011-11-25
> **xic816 said:**
> Yeah okey, but what does that means in terms of tracing the IP?
U said "routable Internet IP addresses wont be in these ranges", can you elaborate?

i presume you are referring back to your other thread where this probably should of been posted.

As i said before, tracing a source is complicated process if the attackers covered their tracks.

However activity is usually traced to a WAN interface (your router address) assigned dynamically or statically by your ISP, it will be an address that can be routed (go from router to router) and arrive at a destination and return from router to router to source.

A non routable address cannot do that, NAT addresses are usually used on a LAN and not a WAN for most home users.

an address of 192.168.1.34 with its default subnet mask of 255.255.255.0 is not an address that would be used for routing internet traffic.

YOU need to study TCP/IP and specifically IP addressing to understand subnet masks, subnetting, routable addresses etc.

However your LAN IP is likely to be NAT'd for LAN purposes, all your traffic goes out your WAN IP (router) and returns to the WAN IP which then passes it back to your LAN IP in a laymans terms.

to the above i would also say kind of ;-) im trying to make it simple

---

### Post by nothingspecial on 2011-11-25
Merged.

---

### Post by nothingspecial on 2011-11-25
I've unsolved it as the discussion is continuing.

---

### Post by haqking on 2011-11-25
Here is an analogy.

Your WAN interface (router) is your front foor

Your LAN interface is your bedroom (i know a terrible analogy ;-)

If someone wanted to send you a letter, if they address it to

xic816
bedroom

it wont get there.

if they address it to your WAN then it gets to the front door, once at the door, someone can pick up your mail and come knock on your bedroom door and say here is your mail.

Terrible i know but im trying to make things sounds simple ;-)

---

### Post by xic816 on 2011-11-25
> **haqking said:**
> Here is an analogy.

Your WAN interface (router) is your front foor

Your LAN interface is your bedroom (i know a terrible analogy ;-)

If someone wanted to send you a letter, if they address it to

xic816
bedroom

it wont get there.

if they address it to your WAN then it gets to the front door, once at the door, someone can pick up your mail and come knock on your bedroom door and say here is your mail.

Terrible i know but im trying to make things sounds simple ;-)

So if a hacker is sitting in the "garden" and getting a letter via lan interface but disappears, is then the latter redirected to his original "bedrom"?

---

### Post by haqking on 2011-11-25
> **xic816 said:**
> So if a hacker is sitting in the "garden" and getting a letter via lan interface but disappears, is then the latter redirected to his original "bedrom"?

Apart from not understanding what you mean there.

I am also struggling to find out what it is you are really asking overall.

If it pertains to tracing an attacker using your internet connection then it is already answered above.

If now it is a seperate question then what is it ?

LAN addresses are used for a LAN (usually NAT based)

WAN routable addresses are used on the internet.

Internet traffic from your LAN can be traced back to your LAN via the WAN interface address. How and why they get to your particular machine depends on the application or service used, port, protocol etc.

as i said before, secure your internet connection as best you can to prevent attackers from using it or your machine.

---

### Post by Dangertux on 2011-11-25
Wee okay let's try this a different way.

You were talking about private reserved IP addresses the 192.x and 172.x series haqking was talking about. Those are not what a hacker is interested in, those are reserved blocks, usually used for networking.

Your WAN interface (the interface that connects you to the internet) is the IP address an attacker is interested in. Those addresses can generally be geolocated to within about 30 miles, they are usually actually traced back to your ISP not your home of residence. However in the case you (or someone who was on your connection) did something bad, the authorities will obtain the records from your ISP. The ISP has a  record of who was assigned what IP at what time, and of course they have your billing information.  Thus authorities show up at your door.

Now that we have that base covered let's look at the reality of the scenario. For the poster who basically said they can spoof an IP just by knowing it. The answer to this, yes and no. For something like a SYN Flood or other method of denial of service, sure they can forge the source IP in the packet header, thus spoofing the IP.

For an interactive attack, where they actually break into the victim machine, no they can not do that. Because they will not be able to interact. The reason is this. The packet goes from the attacker's computer, with a spoofed source ip, it then goes to the victim machine. The victim machine replies to the spoofed source ip, the spoofed ip's machine (if it's even up) wasn't expecting it, so ignores it, thus nothing happens. The connection is broken here.

This is why an attacker will commonly try to compromise a middle man machine to use to route traffic through, they will usually do this through many many machines, making it much harder to trace the attack.  Commonly they look for machines that are easily compromised, weak configurations, out of date services, etc. Weak wireless credentials also can be a target, however usually only to compromise a machine internal to that network and place it in a larger chain. The reason being, wireless doesn't have a very long range, and obviously the FBI showing up 300 feet from your home is not preferable to INTERPOL checking on someone half way around the world.

Now in terms of logging -- yes you can keep logs, but they can be tampered with or destroyed. As I said, in the grand scheme of things most law enforcement knows that your machine was probably compromised and used as an attack platform, they also know that it is likely only one of many compromised systems that was used. Thus you would realistically not be in trouble.

Hope this clarifies.

---

### Post by xic816 on 2011-11-25
> **haqking said:**
> Apart from not understanding what you mean there.

I am also struggling to find out what it is you are really asking overall.

If it pertains to tracing an attacker using your internet connection then it is already answered above.

If now it is a seperate question then what is it ?

LAN addresses are used for a LAN (usually NAT based)

WAN routable addresses are used on the internet.

Internet traffic from your LAN can be traced back to your LAN via the WAN interface address. How and why they get to your particular machine depends on the application or service used, port, protocol etc.

as i said before, secure your internet connection as best you can to prevent attackers from using it or your machine.

It seems you understood my question, "Internet traffic from your LAN can be traced back to your LAN via the  WAN interface address. How and why they get to your particular machine  depends on the application or service used, port, protocol etc." answered it.

 I now understand it a little bit more

Thanks

---

### Post by haqking on 2011-11-25
> **xic816 said:**
> It seems you understood my question, "Internet traffic from your LAN can be traced back to your LAN via the  WAN interface address. How and why they get to your particular machine  depends on the application or service used, port, protocol etc." answered it.

 I now understand it a little bit more

Thanks

DT's post above clarifies things a little better, i probably should of mentioned the ISP thing in a little more detail as he said most traffic is traced back to your ISP, then the ISP would need pass on information about who that IP belongs to etc.

---

### Post by PapaGary on 2011-11-25
If you want to see your IP address type **what is my ip** in a Google search box.

---

### Post by xic816 on 2011-11-26
> **Dangertux said:**
> Wee okay let's try this a different way.

You were talking about private reserved IP addresses the 192.x and 172.x series haqking was talking about. Those are not what a hacker is interested in, those are reserved blocks, usually used for networking.

Your WAN interface (the interface that connects you to the internet) is the IP address an attacker is interested in. Those addresses can generally be geolocated to within about 30 miles, they are usually actually traced back to your ISP not your home of residence. However in the case you (or someone who was on your connection) did something bad, the authorities will obtain the records from your ISP. The ISP has a  record of who was assigned what IP at what time, and of course they have your billing information.  Thus authorities show up at your door.

Now that we have that base covered let's look at the reality of the scenario. For the poster who basically said they can spoof an IP just by knowing it. The answer to this, yes and no. For something like a SYN Flood or other method of denial of service, sure they can forge the source IP in the packet header, thus spoofing the IP.

For an interactive attack, where they actually break into the victim machine, no they can not do that. Because they will not be able to interact. The reason is this. The packet goes from the attacker's computer, with a spoofed source ip, it then goes to the victim machine. The victim machine replies to the spoofed source ip, the spoofed ip's machine (if it's even up) wasn't expecting it, so ignores it, thus nothing happens. The connection is broken here.

This is why an attacker will commonly try to compromise a middle man machine to use to route traffic through, they will usually do this through many many machines, making it much harder to trace the attack.  Commonly they look for machines that are easily compromised, weak configurations, out of date services, etc. Weak wireless credentials also can be a target, however usually only to compromise a machine internal to that network and place it in a larger chain. The reason being, wireless doesn't have a very long range, and obviously the FBI showing up 300 feet from your home is not preferable to INTERPOL checking on someone half way around the world.

Now in terms of logging -- yes you can keep logs, but they can be tampered with or destroyed. As I said, in the grand scheme of things most law enforcement knows that your machine was probably compromised and used as an attack platform, they also know that it is likely only one of many compromised systems that was used. Thus you would realistically not be in trouble.

Hope this clarifies.

It did, thanks for taking the time to reply ;)

---

