---
title: "change to static IP"
date: 2012-09-21
forum: Networking &amp; Wireless
---

### Post by DK555 on 2012-09-21
Hi there
 
would someone beable to help? I have change my server ubuntu 12.04 to a static IP 192.168.0.10 following this tech page; [https://help.ubuntu.com/8.04/serverguide/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/network-configuration.html)
 
but now when when I try and browse internet I have no connection, and now when I try and go back into the networking/interfaces file nothing shows up. (I am not even able to chnage back to DHCP) and when I go to etc/resolve.conf its an empty page.
 
Please can someone help me sort out and explain how to get a static IP
 
:mad:
 
many thanks for your help

---

### Post by JKyleOKC on 2012-09-21
Post the contents of your /etc/network/interfaces file here and we can tell you how to get back to DHCP operation. You can simply display the file on your screen in a text editor, hit Ctrl-A followed by Ctrl-C to copy it, then paste it into a reply, highlight it, and click the "#" icon on the toolbar above to surround it with "code" tags so that it's easy to read.

I assume that you are behind a router that gives you an IP via DHCP; tell us the brand and model of the router and someone will probably be able to give you step by step instructions for assigning a static IP for your server. Each different router has different commands for doing this.

---

### Post by DK555 on 2012-09-21
Hi there
 
thanks for the reply, I'm using a SKy Sagem router, when I go to sudo gedit /etc/networking/interfaces the conf file show nothing? :(

---

### Post by JKyleOKC on 2012-09-21
> **DK555 said:**
> Hi there
 
thanks for the reply, I'm using a SKy Sagem router, when I go to sudo gedit [COLOR=Red]/etc/networking/interfaces[/COLOR] the conf file show nothing? :(The file name is /etc/network/interfaces; the added "ing" causes gedit to create a new empty file with that name, instead of opening the existing file. Give it another try with the correct name and we'll get you going.

I've never heard of that router so can't help; hopefully someone else will chime in with the details. Do you have an instruction manual for it, or an address for an on-line copy we could read?

---

### Post by DK555 on 2012-09-22
HI there

sorry feel bit of a donkey not typing correct.:0 Just a quick update; I have webmin installed so I logged in and managed to change back to DHCP. I open up the network conf file this is what I now have;


> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
    gateway 192.168.0.1 


So if I start again should I put;
> auto eth0
iface eth0 inet static
address 192.168.o.10  (my static IP for server)

netmask 255.255.255.0
gateway 192.168.0.1


My only concern is that it would again drop internet connect?

many thanks for the help!

---

### Post by JKyleOKC on 2012-09-22
Yes, it would lose the connection, unless you change settings in the router to force it to provide the correct static IP to your machine. The change of /etc/network/interfaces just tells the machine what to look for, from the router; it has no effect at all on the router's choice of an IP.

I found the router pages on line, using Google to search for "SKy Sagem router" which took me to their web pages, but I could find no mention there of how to set up static IPs. My old Linksys WRT54G and my current Motorola 3347 both do have that capability, but I could find no mention of it on the Sagem pages.

What I did find was a page on port forwarding, that might solve your actual need. It looks similar to a feature on my 3347, that eliminates the need for a static IP, by passing incoming traffic on specific ports through the firewall to a machine that you designate by name. If you're running specific server programs or games, you can select them from a list, with no need to know the exact port numbers, and it all just works.

However if you're looking for a way to let other internet users access your system, the "static IP" you'd need would be the one assigned by Sky to your router, not the one assigned by the router to your specific machine. I don't know about Sky's policy in such things; I'm on AT&T in the USA and have to pay considerably more than most to get a true static IP assigned -- and the alternative available to me, Cox Cable, does not provide them at all, which is likely to be the case for Sky.

Fortunately, there are companies that provide "dynamic IP" service that you can use. These services keep track of the actual IP that your ISP provides you (using a small program that you install on the machine to "call home" periodically and tell them the IP), and assign it to a name that you've chosen, Google for "dynamic IP" and you will find quite a few of them. The most popular appears to be "dyndns" and both my routers have supported that one automatically. Some of them are free while others have yearly subscription fees. Before I got my true static IPs, I signed up with "dns2go" and still subscribe, since I wrote several tools that had my "dns2go.com" address built into them.

Tell us more about why you want the static IP and we may be able to give more guidance...

---

### Post by dmn_clown on 2012-09-23
> **DK555 said:**
> So if I start again should I put;

```
auto eth0
 iface eth0 inet static
 address 192.168.o.10 (my static IP for server)
```

Why not configure dhclient or dhcpd to resolve the same address after a reboot rather than bending over backwards for static networking for your home network?

```
man dhclient.conf
``` or ```
man dhcpd.conf
``` for the proper syntax.

---

### Post by DK555 on 2012-09-23
Hi there
 

many thanks for your reply, would just like say that the community forum is fantastic and its great that people help each other, its nice to know that there is poeple out there willing to help each other! thank you.
 

OK, let me give you the back ground of what I have done. I have only been using linux for the last few months as I had an old pc so I wanted to set up a media server so I can save/access files internal and remotely. I went through the tech note on how to set up a home server(this is what I used: [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)), I have the server up and running, install samba LAMP and all the other goodies to get working. Brilliant!
 

So the first issue I encounter was the fact that my Sky router changes IP every few weeks, which was not idea as a server as sometimes I couldn't connect remotley as it had change and I didn't know the new IP. So, to resolve this problem I have paid for the Dyndns and have installed the client on my ubuntu machine so this monitiors the ip and changes accordingly.Great! working!
 

What has happen recently is for some reason, maybe due to a power cut my server pc(ubuntu 12.04) change IP addresses from 192.168.0.10 to 192.168.0.9, the problem was that I used Port forwarding on my sky router(I used this help page: [http://www.skyuser.co.uk/forum/sky-broadband-tutorial-section/12815-how-set-up-port-forwarding-internal-server-any-type.html](http://www.skyuser.co.uk/forum/sky-broadband-tutorial-section/12815-how-set-up-port-forwarding-internal-server-any-type.html)) 

So now my Sky router is set up so when traffic comes in it looks for the IP 192.168.0.10, but now as my server IP address has changed for some reason, it no longer finds(works) the internal server-PC. 
 

So, I have now, change, in my router the IP to 192.168.0.9 for all the port forwards.

Now, the reason why I ask if possible to change the Server PC to a static IP is so that I do not have to keep changing the sky router port forward IP everytime.
 

My question is; why did my server change IP address when it has always been 192.168.0.10. Hence the reason why I need to create a static IP on thte server PC...is this the correct way of doing it?
 

phew! think that's just about all the info :0
 

many thanks for your time and help.
 

NB:Sky routers, I believe they don't really offer static IP addresses as they claim the service is for home not business(although what I use it for is for home and not business) use and if they do, they charge quite alot.

---

### Post by DK555 on 2012-09-23
hey dmn_clown
 
many thanks for the reply, could you explain a little more as am new to linux
 
many thanks

---

### Post by JKyleOKC on 2012-09-23
That how-to by Mossywell is for making your home file server available to the entire internet, not just for your home network. If that's what you want, then you were on the right track to start with. However you cannot force the ubuntu machine to a specific IP address and retain connection when the router is not assigning that address.

What you needed to do was change the "192.168.0.10" value in your original /etc/network/interfaces file rewrite -- the one in which you were changing to static IP -- to "192.168.0.9" if that's what the router is assigning. Unfortunately, that will prevent the Ubuntu machine from requesting an address at all and this may, in turn, keep the router from assigning anything. It's a Catch 22 situation unless you can find a way to force the router to assign the same IP every time.

The "dhclient.conf" file may offer a solution but the man page for it is far from clear. Perhaps a google search would help, but I couldn't find any mention of getting a fixed IP via dhclient...

---

### Post by Iowan on 2012-09-23
If you are going to assign a static address, it needs to be outside the DHCP server (the router?) range. Otherwise, you may end up with two machines claiming the same address.

---

### Post by chili555 on 2012-09-23
> **Iowan said:**
> If you are going to assign a static address, it needs to be outside the DHCP server (the router?) range. Otherwise, you may end up with two machines claiming the same address.Exactly! I suggest this format:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.[COLOR="Red"]1[/COLOR]10
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1
```

---

### Post by DK555 on 2012-09-24
Hey Jim
 
Thanks for the info, yes I also want my homeserver to be accessed over the internet. :)

If I understand correclty, I can not specify and keep a certain IP on ubuntu, yes?
 
I am unsure where to start with the dhclient, looking at dmn_clown post? Can the dhclient force to a specific IP address on reboot?

---

### Post by DK555 on 2012-09-24
hey Iowna, Chili555
 
thanks for the reply!
 
ok from what you are saying if I change IP to 192.168.0.[COLOR=red]1[/COLOR]10 outside the range of IP's  being used on my network, this will enanle the static to work and not knock out the server from the internet?
 
yes?

---

### Post by DK555 on 2012-09-24
is there a limit in how high I can set the IP address for example could I use 192.168.0.[COLOR=#ff0000]200[/COLOR]

---

### Post by JKyleOKC on 2012-09-24
> **DK555 said:**
> Hey Jim
 
Thanks for the info, yes I also want my homeserver to be accessed over the internet. :)

If I understand correctly, I can not specify and keep a certain IP on ubuntu, yes?Honestly, I do not know. I do know that my installation here pulls the same local IP every time I boot despite my router providing lower-numbered addresses to other machines in the house. This **may** be related to settings in /etc/dhcp3/dhclient.conf but I'm not certain of that. The only active lines in my dhclient.conf are ```

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;

```And nothing there seems to specify an address. However the dhclient program maintains a file at /var/lib/dhcp3/dhclient.eth1.leases and here's the first of several "lease" entries in that file:```
lease {
  interface "eth1";
  fixed-address 192.168.1.103;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.254;
  option dhcp-lease-time 3600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.254;
  option dhcp-server-identifier 192.168.1.254;
  option dhcp-renewal-time 1800;
  option ntp-servers 64.73.32.135,149.20.68.17;
  option broadcast-address 255.255.255.255;
  option dhcp-rebinding-time 3150;
  renew 1 2012/09/24 09:54:05;
  rebind 1 2012/09/24 10:17:15;
  expire 1 2012/09/24 10:24:45;
}

```> **DK555 said:**
> I am unsure where to start with the dhclient, looking at dmn_clown post? Can the dhclient force to a specific IP address on reboot?Here's a part of my /etc/dhcp3/dhclient.conf file that's commented out and thus inactive. It's possible that removing the "#" character at the start of each line, after changing all the values to match those in the "lease" snippet above, just **might** force the desired IP address -- but I'm unwilling to experiment with it on this production machine;) since it might cut me off from the outside world. However after careful study of the man pages, that's where I would start.```
#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```If you **do** try this, make sure that the "routers" line has the internal address of **your** router -- the one that you address to do router setup. Don't just copy mine. And don't leave any of the "sample" values in the commented-out example in place, such as the "medium" line. Instead, copy the most recent lease entry from the file in /var/lib, and put it into dhclient.conf in place of the commented-out area. Be sure, too, to make a backup copy of dhclient.conf first, just in case it all goes pear-shaped on you...

EDIT: The upper limit will be 253 or 254. The value 255 is reserved for the broadcast address, and 254 **may** be your router's access address (it is on my 3347). Unless you can find a page in your router's advanced setup area that deals with its DHCP server, it's just guesswork. And if you **can** find such a page, it might have the setting you need to force a static IP from that end...

---

### Post by DK555 on 2012-09-24
wow! thanks for that, ok will read through and see how I go
 
will keep you updated
 
Many thanks!

---

### Post by chili555 on 2012-09-24
> **DK555 said:**
> hey Iowna, Chili555
 
thanks for the reply!
 
ok from what you are saying if I change IP to 192.168.0.[COLOR=red]1[/COLOR]10 outside the range of IP's  being used on my network, this will enanle the static to work and not knock out the server from the internet?
 
yes?I know little about accessing your server from the internet, but yes, an address outside the range of the DHCP server in the router will enable you to keep a static IP. I assume you do not have any interference such as Network Manager installed.> is there a limit in how high I can set the IP address for example could I use 192.168.0.200You could. I wouldn't go above x.250, though.

Of course, ideally, you'd check the router's DHCP settings and configure in knowledge rather than guessing.> If I understand correclty, I can not specify and keep a certain IP on ubuntu, yes?
NO. My server and my stay-at-home laptop have run static IPs forever.

---

### Post by blackened on 2012-09-24
As Chili555 already mentioned, this is easier to do with dhcp reservations at the router level, but, so long as the address is outside the dhcp assignment range, setting a static IP in /etc/network/interfaces works just fine.

Because you didn't mention the model number, we don't have enough information to say whether your router supports dhcp reservations, so the latter option is probably the best.

Personally, I configure my home network to use 192.168.1.15-150 for dhcp, I reserve 1-15 for internal networking equipment (switches, hubs, etc), and >150 for static IP machines (printers, servers, both physical and virtual). dhcp is handled by my 10/100 FiOS modem/router.

---

### Post by Iowan on 2012-09-24
I can't go into specifics about accessing your server from the Internet - other than to say port forwarding will be easier to a machine with a constant address (static address or DHCP static lease/reservation).

---

### Post by DK555 on 2012-09-25
Hye Blackened
 
thanks for the reply, when I get back home tonight I will find out the router model and let you know
 
many thanks :)

---

### Post by DK555 on 2012-09-25
I found solution.

I went into my router, inside advanced settings is a LAN IP setup, within here I can reserve an IP address, so I used the current server IP and MAC address to reserve IP

This seemed easier than setting up static IP. 

Many thanks to all that helped and gave input, much appreciated

:)

---

### Post by RKBA on 2012-09-25
I'm glad you finally solved your problem DK555, but having scanned this thread it appears to me that the answer to your original question is that if you want a static IP address you must call up your Internet Service Provider (ISP) and ask them how much it would cost to provide you with a static IP address rather than the dynamic IP address you have now that changes every so often. It is usually quite a bit more expensive for a static IP address than for a dynamic (changing) IP address. Good luck. 


P.S. Just to make it clear, there is no way that you can obtain a static IP address by configuring your computer or router because it is a function of your ISP. Personally, I use a web application called ["Dynamic DNS"]("http://dyn.com/dns/") (which used to be at  dyndns.com but is now at dyn.com) to keep my DNS entry updated when my dynamic IP address changes.

---

### Post by DK555 on 2012-09-26
Hey RKBA
 
many thanks for your reply, yes, you are correct in what you say regarding ISP, mine is sky and from I understanding they don't really offer static IP's as they say the service is for home use and not business and if they do, yes the cost would be considerably higher, which I'm trying to avoid, hence going through the work around, eek!
 
Yes, I have the Dynamic DNS(dyn.com) set up on the server and that is what is monitoring my router IP changes and this works great, think it cost around £50 for 5 years subscription.
 
Maybe at somepoint I will check out full cost of a static IP from ISP but as I'm new to playing around with linux servers this seems like a cheaper option for now :)
 
many thanks for your input ;)

