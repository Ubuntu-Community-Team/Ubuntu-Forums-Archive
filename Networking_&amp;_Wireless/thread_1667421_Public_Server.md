---
title: "Public Server"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-01-14
Hello everyone,

I just had a quick question.  I installed Ubuntu Server 10 and I have it working on my network just great, but I want to make it public.  

I have a FIOS router port forwarding port 80 and 21, I believe on the FIOS then I have my Airport Base Extreme port forwarding the same ports.  Any conflicts here?  Even though I have those forwarding, why isn't it public?  Am I missing something?

Any advice would be greatly appreciated.  

-Fox


I forgot to mention that the FIOS sends an ip to the Airport and then the Airport sends out a different range of ip's.  The server is connected to the Airport.

---

### Post by computerfox on 2011-01-15
Anyone?

---

### Post by lisati on 2011-01-15
If I understand you correctly, your FIOS box is connected to the outside world, and is forwarding port 80 to your Airport box, which in turn forwards to your server.

One thing to look at is the system logs, to see if *something* is getting through.

---

### Post by computerfox on 2011-01-16
That's what I'm not 100% sure because the FIOS is porting port 80 as http to the old ip address and then the Airport is forwarding 80 to the actual ip address of the server.

How would I check if anything is going on in the logs?  I know the server itself works on the private network, but for some reason I can't forward traffic from my dns to the server outside of the network.

---

### Post by computerfox on 2011-01-16
Attached is some more information based on the ethernet port.

---

### Post by computerfox on 2011-01-16
Any other suggestions?

---

### Post by computerfox on 2011-01-17
Attached is even more information about my configuration via Webmin.

---

### Post by anders_c_ on 2011-01-17
I used to have the same problem, then i changed the MAC address of the routers wan-port to the same as the server and now it works! Don't know if it's supposed to be that way though...

---

### Post by computerfox on 2011-01-17
I double checked my routers and attached are my current settings.  It still don't work.  Am I really that much of a noob?

---

### Post by computerfox on 2011-01-18
I now set up a DMZ on my Airport and it's still not public. WTF?

---

### Post by v1ad on 2011-01-18
how to check if it is public or not, maybe thats the issue.

---

### Post by computerfox on 2011-01-18
Okay, so let's think.  In order for it to be public, you have to forward port 80 on the router to the ip address of the server.  Do I have this correct so far?  

Or you can have a DMZ that in a way opens up a certain ip address to the public.  Is this correct?

Next, keep in mind that I have two different routers (the modem/router sends the master ip to the second and then the second sends out a different range).  Both are forwarding port 80 and I even have a DMZ on my Airport.  I am not sure if the FIOS also has a DMZ.  I think it does, but I think the DMZ is the ip that is being sent from the FIOS to the Airport.

Almost there.  I feel like we're missing one small detail.

---

### Post by v1ad on 2011-01-19
also port 80 only opens up the http port, if you want to host a website or something.
on the first router that is connected to the internet, open a port for the second router. it gives the second router an ip, forward it to that 1, and on the second router forward to the proper local ip address.

router 1 -> assign(192.168.0.101)router2 -> assaign(192.168.2.102)device

in router 1 open port for ^ and the second router you prob took care of already.

---

### Post by computerfox on 2011-01-20
router 1->192.168.1.1
router 2 on router 1->192.168.1.3
router 2->10.0.1.1

port forward on router 1->192.168.1.3:80

port forward on router 2->10.0.1.3:80

would this be correct?

---

### Post by rbishop on 2011-01-20
Is your second router setup as DHCP or is it staticly set?  

You should end up with a config such as this:

Fios Wan IP: x.x.x.x
Fios Lan IP: 192.168.1.1

Airport Wan IP: 192.168.1.3 (staticly set)
Airport Lan IP: 10.0.1.1

Server IP: 10.0.1.3

The Fios router should have port 80 opened up to 192.168.1.3.  The Airport router should have port 80 opened up to 10.0.1.3.

If this doesn't work.  Try taking out the Airports port 80 forward and see if you can get to the Airport config page, which I assume is on port 80.


Just a question.....Why are you going through 2 layers of NAT?  It just adds lots of problems to the equation....IMHO.

---

### Post by rbishop on 2011-01-20
Duplicate Post

---

### Post by rbishop on 2011-01-20
Triplicate Post

