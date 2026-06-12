---
title: "Can I utilize two simultaneous internet connections?"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by heyzeusbrains on 2009-11-06
Tell me:

Is it possible to utilize two internet connections at once in Karmic?  I want to use my wireless (wlan0) for bittorrent downloads (Deluge), while simultaneously using my wired connection (eth0) for web browsing (Firefox).  Network Manager connects to both simultaneously but applications default to eth0.  Can I configure specific applications (such as Firefox and Deluge) to use one network and some the other using routing tables, proxy settings, or in any other way?

---

### Post by falconindy on 2009-11-06
What you have are two **LAN** connections, not internet connections. Splitting your traffic will solely be a semantic difference, as you won't see any noticeable difference in performance.

---

### Post by heyzeusbrains on 2009-11-06
falconindy:  Perhaps I am missing something... (am new to ubuntu / linux / networking).  I am connecting to two different networks.  I am using eth0 to go online via my own DSL account.  I am using wlan0 to go online via an unsecured wireless network in my area (not my own).    If I could figure out how to utilize both connections at once, I feel as if my bittorrent downloads would no longer slow my web browsing experience.  Am I suffering from a fundamental misconception about networking or is my theory plausible?

---

### Post by falconindy on 2009-11-07
Sure, it's plausible. I didn't realize you were connecting to two physically separate networks. Deluge will let you specify an interface for its connections. However, given that you're admitting to pirating someone else's network, I won't be giving you any more help.

---

### Post by heyzeusbrains on 2009-11-07
falconindy:  I didn't think an in-depth personal explanation would be necessary here, as I already stated I was connecting to an unsecured wireless network in my area, and wasn't expecting a holier-than-thou attitude.  Do you have to be a pirate to connect to a public wifi hotspot configured for open access?  Thanks anyway for your time.

---

### Post by Iowan on 2009-11-07
I suppose it depends whether it's connection configured for public access - or just a neighbor who hasn't secured their network. (My laptop insists on doing that - I need to turn off wireless to insure it connects via my wired network). The public access (hotspot) may not have come across in the first post... You could probably configure either iptable rules, or routing table rules to send connections different directions - I haven't tried it, but the theory sounds plausible.

---

### Post by heyzeusbrains on 2009-11-07
Iowan:  thanks for the reply.  I tried using iptables to mark packets routed through a specific port, then using ip rules to funnel the marked packets to an alternate table which specifies the default gateway that I want to use for bittorrent transfers (as detailed at [http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html)).  Then I tried setting the port in Deluge to match...  This did not work for me.  While I am learning, my understanding of advanced ip routing is still very limited. Everything I read seems oriented towards a server/client setup, and I'm not sure how much of it is applicable to a lone computer trying to juggle two internet connections.  I also tried to add my desired gateway as an additional host in the Deluge connection manager, but it will not connect (connect button is shaded out).  Connection manager will only connect via local host.  I know the Daemon features in Deluge have to do with server/client setup and I am not sure if I can use the connection manager just to specify the network interface I want to use, or how to do it.    Please, someone nudge me in the right direction.

---

### Post by heyzeusbrains on 2009-11-09
In Windows XP, I could select which applications are allowed to access the net - this could be done with even the basic windows firewall.  Does Ubuntu support application-specific access filtering through its built in firewall system (ip routing)?  I am trying to direct certain applications to an alternate routing table which will connect to the internet through a different network.

---

### Post by tamasrepus on 2009-11-09
From your description, you don't need iptables to accomplish what you want to do.

Your BitTorrent client has an option somewhere to bind to an interface. Here, enter the IP address that the wireless network gives you. All BitTorrent traffic will now go through the wireless.

Since your default gateway is still the wired connection, all other traffic (including web browsing) will continue to go through it.

This is identical to how you'd set this up on Windows. Linux iptables' does support per-application/program routing, but again, that's a level of complication that isn't needed here.

---

