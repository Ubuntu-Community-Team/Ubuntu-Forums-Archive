---
title: "Internet access on a Windows network"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by dckirba on 2006-07-07
Hey everyone,

I posted thsi question on the absolute beginner's forum and then it kinda got piled under. It is a networking question so I hope I'm posting in the right place now. I basically have a windows network at work and we connect to the internet from one dialup connection on one computer and everyone uses that for the internet. I ran Ubuntu 6.06 from the CD to test it out on one computer. The network works great, but I can't connect to the internet. I'm not too good at networking, so please talk to me as you would to a 1 year old :)

Here's the link to my previous post and the replies and things I've tried so far: [http://www.ubuntuforums.org/showthread.php?t=208476](http://www.ubuntuforums.org/showthread.php?t=208476)

Thanks in advance. Sorry to have posted the same question in two different forums.

Cheers,
David K

---

### Post by raldz on 2006-07-07
Ok, let's get back to basic networking..

First of all, you are using a Windows machine to connect to the internet via dial up.. and this same machine is your gateway to share internet connection among other computers, right?.. So, I suppose you are using Windows' ICS or Internet Connection Sharing?  If this is true then:

Your subnet is 192.168.0.0
Your gateway is 192.168.0.1 (Your Windows machine's IP)
and your IP should be 192.168.0.x (x is from 2 to 254)
Your Subnet mask is: 255.255.255.0
and your DNS is supposedly provided by your ISP..

ICS gives Windows the capability to act as a DHCP server to other Windows clients.. the thing is, I don't know if it allows Linux to share the internet.. in this case, you have to configure your netwrok settings manually..

in your Ubuntu open:
System>Administration>Networking

under Networking, select your Ethernet Card, then Properties

Under Properties: Enable Connection, Set as Static IP,
IP Address: 192.168.0.x (x is from 2 to 254 as long as no conflict)
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1
Then Click OK.

Now go to the DNS Tab:
Add 2 DNS Servers, you may select from this list: [Public Name Servers]("http://jheps.blogspot.com/2006/05/reliable-public-nameservers.html")

I hope this solves your problem...

---

### Post by dckirba on 2006-07-08
Hey, thanks! I will try this out as soon as I get to work on Monday and see how it goes. As I said I know zilch about networking. Thanks again for the help and the patience.

Cheers,
David K

---

### Post by eMepher on 2006-07-12
I'm having similar trouble trying to get the same setup to work:

I have a Windows XP machine connected to a cable modem, and my Ubuntu machine is connected to the Windows machine. The Ubuntu box connects fine if plugged directly into the modem, but I don't have a router, don't have any money to spend right now, and need to have the Windows machine as the primary connection. (The extra NIC I have is a MS model that I was never able to get running under linux.)

I have the Ubuntu network settings configured as suggested, and I can successfully ping 192.168.0.1 or the IP that the windows machine's other network card is using. I can even ping other IPs just fine over the internet, for example 4.2.2.1

I can not connect to anything using domain names. I've tried using the DNS servers I always use with my ISP (and that work fine from windows) as well some other ones. Firefox justs tries patiently then decides it couldn't connect.

In windows, for the second network interface (the one that connects to the linux box), I am not sure what settings I need to fill in. The IP address is 192.168.0.1, subnet mask 255.255.255.0. Should I have something for the default gateway? Nothing was automatically filled-in for that or DNS servers, and I tried everything that seemed logical, as well as leaving these fields blank. I'm thinking my problem lies here.

I'm stumped, but I want to get my Ubuntu box usable so I can really play with it. I've used Fedora, Suse, and Mepis a LITTLE bit in the past, but I'm obviously not comfortable with linux quite yet. Dual-booting was cumbersome in the past, but now I have an older dedicated machine to play with, which SHOULD be more convenient. Any input would be great!

---

### Post by eMepher on 2006-07-12
Wow... On a hunch, I disabled the "Bitdefender Firewall NDIS Filter Driver" for both network connections (in XP) and everything seems to work splendidly! However, I'm not sure if this is a crucial part of my firewall in Windows? Maybe an incompatibility issue with Bitdefender, and I should switch firewalls?  Whatever the case, this was what was keeping me from getting a complete connection through to the other machine, I guess. I'm just afraid this breaks Bitdefender.

---

### Post by eMepher on 2006-07-13
So now I guess my windows firewall is my problem, since disabling it yields the results I'm looking for. This is probably the wrong place to ask, but I'll try: is there an easy way for me to allow my Ubuntu box to have full access to my net connection, through the firewall on the windows machine? I tried altering permissions in Bitdefender but I wasn't too sure how to do it and couldn't make it work. I know, I need to scrape together a few bucks for a router and forget the connection sharing BS.

Thanks for bothering to read this.

---

### Post by krazykirk on 2006-07-13
Hmm... I don't know about Bitdefender, but you could try Zonealarm as a firewall, It's free, and it's relatively simple to use. In my experience, it's very network friendly.

---

### Post by eMepher on 2006-07-14
Thanks. I ran zonealarm for a year or two. Maybe I'll try it again, since it can't hurt, I guess.

---