---

### Post by computerfox on 2011-01-20
> **rbishop said:**
> Is your second router setup as DHCP or is it staticly set?  

You should end up with a config such as this:

Fios Wan IP: x.x.x.x
Fios Lan IP: 192.168.1.1

Airport Wan IP: 192.168.1.3 (staticly set)
Airport Lan IP: 10.0.1.1

Server IP: 10.0.1.3

The Fios router should have port 80 opened up to 192.168.1.3.  The Airport router should have port 80 opened up to 10.0.1.3.

If this doesn't work.  Try taking out the Airports port 80 forward and see if you can get to the Airport config page, which I assume is on port 80.


Just a question.....Why are you going through 2 layers of NAT?  It just adds lots of problems to the equation....IMHO.


I believe it is set up like that, but I would have to wait until I get home since I'm in class right now.

The reason I have a double layer is because the FIOS is actually the master router and my parents get upset anytime I screw around with it. 

Question, would it cause any issues if I have both port forwarding AND DMZ?

It's a good thing I have a networking class this semester, but I want to know something before my first class.

---

### Post by SoftwareExplorer on 2011-01-20
> **computerfox said:**
> I believe it is set up like that, but I would have to wait until I get home since I'm in class right now.

The reason I have a double layer is because the FIOS is actually the master router and my parents get upset anytime I screw around with it. 

Question, would it cause any issues if I have both port forwarding AND DMZ?

Usually turning on port forwarding and DMZ at the same NAT layer does not work. Why? Because DMZ usually forwards ALL ports, including the ones you previously forwarded. Most routers deal with these seemingly conflicting settings by ignoring port forwards while DMZ is on and just sending everything to the DMZ'ed computer.

Have you tried accessing your site from a proxy? You may have it working already. When you try to access the 'outside' (by this I mean outside of the NAT) address of a router doing NAT from behind the NAT, most NAT's don't apply the port forwarding rules, so instead the router doing the NAT responds to requests, instead of your server. The consequence of all this is that the world can see your server, but people behind the same NAT as your server is behind who are trying to access the server using the outside address can't see the server. So try a proxy. You might already have it working. That's what happened to me when I was setting up my first home server.

