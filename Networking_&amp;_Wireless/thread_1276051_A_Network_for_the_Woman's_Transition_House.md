---
title: "A Network for the Woman's Transition House"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by sTpny on 2009-09-26
Hi all, 

I've been running a company called 'Penguin Migrations', which basically helps people to become Linux (mainly Ubuntu) users. To promote my (so far) small company, I'm trying to work a deal to install a Ubuntu based computer network in the local "Woman's Transition House". 

They do such good and meaningful work, and are so very deserving. My ex has a new man who doesn't treat her very well, and they have always been there for her, and I would like to show my appreciation by giving them a computer network that anyone could be proud of. This means working a few deals around town.

The Computers I'm going to try to get from e-Waste, which is the local computer recycling depot. I do some volunteer work there, so I know that they throw away lots of perfectly good computers that are just a little dated. I am thinking that they will do it for some publicity. 

The publicity will come from mainly from the local news media. It shouldn't be hard to get coverage for a donated computer network for the "Women's Transition House". 

The network itself stands to be the most difficult. I'm no guru.  I know quite a bit of Linux stuff, but networking is an area where I am lacking, so if this project is going to be a success. I'll be needing some help. Are there any Networking Guru's out there that would care to offer their expertise?  


Tony

---

### Post by lenswipe on 2009-09-26
> **sTpny said:**
> Hi all, 

I've been running a company called 'Penguin Migrations', which basically helps people to become Linux (mainly Ubuntu) users. To promote my (so far) small company, I'm trying to work a deal to install a Ubuntu based computer network in the local "Woman's Transition House". 

They do such good and meaningful work, and are so very deserving. My ex has a new man who doesn't treat her very well, and they have always been there for her, and I would like to show my appreciation by giving them a computer network that anyone could be proud of. This means working a few deals around town.

The Computers I'm going to try to get from e-Waste, which is the local computer recycling depot. I do some volunteer work there, so I know that they throw away lots of perfectly good computers that are just a little dated. I am thinking that they will do it for some publicity. 

The publicity will come from mainly from the local news media. It shouldn't be hard to get coverage for a donated computer network for the "Women's Transition House". 

The network itself stands to be the most difficult. I'm no guru.  I know quite a bit of Linux stuff, but networking is an area where I am lacking, so if this project is going to be a success. I'll be needing some help. Are there any Networking Guru's out there that would care to offer their expertise?  


Tony


Id be willing to lend a hand where i can for the networking part...

---

### Post by Iowan on 2009-09-27
> **sTpny said:**
>  Are there any Networking Guru's out there that would care to offer their expertise?  There's a whole forum full of folks who's love to help... ;)

---

### Post by sTpny on 2009-09-27
Thanks Guys. 

Some say its the security and stability that makes Linux so much better than Windows, but I say it's the people.  

Now I'll need to make a couple of crucial contacts. Ellenor, from the transition house, who has apparently heard of my idea through the grape vine and is anxious to speak with me, and Lise, who says what is at the local PACE cooperative, of which e-Waste is a member business. 

After speaking with these people, I will have a much better idea about the sort of network we'll be building. I'll post again afterwards. 

TTFN, 

Tony.

---

### Post by doas777 on 2009-09-27
there is a non-profit in my town called Freegeek. they accept donations of computers from individuals and businesses and then either repair them for resale or donates them on to other non-profits. check to see if they have operations near you, and they may be able to help get you some equipment.

