---
title: "Parental control/web content filtering in Ubuntu"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by mbuotidem on 2010-07-29
I work at a cybercafe and i am currently plagued by users who, despite the warning not to, continue to watch porn and use p2p software on my connection. 

I have done some preliminary research on how to filter the web content as well as to reduce the bandwidth used by p2p software on my network. I found that a solution that has worked for many with regard to web content control is danguardian + squid or privoxy in conjunction with a firewall like firehol or something of the sort. Others use an os like untangle or clear os and install it on a stand alone server. then others use open dns. although i would like the open dns solution, i will need to install a dns client, ddclient and i am a linux newbie so and ddclient requires some compiling or so, and i'm not yet into that. I am also currently not in the mood to dabble into untangle or clear os bcos it will cost me a lot do download the iso's. Internet access is costly over here. 

Before i go ahead to implement the steps in any of the tutorials i have seen, i am wondering if such a measure will even help at all. 

You see, at my cafe, i use my server to share the connection to all my clients. I connect to the internet using a gsm modem. then i have two nic's.  nic1 is set to share my connection and my router connects to that nic1. nic2 connects to my router using a static ip to enable communicate with my clients. 

If i implement something like dansguardian on my server, will it solve the problem for me, that is, do i have to also re-implement the steps i took to configure dansguardian on all the other pc's, that is, my clients?

You know, since my server shares the connection to my router and then to others, i am hoping that if i just configure dansguardian on my server that will be all, but i am not sure. 

does anyone know definitively?

---

### Post by Script Warlock on 2010-07-30
well afaik this is the simpliest method of [webfilter]("http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/") for ubuntu try to check this out..

and for bandwidth limiting you may use [wondershaper..]("https://launchpad.net/ubuntu/lucid/+package/wondershaper")
and a gui for [wondershaper]("http://ubuntuforums.org/showpost.php?p=2646755&postcount=1")

---

### Post by mbuotidem on 2010-08-04
thanks, it works.

---