(Hopefully I didn't confuse you...If I did, let me know)

> **computerfox said:**
> It's a good thing I have a networking class this semester, but I want to know something before my first class.

Right now, there are two main protocols on the internet, IPv4 and IPv6. (Web browsing, email, ssh, etc run on top of these protocols.) IPv4 is the most common, but is running out addresses, which is why your ISP does the first layer of NAT: so they don't have to give you an address for every computer you connect to your main router. IPv6 is almost identical to IPv4, but the addresses are allowed to be 4 times longer, so that every internet connected computer can have it's own public address. Anyway, the thing that really broke barrier for me learning networking was getting an IPv6 tunnel and a block of IPv6 addresses. This allowed me to start on the easier things like routing, instead of the (much harder) hackish things like NAT, which I would have had to learn networking starting with IPv4. The nice thing is once you learn something from IPv6, you can then apply it to IPv4. 
If you want to get an IPv6 tunnel, you could try [Hurricane Electric]("http://tunnelbroker.net/"). They give out tunnels faster than [Sixxs]("http://www.sixxs.net/") (which would be my second suggestion). Unfortunately, Hurricane Electric tunnels don't make it through all NAT's (remember, NAT is a little tricky to do right), but Sixxs' do. The drawback to Sixxs is that they take a few days to approve tunnel requests. Both are free and will give out a block of IPv6 addresses for free.

---

### Post by computerfox on 2011-01-20
Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?

---

### Post by computerfox on 2011-01-20
Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?

---

### Post by computerfox on 2011-01-20
Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?

---

### Post by computerfox on 2011-01-20
Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?

---

### Post by computerfox on 2011-01-20
Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?

---

### Post by computerfox on 2011-01-20
Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?

---

### Post by SoftwareExplorer on 2011-01-20
> **computerfox said:**
> Wow, that was extremely helpful.  Thank you.

So I just got home and checked my FIOS router.  It does not have DMZ nor does my Airport.

Right now the complete configuration is 

FIOS:
ip:192.168.1.1
forwarding 80,21 to 192.168.1.3
static (i believe)

Airport:
ip from FIOS: 192.168.1.3
ip range: 10.0.1.x
forwarding 80,21 to 10.0.1.3
dhcp

Server:
static ip: 10.0.1.3


How should I try going through a proxy?
I usually go to a web proxy like [http://proxify.com/]("http://proxify.com/"). There are tons of web proxies if you just search google for proxy. You just put in either your webservers DNS name, like something.com, or your external address. You can find your external address by going to somewhere like [whatismyip.org]("http://whatismyip.org/").

The settings you listed sound right.

The reason I mention using the public address instead of the name is that I think in one of your pictures, the Airport is updating your dns name. The problem is that the Airport probably updates the address to its WAN address, which would work great if that was really your external address. However, the airport is behind the FIOS router's NAT (but the airport probably doesn't know this), so it would update the DNS name to 192.168.1.3 which wouldn't be accessible from the internet. So the proxy would lookup your DNS name, get 192.168.1.3 as an answer, and then try to connect to a computer in it's private network (if any computer in the proxy's private network happens to be using such an address. Otherwise, it will just time out trying to connect.) If you give it your public IP, it will try to connect to your FIOS router's port 80, which should get forwarded through the First NAT level to your Airport's port 80, which should get forwarded through the second layer of NAT and the request should arrive at your server.

Edit:(well, kind of. I finished the last paragraph and then decided to look at the picture before I posted, which is taking ages today...) So I looked at the picture, and saw that the picture has the DNS name in it. I tried looking it up, and got the answer of 10.0.1.3, which is the private address of the server. So using the DNS name won't work for now. Instead, just use the public address you get from [whatismyip.org]("http://whatismyip.org").  

Note:If you want to look up the IPv4 address for a dns name, run 'dig a foxwebhosting.dyndns.org'. For the IPv6 address of a dns name, run 'dig aaaa foxwebhosting.dyndns.org'.

---

### Post by computerfox on 2011-01-21
Okay, so I tried looking for my public IP, but I couldn't find it.  I entered the 74.xxx from my laptop, but then it completely screwed up my settings.  I got it back and running on a private network, but how would I find my public ip for my server?  Or do I just have that one public ip from the modem that is being broadcasted from the FIOS?

---

### Post by SoftwareExplorer on 2011-01-21
> **computerfox said:**
> Okay, so I tried looking for my public IP, but I couldn't find it.
This shouldn't be to hard, just go to [http://whatismyip.org/]("http://whatismyip.org/"). 
(How does this server know your public IP? When your server requests the web page, it sends the request to the AirPort router which NATs the connection so that it looks like the connection is coming from 192.168.1.3 instead of 10.0.1.3. It then passes the request on to the FIOS router. The FIOS router NATs the connection so that instead of looking like the connection is coming from 192.168.1.3, the connection looks like it's coming from the public (WAN) IP address of the FIOS router, which sounds like it's 74.xxx.xxx.xxx in this case. When the server at whatismyip.org has a connection coming in, it takes note of the source address (which would be your FIOS routers WAN address) and serves up a page that tells you what address you are using to connect to the server.)
> **computerfox said:**
>   I entered the 74.xxx from my laptop, but then it completely screwed up my settings.
74.xxx.xxx.xxx sounds like a valid external address. You would want to enter this address in a proxy, like [proxify.com]("http://proxify.com"). I'm not sure how trying to load a web page using an IP address would change settings. When you say that you entered 74.xxx.xxx.xxx, I'm not sure where you entered it. Your browser? a proxy? or one of your router configuration pages?
> **computerfox said:**
>   I got it back and running on a private network, but how would I find my public ip for my server?  Or do I just have that one public ip from the modem that is being broadcasted from the FIOS?
I think your last sentence is the closest to correct. Your FOIS router has just one public IP. All the computers attached to the FOIS router (and therefore all computers attached to the Airport) have no idea what their public address is, however, the NAT rewrites the packets from the computers attached to the router so that they are using the router's public address without even knowing what is. So, yes you have one public IP, but it is not broadcasted to the computers on the network. Instead, the router rewrites the connections from computers attached to it on the fly with NAT. With your setup, this happens at two levels: the FIOS router and the Airport. The only difference with the Airport's NAT in comparison to the FOIS router is that the Airport is treating 192.168.1.3 as it's public address. Your server does not have a public ip; it uses the FOIS router's public IP by having the server's connections rewritten on the fly. The server has no clue of it's public IP. The only IP address the server knows is 10.0.1.3.

---

### Post by computerfox on 2011-01-21
well, when i went to webmin, i changed the 10.0.1.3 to the public ip.  when i did that, i couldn't access it only if i manually changed it in the server.  then i changed my dns, that didn't help either.  then when i entered the dns into my browser, it was gone.

i think i understand where i get the public ip from, but i don't know what i should do to forward port 80 to the server, even though that sounds pretty explanatory.

---

### Post by computerfox on 2011-01-21
right now i tried doing something like this

dns(public ip)->FIOS:80->192.168.1.3(Airport)->:80->10.0.1.3(server)

shouldn't this work?

---

### Post by computerfox on 2011-01-22
Good news!

Took out my Airport
Made my dns the public IP
port forwarding port 80,22

Boom!

I was making things more difficult than should be, but I guess my parents would just have to deal with some inconvenience at times.

Thank you everyone who contributed to my silly little problem and thank you so much softwareexplorer.  you especially taught me quite a bit and i think i should be set to learn more.

---

### Post by SoftwareExplorer on 2011-01-23
> **computerfox said:**
> right now i tried doing something like this

dns(public ip)->FIOS:80->192.168.1.3(Airport)->:80->10.0.1.3(server)

shouldn't this work?
Yes, that looks like it should work.
> **computerfox said:**
> Good news!

Took out my Airport
Made my dns the public IP
port forwarding port 80,22

Boom!

I was making things more difficult than should be, but I guess my parents would just have to deal with some inconvenience at times.

Thank you everyone who contributed to my silly little problem and thank you so much softwareexplorer.  you especially taught me quite a bit and i think i should be set to learn more.
Glad you got it working. Unless you specifically bought a static address, your public IP will probably change every couple of days and when the FOIS router gets restarted. If your address does change you will probably want to use a program like 'inadyn' to update your address. (I don't know if you have already done this.) Your FOIS router may also have an option to update the DNS. Since it knows your public IP, it knows when it changes, so it doesn't have to check every so often like a program like inadyn does.
I noticed you said that you forwarded port 22. (I saw 21 earlier, so I'm not sure that this isn't a mistake.) If you really did forward port 22, which is for ssh, use STRONG passwords for all your computer users, or, set up public key authentication for the ssh server and disable password authentication for the ssh server (you'll still be able to use whatever  password you want to set to login to the physical computer, but you'll have to use your key when logging in remotely with ssh).

---

### Post by computerfox on 2011-01-23
Okay, so my server is public now, but when I was trying to point a website to my server, it stayed the same as before.

what i did was i (believe) made to nameservers in webmin and pointed the address to them.  now am i having issues with the directories and how they pick the right directory or did i not really create the nameservers?

---

### Post by computerfox on 2011-01-23
here's what i have right now

1and1:
computerfoxdesign.net
foxwebhosting.dyndns.org ns1
foxwebhosting2.dyndns.org ns2

root is /var/www/computerfoxdesign.net

then i added the hostname and my public ip to the host addresses in webmin
also made a virtual server with the root in my apache webserver list via webmin


what's wrong here?

---

### Post by SoftwareExplorer on 2011-01-24
> **computerfox said:**
> here's what i have right now

1and1:
computerfoxdesign.net
foxwebhosting.dyndns.org ns1
foxwebhosting2.dyndns.org ns2

root is /var/www/computerfoxdesign.net

then i added the hostname and my public ip to the host addresses in webmin
also made a virtual server with the root in my apache webserver list via webmin


what's wrong here?

I'm not very familiar with webmin, but I I tried looking up computerfoxdesign.net and I didn't get any address. So are you sure that you have DNS set up and working right? (Do realise that it can take a day or two for a DNS change to get picked up by all the DNS servers. It all depends on the TTL (time to live) of the record. A server (or even maybe a DNS client) if it has already looked up a specific name will not look for new changes until the TTL amount of time has gone by.)

---

### Post by lisati on 2011-01-24
Your web site seems to be working now. Good luck, and well done!

By the way, there's information  about webmin here: [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)

---

### Post by computerfox on 2011-01-24
it does work, but i don't think it's the way i want it to.

i have one server, which i plan on hosting at least 3 websites.  how can i make it so that when someone is looking for let's say example.com it will go to /var/www/example.com on my server?

---

