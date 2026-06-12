---
title: "Ubuntu novice with port forwarding issues &amp; dynamic ip"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by Luddite Savant on 2012-07-21
Hi, 

I've recently switched to Ubuntu 12.04 from Windows XP and I've been having problems setting up port forwarding on my machine. I've searched around on the net and tried a lot of things but can't get things set up right.

The issues are my isp gives me a dynamic IP address set by their server and I need a static to forward ports. I've followed [http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu](http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu) and tried to set /etc/network/interfaces as a static ip but always get problems with the system reading /etc/network/interfaces or ignoring eth0 after I've saved /etc/resolv.conf and restarted networking.

Am I on the right track here? is it possible to change the dynamic ip set by isp to a static one? if so what am I doing wrong. 

I didn't have any problem on Windows with the dynamic ip, had full connectability for file sharing & had a tor relay set up so I reckon its fixable, I just don't know enough about Ubuntu to realise where I'm going wrong.

Can anyone help me out?

---

### Post by bakegoodz on 2012-07-22
You don't need your routers public IP to be set staticly, so it doesn't have anything to do with your ISP. So it sounds like you have tried to set your Ubuntu computer to a static IP via /etc/network/interfaces. Ubuntu Desktop by default uses the settings set in Network Manager graphic interface. If you uninstall Network Manager it will uses settings from /etc/network/interfaces

What I recomend is to use Static Leases in the DHCP settings on your router, thought it may be named different. You can set it static on your computer, but it can cause IP conflicts if you choose a IP from the same range your router gives out. One you get that sorted out you will know what IP to forward to in your router settings.

---

### Post by Luddite Savant on 2012-07-22
> **bakegoodz said:**
> You don't need your routers public IP to be set staticly, so it doesn't have anything to do with your ISP. So it sounds like you have tried to set your Ubuntu computer to a static IP via /etc/network/interfaces. Ubuntu Desktop by default uses the settings set in Network Manager graphic interface. If you uninstall Network Manager it will uses settings from /etc/network/interfaces

Thanks, unfortunately I really have very basic ubuntu knowledge so I'm still a bit in the dark.

I have network manager installed (network-manager-gnome 0.9.4.1-0ubuntu2) according to software manager but I can't see how to access it. All I can find are 'network tools' & 'network connections', which I think are different.