### Post by heyzeusbrains on 2009-11-09
tamasrepus:  thanks for the tip.  I cannot configure Deluge or qbittorrent bind to an interface.  Ktorrent has the option to specify the network interface device.  However after setting this to wlan0 and rebooting, ktorrent still wants to use eth0.  Finally... I can bind rtorrent to the network of my choice, however when bound to the wireless network, it is unable to grab the torrent file to begin the download (as long as the network on eth0 is connected).  Further assistance welcome.

---

### Post by tamasrepus on 2009-11-09
I'm very sure Deluge has an option to bind to an interface (Transmission does), but it may not be in the UI and only accessible by config file. Check the docs.

When it says "interface", it's actually asking for an IP address, not a network device name. You need to enter the IP address given to you by the wireless network.

---

### Post by heyzeusbrains on 2009-11-09
Still haven't figured out how to edit the config files to bind to a network in Transmission or Deluge.  I am still trying to search online documenation to figure out which config file I need to edit and its location.  With rTorrent, binding to a network is straightforward with the -b option.  My IP address on the wireless network is 192.168.0.101.  In terminal I type "rtorrent -b 192.168.0.101".  This starts up rTorrent with the message [Bind 192.168.0.101] at the bottom of the screen.  However, if the ethernet network on eth0 is connected, rTorrent cannot connect to the internet to download torrents.  Then if I disconnect eth0, rTorrent is suddennly able to connect.  And then if I again enable eth0, the connection is dropped and rTorrent is blocked.  (Note that when I use the -b option to bind rTorrent to the wireless network while both networks are connected, rTorrent is unable to use eth0, but is also blocked from connecting via wlan0.  Sorry to be repetitive but trying to state the situation clearly.)  Seemingly, the computer is just not capable of handling the two simultaneous connections.  But I know there has to be a way.

---

### Post by viper250 on 2009-11-09
what falconindy was trying to say is that unless you are using a public wifi access connecting to an unsecured network is classed as pirating by law enforcement agencies.
if you are just checking email or using an I.M. it does not cause a problem but downloading and using bittorrent on someone elses wireless can bog down their service and it can be easily traced leaving you at their mercy as far as lawsuits are concerned.
not to mention the fact that you could lose your computer if the law declares you a cyber criminal because of it.
please do not consider it a holier than thou attitude. we are here to help you even if it means pointing out when you perform an illegal activity.
 it is the hope to prevent you from getting into serious trouble

---

