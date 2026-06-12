---
title: "Sharing the Internet with multiple clients"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Captain Smiley Pants on 2011-03-22
Hey ya'll, I hope this is the right place to post this but I'll give it a go.

So (if all goes well at this interview), I'll be moving in with a few friends who have Internet access. Now, I like to rip my high definition movies because I'd rather have them on the HD and preserve my disks, and I like to stream them to my PS3.

Obviously, this will take up a lot of bandwidth. In a house of three, and I'm sure they'd already be doing things like looking at YouTube HD videos and streaming HD Netflix, me being selfish on my media server would make things much worse.

I have a solution. Kind of. This is where I need help.

I can share my Internet connection to all of my wired and wireless devices via a wireless router I have lying around. In Windows, I can just enable ICS for the card accepting the Internet, and the next available card will have a static IP and take in new IPs for a new, local network.

You can do this in Ubuntu (or with Network Manager in general, might switch to Debian soon) by going ahead and setting up your wireless connection to accept Internet access, and then set up the Ethernet (or other) card under the IPv4 settings to "Shared to other computers".

Now, I have a netbook that will connect this way wirelessly and my PS3 will connect via a very long Ethernet cable I have to handle the HD movies on my hard drive. This should eliminate the problem of hogging the bandwidth to the main router.

I have a few questions though:

 - I want to be able to play games online through this. I don't have Internet at my house currently to test this, so I'll ask in case someone else out there has done this before: Will this set up support NAT 2? Are there any huge problems?
 - With my very small network I tried, it looks like there is a DHCP service going which is fantastic, but are there any other packages I should install? I've read some guides and some people mention installing dnsmasq-base [FONT=Verdana]and the like.
 - Am I going to be forced with the IP given to me, or can it be changed? I think it turns out to be something like 10.42.43.x which is fine, but some day I might want to change it.
 - I know people like PS3MediaServer and admittedly I do too, but can anyone suggest any other media servers in case that one doesn't float my boat? I've heard about Mediatomb before but I'm not sure about it. I'd like something that I can direct all my traffic into one card, so my room mates can't pick up on my server unless I allow them.
 - What does the "Link-local only" option mean? Should I be using that instead? I have more than one machine though.

Here's the outline to what I want to do, hopefully it will be a bit clearer this way:

*-Internet-*
|
Wireless Modem
(Room mates connect to this through their computers, I will connect my wireless card to this to get Internet access)
|
My Wireless Card
(Again, gets Internet access)
|
My Ethernet Card
(This will be connected to a wireless router I have, and have shared Internet access enabled to come through the Wireless card.)
\
My Wireless Router
- - Netbook wireless connection
(Should be able to access Internet from this)
- - PS3
(Should also be able to access Internet from this as well as media server and support NAT 2 to play games with other people)
[/FONT]

---