[http://www.freegeek.org/](http://www.freegeek.org/)

good luck,
franklin

---

### Post by sTpny on 2009-10-03
Hi everyone, 

Before I begin, I'd like to thank everyone who responded to my post, both here in the forums, and via personal messages. 

I spoke with Mrs. E today on the telephone. She was excited by the idea of a computer network, but said that she had reservations about having a pc each room, because children might use them unsupervised. I have assured Mrs E that this would not be a problem, as we can limit the private workstations roaming to specific "approved" websites. 

Is that right? I am not sure, but I think it is, via IP tables or through a firewalls GUI. Either way, I'll need help implementing that when it comes time.  

My conversation with Mrs E was brief by design, as I want to speak to her in person. We meet face to face on Monday, to discuss her new network. 

Like most users of trashy commercial operating systems, she has no idea about how powerful a computer really is, especially when it is connected to other computers. On Monday, I will relieve her of the burden of her ignorance, and enlighten her to the wonders of Linux network. The points I would like to make are as follows:

1. One Tower can power two workstations, each having its own keyboard, speakers, microphone, monitor, and mouse. 

2. An Unraid Server is a special computer on a network used for storing important data that cannot be lost due to user error or hardware failure.  

3. All computer activity can be logged for later reference, or even monitored remotely and securely in real time.   

4. A Linux network can be used for security. It can monitor locations, such as the front door or the back yard, via cameras connected to the network, and when motion is detected, the network can take a predetermined action, such as sending a picture to a workers cellular phone.

5. That a Linux network can be operated remotely and securely via the Internet.  

6. That Linux has lots of open source games that are fun to play, and that the children deserve their own arcade. 

If I am off the wall about any of this stuff, please let me know before Monday. Also, have I missed any important points? 

Cheers, 


Tony.

---

### Post by sTpny on 2009-10-08
The meeting went as expected, pretty much.  Mrs. E will get back to me after she has a chance to discuss matters with the other ladies of the house.

---

### Post by houstonbofh on 2009-10-08
You have bitten off quite a bit here.  More than just "Linux" for sure.  I am going to lists some projects.

> **sTpny said:**
> Hi everyone, 

Before I begin, I'd like to thank everyone who responded to my post, both here in the forums, and via personal messages. 

I spoke with Mrs. E today on the telephone. She was excited by the idea of a computer network, but said that she had reservations about having a pc each room, because children might use them unsupervised. I have assured Mrs E that this would not be a problem, as we can limit the private workstations roaming to specific "approved" websites.

You will need a proxy to filter, and something to log.  You will also need a gateway, and something to remote into for support.  Consider Untangle.  [http://www.untangle.com](http://www.untangle.com)  The FOSS version is quite good, but it will take some more powerfull hardware than some things...

> **sTpny said:**
> Like most users of trashy commercial operating systems, she has no idea about how powerful a computer really is, especially when it is connected to other computers. On Monday, I will relieve her of the burden of her ignorance, and enlighten her to the wonders of Linux network. The points I would like to make are as follows:

1. One Tower can power two workstations, each having its own keyboard, speakers, microphone, monitor, and mouse.

I have seen up to 16 "desktops" on a single system.  However, keeping the KVW matched up between reboots can be a challenge.  I just use single systems.  However, Diskless is a real option.

> **sTpny said:**
> 2. An Unraid Server is a special computer on a network used for storing important data that cannot be lost due to user error or hardware failure.

Just a file server?  FreeNAS. [http://www.freenas.org/](http://www.freenas.org/)

> **sTpny said:**
> 3. All computer activity can be logged for later reference, or even monitored remotely and securely in real time.

Untangle also logs very well.

> **sTpny said:**
> 4. A Linux network can be used for security. It can monitor locations, such as the front door or the back yard, via cameras connected to the network, and when motion is detected, the network can take a predetermined action, such as sending a picture to a workers cellular phone.

A network is just a way to connect computers.  You want a ZoneMinder box. [http://www.zoneminder.com/](http://www.zoneminder.com/)

> **sTpny said:**
> 5. That a Linux network can be operated remotely and securely via the Internet.

You are confusing "network" and computers.  But yes, Linux computers can be easily remotely managed.  If you have a proper firewall like Untangle.

> **sTpny said:**
> 6. That Linux has lots of open source games that are fun to play, and that the children deserve their own arcade.

Edubuntu. Educational games.

> **sTpny said:**
> If I am off the wall about any of this stuff, please let me know before Monday. Also, have I missed any important points?

Virus proof.  Mallware Proof.  Had to hack. No need to buy AntiVirus...

---

### Post by sTpny on 2009-10-20
Wow, Thanks for your generous and thoughtful input. You are right. I have taken quite a big bite. Much of it, I'm well prepared for, but some of it is totally out of my league, and if I were alone, I would never attempt such a thing, but I am not alone. I have people like to help me, which to me, is the best thing about Linux. 

Currently, I'm just waiting to hear back from Donna, who is my contact with the ladies at the transition house, so I'll have plenty of time to check out those links you posted. I should also look more into what a proxy actually is, because I'm still a little bit unclear on that. 

I plan on taking my time with this, and I'd like to document the process so that it can be duplicated in other places. I have learned that there are actually two Womens Transition Houses here in my own home town, so I'll likely end up doing a network for both of them. Excellent experience for me, and a great way in general to get Linux into the spotlight of the local media, since publicity is almost guaranteed.  Hopefully, the work that we do here will simplify the process so that its easier for other Linux users to implement similar setups for the transition houses in their own cities. 

I did have one additional thought of my own on the matter, and that was for a web based interface, that not only allows for remote usage, but also acts as a central resource, for all of the womens transition houses out there, so that they can collaborate with one another and share stories of success, (or failure) of the various programs and operations that they themselves carry out. This website would be universal, so would not itself be part of the network, ie: all networks would share this as a resource; it would not be implemented for each individual Womens Transition House. I just thought I should mention it, just in case it matters. 

Thanks again, 

Tony. 

Penguin Migrations at gmail dot com

---

### Post by sTpny on 2009-10-20
Unraid looks like the better solution to me for network storage.  Though mainly because FreeNAS is still in beta, and they both look to be pretty much the same thing.  Unraid, the free version, only allows for three drives though, (2 storage, one parity) but I expect that they might upgrade us to a paid version for free, since we are committing an act of unreasonable kindness, and even if not, the upgrade, if its even needed, is very reasonable. I have no personal experience with any of this though, so if someone knows more, or has another idea to share about secure data storage on a network, I'm all ears.

---

### Post by sTpny on 2009-10-20
Untangle looks perfect, but I would ask that the community offer some other suggestions. Is it the only solution? Is it the best solution? What other options are there? My concern is with the hardware requirements.  I'm assuming that most everyone who implements such a system will be doing so with donated hardware, like I am, so its likely that anything with stiff hardware requirements could be a problem for someone else somewhere down the line, though I do not think it will be a problem for me. It seems very likely that I will have my pick of hardware from our local ewaste recycler, but others might not have this luxury, so, any options?

---

### Post by sTpny on 2009-10-20
ZoneMinder also looks like a perfect solution. Unfortunately, this particular transition house already has a contract with one of the local security companies. In spite of this, I would still like to incorperate security into the finished network, as many transitions houses are underfunded and will need the security. I'll retouch this point when I meet again with Donna.

---

### Post by houstonbofh on 2009-10-21
> **sTpny said:**
> Unraid looks like the better solution to me for network storage.  Though mainly because FreeNAS is still in beta, and they both look to be pretty much the same thing.  Unraid, the free version, only allows for three drives though, (2 storage, one parity) but I expect that they might upgrade us to a paid version for free, since we are committing an act of unreasonable kindness, and even if not, the upgrade, if its even needed, is very reasonable. I have no personal experience with any of this though, so if someone knows more, or has another idea to share about secure data storage on a network, I'm all ears.
How long was gmail in beta? :) In my opinion, FreeNAS has been stable for production use for well over a year. (Perhaps two...  Time goes by so fast...)  It is rock solid, and based on m0n0wall, which is also rock solid.  (But I am biased as a m0n0wall dev)

As to untangle, the free version is just a repackaging of FOSS tools in an easy to use and configure GUI.  And older hardware is fine, but with low ram, it will slow down.  However, as a 32bit OS it maxes at 4gig, which is cheap.  But, yes, you can just roll your own.  It will just be harder to configure and manage. Also, no easy reporting.

---

### Post by sTpny on 2011-11-27
Sorry to everyone.. I had to move for personal reasons so I'm in a different city now.  I will make the offer to the transmission house here in my new city but not until after I get my feet firmly planted under me. Thanks again for everyone's help and advice. I learned lots, and I am happy to know that I can get lots of support for Initiatives like this from the community, but for now, this Initiative is dead. 

I would like to encourage everyone with a bit of extra time to consider offering similar services to their local women's transition house however. It's good for them and good for us. (promotes Linux) Anyone who does, share, share, share! Keep notes and records so others can benefit from what you do. 

You might also want to look at Linux MCE.. looks very promising for things like this, but it isn't really stable yet...  not for me anyhow.  

Thanks again all. 

:)

Tony.

---