### Post by heyzeusbrains on 2009-11-10
Thanks, I appreciate you guys looking out for me.  I'll make sure to only connect to the wireless networks where I am authorized access.  Meanwhile, I'm still trying to figure this out.  [http://forums.freebsd.org/archive/index.php/t-3149.html](http://forums.freebsd.org/archive/index.php/t-3149.html)   Looks like they can do it with FreeBSD, why can't I do it with Ubuntu?  I may look back into ip table routing because binding the bt client to the interface isn't working for me.  From what I can figure out, the only way ip routing would work for my purpose is to create a personal local network, using one computer to route traffic coming from another computer to the two internet connections by marking the packets and using ip rules.  If I can run applications off the second networked computer and set them to use a certain port, then I can mark the packets coming through that port on the first computer, use ip rules to route them to a second routing table with an alternate default gateway.  As convoluted as that sounds it's the only solution I can conceive right now.  With a single computer set-up, I don't understand how marking packets that go from an application out through a certain port for alternate routing would be possible, since iptables wants a source network to be specified along with a port and protocol...

---

### Post by tamasrepus on 2009-11-12
Something I forgot to mention, you you use for each Internet connection are different. I.e. if you get an IP address from 192.168.0.0/255.255.255.0 (e.g. an address within the range 192.168.0.1-192.168.0.254), the other connection needs to have an IP address in a different subnet, like 10.0.0.0/255.255.255.0, or even 192.168.100.0/255.255.255.0. (If you don't understand what I said—look it up, it's fairly standard networking terminology)

I looked into this. For whatever reason, Deluge doesn't support binding to an interface (yet).

Transmission does, and I can verify because I used to use it in this way (with two internet connections, one DSL and one cable). I don't know if an option is in the UI, as I use it from the CLI with transmission-daemon/transmission-remote, but there is an option in ~/.config/transmission/settings.json.

I don't know why rtorrent doesn't work (I've never used it myself). You may want to check with them on why.

You're really not motivating people to help you when you start attacking Linux ("Ubuntu can't do this!") when people have already told you that you can and have given you specific instructions. It also doesn't help when there's a question of whether what you are doing is legal. Please keep that in mind.

Yes, you can use iptables, but as I said, from the description you gave you don't need it. If you're wanting to toss multiple machines and other operating systems into this and make it more complicated (without any actual guarantee of it actually working), go ahead, more power to you. You should read the Linux Advanced Routing & Traffic Control HOWTO, particularly the [Routing for multiple uplinks/providers section](http://lartc.org/howto/lartc.rpdb.multiple-links.html).

---

### Post by heyzeusbrains on 2009-11-15
tamasrepus: thanks for your continued assistance.  When I bind Transmission to the wireless network, the same things happens as with rTorrent - the eth0 connection seems to block it from working.  
(results from ip route show):
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.109  metric 2 
172.16.0.0/16 dev eth0  proto kernel  scope link  src 172.16.1.33  metric 1 
default via 172.16.0.1 dev eth0  proto static 
I changed the line in the transmission/settings.json file to read    "bind-address-ipv4": "192.168.0.109",
Now, Transmission will NOT use eth0, however as long as eth0 is connected, it cannot function via wlan0 either.  If I disconnect from eth0, it will immediately begin downloading, seeding, etc. via wlan0.

---

### Post by void09 on 2009-11-16
Use your default connection (the one with the default route) with the p2p client.

Use a proxy server for ordinary browsing. Make a static route that sends all traffic destined to the proxy through the other interface.

The you have split the traffic.

Or use static routes for services you use a lot. A lot of manual configuration...

---

### Post by heyzeusbrains on 2009-11-17
void09:    I am already using privoxy with tor for anonymous browsing, so I have firefox proxy configured to localhost port 8118.  I reconfigured privoxy to forward all traffic to 192.168.0.1, but firefox is unable to connect to the web.  I also tried 192.168.0.109 with the same result.  I don't understand what IP address I need to put in to get it to connect via the wireless network, or how to use a static route in conjunction with this.  I know how to add a static route with ip route add - I just don't understand what IP numbers to use for the ip range and the gateway.  See my 'ip route show' results above.

---

### Post by heyzeusbrains on 2009-11-18
I think my problem might be more fundamental... I can't even successfully change the default gateway.  Seems like no matter what I do, my computer will not use the network on wlan0 as long as eth0 is connected.

When I disconnect eth0, here is my ip route show:

192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.102  metric 2 
default via 192.168.0.1 dev wlan0  proto static 

At this point the wireless network is working great wiith all my applications.  Here is my ip route show after reconnecting eth0:

192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.102  metric 2 
169.254.0.0/16 dev eth0  scope link  metric 1000 
172.16.0.0/16 dev eth0  proto kernel  scope link  src 172.16.1.33  metric 1 
default via 172.16.0.1 dev eth0  proto static 

Then I type the following commands to change the default gateway:

sudo ip route del default via 172.16.0.1 dev eth0  proto static
sudo ip route add default via 192.168.0.1 dev wlan0  proto static

Now, here is my ip route show:

192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.102  metric 2 
169.254.0.0/16 dev eth0  scope link  metric 1000 
172.16.0.0/16 dev eth0  proto kernel  scope link  src 172.16.1.33  metric 1
default via 192.168.0.1 dev wlan0  proto static 

And what happens now?  Nothing is able to connect (pages stay loading indefinately).  However as soon as I disconnect eth0, everything works instantly through wlan0.

I also tried reversing the metric numbers (changed 192.168.0.0 to metric 1 and 172.16.0.0 to metric 2).  No effect.

What am I missing here?

---

### Post by heyzeusbrains on 2009-11-29
WELL thanks anyway guys.  After weeks of research and testing, in my final analysis a single Ubuntu linux system is not capable of utilizing two simultaneous internet connections for my purpose.  I was able to achieve what I wanted by creating a virtual machine to run the applications using the wireless network.  Aside from being memory intensive, this feels more like a work-around than a real solution to the original problem.

---

