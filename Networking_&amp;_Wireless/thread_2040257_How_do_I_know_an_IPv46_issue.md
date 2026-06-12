---
title: "How do I know an IPv4/6 issue?"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by ookooboontoo on 2012-08-10
Hi all,
I work in a company that has a single broadband connection of about 1.5 Mbps, but we have generally only users that use the internet in total and even then only very intermittent use of things like eSeller uploading items and email.

We have 90% of the machines are Ubuntu 12.04 and a couple of windows machines. All pcs are linked through a wired network and I feel the windows machines are a little nippier online. With the ubuntu machines there can be delays of up to 30 seconds before pages start to load and when they do, it seems fast enough to be broadband speed.

I am aware that Ubuntu can have issues with conflicts between IPv4 and IPv6, and often switching of IPv6 can speed up connecting. Our IT person says that it is purely the broadband of a rural location that is slowing up the system but I am not sure.

I am not allowed to install anything, but is there any way I can test if there are conflicts causing delays in connecting? I can then take this to the IT person to carry out testing to prove one way or the other if it is causing delays.

Many thanks,

A

---

### Post by poolet on 2012-08-11
ok to be clear something first....Since you're a company, and your using 1.5Mbps connecting keep in my that may differ with a normal connection.. Most companies are using business Internet connection which has some points that you may see before monitoring your traffic..  For example if your company is using IP Transit Port or a corporate symmetric Internet things are getting more difficult even for a network engineer to be able to determine the problem, especially for delays problem.. I suggest to talk with ISP company that provides Internet and ask them if is possible to separate the network to be more easily for troubleshooting..

**Note example info:: **( If the company consists by one branch then a good idea is to separate the VOIP (if exist) from the entire network. Also another good idea is to manage any linux machines more careful instead of windows machines.. Linux come across with a iptables which is responsible for filtering and setting up of network according to your needs.. That's may occurs problems some times if we're using a hardware firewall.. Also make sure that if your using VOIP a good idea is to flash your dns cache more often, even if your VOIP is outside of network, a good trick is to setup the  interfaces on the switches and remove the command "no shutdown" into a port number (for example interfaces port 10 on the switches) and try to call the extension number from other extension, if the telephony is working but you can't see who is call, then flash you dns caches and try again also keep in mind that you must change the interface port 10 back to "no shutdown").. 

Now if your using dual IPv4 and IPv6 Support on an Interface you need to approximate number of feature resources, allowed by each template for desktop or aggregator switches.. Now keep in mind that, An IPv4 route requires only one TCAM entry. Because of the hardware compression scheme used for IPv6. An IPv6 route can take more than one TCAM entry, reducing the number of entries forwarded in hardware. For example, for IPv6 directly connected IP addresses, the desktop template might allow less than two thousand entries. **Back to your problem now,** you may want to talk with your IT department. It's the best way to find a solution. A good idea is to start with linux machines. To monitor your entire network you can used **wireshark** application which is a free application and is working with linux and windows machines... In my opinion (since I don't have a lot of information about the network) it could be wrong they way of ip summarization/metric, is the most common problem with delays especially with dual IPv4 and IPv6.. 

To conclude, best way for troubleshoot::: make a synopsis of the network, starting from your servers/routers/switches then create a simple topology of the network and run it in a virtual time, check how it is responds, after that, implement in the real time and synopsis all linux, windows machines if everything seems fine, you can run wireshark to capture the network and see which protocol it takes to long to respond.. A delay problem, could be anything, from a simple firewall setup to a whole ip summarization /metric issues..Delay problems, sometimes needs a rebuild of the whole network,So keep in mind that it's not simple, if you have good results with monitoring (wireshark) then the problem is very very worst that you thought..!! .

Hope that helps you!! Good luck!!

---

### Post by ookooboontoo on 2012-08-12
Poolet,

Thank you so much for your information and for taking the time to reply, I really do appreciate it. Also you seem to have great knowledge and have many recommendations that I must follow up. The best way will be to print of and, as you say, I need to liaise with the IT guy more closely. Fortunately we don't use things like VOIP so that helps but servers and sub-networks may be part of the problem. I will also recommend Wireshark as I am unable to install myself due to privileges.
 I think that there will need to be much investigation and this will take some time. I will work too only teaching myself more on the net work issues you suggest so that I can rule those out.
Thank you again for responding, I will consider this solved for now and will report back my findings when testing/changes are in place.
Please continue your good work within our community.
A

