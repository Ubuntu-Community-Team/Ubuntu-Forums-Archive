---
title: "Upnp Support"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Brindle7211 on 2009-07-05
I have setup my Linux machine as the router for my home network. My setup is as follows.

Internet -> Ubuntu 9.04 server -> client machines

Among my Clients I have:
2 xbox 360s (however during Lan night this can reach 5-10)
1 Macbook
2 Windows 7 PC's
1 Windows XP box (not used very much)


I'd like to be able to provide UPnP support for my Xbox's as the stupid error about the NAT not going completely open doesn't go away. Although the error on the boxes specifies NAT I know that the lack of UPnP support is the cause because when I had my Linksys router running DD-WRT I enabled the UPnP support on the router and elimated the error.

I've searched online and found lots of forum posts about setting up a UPnP Media Server that will provide the ability to serve audio, video and pictures to UPnP devices such at the PS3 and Xbox 360 but at this time I'm just trying to add the basic UPnP support that my old DD-WRT router provided.

---

### Post by computer13137 on 2009-07-05
This is actually a very good question.  I did some Googling for you, and found another similar thread. 
[http://ubuntuforums.org/showthread.php?t=1011435](http://ubuntuforums.org/showthread.php?t=1011435)

The solution was to manually forward the ports required by the Xbox.  Really, all uPNP does is automate the port forwarding.  As they said in that thread, it's really not the best idea in the world.  I would try to control the IP address the Xboxes are on, and find out what ports they require.  Then forward them with iptables or whatever firewall you're using.

You can do this for any port you need to forward to anything, Xbox or otherwise.  Please tell us what firewall you're using so we can help you forward the necessary ports.  (iptables, ipchains, etc... do you have squid running?)

Cheers,
Kirk

---

### Post by Brindle7211 on 2009-07-05
Kirk thank you for your reply. I was thinking about manually forwarding the ports as well seeing as how that would most likely solve the problem I will have to test it myself.

Now here are the iptables commands I have already issued for one of my computers:

sudo iptables -I FORWARD -p tcp -i eth0 -d 192.168.1.** --dport 37298 -j ACCEPT
***note** Coould I remove the "-i eth0" and leave "-d 192.168.1.**" or would it break it?*

sudo iptables -t nat -I PREROUTING -p tcp -i eth0 -d ***.***.***.*** --dport 37298 -j DNAT --to-destination 192.168.1.**:37298
***note** in this port forward would I need the "-d WAN address" or could I remove it?*
       


Would there be a way to instruct my DHCP server on my ubuntu box to automatically assign an IP address to a specific mac address? I ask this because it would be relatively easy for me to sniff mac addresses and make a list of xboxs that come to my house. I figure I could setup a script that I'd have to run that would assign the mac address of my choosing with the ip address of my choosing as well as the needed port forwards...

---

### Post by Brindle7211 on 2009-07-05
There are the port microsoft says need to be opened:
TCP 80
UDP 88
UDP 3074
TCP 3074
UDP 53
TCP 53

I took the liberty of forwarding ports 88(UDP) and 3074(UDP/TCP) to my xbox which I assigned a Static IP address. I still receive the error about the open NAT and I am affraid to forward port 80 to my xbox for obvious reasons, and I'm pretty sure port 53 is used for DNS requests so I don't think I should forward that one either...

When I connect to play Halo 3 it seems to connect just fine in Matchmaking however I am concerned about running multiple xboxs and running into new errors.

Could I forward a single port to a range of IP addresses? If so, wouldn't this just create problems? 

I found these websites:
[http://www.daishar.com/blog/archives/2005/01/xbox_live_linux.html](http://www.daishar.com/blog/archives/2005/01/xbox_live_linux.html)
[http://sourceforge.net/projects/linux-igd/](http://sourceforge.net/projects/linux-igd/)

the first site seems to be a nice set of instructions for setting up the upnp deamon to mimic Microsoft's Internet Gateway Device service which seems to resolve this issue. However I have only ever installed programs and the such on my server with apt-get and I am sure that I would botch it.

---