---

### Post by DK555 on 2012-09-26
Hi all
 
is there away to tag this thread as resovled??

---

### Post by lisati on 2012-09-26
> **DK555 said:**
> Hi all
 
is there away to tag this thread as resovled??

You can use the "thread tools" menu item near the top of the page to mak your thread solved.

p.s. It looks like I came by too late to note that my public IP address is a static IP address set by my ISP, and within my home network, my server has a static local IP address assigned by my router; in my server's configuration file, all I have is "auto eth0" and "iface eth0 inet dhcp" for the primary network interface.... :D

---

### Post by DK555 on 2012-09-26
Hey lisati
 
thanks for that! 
 
this is what I did for trying to use a static IP, but from what I understand you need to edit the resolve.conf file, and also make sure the number you use is outside the range of your DHCP numbers. have a read through these posts there is some good help here.
 
here is the static IP way;
 
>  
auto eth0
iface eth0 inet static
address 192.168.0.10 (<<<my static IP for server)
netmask 255.255.255.0
gateway 192.168.0.1  (this is my gateway router)

 
 
Make sure you edit the resolv.conf file (/etc/resolve.conf) to point to one or two dns servers
My sky IP's   87.86.189.16 and 87.86.189.17, so add on separate lines.
 
>  
nameserver 87.86.189.16
nameserver 87.86.189.17 

 
you will need to find your nameserver addresses, hope that helps! 
 
:)

---

