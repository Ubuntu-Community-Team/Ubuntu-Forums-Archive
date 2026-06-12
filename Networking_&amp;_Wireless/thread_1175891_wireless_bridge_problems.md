---
title: "wireless bridge problems"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by crewbie21 on 2009-06-01
Hello everyone,

                         I made the switch from XP to Ubuntu when 8.04 was current, and I have never looked back. That being said, creating a wired/wireless bridge has always been one issue that, being so easy with XP, has been (seemingly) very frustrating to duplicate in Ubuntu. I have scoured the internet and read what seems like hundreds of posts and guides, installed all sorts of bridging and routing utilities, and for one reason or another it never works. So I am using my first forum post here to call upon your wisdom and hopefully find a solution to this issue.

        The setup is as follows:

internet signal <--wired--> router <--wired--> desktop    
/from router<--wireless--> laptop <--wired--> xbox

 I have an Xbox runnig XBMC that I would like to use to play the media stored on my deskop. Since the desktop is stored in a seperate room with the router (modem), I had windows on my laptop and simply bridged the wired and wireless connections on the laptop to pass everything along to the xbox. I also accsessed media streams from the internet on my xbox. Whenever I attempt to bridge the connections with linux, either with bridge-utils or simply creating a bridge in /etc/network/interfaces, not only is the xbox not able to connect to anything, but I loose network connectivity on my laptop as well. I at one time had the xbox connected to the desktop and created a bridge by editing /etc/network/interfaces to create br0 and use the bridge_all command, and this had worked fine. Also, after creating a bridge on my laptop, the internet works fine unti I actually plug in the cord from the xbox. When I plug in, my wireless drops and I get the message "aquiring network address from wired network" That knowledge, along with what I've read online, is leading me to believe that it may have something to do with a buggy network manager (i'm using ubuntu 8.10) or an issue with ubuntu wanting to default to a wired connection over wireless. I've gone and put everything back to "normal" so I can start from scratch with whatever help I get here.

laptop interfaces are:
eth0 - wired
eth1 - wireless
lo - loopback

/etc/network/interfaces is:
auto eth0 eth1 lo
iface lo inet loopback

NM system settings is:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

I greatly appreciate any help you can offer, will provide any more information on request, and greatly apologise if this issue has an easily findable solution. Thanks.

---

### Post by vyvee on 2009-06-04
Hi,
I was also trying to tackle the problem and found that the NetworkManager in the latest version has provided a very simple solution for it... and it works great for me!
[http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)
I did exactly what stated there, except that I skipped Step 1 of installing the 'dnsmasq' package.
Hope it helps!

---

