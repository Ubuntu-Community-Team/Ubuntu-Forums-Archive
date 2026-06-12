---
title: "Need high-end Home Network information for setup."
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by irv on 2012-12-01
I know there are other posts out here on Home Networks, but what I am look for is some ideas about setting up a high end Network.
First, I know I need to replace my router. I am using a Linksys WRT54G which only allows me to run at 22 Mbps max on my wireless. I have a 40 Mbps connection, which I can get on the wire by not wireless. I am thinking about replacing it with a Asus RT-AC66U Dual Band wireless AC1750 Gigabit Router. The reason is to stream 1080 dpi videos over the wireless. I also like the idea of connecting a couple of USB drives to the router for Data sharing.
I see that with a firmware upgrade this router has a feature called AiCloud which allows me to access my home network over the Internet.
Now I know that there are others out here that have setup a home network so I am looking for some advice before I start this project. I want to do it right from the get-go. I have done other projects that I wished I had did more research on before starting, so I want to do this one right.
My home devices are as listed:
> 2 Nooks tablets
1 Asus Transformer Tablet.
1 Chromebook
1 Laptop
1 Roku box
All of the above are wireless.
1 Desktop
1 Server (It is a web server with it own IP address )
1 BlueRay Sony DVD with Netflix, Hulu Plus etc.
These devices are all on the wire.
I also have family that visits and they have cell phone, ipads etc, which will use my network.

