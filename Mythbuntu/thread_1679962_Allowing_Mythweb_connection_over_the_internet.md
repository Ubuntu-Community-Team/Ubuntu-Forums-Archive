---
title: "Allowing Mythweb connection over the internet"
date: 2011-02-01
forum: Mythbuntu
---

### Post by Pascal11110 on 2011-02-01
I have a base install of Mythbuntu where everything is working perfectly. I can access Mythweb from my local network and stream just fine. My problem is that I cannot get mythweb to allow me access over the internet. Exactly how would I go about doing this after I have my Mythweb working on my local network? (mythbuntu 10.10, All local network and internet traffic is through a Linksys WRT54G)

---

### Post by tgm4883 on 2011-02-01
You would need to forward port 80 traffic on your router to your machine with mythweb on it. Then either use your IP address when remote to access it, or set up some dynamic dns so you can use a hostname.

At the very least you should set up a password on your mythweb. For a more secure solution you should actually create an ssh tunnel and access mythweb that way.

---

### Post by Pascal11110 on 2011-02-01
I tried just temporarily setting up port 80 to be forwarded to my server and I tried to connect to it with it's IP ([http://45.45.45.45:80/mythweb](http://45.45.45.45:80/mythweb)) but I get the connection was reset message. I will set up security as soon as I am able to get it working without the security, but I will probably SSH tunnel it when I get to that point.

---

### Post by andree_b on 2011-02-02
Make sure you have enabled MythWeb on your Lan-interface - by default it is only enabled on loopback interface(127.0.0.1) afaik.

---

### Post by newlinux on 2011-02-02
Also, it is possible your ISP blocks port 80 so people can't run web sites off a residential account. you might want to try a different port.

---

### Post by Pascal11110 on 2011-02-02
But if I can access it on my lan by it's IP, then wouldn't it be enabled on my lan interface? And if my ISP is blocking port 80 how would I go about changing the port Mythweb uses?

---

### Post by tgm4883 on 2011-02-02
> **Pascal11110 said:**
> But if I can access it on my lan by it's IP, then wouldn't it be enabled on my lan interface? And if my ISP is blocking port 80 how would I go about changing the port Mythweb uses?

Don't bother changing the port, have your router forward another port to port 80. It would look something like this.