From network connections I've worked out my ip is ipv4, though I've also got ipv6 (& loopback interface which I've no clue on). I can edit ipv4 settings in network tools & there's the option to change from DHCP to manual so I'll give that a try.

> What I recomend is to use Static Leases in the DHCP settings on  your router, thought it may be named different. You can set it static on  your computer, but it can cause IP conflicts if you choose a IP from  the same range your router gives out. One you get that sorted out you  will know what IP to forward to in your router settings.I've no idea how to get into the DHCP settings on my router. Can you be a bit more specific? I'm interested in learning how ubuntu handles external connections to internet as well as how to set it up right. Looks like I've a lot to learn.

Thanks

---

### Post by bakegoodz on 2012-07-22
Use ipv4 settings.

Hows is this for being specific?
[IMG]http://i50.tinypic.com/2up5qgg.jpg[/IMG]
Of coarse it may be no use to you.

---

### Post by Luddite Savant on 2012-07-23
Ah, I understand now, the actual router settings, I was being a bit dense there. I haven't seen anything there called static leases but I'll check again and see if there's anything that seems similar.

Any pointers on the network manager ipv4 bit?

Cheers

---

### Post by Luddite Savant on 2012-07-23
'Address reservation' or 'static routes' seem to be the only 2 likely equivalents of 'static leases' on my router. I'll do a bit more digging on these.

Sorry just see you've already advised to use ipv4.

---

### Post by Luddite Savant on 2012-07-23
Ok, I've set up network tools to manual & forwarded ports but I'm getting some inconsistent results:
I can connect to the net & can now upload via vuze,
but on [http://www.canyouseeme.org/](http://www.canyouseeme.org/) its still showing the dynamic ip of the router so I can't check ports there.

Also with TOR I've got the following:

> [Mon Jul 23 18:16:35 2012] Server Port Reachability Test Failed - Your relay's server port is not reachable by other Tor clients. This can happen if you are behind a router or firewall that requires you to set up port forwarding. If 81.141.68.69:44444 is not your correct IP address and server port, please check your relay's configuration.

again its using the dynamic ip. 
I guess I'm missing something really obvious. 
Is vuze only working because of UpnP? if so do I need to set up the 'static leases', if I do this should I keep the network tools as manual?

---

### Post by bakegoodz on 2012-07-23
Sounds like you need a little education on NAT and Port forwarding. [http://www.canyouseeme.org/](http://www.canyouseeme.org/) only shows your Public IP address. Outside of your location, on Internet, everything on your network looks like it coming from one device, your router. Only your router and computer inside your own network know how to reach each other by their private IP address (192.168.x.x) Your router uses NAT to keep track of connections initiated by computers in your network and will know were to forward those connections inside your private network. The problem with NAT is that computers on the Internet don't know how to initiate connections with your specific computers, they can only initiate connections with the router. This is were Port Forwarding comes in. The router will forward all connection requests on a specific network application port(s) to the IP address you designate. The reason you want that computer set to a static private IP is so that the forwarding rule always goes to the same computer.

[http://www.howstuffworks.com/nat.htm](http://www.howstuffworks.com/nat.htm)

---

### Post by Luddite Savant on 2012-07-26
Thanks, that article was useful, as was your explanation. I'll give it another shot. 

As I understand it I'll need to set the static leases (I think  'static routes' on my pc) to one ip address eg 192.168.13.13 then ensure that ports are forwarded to that address in the router settings. 

Router will still set the public ip and route everything from  192.168.13.13 through the public ip & let through everything coming from forwarded ports(where particular applications are set up to use those ports).

I'm still a little unclear on the dhcp/dynamic router but I think that I can leave this as is, not need to change anything on  /etc/network/interfaces and no need to restrict the dhcp address range (eg leave it as 192.168.13.1-254).

Am I on the right track here or have I got any of the above wrong?

Thanks for your help & patience.

---

### Post by bakegoodz on 2012-07-27
I wouldn't get stuck on static leases if your router does not do it. It just prevents IP conflicts. You can set a LAN/Private IP just fine on your computer, just set it to one that isn't the range of IPs your router's DHCP server gives out or least not the first 10 or 15 IP of the DHCP range. For instance if the DHCP range is 192.168.1.100 - 192.168.1.200, if you set your computer 192.168.1.205 or even 192.168.1.150 you would be fine. Remember most private IP ranges are only x.x.x.1 - x.x.x.254 And "static routes" are somthing else entirely. I assume that you have no need to set your routers WAN/Public IP staticly, you would probally have to be doing something pretty serious with a web server hosted on your network to need that. Your ISP would have to enable static public IP for you anyways.

---

### Post by Luddite Savant on 2012-07-28
Hi Bakedgoodz, I think I've finally got it - after a scary few hours today when I couldn't even connect to the router.

But I've now made some changes, removed the DNS setting in the ubuntu network connections and removed the static routes.
Basic tests are now ok and I can connect to the internet ok.
My router is now adjusted so its ip is 192.168.13.254 (which is what ports are forwarded for) rather than 192.168.0.1 which it was before. 

Is this ok? could I have kept 192.168.0.1 - I don't think so but want to check.

As far as I know the only way to check if its working now is to setup a tor relay & see if it works. I'm doing this now & have got 2 reports from the TOR message log:

"[Sat Jul 28 23:48:56 2012] Server Port Reachability Test Successful! - Your relay's server port is reachable from the Tor network!"

"[Sun Jul 29 00:06:51 2012] Directory Port Reachability Test Failed - Your relay's directory port is not reachable by other Tor clients. This can happen if you are behind a router or firewall that requires you to set up port forwarding. If 81.141.68.109:9030 is not your correct IP address and directory port, please check your relay's configuration."

Looks like I've still not got it but I can't see what I've missed.
I've got my Relay Port set up on TOR & forwarded on router, I hadn't changed my directory port on TOR (set as 9030) but I'd ticked the box to 'mirror the relay directory'. 

When I tried to change 9030 to my forwarded port I got "Vidalia was unable to apply your server settings to Tor.
Unable to set option: Failed to bind one of the listener ports." 

Hopefully this is fairly simple?

---

### Post by bakegoodz on 2012-07-28
> My router is now adjusted so its ip is 192.168.13.254 (which is what ports are forwarded for) rather than 192.168.0.1 which it was before.

I can't exactly follow what you have done. Did you set the router to port forward to its self? Or did I misread that.
I don't see any reason for you to change the router's own private IP address. You can change it if your more fond of certian numbers for your networks IP addresses, but technicaly it is pointless. Any 192.168.x.x or 10.x.x.x are vaild private IPs. 

 I don't know why your doing anything with DNS or static routes. The 2 guides on found on setting up TOR don't do anthing with that.
[http://www.technohunk.com/2012/06/tor-linux/](http://www.technohunk.com/2012/06/tor-linux/)
[http://www.upubuntu.com/2012/04/how-to-install-and-run-tor-under-ubuntu.html](http://www.upubuntu.com/2012/04/how-to-install-and-run-tor-under-ubuntu.html)

I can tell you that port forwarding does not involve: Changeing your Routers own IP addresses or changing anything with DNS or setting static routes.

I'm curious, what guide are you following to setup TOR?

---

### Post by Luddite Savant on 2012-07-29
> **bakegoodz said:**
> I can't exactly follow what you have done. Did you set the router to port forward to its self? Or did I misread that. 
I don't see any reason for you to change the router's own private IP address. You can change it if your more fond of certian numbers for your networks IP addresses, but technicaly it is pointless. Any 192.168.x.x or 10.x.x.x are vaild private IPs. 
 
Ok, I guess i was wrong there then, I couldn't see a clear way to point the internal ip to the router without setting the router ip to match the ip address in network connections. 
 
Thinking about it it looks like the router was set to port forward to itself. 
 
I set the router LAN IP setup IP address to 192.168.13.254,  which matched what I'd got setup on ubuntu's network connection. I'd set the router dhcp range as 192.168.13.2-253 and network connections additional settings were: 
Netmask 255.255.255.0 
Gateway 192.168.0.1 
 
Port forwarding was set up for 192.168.13.254

If I don't do it this way how do I ensure the router knows the internal ip - purely via the forwarded ports? 
 
> I don't know why your doing anything with DNS or static routes.  Yeah, I had tried using static routes earlier (as I'd thought it different terminology for static leases) but it didn't work so I deleted it. On the dns there is a box in the network connection settings for it so I'd initially filled it in, but I realised it wasn't helping so deleted it too. 
 
>  I'm curious, what guide are you following to setup TOR?I'm not using any guide to set up Tor, I used it on windows and its the same, fairly simple, setup. On windows the tor relay worked without changing any other settings other than forwarding ports. That's obviously the area I've still got a problem in.

---

### Post by bakegoodz on 2012-07-29
Port forwording is pretty simple. If I want to ssh into my home computer from work I just ```
ssh username@recoverydigital.com
``` recoverydigital.com resolves through DNS to my public IP 74.211.17.27 (see WAN IP in the picture) The router passes data from the public interface (74.211.17.27) to the private interface (192.168.1.1)  When my router see the connection is for port 22 it uses the Port Forward rule and sends it to 192.168.1.10, my home computer's private IP address. Without the port forward rule my ssh connection would go to the router instead. Which does support ssh login, I changed my routers ssh port to 2222 so I can still do that too.

[IMG]http://i50.tinypic.com/286tu7o.jpg[/IMG]

I have yet to setup TOR, but looking over the guide on [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor) I don't see anywhere it says to setup port forwarding on your router. It looks like it has your browser connect through another port so talks to the proxy software the guide has you install on your computer.

---

### Post by Luddite Savant on 2012-07-31
For some reason nothing I try seems to work. I've had persistent problems connecting whenever my ip is set as manual rather than dhcp. Even when I'm able to connect when I restart I can't connect again. I think this is because on the router Lan IP setup there's a box > **Use Router as DHCP Server** Starting IP Address ... Ending IP Address I've  switched this off but it didn't make a difference so I've switched it back on.
 

 When running the connection test in my router I usually get:
 > 
                                                      **Testing Internet Connection**
                                                              
                                                             This Page will Automatically                 Display the NETGEAR Website if a Successful Internet Connection                 is Detected.                  
                             

                                                               [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Connection                 time**[/SIZE][/FONT]
                                           [FONT=Arial, Helvetica, sans-serif][SIZE=2]00:00:03[/SIZE][/FONT]
                                                             [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Connecting                 to server**[/SIZE][/FONT]
                                           [FONT=Arial, Helvetica, sans-serif][SIZE=2]Connected[/SIZE][/FONT]
                                                             [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Negotiation**[/SIZE][/FONT]
                                           [FONT=Arial, Helvetica, sans-serif][SIZE=2]Success[/SIZE][/FONT]
                                                             [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Authentication**[/SIZE][/FONT]
                                           [FONT=Arial, Helvetica, sans-serif][SIZE=2]Success[/SIZE][/FONT]
                                                             [FONT=Arial, Helvetica, sans-serif][SIZE=2]**Getting                 IP address**[/SIZE][/FONT]
                                           [FONT=Arial, Helvetica, sans-serif][SIZE=2]86.175.136.15[/SIZE][/FONT]
                                                                                  If connnection fails, check your                 Login, Password, and other data.
                                                              
                                            
               

  And then it goes to:
 > 
 

         Server not found
       
           Firefox can't find the server at [www.netgear.com]("http://www.netgear.com").
          
 

   Check the address for typing errors such as
     ww.example.com instead of
     [www.example.com]("http://www.example.com")
   If you are unable to load any pages, check your computer's network
     connection.
   If your computer or network is protected by a firewall or proxy, make sure
     that Firefox is permitted to access the Web.
    So its showing success then saying it can't find the netgear server. When running with the network connection settings on automatic (DHCP) it manages to connect to the netgear server.
 

 > 
 The router passes data from the public interface (74.211.17.27) to the private interface (192.168.1.1) Do you note on the router anywhere the IP of the private interface?
 The private interface ip ( 192.168.1.1) – am I right in thinking this is the router ip (on mine 192.168.0.1)? if not where does this ip come in – where is it shown on router or network settings?
 

 I've got some confusion as to which IP should be set as the private ip address and which is the private interface & where I respectively note them on my settings. The port forward rule shows when something comes in via 44444 it goes to 192.168.13.254 but when this is set as my private IP I was getting the following system authentification failed error on the router.
 

 > [COLOR=#0099cc][FONT=Arial, Helvetica, Geneva, Swiss, SunSans-Regular, sans-serif][SIZE=4]Warning[/SIZE][/FONT][/COLOR]
  [FONT=Arial, Helvetica, Geneva, Swiss, SunSans-Regular, sans-serif][SIZE=3]**System Authentication Failed.**[/SIZE][/FONT]
 
[FONT=Arial, Helvetica, Geneva, Swiss, SunSans-Regular, sans-serif][SIZE=2]Another Administrator online.[/SIZE][/FONT]
  I got this a few times, now when I try I'm just getting the netgear error above.
 

 When the computer IP is set to something different, eg 192.168.13.150 I get the netgear error shown above.
 

 I'm only able to connect to post this when I've got the network connection set as automatic (DHCP)
 

 >  When my router see the connection is for port 22 it uses the Port Forward rule and sends it to 192.168.1.10, my home computer's private IP address. which is what is set up in network connections (on my comp) as IP address 192.168.13.254.
 

 > 
 I have yet to setup TOR, but looking over the guide on [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor) I don't see anywhere it says to setup port forwarding on your router. It looks like it has your browser connect through another port so talks to the proxy software the guide has you install on your computer.
  I don't need the port forwarding to run TOR, I need it to run Vuze and a Tor relay – that is to route traffic through the TOR network & increase its effectiveness as an anonymizer of internet traffic.
Rightnow checking the tor relay error messages is the only way I can check if port forwarding is working.

---

### Post by bakegoodz on 2012-08-01
Sorry I can't help you more. Port forwarding is really easy. Now bittorrent over TOR is probably what is giving you complications. [https://blog.torproject.org/blog/bittorrent-over-tor-isnt-good-idea](https://blog.torproject.org/blog/bittorrent-over-tor-isnt-good-idea)

Wait a minute, you router 192.168.0.1 and your computer is set to 192.168.13.254? Unless your network is using a supernet, your going to have serious problems. And using a Supernet like: Netmask 255.255.240.0 and range 192.168.0.0 - 192.168.15.255 [http://en.wikipedia.org/wiki/Supernet](http://en.wikipedia.org/wiki/Supernet)
Consumer routers typically only use a Class C for local network, so only a range of 1-254 on the last dotted octet of the IP address. [http://en.wikipedia.org/wiki/Classful_network](http://en.wikipedia.org/wiki/Classful_network)



[IMG]http://i46.tinypic.com/262s5rq.jpg[/IMG]

---

### Post by Luddite Savant on 2012-08-02
Thanks BakedGoodz,  you've been very patient and helpful.
I'll check out your links and try somemore.

Cheers

---