---

### Post by ookooboontoo on 2012-08-12
PS My beans are on 40 so I have not been able to change my system status, I am now on 12.04 but will not be able to update this until another 9 beans/posts.
Hardy was a great install though when I were younger :)
I wish Ubuntuforums would add the ability to register thanks votes, if they did, I would have clicked it to thank you for your help :)
A

---

### Post by chadk5utc on 2012-08-12
Hello I to run a small office in a very rural area 30 miles from any town and am limited to business class DSL(8meg) and have had great service. I had to have a service tech come and do some field testing in order to make needed changes/repairs to lines and have been very happy since. Im not sure the ISP or type of connection you have but you may also be able to simply contact them and get it increased? My Linux machines are much faster than the one windows machine is online. May be worth an easy phone call?

---

### Post by poolet on 2012-08-12
ookooboontoo,

Thank you and no problem!! my pleasure!! :) Hope that I have pointed you into the correct direction!! :) 

 chadk5utc,

[LEFT]As I mentioned before there are many problems that may contribute as a Delay Problem... A telephony in a company can be configure with different ways.. I don't want to started a thread about that, it will takes me hours to explain how it's works, and how it's respond into the backbone of your network.... I will suggest you to talk with an IT department for that... In my opinion?? Check your QoS services on your windows machines.. Set QoS rules as normal.. search on google for more informations.. Keep in mind that, QoS isn't increase the speed or reliability of an Internet connection. It reserves portions of bandwidth for specific services. At the end check the following link:: '[_**here**_]("http://en.wikipedia.org/wiki/Quality_of_service")'. Also make a capture of your network.. ping windows machines each other and check the difference of TTL and delay respond, and try the same for linux.. what was the results?? a good idea is also to traceroute the path of your network may windows occurs by software firewall or something...  Another idea, is to consult your ISP is the best way you have.!!! 

Good luck to you!! :) 

c ya guys!!  
[/LEFT]

---

### Post by ookooboontoo on 2012-08-13
> **chadk5utc said:**
> Hello I to run a small office in a very rural area 30 miles from any town and am limited to business class DSL(8meg) and have had great service. I had to have a service tech come and do some field testing in order to make needed changes/repairs to lines and have been very happy since. Im not sure the ISP or type of connection you have but you may also be able to simply contact them and get it increased? My Linux machines are much faster than the one windows machine is online. May be worth an easy phone call?

Thank you chadk5utc for your comments, I agree that ensuring the phonelines coming to the workplace are really important to be on top of. I live 10 miles from work and get 6 Meg-ish. I have family locally who had a terrible time online until the phone company sorted out the line, and now they get around 1Meg. The phone company has offered to install much faster line if the company paid thousands to have it installed but for us that would not be cost effective and we would be paying to deliver high speed to the whole local area and the phone company is responsible for that. Secondly, where the problem appears more in the time to connect rather than actual time when downloading, coupled with the fact windows machines did not appear to have the connecting time lag makes me think the lines may not be at fault. But still you are lucky with 8Meg :) And at least we do not need dial up! :D
Thank you Poolet, I can see you have obviously had experience of network problems before. I will let you know of the resolution to this.
Looks like I will reach my 50 posts soon enough :D

Thanks all,
A

---

### Post by Tobeus on 2012-08-13
I am no network engineer by any means, but I would suggest eliminating the simple things first.

If you try to access a website via IP address directly, rather than by the URL on the Ubuntu machines, does it seem faster?  If so, you are probably experiencing a DNS lookup slowdown.

I believe where the IPv4/6 issue might have come in is a Google search, such as this article:

[INDENT][http://superuser.com/questions/232704/website-lookup-extremely-slow-in-ubuntu](http://superuser.com/questions/232704/website-lookup-extremely-slow-in-ubuntu)
[/INDENT]The top answer suggests why a DNS lookup would take longer if the Ubuntu browser were looking up an IPV6 address first, failing, then the IPV4 address.

Either way, I hope you figure it out.  Good luck!

-Tobeus

---

### Post by ookooboontoo on 2012-08-13
Many thanks for this Tobeus, I will indeed test this out. The reason I wondered if it was an IPv4/6 issue is that 2 years ago on my Hardy, I made these changes which did at that time speed up my system. I too hope I can work to figure it out and I will post my findings in time.
I am very heartened by the support, I was worried that it may have waned due to a drop in users but faith is restored :)
A

---