Externally, you would use [http://45.45.45.45:981/mythweb](http://45.45.45.45:981/mythweb), your router would be set up to forward any traffic using port 981 to your backend on port 80

---

### Post by Pascal11110 on 2011-02-02
I don't think my router supports that. I have a WRT54G and I can forward a certain port to an IP, but I can't forward a port to a different port.

this is what the port forwarding page looks like on my router:
[http://screenshots.portforward.com/Linksys/WRT54Gv2/Port_Range_Forward.jpg](http://screenshots.portforward.com/Linksys/WRT54Gv2/Port_Range_Forward.jpg)

---

### Post by newlinux on 2011-02-02
> **Pascal11110 said:**
> But if I can access it on my lan by it's IP, then wouldn't it be enabled on my lan interface? And if my ISP is blocking port 80 how would I go about changing the port Mythweb uses?

Not sure I'm understanding you (which IP are you talking, LAN or WAN?), but yes, port 80 would be enabled on your LAN interface, but I'm talking about your ISP blocking access to port 80 from the WAN - which they can control.


> **Pascal11110 said:**
> I don't think my router supports that. I have a WRT54G and I can forward a certain port to an IP, but I can't forward a port to a different port.

this is what the port forwarding page looks like on my router:
[http://screenshots.portforward.com/Linksys/WRT54Gv2/Port_Range_Forward.jpg](http://screenshots.portforward.com/Linksys/WRT54Gv2/Port_Range_Forward.jpg)

Your router probably supports it, the Linksys software doesn't. I have 3 WRT54Gs - but I've flashed them with 3rd party software (in my case dd-wrt) that has much more capability. There are others you can flash - but if you don't want to go through that trouble then you'll need to add a port to listen to in apache via /etc/apache2/ports.conf (Listen <port#>) restart/reload apache.

---

### Post by newlinux on 2011-02-02
also, make sure you are testing accessing your mythweb via it's wan name/IP from a network other than your LAN.

---

### Post by Pascal11110 on 2011-02-02
I've actually been meaning to put DD-WRT on my Linksys because I've heard a lot of good things about it, but right now it is my only functioning router so I am scared to mess with the firmware. With your instructions I got Mythweb to be available on port 5678 instead (tested working on my local network), and as soon as I get on another network I'll try it out (currently snowed in). Thank you very much!

---

### Post by Pascal11110 on 2011-02-03
I just tried connecting to the server from another location and it gave me the connection timed out message. I used the address from whatismyip.com with port 5678 forwarded to my server on my router. ([http://45.45.45.45:5678/mythweb](http://45.45.45.45:5678/mythweb)). 
[http://192.168.5.104:5678/mythweb](http://192.168.5.104:5678/mythweb) works fine on my local network. Any other suggestions?

---

### Post by larsolav on 2011-02-03
Silly question from me: 45.45.45.45 is not really the IP address for your internet connection is it? You are just using that as a stand in here in the forum right? Sorry for my ignorance, just curious...

Also, tgm4883, how do you create an ssh tunnel and access mythweb?

---

### Post by newlinux on 2011-02-03
Only suggestions are to make sure there isn't a setting on your router or other firewall blocking most ports, or check to see what ports your ISP blocks. If it works internally, it is probably a router/ISP/NAT issue. Maybe the linksys firmware has logging that can tell you what is happening with the request.

Have you been able to successfully connect externally to your home network for anything else (ssh, ftp, etc.)?

---

### Post by newlinux on 2011-02-03
> **larsolav said:**
> ...

Also, tgm4883, how do you create an ssh tunnel and access mythweb?

I'm not tgm4883, but I hope you don't mind if I answer.

From a remote machine outside your network, you would set the ssh source port to a port you can access that isn't being used for something else, say 1212. Then set the remote port to whatever port your mythweb is listening (default 80).

So if your remote machine runs Linux you would do something like:
```

ssh -f user@myth-server-ip -L 1212:myth-server-ip:80 -N

```

to set the tunnel (openssh would need to be installed on your mythserver).

Then go to your web browser on the remote machine and type in localhost:1212/mythweb as the URL and that would open up mythweb (if coming from external to your network you would need to have your router forward ssh - port 22 by default - to your mythweb machine). this connection with be tunneled (secure and encrypted) through ssh

If your remote machine is windows - you'd probably use Putty.

[http://www.ehow.com/how_2036605_create-ssh-putty.html](http://www.ehow.com/how_2036605_create-ssh-putty.html)

gives and idea - just change the ports appropriately.

---

### Post by larsolav on 2011-02-03
Do I mind? Silly you! :D
Thanks for the great detailed answer, newlinux. Will give it a try this weekend!

---

### Post by Pascal11110 on 2011-02-03
> Silly question from me: 45.45.45.45 is not really the IP address for your internet connection is it? You are just using that as a stand in here in the forum right? Sorry for my ignorance, just curious...

Yup, wouldn't want any slightly evil people out there testing my real IP :P

> Only suggestions are to make sure there isn't a setting on your router or other firewall blocking most ports, or check to see what ports your ISP blocks. If it works internally, it is probably a router/ISP/NAT issue. Maybe the linksys firmware has logging that can tell you what is happening with the request.

Have you been able to successfully connect externally to your home network for anything else (ssh, ftp, etc.)? 

I can probably run a port scan to see which are blocked by my ISP, but I figured 5678 would have a pretty good chance to be open. I'll check the router logs to see if it comes up with anything. I've never tried setting up an ftp server or anything before since I'm pretty networking challenged, so I don't know if other services work. Is there a quick way to test that?

and thanks again for all the help!

---

### Post by newlinux on 2011-02-03
There's no need to test other services and further expose your network, I was just curious if you had gotten anything working previously. Might as well troubleshoot with http.

---

### Post by nhtrader on 2011-02-03
Here's what I did to get WAN access...
1. enter terminal mode
2. enter command: ifconfig
3. now look for net addr: 192.168.x.x  (you need  your PCs ip address)
4. Now enter Frontend 
5. Select Utilities/Setup | Setup | General
6. change Hostname: 192.168.x.x (on database configuration page 1)
7. save changes

Enter Router's configuration
Enable port forwarding
Enter IP address of MythTV PC 192.168.x.x
Enter starting port  80  ending port 80 ( you can specify a range of ports but you only need one)
save changes

goto   [www.whatismyip.com](www.whatismyip.com) to get your WAN IP
(this will be your IP address to access your home network)

Now go to a friend's house (work, library, public hotspot, etc.) and try to enter you home network using this URL...
[http://WAN_IP/mythweb](http://WAN_IP/mythweb)  (ex:[http://45.45.45.45/mythweb](http://45.45.45.45/mythweb))

TO enable/set pasword for MythWeb
Enter Mythbuntu Control Centre |Plugins
Select Enable Password Protect Mythweb
set username & password

---

### Post by nhtrader on 2011-02-03
I forgot to ask, do you have more than one router connected together?

Do you have a router connected to another router resulting in the creation of 2 subnets {different ip address ranges) ?

---

### Post by Pascal11110 on 2011-02-03
> I forgot to ask, do you have more than one router connected together?

Do you have a router connected to another router resulting in the creation of 2 subnets {different ip address ranges) ? 

Nope, I'm just using one WRT54G, the incoming is plugged directly into that and the server is wired into that router. I'll go through your suggestions now to make sure I don't have anything different (although I'll still probably use port 5678 because I think my ISP blocks it because they're kind of jerks)

---

### Post by nhtrader on 2011-02-03
> **Pascal11110 said:**
>  I think my ISP blocks it because they're kind of jerks)


I thought the same thing, but then I decided to take a chance and use port 80. It worked.

So far, I've noticed that making changes to the installation defaults isn't a good idea. Try to use port 80 then if that fails try changing the port to something.

Btw, how are you reconfiguring Mythbuntu to use another port other than 80?

---

### Post by nhtrader on 2011-02-03
I just opened my backend to check if there was anything else I forgot. And yes I did.

Enter 1. General
Host Address Backend Setup page:
Change Local Backend IP Address: 192.168.x.x
Change Master Backend IP Address: 192.168.x.x
save changes
exit backend

---

### Post by Pascal11110 on 2011-02-03
It's actually not hard to configure it to use a port other than 80, I just edited this
(/etc/apache2/ports.conf) to include port 80 and then edited /etc/apache2/sites-enabled/default-mythbuntu so the virtual host was port 5678. That allowed me to connect through port 5678 and blocked port 80.

---

### Post by Pascal11110 on 2011-02-03
I went on my router and strangely even when I try to connect to my mythboxes IP nothing shows up on the incoming log, and I still cannot get access to the mythbox over the internet even after trying nhtrader's suggestions. I have found that if I use the routers IP ([http://172.x.x.x:5678](http://172.x.x.x:5678)) Mythweb shows up, and that shows up in the incoming log. I don't know if that helps in any way but I thought I might as well throw it out there.

---

### Post by nickrout on 2011-02-04
please confirm that your attempts to connect to the public IP ARE from another LAN, ie one not connected through the same public IP address, ie a friend's house, your workplace etc.

---

### Post by Pascal11110 on 2011-02-04
Yes, when I attempt to connect I am usually using the network at my college.

---

### Post by nhtrader on 2011-02-04
Here's something else for you to check: networking settings


There are two files that control the traffic to your MythTV PC

sudo pico /etc/hosts.allow
sudo pico /etc/hosts.deny

Make sure the that they are not restricting traffic to your local network. For example...

These two files work together to create a ruleset that determines which PCs can communicate with your PC

So If you have an entry in /etc/hosts.allow such as ALL: 192.168.  : allow
and you have an entry in /etc/hosts.deny such as ALL: ALL : DENY

These two rules combined will block all incoming traffic except for those on your local network

However, I will note that the current version of Mythbuntu 10.10 does not contain these entries, but I can't vouch for ubuntu installs.

Lastly, be sure to check your iptables (linux's implementation of a firewall). This is a bit more complicated, but a simple test is to see if any rules exist:  
sudo iptables -L

---

### Post by newlinux on 2011-02-04
> **Pascal11110 said:**
> I went on my router and strangely even when I try to connect to my mythboxes IP nothing shows up on the incoming log, and I still cannot get access to the mythbox over the internet even after trying nhtrader's suggestions. I have found that if I use the routers IP ([http://172.x.x.x:5678](http://172.x.x.x:5678)) Mythweb shows up, and that shows up in the incoming log. I don't know if that helps in any way but I thought I might as well throw it out there.

This is your router's WAN IP? Then this should be your external IP and the one that you would use off your network.

---

### Post by Pascal11110 on 2011-02-04
Isn't 172.16.x.x a private IP and not internet routable? I figured that my router just had this IP as part of my ISP's setup. My router show's it's gateway a 172.16.x.1 while the router is 172.16.x.2.

---

### Post by Pascal11110 on 2011-02-04
> Here's something else for you to check: networking settings


There are two files that control the traffic to your MythTV PC

sudo pico /etc/hosts.allow
sudo pico /etc/hosts.deny

Make sure the that they are not restricting traffic to your local network. For example...

These two files work together to create a ruleset that determines which PCs can communicate with your PC

So If you have an entry in /etc/hosts.allow such as ALL: 192.168. : allow
and you have an entry in /etc/hosts.deny such as ALL: ALL : DENY

These two rules combined will block all incoming traffic except for those on your local network

However, I will note that the current version of Mythbuntu 10.10 does not contain these entries, but I can't vouch for ubuntu installs.

Lastly, be sure to check your iptables (linux's implementation of a firewall). This is a bit more complicated, but a simple test is to see if any rules exist:
sudo iptables -L 

I'll check it when I get home, but this is just a straight install of mythbuntu so I don't see any reason for my settings to be different from other peoples.

---

### Post by nhtrader on 2011-02-04
> **Pascal11110 said:**
> Isn't 172.16.x.x a private IP and not internet routable? I figured that my router just had this IP as part of my ISP's setup. My router show's it's gateway a 172.16.x.1 while the router is 172.16.x.2.

Go to your MythTV box
enter terminal mode
enter ifconfig
this will tell you and us what your local network address range is.

Then use browser from mythtv box  and goto whatismyip.com . This IP is your WAN.

This is what you need to "phone home" from a remote location/network.

Then your router needs to be configured to send inbound traffic to local IP address and port which should be the MythTV box.

You only use the local IP address when your on your home network. Not when you're on the outside of the router. Then you need your WAN IP address, which is assigned to you by your ISP. And furthermore, this more than likely is a dynamic address which means that your ISP can change this WAN IP at any time.

---

### Post by newlinux on 2011-02-04
I didn't really check what the IP was and I wasn't sure how much of it was fictional - you just said your router's IP. That's why I asked if you referring to your WAN IP. yes 172 is typically a private IP class.

---

### Post by Pascal11110 on 2011-02-04
> o to your MythTV box
enter terminal mode
enter ifconfig
this will tell you and us what your local network address range is.

Then use browser from mythtv box and goto whatismyip.com . This IP is your WAN.

This is what you need to "phone home" from a remote location/network.

Then your router needs to be configured to send inbound traffic to local IP address and port which should be the MythTV box.

You only use the local IP address when your on your home network. Not when you're on the outside of the router. Then you need your WAN IP address, which is assigned to you by your ISP. And furthermore, this more than likely is a dynamic address which means that your ISP can change this WAN IP at any time.

I have been using the IP from whatismyIP.com to try the remote connection and I have my router setup to use local addresses 192.168.5.100-192.168.5.255. I have also forwarded the correct port to my mythbox.

---

### Post by newlinux on 2011-02-04
> **Pascal11110 said:**
> I have been using the IP from whatismyIP.com to try the remote connection and I have my router setup to use local addresses 192.168.5.100-192.168.5.255. I have also forwarded the correct port to my mythbox.

Now I'm confused. Your router LAN IP (172...) is not on the same net as your addresses it hands out? (192...)?

---

### Post by tgm4883 on 2011-02-04
> **newlinux said:**
> Now I'm confused. Your router LAN IP (172...) is not on the same net as your addresses it hands out? (192...)?

Likely he means this
The "outsite" of his router, which connects to his modem

Internet---<WorldIP>---Modem----<172 address>----router-----<192 addresses>

I would think he may need to set up his modem to forward the ports as well, but i'm unsure. I have mine set up so my router actually gets the world IP address

---

### Post by newlinux on 2011-02-04
> **tgm4883 said:**
> Likely he means this
The "outsite" of his router, which connects to his modem

Internet---<WorldIP>---Modem----<172 address>----router-----<192 addresses>

I would think he may need to set up his modem to forward the ports as well, but i'm unsure. I have mine set up so my router actually gets the world IP address


If that's true then he effectively has two devices operating as routers on his networking (modem is also acting as a router in this case, handing out an internal IP to be assigned as the other router's "WAN" IP.) and two NATs to deal with - then yeah, you right that's what he needs to do (or have his modem not route or give the external IP to the router. My modem forwards the external IP on to my router as well.

His internal router effectively thinks the 172 address is the WAN IP.

---

### Post by Pascal11110 on 2011-02-04
> Likely he means this
The "outsite" of his router, which connects to his modem

Internet---<WorldIP>---Modem----<172 address>----router-----<192 addresses>

I would think he may need to set up his modem to forward the ports as well, but i'm unsure. I have mine set up so my router actually gets the world IP address 

So do you think this is why it's not working? I think my ISP doesn't allow access into their modems by the customer (I have internet where my modem connects to a canopy antenna and I receive my signal over radio waves), so that would make it so I can't set my modem to port-forward :(

---

### Post by newlinux on 2011-02-04
> **Pascal11110 said:**
> So do you think this is why it's not working? I think my ISP doesn't allow access into their modems by the customer (I have internet where my modem connects to a canopy antenna and I receive my signal over radio waves), so that would make it so I can't set my modem to port-forward :(

Yes if your setup is as described it won't work. The modem is getting the outside request and must forward it on to the appropriate machine if it is actually doing routing. This is why your internal router never logs nor receives the outside requests - they never make it there, they only go to your modem.

---

### Post by Pascal11110 on 2011-02-05
Is there any way to get around that without accessing the modem?

---

### Post by newlinux on 2011-02-05
> **Pascal11110 said:**
> Is there any way to get around that without accessing the modem?

Not that I know of. You'd have to figure out how to get your internal router to be seen from the WAN. Right now it appears that is controlled by the  modem which is handing your router an internal IP.

---

### Post by Pascal11110 on 2011-02-06
I guess I'll mark this thread a solved then, because now I know the issue. Thanks to everyone that helped.

---

### Post by nhtrader on 2011-02-07
BTW, there is a way for you to forward traffic through multiple devices.

Could I ask you to post the model numbers of the equipment that you are using?
Which modem? Which Router? 
In addition, would you please specify the order in which the equipment is connected. Plus include whether they are wired or wireless connections.

---

### Post by Pascal11110 on 2011-02-07
My system is set up so that I have an external antenna connected into my modem. This modem is on my roof so I don't have physical access, but if I go to it's page where I would log in if I had access the software is CANOPY 10.5 SM-DES. Then, I have this connected to the router (WRT54G software V. 1.02.0) which controls all my local traffic. My 2 desktops (one of which is the mythbox) are connected by a cable, and I have several laptops that connect wirelessly. I don't have any security set up on my wireless network because I live in the middle of the woods.

---

### Post by nhtrader on 2011-02-09
First here's a link that might helpful...
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking)

Scan to find heading: [B]How to Configure Two Gateways
[/B]
Second, if you could determine the model number of your modem that would be great. This will help future users in your situation. I still don't know what this modem's features are. For example, does is act as a router? Does it have a DHCP server? Can you enable/disable NAT? 

Scenario 1: If you have two routers connected in series, you would probably have two subnets: 172.x.x. and a 192.x.x.  So now you have to open traffic from the outside through two devices. But this could be simplied if the second router would change its subnet. Change router #2 to use the same IP address range as router #1. Consult Router #2 User Guide for details. Usually disabling NAT works after you reset the LAN settings to use 172.x.x.

Scenario 2: WAN IP is 45.45.45.45 and default gateway is 45.45.46.47 and home network is 192.168.0.x

the following  was copied from [http://support.microsoft.com/kb/164015](http://support.microsoft.com/kb/164015) b/c it offers this explanation...

Incorrect Default Gateway: A computer configured with an incorrect default gateway will be able to communicate with hosts on its own network segment, but will fail to communicate with hosts on some or all remote networks. If a single physical network has more than one router, and the wrong router is configured as a default gateway, a host will be able to communicate with some remote networks, but not others. This problem is common if an organization has a router to an internal TCP/IP network and another router connected to the Internet. 

Hopefully this points you in the right direction. Please post solution when you figure it out.

---

### Post by nickrout on 2011-02-09
I think the problem for the original poster is that the modem was locked down by his ISP.

---

### Post by Sum Guy on 2011-02-12
A solution is to use remote port forwarding with SSH. This works by having the server initiate the connection from inside the network, removing the need for router port forwarding altogether. It is all explained here:

[http://www.symantec.com/connect/articles/ssh-port-forwarding](http://www.symantec.com/connect/articles/ssh-port-forwarding)

EDIT: Note that you want to follow the instructions for RemoteForward, not LocalForward.

EDIT 2: If manually setting the tunnel each time doesn't appeal, you could probably set up a script that waits for a message from a free online messaging service (eg email,IM), and initiates the tunnel automatically.

Hope that helps

---

### Post by newlinux on 2011-02-13
> **Sum Guy said:**
> A solution is to use remote port forwarding with SSH. This works by having the server initiate the connection from inside the network, removing the need for router port forwarding altogether. It is all explained here:

[http://www.symantec.com/connect/articles/ssh-port-forwarding](http://www.symantec.com/connect/articles/ssh-port-forwarding)

EDIT: Note that you want to follow the instructions for RemoteForward, not LocalForward.

EDIT 2: If manually setting the tunnel each time doesn't appeal, you could probably set up a script that waits for a message from a free online messaging service (eg email,IM), and initiates the tunnel automatically.

Hope that helps

We've already discussed ssh tunneling earlier in this thread. It still won't work, however, in this case. This solution forwards other ports securely through the ssh port. For Localforward, your router still has to forward the ssh port to right machine (which he won't be able to do unless he can access is modem/router).  In other words this solutions requires he be able to ssh into his LAN from the WAN, which he can't do. For remote forward, he'd have to know ahead of time which machine on Internet he wants to use  and then have ssh access to it and connect to it sometime before he goes to use it and hope that connection is still up when he gets there...

---

### Post by Sum Guy on 2011-02-13
Ahh, well, just throwing it out there.

---

### Post by Pascal11110 on 2011-02-20
Sorry I didn't reply for a while, got a new job with plenty of hours :D. I can confirm that my modem has a 172.x.x.x address and then I have my own 192.168.5.x subnet from my router. I can't determine the model number of the modem because I can't log into it and the modem is on an antenna... on my roof... over 60 feet in the air and I feel like it's not worth risking my life for this little project :). The SSH tunnel idea is intriging but I think in the end it would take a little more work to watch a movie remotely then it'd be worth. I'll try to contact my ISP to make sure that I am not allowed access to the modem but they're office hours are conveniently placed when I'm working. Once I get ahold of them I'll get back to you.

---

### Post by nickrout on 2011-02-20
I believe that you can initiate an ssh session from the other end, ie from inside your network. You would need to do something like:

1. have a script that looks for some external event, like a change to a web page or an specially encoded email coming in to a secret address. This 'external event' will be triggered by you doing something on your laptop - sending the email, or interacting with a web page on some external web server.

2. On the external event happening the internal script starts a ssh session out to your laptop.

3. You will need to have a dynamic dns service on your laptop.

---