Now I also know I will need to replace my wifi card in my laptop to use the full 40 Mbps. But any other ideas will be helpful. By the way, the 40 Mbps is only for the outside world, (the Internet), my inside network will be running much faster. And this router has a range of 178.5 and a throughput of 339.2. This is on the 5Ghz setting. On the 2.4Ghz it is lower.
I guess the only downside to this router is the price (around $200), and it runs on the hot side. At lease that's what I got from the reviews. 
Thank to all on this forum. 
[ATTACH]228031[/ATTACH]  [ATTACH]228032[/ATTACH]  [ATTACH]228033[/ATTACH]
[http://reviews.cnet.com/routers/asus-rt-ac66u-802/4505-3319_7-35406080.html]("http://reviews.cnet.com/routers/asus-rt-ac66u-802/4505-3319_7-35406080.html")
[http://www.amazon.com/RT-AC66U-Dual-Band-Wireless-AC1750-Gigabit-Router/dp/B008ABOJKS/ref=sr_1_1?ie=UTF8&qid=1354243788&sr=8-1&keywords=asus+rt-ac66u+router]("http://www.amazon.com/RT-AC66U-Dual-Band-Wireless-AC1750-Gigabit-Router/dp/B008ABOJKS/ref=sr_1_1?ie=UTF8&qid=1354243788&sr=8-1&keywords=asus+rt-ac66u+router")
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320115&Tpk=asus%20rt%20ac66u]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320115&Tpk=asus%20rt%20ac66u")

---

### Post by irv on 2013-01-01
I started this thread about 4 weeks ago, and I ended up doing something different. First I did purchase the Asus Router, but ended up sending it back. I had a few issues with it, which I will not go into here. The more I thought about it, my Linksys router is not really that bad. The only thing I really want is the  ability to plug in some USB drive and be able to access them from my network and over the Internet. Well, I came up with a solution and I can do it with a $20 piece of hardware.
I order a [URL="I started this thread about 4 weeks ago, and I ended up doing something different. First I did purchase the Asus Router, but ended up sending it back. I had a few issues with it, which I will not go into here. The more I thought about it, my Linksys router is not really that bad. The only thing I really want is the  ability to plug in some USB drive and be able to access them from my network and over the Internet. Well, I came up with a solution and I can do it with a $20 piece of hardware.
I order a Pogo P21. I scheduled for delivery in a couple of days. After I get it setup I will update this thread and let you know how things work out."][Pogo P21.]("http://www.amazon.com/gp/product/B005FNDJHS/ref=oh_details_o00_s00_i00")[/URL] It's scheduled for delivery in a couple of days. After I get it setup I will update this thread and let you know how things work out.

---

### Post by TheFu on 2013-01-01
Sorry I missed your post a few weeks ago.  Xmas got in the way.

A few statements.
* Wifi will never be a good way to use bandwidth. There will always be too many unknowns, mainly because you do not have complete control over the available bandwidth, the total number of devices and which channels are available unless you live at least 0.5 mi from your neighbors.  If you want a solid HiDef streaming solution, always choose wired over wireless.  Every device on a wifi network, even when not transmitting, approximately halves the available bandwidth.  Further, the slowest device will often set the max throughput available.  So if you have a single "B" wifi device, then all of them will be limited to 11Mbps before you start halving the bandwidth for each added device.  These are rough estimates from deploying wifi in corporate environments to over 1200 locations.  Just looking over your list, there is no way you will stream 1080p content without stuttering over any wifi with that number of devices connected. NO WAY.

* If you want a "high end" home router, look for something that runs DD-WRT, Tomato and/or OpenWRT.  These are maintained much more (while sometimes they suck for your specific model) than the commercial firmware releases.

* If you are here, I assume you have a Linux box somewhere on the network. For $99, you can build an Atom or AMD-E350 system that uses less than 20W of power, while still providing x86 and amd64 compatibility. Sure, you can use an Arm-based solution and these are cool, but all the Arm-based solutions have limitations that will bother you after a while.

* If you want to see interesting network designs, check out RateMyNetworkDiagram.com
I like this one: [http://www.ratemynetworkdiagram.com/?i=15442](http://www.ratemynetworkdiagram.com/?i=15442)  There are lots of interesting small network diagrams there that might give you more ideas.

* If using wired ethernet (I really like GigE over 100base-tx), isn't an option for your hidef media, we all don't have nice house setups, then consider using powerline networking for the most difficult locations. These can provide about 300Mbps bandwidth in the real world and with a GigE switch at the entertainment area, you can connect multiple devices to a single powerline bridge.  I've never tried this myself, but have followed the tech and read about real-world throughput.

* When looking for real-world solutions to a small network, [http://www.smallnetbuilder.com/](http://www.smallnetbuilder.com/) is a great site to start too.

I'd also encourage you to setup 2 or more different wifi networks. Just be certain that you don't use overlapping channels. For B and G, only channels 1, 6, and 11 should be used. All others overlap.  Put your "guests" on their own wifi network and firewall them off from the rest of your internal network.

So, here are my recommendations:
* GigE wired networking everywhere you can. If it is wired, it should be CAT5e/CAT6 and wired.
* Separate WiFi networks based on guests, and connection performance. Do not mix N-capable devices with slower G and B devices.
* Do not stream any hidef content over wifi. It never works out well.
* Limit the number of devices on any wifi network. Every device halves the theoretical max throughput. This is a rough estimate, but has proven to be fairly close to real world outcomes.
* Use DHCP reservations for your devices at the router to force static IPs and easy local DNS lookups.
* With a Linux "server", you can have a firewall, router, storage, proxy, all in the same machine. Leverage it.  Instead of using cheap storage, look into adding a DAS to your server where you can run Samba and NFS and have complete control over the file sharing on your network.  Prefer eSATA and SATA over all other connections.  USB3 would be next. USB2 should be avoided now as should firewire.  Firewire has too many security issues for any consideration as a storage bus.

* All servers/desktops will be happiest with an Intel PRO/1000 ethernet card. This assumes you need to update the NIC to get GigE performance. If not, and the current chips are providing 650+Mbps throughput, then be happy.  However, the Intel PRO/1000 is the standard and less than $30 each, so there isn't any reason when shopping NOT to buy the real Intel NICs.

Again, sorry that I'm late to reply and I'm happy that you found a solution that works for you today.

Also, I'm just some guy on the internet providing advice based on my background and understanding of your setup. Only you can decide what actually fits.

---

### Post by tgalati4 on 2013-01-01
Look on craigslist.org for used, business-grade routers.  Wire up as much as possible.  Any device with a plug needs a plug.  High-quality wiring (Gepco or Belden) and decent crimps plugged into a business-grade router will get you the speeds and reliability that you expect.  

Wireless is a convenience and really doesn't have the throughput to do high definition.  OK for music or standard-def youtube streaming.

A 16 or 24 channel, gigabit business-grade router with your wireless hung off of it will give you the bandwidth that you expect from all of your devices.

Remember your phones, tablets, laptops, roku/netflix dongles all split up the same wireless bandwidth.  That is why you need to wire up everything that can take a wire.

---

### Post by irv on 2013-01-01
TheFu, All I can say is WoW! Thanks for the post. I checked out the link you posted and read the complete post. I am a old retired IT guy who was in charge of our corp. Network, but only worked with wired networks. Never had anything to do with wireless. As you can see from my first post, I do have some of my devices on the wire where I can. Most of my wireless (Nooks, Chromebook etc) do not need a fast connection. My main laptop is very easy to put on the wire when needed. I do have a server on the wire and it is running Linux 10.04. 
[ATTACH]229450[/ATTACH]
I remote into it to do updates from my laptop, but the update are done over the wire. Only use my laptop for control.

I know what you are saying about USB2, but I am afraid I will be stuck with some devices only having USB2 ports.

Right now I have one device on the wire and one wireless for video, I might be making some changes on that soon. I am still moving things around. Will post when I am done and will mark solved.

---

### Post by irv on 2013-01-01
tgalati4, another good post. Thanks. Everything depends on how much my wife will let me spend. She is my biggest obstacle.
Thanks again

---

### Post by irv on 2013-01-04
> **irv said:**
> I started this thread about 4 weeks ago, and I ended up doing something different. First I did purchase the Asus Router, but ended up sending it back. I had a few issues with it, which I will not go into here. The more I thought about it, my Linksys router is not really that bad. The only thing I really want is the  ability to plug in some USB drive and be able to access them from my network and over the Internet. Well, I came up with a solution and I can do it with a $20 piece of hardware.
I order a [URL="I started this thread about 4 weeks ago, and I ended up doing something different. First I did purchase the Asus Router, but ended up sending it back. I had a few issues with it, which I will not go into here. The more I thought about it, my Linksys router is not really that bad. The only thing I really want is the  ability to plug in some USB drive and be able to access them from my network and over the Internet. Well, I came up with a solution and I can do it with a $20 piece of hardware.
I order a Pogo P21. I scheduled for delivery in a couple of days. After I get it setup I will update this thread and let you know how things work out."][Pogo P21.]("http://www.amazon.com/gp/product/B005FNDJHS/ref=oh_details_o00_s00_i00")[/URL] It's scheduled for delivery in a couple of days. After I get it setup I will update this thread and let you know how things work out.
OK, I got the pogoplug yesterday and got it hooked up. Only took a couple of minutes to to this. Right now I have two hard drives plugged into it and it works great. I can get to my files from anywhere I have an Internet connection. All I I have to do is login to my pogoplug account at my.pogoplug.com and There are all my files on the two drives I have plugged into it.
[ATTACH]229568[/ATTACH]

---

### Post by TheFu on 2013-01-04
> **irv said:**
> OK, I got the pogoplug yesterday and got it hooked up. Only took a couple of minutes to to this. Right now I have two hard drives plugged into it and it works great. I can get to my files from anywhere I have an Internet connection. All I I have to do is login to my pogoplug account at my.pogoplug.com and There are all my files on the two drives I have plugged into it.
[ATTACH]229568[/ATTACH]

I've never looked at pogoplug in much detail, but any service like that also means that at least 1 person and perhaps the entire staff can see all your shared files. It probably isn't a big deal, but might be a huge concern.

Any service that doesn't require you to open a port on YOUR router for access while traveling outside the network is either using insecure PnP (always disable this!!!!) or the device/software is opening the port through an automatic request that causes all routers with NAT and/or firewall to open the port for connections between their hardware AND their remote server.  This is the sort of trick that Napster learned in the 1990s which freaked out corporate security people.

I'm just saying that anything that is too easy probably has traded security for convenience. This is extremely common with lots of "online services" these days.

---

### Post by irv on 2013-01-06
> **TheFu said:**
> I've never looked at pogoplug in much detail, but any service like that also means that at least 1 person and perhaps the entire staff can see all your shared files. It probably isn't a big deal, but might be a huge concern.
Yes this could be an issue, but we are not talking plans for a new rocket here. I don't plan on keeping all the drive plugged in all the time, but only when I need to find something. I have files from back in the 70's. 
One thing about the pogoplug I did not like was it does not support my Linux format partitions ext4. That won't be a problem in my case because I don't have data on those partitions. I guess for $20 it still wasn't that bad of a deal. I didn't buy any cloud storage because I use Ubuntuone.
[ATTACH]229687[/ATTACH]

---

